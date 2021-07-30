## Using-SLAM-map-to-launch-the-navigation 
https://emanual.robotis.com/docs/en/platform/turtlebot3/nav_simulation/
 
# 1- Launch Simulation World
   Terminate all applications with Ctrl + C that were launced in the previous sections.
 
   In the previous SLAM section, TurtleBot3 World is used to creat a map. The same Gazebo environment will be used for Navigation.
 
   Please use the proper keyword among burger, waffle, waffle_pi for the TURTLEBOT3_MODEL parameter.
 
        $ export TURTLEBOT3_MODEL=burger
        $ roslaunch turtlebot3_gazebo turtlebot3_world.launch
 
# 2- Run Navigation Node
 Open a new terminal from Remote PC with Ctrl + Alt + T and run the Navigation node.
 
    $ export TURTLEBOT3_MODEL=burger
    $ roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=$HOME/map.yaml
 
# 3- Estimate Initial Pose
   Initial Pose Estimation must be performed before running the Navigation as this process initializes the AMCL parameters that are critical in 
   Navigation. TurtleBot3 has to be correctly located on the map with the LDS sensor data that neatly overlaps the displayed map.
 
1.  Click the 2D Pose Estimate button in the RViz menu.
2.  Click on the map where the actual robot is located and drag the large green arrow toward the direction where the robot is facing.
 
3.  Repeat step 1 and 2 until the LDS sensor data is overlayed on the saved map.
 
4.  Launch keyboard teleoperation node to precisely locate the robot on the map.
 
        $ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
 
5. Move the robot back and forth a bit to collect the surrounding environment information and narrow down the estimated location of the TurtleBot3 on the 
   map which is displayed with tiny green arrows.
5.  Terminate the keyboard teleoperation node by entering Ctrl + C to the teleop node terminal in order to prevent different cmd_vel values are published 
    from multiple nodes during Navigation.
 
# 4- Set Navigation Goal
1. Click the 2D Nav Goal button in the RViz menu.
2.  Click on the map to set the destination of the robot and drag the green arrow toward the direction where the robot will be facing.
 
*  This green arrow is a marker that can specify the destination of the robot.
 
*  The root of the arrow is x, y coordinate of the destination, and the angle θ is determined by the orientation of the arrow.

*  As soon as x, y, θ are set, TurtleBot3 will start moving to the destination immediately.
