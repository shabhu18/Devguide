# Visual Studio Code IDE (VSCode)

[Visual Studio Code](https://code.visualstudio.com/) is a powerful cross-platform source code editor/IDE that can be used for PX4 development on Linux 18.04 LTS and macOS (Windows support coming soon).

> **Note** VSCode works on Ubuntu 18.04 configured with the [normal PX4 SITL/NuttX development environment](../setup/dev_env_linux_ubuntu.md). Ubuntu 16.04 allows you to build but not debug targets.

There are a number of reasons to use VSCode for PX4 development:

- Getting setup *really* only takes a few minutes.
- A rich extension ecosystem that enables a huge range of tools needed for PX4 development: C/C++ (with solid *cmake* integration), *Python*, *Jinja2*, ROS messages, and even UAVCAN dsdl.
- Excellent Github integration.

This topic explains how to setup the IDE and start developing.

> **Note** There are other powerful IDEs, but they typically take more effort to integrate with PX4. With *VScode*, configuration is stored in the PX4/Firmware tree ([Firmware/.vscode](https://github.com/PX4/Firmware/tree/master/.vscode)) so the setup process is as simple as adding the project folder.

## Preconditions

You must already have installed the command line [PX4 developer environment](../setup/dev_env.md) for your platform and downloaded the *Firmware* source code repo.

## Installation & Setup

1. [Download and install VSCode](https://code.visualstudio.com/) (you will be offered the correct version for your OS).
2. Open VSCode and add the PX4 source code:
    
   - Select *Open folder ...* option on the welcome page (or using the menu: **File > Open Folder**): ![Open Folder](../../assets/vscode/welcome_open_folder.jpg)
   - A file selection dialog will appear. Select the PX4 **Firmware** directory and then press **OK**.
    
    The project files and configuration will then load into *VSCode*.

3. Press **Install All** on the *This workspace has extension recommendations* prompt (this will appear on the bottom right of the IDE). ![Install extensions](../../assets/vscode/prompt_install_extensions.jpg)
    
    VSCode will open the *Extensions* panel on the left hand side so you can watch the progress of installation.
    
    ![PX4 loaded into VSCode Explorer](../../assets/vscode/installing_extensions.jpg)

4. A number of notifications/prompts may appear in the bottom right corner
    
    > **Tip** If the prompts disappear, click the little "alarm" icon on the right of the bottom blue bar.

- If prompted to install a new version of *cmake*: 
   - Say **No** (the right version is installed with the [PX4 developer environment](../setup/dev_env.md)).
- If prompted to sign into *github.com* and add your credentials: 
   - This is up to you! It provides a deep integration between Github and the IDE, which may simplify your workflow.
- Other prompts are optional, and may be installed if they seem useful. <!-- perhaps add screenshot of these prompts -->

## Building PX4 {#building}

To build:

1. Select your build target ("cmake build config"): 
   - The current *cmake build target* is shown on the blue *config* bar at the bottom (if this is already your desired target, skip to next step). ![Select Cmake build target](../../assets/vscode/cmake_build_config.jpg)
   - Click the target on the config bar to display other options, and select the one you want (this will replace any selected target).
   - *Cmake* will then configure your project (see notification in bottom right). ![Cmake config project](../../assets/vscode/cmake_configuring_project.jpg)
   - Wait until configuration completes. When this is done the notification will disappear and you'll be shown the build location: ![Cmake config project](../../assets/vscode/cmake_configuring_project_done.jpg).
2. You can then kick off a build from the config bar (select either **Build** or **Debug**). ![Run debug or build](../../assets/vscode/run_debug_build.jpg)

After building at least once you can now use [code completion](#code completion) and other *VSCode* features.

## Debugging PX4 {#debugging_sitl}

To debug PX4 on SITL:

1. Select the debug icon on the sidebar (marked in red) to display the debug panel. ![Run debug](../../assets/vscode/vscode_debug.jpg)

2. Then choose your debug target (e.g. *Debug SITL (Gazebo Iris)*) from the top bar debug dropdown (purple box).
    
    > **Note** The debug targets that are offered (purple box) match your build target (yellow box on the bottom bar). For example, to debug SITL targets, your build target must include SITL.

3. Start debugging by clicking the debug "play" arrow (next to the debug target in the top bar - pink box).

While debugging you can set breakpoints, step over code, and otherwise develop as normal.

## Code Completion {#code completion}

In order for the code completion to work (and other IntelliSense magic) you need an active configuration and to have [built the code](#building).

Once that is done you don't need to do anything else; the toolchain will automatically offer you symbols as you type.

![IntelliSense](../../assets/vscode/vscode_intellisense.jpg)