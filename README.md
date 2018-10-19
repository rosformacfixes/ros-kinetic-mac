# ros-kinetic-mac

This is for the desktop-full install of ros kinetic.

To complete this installation, follow http://wiki.ros.org/kinetic/Installation/OSX/Homebrew/Source up to the point where you see this command:

```
rosinstall_generator desktop_full --rosdistro kinetic --deps --wet-only --tar > kinetic-desktop-full-wet.rosinstall
```

Instead, copy the kinetic-desktop-full-wet.rosinstall from this folder into ~/ros_catkin_ws/ instead.

Then, continue until this point:

```
./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release
```

And use the following instead:

```
brew install boost-python
brew install boost
cd /usr/local/lib/
ln -s libboost_python27-mt.a libboost_python-mt.a
ln -s libboost_python27-mt.dylib libboost_python-mt.dylib
ln -s libboost_python27.a libboost_python.a
ln -s libboost_python27.dylib libboost_python.dylib
cd ~/ros_catkin_ws/
rm -Rf ~/ros_catkin_ws/src/opencv*
brew install opencv3
./src/catkin/bin/catkin_make_isolated --install -DCMAKE_BUILD_TYPE=Release -DCMAKE_FIND_FRAMEWORK=LAST
```

Whenever it says you have an issue with a package/library/etc., check if it is a python package/library or a brew package and do either of the following accordingly.

Brew packages:

```
brew install package
```

Python packages:

```
sudo -H pip install package
```

If you have any troubles with any needed packages, be sure to try this:

```
brew unlink package && brew relink package
```

Additionally, if you get this message from any package after installation

```
To force the link and delete this file, do:
brew link --overwrite formula_name"
```

Do execute the overwrite command as long as you won't have any issue with other things. It may be necessary.

I won't get any emails/notifications if you have any issues. So, if you have any issues, contact me via Discord: Bob Jones#5612
