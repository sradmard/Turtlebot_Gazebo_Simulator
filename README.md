# Turtlebot_Gazebo_Simulator
This is a repository for Turtlebot robot simulator in Gazebo simulation environment. 

In order to start with this simulator, first create a workspace, and an src folder within that workspace:
$ mkdir gaz_turtle_ws
$ cd gaz_turtle_ws
$ mkdir src
Then download the "Turtlebot_Gazebo_Simulator" mega package in the src folder:
$ cd src
$ git clone https://github.com/sradmard/Turtlebot_Gazebo_Simulator.git
Then within your workspace main folder compile the package:
$ cd ..
$ catkin_make
If catkin_make compiles without any error, then the package is properly installed and is ready. You just need to set up the environment correctly. In order to do that either type in the following command in each terminal, or add it to ~/.bashrc:
$ source ~/gaz_turtle_ws/devel/setup.bash

- Make sure the environment variables are set properly in each terminal (or add the export line to ~/.bashrc):
$ env | grep TURTLEBOT
$ export TURTLEBOT_GAZEBO_WORLD_FILE=/home/sina/catkin_ws/src/turtlebot_simulator/turtlebot_gazebo/worlds/empty.world
- After setting the environment, lunch turtlebot in an empty world, objects can be added to the environment through gazebo interface. 
$ roslaunch turtlebot_gazebo turtlebot_world.launch
- Sensory data can be accessed and visualized through rviz, as well as lunching a map in rviz. Follow the instruction here:
http://wiki.ros.org/turtlebot_gazebo/Tutorials/indigo/Make%20a%20map%20and%20navigate%20with%20it
- In order to move the robot around using keyboard, launch the keyboard control from turtlebot_teleop package:
$ roslaunch turtlebot_teleop keyboard_teleop.launch 


Here is a disceription on how this mega package was created:
- Download the following packages from source and place them in your catkin workspace src folder:
turtlebot_simulator meta package for indigo from the following link (this meta package includes turtlebot_gazebo, turtlebot_simulator, turtlebot_stage and turtlebot_stdr):
http://wiki.ros.org/turtlebot_gazebo
turtlebot meta package for indigo from the following link (it provides teleoperation capability). This meta package includes turtlebot_bringup package which is a dependency for turtlebot_gazebo package. In the package.xml file of turtlebot_bringup package, comment the line related to astra_launch package dependency (<!--<run_depend>astra_launch</run_depend>-->). It is for astra camera which is not necessary and you avoid the headache of installing its ros packages. 
http://wiki.ros.org/turtlebot
and then add turtlebot_msgs package for indigo to turtlebot meta package:
http://wiki.ros.org/turtlebot_msgs
you also need turtlebot_apps meta package for indigo from the following link as it provides some of the dependencies.:
http://wiki.ros.org/turtlebot_apps
check the dependencies for all packages by the follwoing command:
$ rospack depends1 turtlebot_gazebo
Then within your catkin workspace directory type:
$ catkin_make
