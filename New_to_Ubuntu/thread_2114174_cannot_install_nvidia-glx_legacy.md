---
title: "cannot install nvidia-glx legacy"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by kieron100 on 2013-02-09
Hello,

I am attempting to install nvidia-glx-legacy, I receive the following error.

> lono@lono:~$ sudo apt-get install nvidia-glx-legacy
Reading package lists... 91%
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ddSome packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nvidia-glx-legacy : Depends: linux-restricted-modules-common but it is not installable
                     Depends: xserver-xorg-core (>= 1:0.99.0-1)
dE: Unable to correct problems, you have held broken packages.

When I then try to install linux-restricted-modules-common I get this error.

> lono@lono:~$ sudo apt-get install linux-restricted-modules-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-restricted-modules-common is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-restricted-modules-common' has no installation candidate

I believe I need to enable the restricted repo however there is not option in my repositories to do this and I'm not sure what to add to manually do this.

Any help would be great.

Thanks

---

### Post by Sealbhach on 2013-02-09
Are you sure you need this? Sounds like it's old and probably been replaced already by the nouveau kernel module. What is your graphics card? To find out do

```
lshw -C display
```.

---

### Post by kieron100 on 2013-02-09
The card is a Riva TNT 2 (very old) which is why I believe I need this driver because it supports this card.

---

### Post by deadflowr on 2013-02-09
What version of Ubuntu are you running?

Edit: Which version of Lubuntu are you running.

You should be able to change the software sources in the lubuntu software center.

---

### Post by kieron100 on 2013-02-09
I am running the most recent version of Lubuntu

---

### Post by deadflowr on 2013-02-09
You could try opening up synaptic and then open the software sources.

Look here for more helpfulness:

[https://help.ubuntu.com/community/Lubuntu/Setup#Applications]("https://help.ubuntu.com/community/Lubuntu/Setup#Applications")

---

### Post by Sealbhach on 2013-02-10
You could try using the driver directly downloaded from the Nvidia site. I always use the driver from there.

[http://www.nvidia.com/object/linux_display_ia32_71.86.13.html](http://www.nvidia.com/object/linux_display_ia32_71.86.13.html)

Download it into your /home folder.

You need to install it from the command line. First you have to stop the X server. So press Ctrl+Alt+F1 (all three keys at the same time).  Log in to the console.

Then do 

```
sudo service lightdm stop 

chmod +x NVIDIA-Linux-x86-71.86.13.pkg1.run

sudo sh  NVIDIA-Linux-x86-71.86.13.pkg1.run
```The script will try to install the driver. Give it a try and see how it works.

To start your graphical desktop again do


```
sudo service lightdm start
```

---

