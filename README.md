# Installation Guide for wlroots and TinyWL on Ubuntu 24.04

This guide provides step-by-step instructions to install the necessary build tools, dependencies, and wlroots, as well as how to build and run TinyWL on a clean Ubuntu 24.04 system.

## Prerequisites

Ensure you have administrative privileges to install packages using sudo and you have clean Ubuntu 24.04 installation.

## Step 1: Install Build Tools

Install essential build tools and utilities required for compiling wlroots and related dependencies.

- sudo apt install git
- sudo apt install gitk
- sudo apt install cmake
- sudo apt install build-essential
- sudo apt install pkg-config
- sudo apt install libtool automake autoconf


## Step 2: Install wlroots Dependencies

Update the package index and install the core dependencies for wlroots.

- sudo apt update
- sudo apt install meson
- sudo apt install libwayland-dev
- sudo apt install wayland-protocols
- sudo apt install libegl1-mesa-dev libgles2-mesa-dev
- sudo apt install libvulkan-dev
- sudo apt install glslang-tools
- sudo apt install libdrm-dev
- sudo apt install libgbm-dev
- sudo apt install libinput-dev
- sudo apt install libxkbcommon-dev
- sudo apt install libudev-dev
- sudo apt install libpixman-1-dev
- sudo apt install libseat-dev
- sudo apt install hwdata
- sudo apt install libdisplay-info-dev
- sudo apt install libliftoff-dev


## Step 3: Install wlroots X11 Support Dependencies

Install additional dependencies to enable X11 support for wlroots.

- sudo apt install xwayland
- sudo apt install libxcb1-dev
- sudo apt install libxcb-render-util0-dev
- sudo apt install libxcb-icccm4-dev libxcb-ewmh-dev


## Step 4: Install libxcb-errors

Install dependencies and build libxcb-errors from source.

- sudo apt install xutils-dev
- sudo apt install xcb-proto
- cd ~
- git clone --recurse-submodules https://gitlab.freedesktop.org/xorg/lib/libxcb-errors.git
- cd libxcb-errors/
- ./autogen.sh
- ./configure
- make
- sudo make install


## Step 5: Build and Install wlroots

Install additional dependencies, clone the wlroots repository, and build version 0.17.0. We switch to version 0.17.0 because there are issues with building higher versions on Ubuntu 24.04.

- sudo apt install libxcb-composite0-dev
- sudo apt install libxcb-res0-dev
- sudo apt install libxcb-dri3-dev
- sudo apt install libxcb-dri2-0-dev
- sudo apt install libxcb-present-dev
- sudo apt install libxcb-shm0-dev
- sudo apt install libxcb-xinput-dev
- sudo apt install libcairo2-dev

- cd ~
- git clone --recurse-submodules https://gitlab.freedesktop.org/wlroots/wlroots.git
- cd wlroots/
- git checkout 0.17.0
- meson setup build/
- ninja -C build/
- sudo ninja -C build/ install


## Step 6: Run TinyWL

Navigate to the TinyWL build directory and run the TinyWL compositor.

- cd ~/wlroots/build/tinywl/
- ./tinywl

While TinyWL is running, open a new terminal window or tab and set the Wayland display environment variable to test the compositor with a sample application (e.g., GNOME Calculator).

- export WAYLAND_DISPLAY=wayland-1
- gnome-calculator

## Notes

- Ensure all commands are executed in the order provided to avoid missing dependencies.
- If you encounter issues, verify that all packages are installed correctly and that the system is up to date.
- For further details on wlroots, visit the wlroots GitLab repository.








