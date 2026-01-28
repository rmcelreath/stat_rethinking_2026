# Setting up the repository

## Get a python package & environment manager

First, you will need to download a python package manager. Because we're working with scientific python packages that require non-python dependencies, we can't use `uv` (which is the standard we usually recommend). A classical alternative to that is using `conda` - and most of the installation instructions out there will typically recommend using it.

However, the thing with conda is that it lives in its own ecosystem and outside of some of the standardization efforts that have been taking place in Python ecosystem. A better alternative exists - `pixi`. It's compatible with `uv` and `pyproject.toml` while seamlessly supporting packages that have non-python dependencies.

So, as a first thing, head to https://pixi.prefix.dev/latest/installation/ and install `pixi`.

## Creating the environment

This repository includes a `pyproject.toml` file that specifies various packages we want to have available. Go, take a look at it. This is where we can make edits to specify additional dependencies. 

We also have a `pixi.lock` file - take a look at it, too. This one isn't meant for humans to read; instead, it stores exact information of packages and versions that satisfy the dependencies listed in the `pyproject.toml` file. `pixi.lock` file helps us ensure that all of us are working off exact same functionality.

The first time you're setting up, you want to get pixi to recreate the environment using the information in the lock file. You do that by running a command in terminal `pixi install`.

You should see that a folder `.pixi` was created. This is where the python executable and all dependencies are stored (e.g. python path is `.pixi/envs/default/bin/python`). If you ever feel like you messed up the environment, all you have to do is delete the `.pixi` folder and recreate it!

## Activating the environment

OK, we're almost done. We have the environment ready, now we just need to activate it. To activate it in the terminal, you want to run `pixi shell`. You'll see the name of the environment (stat_rethinking_2026) appearing as a prefix in your terminal.

Now, we also want to make sure Cursor recognizes it:

* First, hit Cmd+Shift+P to open the command palette, and find command "Python: Select interpreter". You should see the path to the environment we just created in the recommendations list, but if you don't, you can also enter it yourself (`.pixi/envs/default/bin/python`).

* Next, let's create a sample Jupyter notebook and make sure it can detect the environment, too. Use the "Create: Jupyter Notebook" command from the pallete. In the notebook, hit "Select Kernel" -> "Python Environments", and you should see "default" shown as the recommended option with the right python path. Select it.

* As a final test, run `import pymc` command in the notebook and confirm it runs successfully (it will take up to one minute the first time - it's normal)

Congrats, you're done!



