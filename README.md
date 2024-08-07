# Example robot URDFs (RoahmLab fork)

[![pipeline status](https://gitlab.laas.fr/gepetto/example-robot-data/badges/master/pipeline.svg)](https://gitlab.laas.fr/gepetto/example-robot-data/-/commits/master)
[![conde version](https://img.shields.io/conda/vn/conda-forge/example-robot-data.svg)](https://anaconda.org/conda-forge/example-robot-data)
[![conde download](https://anaconda.org/conda-forge/example-robot-data/badges/downloads.svg)](https://anaconda.org/conda-forge/example-robot-data)
[![PyPI version](https://badge.fury.io/py/example-robot-data.svg)](https://badge.fury.io/py/example-robot-data)
[![pre-commit.ci status](https://results.pre-commit.ci/badge/github/gepetto/example-robot-data/master.svg)](https://results.pre-commit.ci/latest/github/gepetto/example-robot-data/master)
[![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/psf/black)


This repository includes a set of robot descriptions that are aimed to be used in benchmarking, unit-tests, teachings,
tutorials or show-cases. These source files do not intend to substitute their original repositories.

## RoahmLab Modification

We add a Digit-v3 from Agility Robotics to this repository. In order to load the robot, we have to modify `python/example_robot_data/robots_loader.py`, where we add a new class `DigitLoader` and a new index `"digit": DigitLoader` in the dictionary `ROBOTS`.

If you already installed the original `example-robot-data` repository through conda (by following the procedures in the next section), we suggest you manually apply the changes according to the following procedure:
1. The urdf and the meshes should be stored in `~/miniconda3/share/example-robot-data/robots`. Copy the folder `robots/digit_description` in this repository to location `~/miniconda3/share/example-robot-data/robots`, together with other robot descriptions.
2. The python robot loader should be stored in `~/miniconda3/lib/python3.12/site-packages/example_robot_data/robots_loader.py`. Add the changes in `python/example_robot_data/robots_loader.py` of this repository to `~/miniconda3/lib/python3.12/site-packages/example_robot_data/robots_loader.py` (new class `DigitLoader` and new index `"digit": DigitLoader` in the dictionary `ROBOTS`).

Then you should be able to import Digit in python really easily:
```
import example_robot_data as erd
robot = erd.load('digit')
```

## :penguin: Installation

### :package: From Debian / Ubuntu packages, with [robotpkg](http://robotpkg.openrobots.org)

1. If you have never added robotpkg's software repository, [do it now](http://robotpkg.openrobots.org/debian.html):
   ```bash
   sudo tee /etc/apt/sources.list.d/robotpkg.list <<EOF
   deb [arch=amd64] http://robotpkg.openrobots.org/packages/debian/pub $(lsb_release -sc) robotpkg
   EOF

   curl http://robotpkg.openrobots.org/packages/debian/robotpkg.key | sudo apt-key add -
   sudo apt update
   ```

2. installation of example-robot-data and its python utils:
   ```bash
   sudo apt install robotpkg-py3\*-example-robot-data
   ```

### :snake: From <img src="https://s3.amazonaws.com/conda-dev/conda_logo.svg" height="18">

As simple as that:
```bash
   conda install example-robot-data -c conda-forge
```

### :turtle: With ROS

Just clone it (with `--recursive`) into a catkin workspace.

### :file_folder: From source

Clone it (with `--recursive`), create a `build` directory inside, and:
```bash
cmake .. && make && make install
```

## :robot: Show a robot with [gepetto-gui](https://github.com/gepetto/gepetto-viewer-corba)

`python -m example_robot_data -h` to list available robots.

## :copyright: Credits

### :writing_hand: Written by

- [Carlos Mastalli](https://cmastalli.github.io/), Heriot-Watt University :uk:
- [Guilhem Saurel](https://github.com/nim65s), LAAS-CNRS :fr:

### :construction_worker: With contributions from

- [Justin Carpentier](https://jcarpent.github.io/), INRIA :fr:
- [Pierre Fernbach](https://pfernbach.github.io/), LAAS-CNRS :fr:
- [Florent Lamiraux](https://gepettoweb.laas.fr/index.php/Members/FlorentLamiraux), LAAS-CNRS :fr:
- [Wolfgang Merkt](http://www.wolfgangmerkt.com/research/), University of Oxford :uk:
- [Josep Martí Saumell](https://www.iri.upc.edu/staff/jmarti), IRI: CSIC-UPC :es:
- [Louis Montaut](https://lmontaut.github.io/), INRIA :fr:, CTU :czech_republic:
- [Sergi Martinez](https://www.romilab.org/team/sergi-martinez), Heriot-Watt University :uk:
