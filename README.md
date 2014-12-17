ONOS SPRING-OPEN CLI
==============================

This repository contains the CLI for the Segment Routing usecase running on ONOS.
The CLI used for this project is a modified version of the CLI originally submitted to open-source here: 
https://github.com/opendaylight/net-virt-platform/tree/master/cli

Follow the instructions for installing and using the CLI here:
https://wiki.onosproject.org/display/ONOS/Installation+Guide#InstallationGuide-CLIforSPRING-OPEN


# Building #
Install prerequisites.  You'll just need a basic functioning build
environment plus a few build-time dependencies.  On Ubuntu, you can
run:

    sudo apt-get install unzip python-dev python-virtualenv \
    	 git build-essential

To build the cli:

1. Clone from repository
2. cd spring-open-cli
3. `./setup.sh`

# Running #

## Sdncon ##
To run the ONOS SR cli, you need to be running a working
instance of sdncon.  The setup script will have created
a python virtualenv for you to make it easy to run the python
components.  You must first activate the virtualenv in your current
shell by running

    source ./workspace/ve/bin/activate

Now you can easily run any of the python commands.

The make targets `start-sdncon` will
automatically start a local copy of sdncon.  There are
corresponding stop commands as well.  These commands require an
activated virtualenv.  If you run

    make stop-sdncon start-sdncon

This will stop any existing sdncon, reset their
databases to zero, and start a new sdncon with a fresh database.  The
output from these commands will go to a log file in your
`workspace/ve/logs` directory.

## Controller ##

ONOS SR cli and sdncon runs ontop of ONOS SDN controller platform. Follow the 
ONOS SDN controller installation instructions to launch the controller
<TODO: Link to ONOS repo> 

## CLI ##

The CLI depends on a running instance of sdncon.  To run the CLI, just
run it from the command line from the CLI directory:

    ./cli.py
    OR
    ./cli.py --controller <IP>[:<port>]

The CLI has online help and tab completion on its commands.

# Eclipse environment #

1) At the shell, create the .project files with `make eclipse`
% make eclipse

2) In Eclipse, create a new workspace:
Click File -> Switch WorkSpace -> Other and then enter the name of
the new workspace, e.g. "Workspace.net-virt-platform"

3) Once in the new workspace, import all of the eclipse projects
Click File -> Import -> General -> Existing Projects into Workspace
-> Next in the "Select Root Directory" dialog, type in or navigate
to your checkout of the ONOS SR CLI base directory, e.g.,
~/git/onos-sr-cli .

Eclipse should automatically find two eclipse projects: 
* cli
* sdncon
Make sure they are all checked (the default) and click "Finish"

If you are looking to do python development, it is recommended that
you install the Eclipse "pydev" modules, as documented at http://pydev.org.
