---
title: "what is scons ?"
date: 2012-03-31
forum: New to Ubuntu
---

### Post by bariamtak on 2012-03-31
I am trying to install a game which I downloaded from one website. It comes in tar. I extracted the files. I read the Readme file and follow accordingly but when I type scons in terminal it prompt me to install scons.
What actually is this? Do i really need this for intalling Games or other softwares ?
And also there is no configure file. there is also no make file. The games is VDrift.
Thank you.

---

### Post by zombifier25 on 2012-03-31
If the game comes with a Readme, then it's good. Follow the instructions.
As for scons, maybe the game needs the package in order to install. Simply
```
sudo apt-get install scons
```
EDIT: According to apt-cache show, scons is
> replacement for make
 SCons is a make replacement providing a range of enhanced features such
 as automated dependency generation and built in compilation cache
 support.  SCons rule sets are Python scripts so as well as the features
 it provides itself SCons allows you to use the full power of Python
 to control compilation.

---

### Post by Perfect Storm on 2012-03-31
You don't need to compile vdrift. There's a game repositories (unofficial) for Ubuntu: [http://www.playdeb.net/updates/ubuntu/11.10/?q=vdrift](http://www.playdeb.net/updates/ubuntu/11.10/?q=vdrift)

---

### Post by bariamtak on 2012-03-31
Thank you for responding. I'll get back after installing sconcs.
Well @ Artificial Inteligence: I want to tried compiling the game once so I am trying to install by compiling from the source.
Anyway thank you for the info. I'll install from synaptic package manager if i cannot manage it.

---

### Post by bariamtak on 2012-03-31
I installed scons and give the command scons and it gives me the following errror.
******************************************************************
scons: Reading SConscript files ...
Package bullet was not found in the pkg-config search path.
Perhaps you should add the directory containing `bullet.pc'
to the PKG_CONFIG_PATH environment variable
No package 'bullet' found
OSError: 'pkg-config bullet --libs --cflags' exited 1:
  File "/home/bariamtak/Downloads/vdrift-src-2011-09-01/SConstruct", line 337:
    env.ParseConfig('pkg-config bullet --libs --cflags')
  File "/usr/lib/scons/SCons/Environment.py", line 1460:
    return function(self, self.backtick(command))
  File "/usr/lib/scons/SCons/Environment.py", line 593:
    raise OSError("'%s' exited %d" % (command, status))
********************************************************
Do i need other packages ?

---

### Post by zombifier25 on 2012-03-31
OK, I'm pretty certain your life would be easier if you do what A.I. told you too:
> **Artificial Intelligence said:**
> You don't need to compile vdrift. There's a game repositories (unofficial) for Ubuntu: [http://www.playdeb.net/updates/ubuntu/11.10/?q=vdrift](http://www.playdeb.net/updates/ubuntu/11.10/?q=vdrift)

---

### Post by bariamtak on 2012-03-31
OK. Now I give up. I've wasted 3 hours googling and installing scons and its library( I think ). I always got get the same error. Now i've installed it through the package manager.
Thank you A.I and Zombifier25 for your help.

---

