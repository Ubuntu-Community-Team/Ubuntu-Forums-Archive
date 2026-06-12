---
title: "unable to install nvidia driver"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by carpk on 2008-07-17
Please someone help me....

            I downloaded a driver from Nvidia but when I go to run It the terminal opens up and say's "ERROR: nvidia-installer must be run as root" and that's as far as I get... I just want to know how to run as root.

---

### Post by Inxsible on 2008-07-17
> **carpk said:**
> Please someone help me....

            I downloaded a driver from Nvidia but when I go to run It the terminal opens up and say's "ERROR: nvidia-installer must be run as root" and that's as far as I get... I just want to know how to run as root.
Add sudo before the command that you are trying to run.

Also AFAIK, you have to run that nvidia script when you are not already logged into an X session. so you might have to hit Ctrl + Alt + F1 and go to tty1 and then run the command from the command line.

---

### Post by overdrank on 2008-07-17
> **carpk said:**
> Please someone help me....

            I downloaded a driver from Nvidia but when I go to run It the terminal opens up and say's "ERROR: nvidia-installer must be run as root" and that's as far as I get... I just want to know how to run as root.

Hi and welcome, to add to Inxsible
 if you would like to try and install the nvidia driver you have downloaded then you can use the keys alt, ctrl, F1 keys at the same time and this will bring you to the command prompt and login.
The use this command to stop X
```
sudo /etc/init.d/gdm stop
```
Then change to the directory that you downloaded the driver to
```
cd ~/Desktop
```
Then you can use the command to install the nvidia drivers 
```
sudo sh NVIDIA-Linux-x86-173.14.09-pkg1.run
```
If that is the name of the driver you have downloaded.
Then you should be able to start x again 
```
sudo /etc/init.d/gdm start
```
If all works as plan then you should have the new driver installed.

---

### Post by TSS on 2008-07-17
Just so you are aware, there is an easier way to do this (unless you need the most recent version). Go to System > Administration > Hardware Drivers.  Type in your password, and use the program to add the nVidia driver.

---

### Post by jwferk on 2008-07-17
Open a terminal session (in Gnome - Applications - Accessories - Terminal)

change directories ("cd") to wherever you have the NVIDIA package (e.g., cd /home/your name/Desktop)

type sudo sh NVIDIA*  (the * is a wildcard so you don't need to type the entire NVIDIA string)

you will get a message saying "sudo password"

type in your password and hit return

NIVIDA will install

You may get a message that you need to exit the X session.

Go to System - Administration - Services

type in your password

remove the check box from GUI (your screen is going to go blank - don't worry)  You are now in a terminal session

go back to the directory where the NVIDIA file resides and repeat the above steps.

After the driver loads type

/etc/init.d/gdm start (I'm assuming you are using Gnome as a desktop; for KDE3 it is /etc/init.d/kdm start

the graphical session will restart

Go back into System -Administration-Services and recheck the box for the GUI at startup

NVIDIA is quirky.  When it installs you may get a message saying libc6 development is missing.

as root type "sudo apt-get install libc-dev" (without the quotes)

libc-dev will install

go back and redo the NVIDIA install

That all sounds complex but it is not.  NVIDIA won't install if the Graphical interface is on.  One of the dependencies for NVIDIA is libc-development which doesn't load automatically when you install Ubuntu.  "gdm" is the Gnome executable to start and stop the graphical interface.  It is located in the file etc/init.d  The command to start the gdm is start.  The stop command is stop.

Hope this helps.

---

### Post by Cl0ud9 on 2008-07-17
> **TSS said:**
> Just so you are aware, there is an easier way to do this (unless you need the most recent version). Go to System > Administration > Hardware Drivers.  Type in your password, and use the program to add the nVidia driver.

An easy way to get the most recent version is to use envyng. This program allows you to install or remove the most recent ati and nvidia drivers.

For command line:
```

sudo apt-get install envyng-core
envyng

```

For gtk GUI:
```

sudo apt-get install envyng-core envyng-gtk
envyng -g

```

---

### Post by Sef on 2008-07-17
What NVidia card do you have?

---

### Post by anjilslaire on 2008-07-17
The newest version in the repo's is 
169.12+2.6.24.13-19.45 (for Hardy)

The latest version from nvidia.com is
173.14.09

Not much difference, IMO. I use Nvidia as well, and just stick with the versions in the repositories, which was just update last week or so. I'd rather have the stability of a repo-approved version when it comes to my display drivers...

---

### Post by TSS on 2008-07-17
> **anjilslaire said:**
> The newest version in the repo's is 
169.12+2.6.24.13-19.45 (for Hardy)

The latest version from nvidia.com is
173.14.09

Not much difference, IMO. I use Nvidia as well, and just stick with the versions in the repositories, which was just update last week or so. I'd rather have the stability of a repo-approved version when it comes to my display drivers...

For me personally (Gefore Go 6150) there is a big difference.  With the driver in the repository, my screen gets blurry each time I have to wake the computer up from sleep.  The newest driver fixes that problem.  I think it just all depends :-p.

---

### Post by anjilslaire on 2008-07-17
Ah, true. If you have problems with the repository driver, it's certainly worth it to try the latest from nvidia. I've got a 6600GT, and its good to go with the repository.

---

### Post by jwferk on 2008-07-18
Near as I can tell the repository driver (Systems - Administration - Hardware Drivers) won't run in TwinView mode for dual monitors.  As a matter of fact, it messes up the 173 NVIDIA driver if you install it.  Although its a bit more complex to install the driver from the NVIDIA site, its the only way I've found to run multiple monitors short of editing the Xorg.config file directly with TwinView options.

---

