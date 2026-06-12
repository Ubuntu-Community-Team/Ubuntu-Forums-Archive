---
title: "ROS lost"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by rbengr on 2015-01-31
Hi,

A few days ago I installed the standard ROS download into 14.04.  Today I tried to find it.  Does Ubuntu install such packages in a default location?

Thanks

---

### Post by ajgreeny on 2015-01-31
I am not certain what ROS is, nor did you say how you installed it, but if you used the normal apt-get commands, or synaptic or software-center, you should be able to find the executable, if it is called ros, with command ```
which ros
``` or use ```
dpkg -L <packagename>
```That will list every file added to your system by installation of the package.

---

### Post by rbengr on 2015-01-31
Thanks

---

### Post by rbengr on 2015-01-31
Thanks.  I located the files.  Here are the terminal results:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/ros-indigo-desktop-full
/usr/share/doc/ros-indigo-desktop-full/changelog.Debian.gz
/opt
/opt/ros
/opt/ros/indigo
/opt/ros/indigo/share
/opt/ros/indigo/share/desktop_full
/opt/ros/indigo/share/desktop_full/package.xml
engine44@engine44-VirtualBox:~$ 

Is it best to leave everything where it is?

Thanks

---

### Post by ajgreeny on 2015-01-31
There is actually no choice available as to where you install the files of any package when using a normal Linux OS, so yes; leave everything where it is.

---

### Post by rbengr on 2015-01-31
Thanks

---

