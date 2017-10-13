# deep-rl-docker :whale: :robot:
Docker image with OpenAI Gym, Baselines and Roboschool, utilizing TensorFlow and JupyterLab.

![Roboschool](https://github.com/eric-heiden/deep-rl-docker/blob/doc/roboschool.png?raw=true)

## Build
CPU version:
```
docker build -f Dockerfile -t uscresl/deep-rl-docker:tf1.3.0-gym0.9.3-py3 .
```

GPU version:
```
docker build -f Dockerfile.gpu -t uscresl/deep-rl-docker:tf1.3.0-gym0.9.3-gpu-py3 .
```

## Run
Execute `run.sh` or `run_gpu.sh`.

*All RL-related dependencies (Roboschool, Gym, etc.) are available from within the python3 environment.*

## Save changes
Commit changes made to the container (e.g. installations, file changes inside the container and not a shared volume) via
```
docker commit $CONTAINER
```
Where `$CONTAINER` is the ID of the docker container.

## Resume
Start and reattach an existing docker container via
```
docker start  $CONTAINER
docker attach $CONTAINER
```
Where `$CONTAINER` is the ID of the docker container. Issue `docker ps` to see all installed containers and their ID's.

## Examples
Here are some cool demos to run:

### Roboschool
```
vglrun python3 $ROBOSCHOOL_PATH/agent_zoo/demo_race1.py
```
```
vglrun python3 $ROBOSCHOOL_PATH/agent_zoo/demo_keyboard_humanoid1.py
```

### OpenAI Gym (from the [OpenAI blog post on DQN](https://blog.openai.com/openai-baselines-dqn/))
```
# Train model and save the results to cartpole_model.pkl
python3 -m baselines.deepq.experiments.train_cartpole
# Load the model saved in cartpole_model.pkl and visualize the learned policy
python3 -m baselines.deepq.experiments.enjoy_cartpole
```

## TODO
* Avoid privileged mode (su access) when running a container
* Fix Roboschool, Baselines dependency to specific GitHub-commit(?)
