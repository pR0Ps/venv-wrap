# venv-wrap
`venv-wrap` provides per-program virtual environments without making it hard to
run them.

## Details
This directory holds all the Python virtual environments that are required for
certain programs. This makes sure that each one has the correct Python version
as well as the libraries they need.

The name of the command to run needs to match the name of the virtual
environment as well as the name of the runner script. Symlinks also work.

For example, a program called "foobar" that requires python2 and provides `foo`
and `bar` commands:

### Installing
```
# Download to a directory
git clone <this project URL> ~/opt/python

# Create the venv and install foobar
virtualenv foobar -p python2
source foobar/bin/activate
pip install foobar
deactivate

# Create a link to the venv for the foo and bar commands
# NOTE: skip this step if the command has the same name as the venv
ln -s foobar foo
ln -s foobar bar

# Add the runner scripts to path with the correct names
cd ~/bin
ln -s ~/opt/venv-wrap foo
ln -s ~/opt/venv-wrap bar
```

Running:
```
foo --help
bar --help
```

The correct virtualenv will be activated and the command will be run.

## License

Licensed under the [Mozilla Public License, version 2.0](https://www.mozilla.org/en-US/MPL/2.0)
