# Cartographer

[![Ubuntu 22.04 Build Status](https://github.com/cartographer-project/cartographer/actions/workflows/ci-jammy.yaml/badge.svg)](https://github.com/cartographer-project/cartographer/actions/workflows/ci-jammy.yaml)
[![Ubuntu 20.04 Build Status](https://github.com/cartographer-project/cartographer/actions/workflows/ci-focal.yaml/badge.svg)](https://github.com/cartographer-project/cartographer/actions/workflows/ci-focal.yaml)
[![Ubuntu 18.04 Build Status](https://github.com/cartographer-project/cartographer/actions/workflows/ci-bionic.yaml/badge.svg)](https://github.com/cartographer-project/cartographer/actions/workflows/ci-bionic.yaml)
[![Debian Bullseye Build Status](https://github.com/cartographer-project/cartographer/actions/workflows/ci-bullseye.yaml/badge.svg)](https://github.com/cartographer-project/cartographer/actions/workflows/ci-bullseye.yaml)
[![Debian Buster Build Status](https://github.com/cartographer-project/cartographer/actions/workflows/ci-buster.yaml/badge.svg)](https://github.com/cartographer-project/cartographer/actions/workflows/ci-buster.yaml)
[![Documentation Status](https://readthedocs.org/projects/google-cartographer/badge/?version=latest)](https://google-cartographer.readthedocs.io/en/latest/?badge=latest)
[![Apache 2 license.](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://github.com/cartographer-project/cartographer/blob/master/LICENSE)

## Purpose

[Cartographer](https://github.com/cartographer-project/cartographer) is
a system that provides real-time simultaneous localization and mapping
([SLAM](https://en.wikipedia.org/wiki/Simultaneous_localization_and_mapping))
in 2D and 3D across multiple platforms and sensor configurations.

[![Cartographer 3D SLAM Demo](https://j.gifs.com/wp3BJM.gif)](https://youtu.be/DM0dpHLhtX0)

## A Note for ROS Users

**Cartographer is no longer actively maintained.** On rare occasions
critical pull requests may be merged, but no new development is
currently taking place, including issue response. If you are installing
Cartographer in ROS 1 / ROS 2 using a binary package that package is a
fork of this repository. The ROS fork of Cartographer is only maintained
in a limited capacity. No new development takes place on this fork, but
pull requests may be merged at the maintainers' discretion.

The ROS fork of Cartographer, and the ROS wrapper library, can be found
at these locations:

-   [Cartographer Fork](https://github.com/ros2/cartographer)
-   [Cartographer ROS](https://github.com/ros2/cartographer_ros)

Additional discussion can be found in [this ROS Discourse
thread](https://discourse.ros.org/t/rolling-and-soon-humble-release-of-both-cartographer-and-cartographer-ros-v2-and-call-for-testing/25137).

## Getting started

-   Learn to use Cartographer at [our Read the Docs
    site](https://google-cartographer.readthedocs.io).
-   You can ask a question by [creating an
    issue](https://github.com/cartographer-project/cartographer_ros/issues/new?labels=question).

## Installation

```sh
# Dependencies
sudo apt update
sudo apt dist-upgrade
sudo apt install -y \
    clang \
    cmake \
    g++ \
    git \
    google-mock \
    libboost-all-dev \
    libcairo2-dev \
    libceres-dev \
    libcurl4-openssl-dev \
    libeigen3-dev \
    libgflags-dev \
    libgoogle-glog-dev \
    liblua5.2-dev \
    libsuitesparse-dev \
    lsb-release \
    ninja-build \
    python3-sphinx \
    stow
# JUST FOR Ubuntu 20.04 LTS (Focal)
sudo apt install -y libgmock-dev protobuf-compiler

# Build and install Cartographer.
cd cartographer
mkdir build
cd build
cmake .. -G Ninja
ninja
CTEST_OUTPUT_ON_FAILURE=1 ninja test
sudo ninja install
```

**Note:** you may need to comment the documentation generation if the Ninja
command fails.
```sh
sousarbarb97@exodus:~/srrg_ros1_ws/src/cartographer$ git diff CMakeLists.txt
diff --git a/CMakeLists.txt b/CMakeLists.txt
index ef2fcb3..2782101 100644
--- a/CMakeLists.txt
+++ b/CMakeLists.txt
@@ -63,10 +63,10 @@ else()
 endif()

 # Only build the documentation if we can find Sphinx.
-find_package(Sphinx)
-if(SPHINX_FOUND)
-  add_subdirectory("docs")
-endif()
+#find_package(Sphinx)
+#if(SPHINX_FOUND)
+#  add_subdirectory("docs")
+#endif()

 # Install catkin package.xml
 install(FILES package.xml DESTINATION share/cartographer)
```

See
[https://google-cartographer.readthedocs.io/en/latest/index.html#getting-started-without-ros](https://google-cartographer.readthedocs.io/en/latest/index.html#getting-started-without-ros)
for the official instructions on how to build and install Cartographer.

## Contributing

You can find information about contributing to Cartographer at [our
Contribution
page](https://github.com/cartographer-project/cartographer/blob/master/CONTRIBUTING.md).

## Open house slide archive

In the past there had been regular open-for-all meetings to discuss
progress and plans for Cartographer. Slides of these Cartographer Open
House meetings are listed below.

-   March 14, 2019:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/190314/slides.pdf)
-   February 21, 2019:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/190221/slides.pdf)
-   January 17, 2019:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/190117/slides.pdf)
-   November 22, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/181122/slides.pdf)
-   October 25, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/181025/slides.pdf)
-   September 13, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180913/slides.pdf)
-   August 16, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180816/slides.pdf)
-   August 2, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180802/slides.pdf)
-   July 5, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180705/slides.pdf)
-   June 21, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180621/slides.pdf)
-   June 7, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180607/slides.pdf)
-   May 24, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180524/slides.pdf)
-   May 3, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180503/slides.pdf)
-   March 29, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180329/slides.pdf)
-   February 22, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180222/slides.pdf)
-   February 8, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180208/slides.pdf)
-   January 18, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180125/slides.pdf)
-   January 11, 2018:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/180111/slides.pdf)
-   December 7, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/171207/slides.pdf)
-   November 23, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/171123/slides.pdf)
-   November 9, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/171109/slides.pdf)
-   October 26, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/171026/slides.pdf)
-   October 12, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/171012/slides.pdf)
-   September 14, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/170914/slides.pdf)
-   August 17, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/170817/slides.pdf)
-   July 20, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/170720/slides.pdf)
-   July 6, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/170706/slides.pdf)
-   June 22, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/170622/sildes.pdf)
-   June 8, 2017:
    [Slides](https://storage.googleapis.com/cartographer-public-data/cartographer-open-house/170608/slides.pdf)
