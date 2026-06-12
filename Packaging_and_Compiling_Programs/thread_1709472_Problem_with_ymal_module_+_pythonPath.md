---
title: "Problem with ymal module + pythonPath"
date: 2011-03-18
forum: Packaging and Compiling Programs
---

### Post by Shamma009 on 2011-03-18
hello,
I had a python version 2.7.1 and I installed then ROS which I guess come with python as well... 

the problem now that I am following the instruction to download SIP from this website 

[http://www.riverbankcomputing.com/static/Docs/sip4/installation.html#configuring](http://www.riverbankcomputing.com/static/Docs/sip4/installation.html#configuring)

and they say 

his assumes that the Python interpreter is on your path.  Something like the following may be appropriate on Windows: c:\python32\python configure.py 
  If you have multiple versions of Python installed then make sure you use the interpreter for which you wish SIP to generate bindings for.
  

so I really don't get what they mean by that ? because when I download  their software I put it in one folder and from there I did the configure  thing...! I don't know shall I move it to the pythonpath directory and  do it from there 


Another Question: I have this error when I try to run some python code in ROS : Robot operating system : 
[PHP]

Traceback (most recent call last):
  File "/opt/ros/diamondback/ros/bin/roscore", line 34, in <module>
    from ros import roslaunch
  File "/opt/ros/diamondback/ros/core/roslib/src/ros/__init__.py", line 41, in <module>
    import roslib
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/__init__.py", line 50, in <module>
    from roslib.launcher import load_manifest
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/launcher.py", line 45, in <module>
    import roslib.manifest
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/manifest.py", line 46, in <module>
    import roslib.packages
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/packages.py", line 58, in <module>
    import roslib.os_detect
  File "/opt/ros/diamondback/ros/core/roslib/src/roslib/os_detect.py", line 49, in <module>
    import yaml
ImportError: No module named yaml


[/PHP]
 
I think I am suffering from the set of Path for python and the environment variable, I just don't know how to fix it 

when I do $PYTHONPATH in command line it gives me : 
***bash: /opt/ros/diamondback/ros/core/roslib/src:: No such file or directory***

although the file do exist and it has some files and when I do $PATH , it gives me : 
***bash:  /opt/ros/diamondback/ros/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:  No such file or directory***

can anyone tell me what the problem could be and how can I fix it  ...Also, what is the difference between python and pythonpath!!! 




thank you

---

### Post by MadCow108 on 2011-03-18
do you have the yaml module installed?
```
sudo apt-get install python-yaml
```

to display variables in bash you have to echo them:
```
echo $PYTHONPATH
```

else it will try to execute the variable which will fail in this case

---

### Post by Shamma009 on 2011-03-19
yes I did that install and it appears that I have it because it gives me 

[B]Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-yaml is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 232 not upgraded.[/B]

and still I got the same error

---

### Post by MadCow108 on 2011-03-19
please provide some more information.
which guide are you following?
Which OS are you using?
why do you need python 2.7? maverick only supports 2.6
why do you need SIP 4.12? maverick has 4.10 in the repos

(why do you have 232 not upgraded packages?!)

---

