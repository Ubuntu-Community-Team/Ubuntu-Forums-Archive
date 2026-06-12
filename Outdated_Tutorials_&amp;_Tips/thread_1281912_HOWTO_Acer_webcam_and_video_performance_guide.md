---
title: "HOWTO: Acer webcam and video performance guide"
date: 2009-10-03
forum: Outdated Tutorials &amp; Tips
---

### Post by X1R1 on 2009-10-03
Ok first thing first, this is my first tutorial and I expect you all profit from it. I have searched for this info for a long time now, so I figured I will better save you all the time and effort and compile the info here in a handy tutorial to get the Acer Webcams (Crystal Eye) to work on ubuntu. Also, the deault driver ubuntu installs (at least in Jaunty) is very buggy and videos play very slow and with poor quality.

NOTE: I have only tested this on an ACER 5810TZ laptop but im pretty sure more acer laptops should work with this setup.

[SIZE="4"]I - Performance[/SIZE]

On to business then:

-First off, we will install and configure the intel chipset drivers to optimize performance.

For this part I used the jaunty intel graphics performance guide by psyke83 (thanks!!!), only the safe method explained here, check at the end of the tutorial for a link to psyke83 thread for more info on this.


0. Optional: If there is no xorg.conf file present on your system, the following command will create a minimal configuration (which you can customize later):
Code:
```

$ sudo dpkg-reconfigure -phigh xserver-xorg
```

Note: Use caution with this command, as it will overwrite any xorg.conf file already present on your system (though it will create a backup).

1. Edit your xorg.conf:
Code:
```

$ gksudo gedit /etc/X11/xorg.conf
```


Find the "Device" section and make sure it looks identical to the following (important: remove or comment any of your previous customizations):
Code:
```

Section "Device"
	Identifier	"Configured Video Device"
	Option		"AccelMethod"			"uxa"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"true" # i8xx users: see note in guide

EndSection

```


NOTE: If you are using an Intel 8xx chipset, tiling cause instability unless you use the Bleeding-Edge configuration. Therefore: if you are using the Safe/Optimal configurations, set tiling to false; if you are using the Bleeding-Edge configuration, set tiling to true.

2. Download Bartec's fixmtrr.sh script and make it executable:
Code:

```
$ sudo wget http://launchpadlibrarian.net/26193373/fixmtrr.sh -O /usr/local/bin/fixmtrr.sh
$ sudo chmod +x /usr/local/bin/fixmtrr.sh

3. Create a symbolic link to ensure the fixmtrr.sh script is executed upon each login via GDM:
Code:

$ sudo ln -s /usr/local/bin/fixmtrr.sh /etc/gdm/PostLogin/Default
```

NOTE: This works only if you are using the GNOME Display Manager (GDM). KDE/other users need to execute this script manually - see the Important Note section.

Part B 

1. Add the X Updates PPA to your sources.list:

Edit /etc/apt/sources.list:
Code:

```
$ gksudo gedit /etc/apt/sources.list
```

Add these entries to the end of your sources.list file (if they do not already exist):
Code:

```
deb http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
deb-src http://ppa.launchpad.net/ubuntu-x-swat/x-updates/ubuntu jaunty main #X-Updates PPA
```

2. Import the X Updates PPA key, update your apt sources, and perform an upgrade:
Code:

```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com AF1CDFA9
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

N.B.: If you are asked to remove any packages, immediately cancel the process. The expected behaviour is only to upgrade packages, not to remove.

That will give you better performance and good 3D acceleration, you can test it with youtube for example, before this method fullscreen videos on youtube get VERY choppy, after you have done this now they will run smoothly :D

[SIZE="4"]II - Acer Crystal Eye Webcams[/SIZE]

NOTE: This can also work with other laptops model, not only Acer, to get a complete list of all working webcam laptops, check the end of this tutorial for the link.

Software Requirements:

To do this you will need the following packages installed on your system

In order to be able to build the V4L-DVB kernel driver modules, you will need:

    * kernel-source or kernel-headers
    * make
    * gcc
    * mercurial

So, lets get and install them:

```
$ sudo apt-get install make gcc mercurial linux-headers-$(uname -r) build-essential
```

After this is done, get the the source code for the V4L-DVB kernel modules:

```

hg clone http://linuxtv.org/hg/v4l-dvb
```

This creates a directory called v4l-dvb in the current working directory.

Compile:

Start by changing into the directory that contains the previously downloaded source:

```
cd v4l-dvb
```

Build/compile the modules from source with the command:

```
make
```

This will create a /v4l directory within which the completed *.ko module files will be written. Generally, this step will tend to take a while to complete; being dependent upon both the number of modules being built and your system's processing power.

And Install:
```

sudo make install
```

The command above will prompt you for your root password, and will then copy the *.ko module files you built in the above step into the /lib/modules/[kernel version]/kernel/drivers/media directories.

ALL DONE!!! 

now REBOOT!!!!! this is very important because the new drivers need to be loaded and the old ones unloaded, if you dont reboot you can have weird problems.

To test it, after reboot open a program such as ekiga, emesene, aMSN or skype and see if you webcam is detected by them. this is the easiest way to test.

that would be all, enjoy!!!

Usefull links:

HOWTO: Jaunty Intel Graphics Performance Guide by psyke83
[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

Applications to test your webcam:
[http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC](http://openfacts.berlios.de/index-en.phtml?title=Linux+UVC)

Other install options and some workarounds, also advanced users options to compile and install:
[http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers](http://www.linuxtv.org/wiki/index.php/How_to_Obtain,_Build_and_Install_V4L-DVB_Device_Drivers)

List of Supported devices by UVC:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

If you find an error in this tutorial, a correction or something that you think I should add just let me know! this tutorial is far from perfect.

thanks for reading and hope it worked for you!!!

---

### Post by gazambuja on 2009-10-22
In Karmic 9.10 beta, webcam work fine, out of the box.
Acer 4810TZ

---

### Post by AlexanderAzimov on 2009-10-22
> **Tax Discs said:**
> It’s not a netbook since it runs Windows Vista (netbooks run Windows XP)



They now make Netbooks with 2 gigabytes of RAM and vista as the OS. (Not trying to be smart, Just figured I would share the Info :P) Also I'll be using the Tut soon enough. I'm running an acer extensa 5620, with Crystal Eye on it. I would like to see that and the Mic working before to long. Thanks for the Tut and I'll post how it works out later on.

---

### Post by miegiel on 2009-10-22
Anyway, back to the topic. I think the how-to can use some more info on the *what* and *why* behind the *how-to* to give people more insight and understanding of the steps being done. Besides that I can't think of any constructive criticism :D

In win7 I found the camera laggy (low fps) in the 720 HD mode. So I'm not really missing that in karmic (32bit) and with the default drivers/modules everything runs as smooth as I'd expect it to.

---

### Post by X1R1 on 2009-10-22
> **miegiel said:**
> reported .. just camouflaged advertisment for your url

Anyway, back to the topic. I think the how-to can use some more info on the *what* and *why* behind the *how-to* to give people more insight and understanding of the steps being done. Besides that I can't think of any constructive criticism :D

In win7 I found the camera laggy (low fps) in the 720 HD mode. So I'm not really missing that in karmic (32bit) and with the default drivers/modules everything runs as smooth as I'd expect it to.

Thanks for the tip, I will add some more info as soon as I can :D

Its sad to know that I spent so much time to gather the info here and post it and now it will soon be forgotten, cause the problem solves just with upgrading :( lol

On the other side, that shows the amazing team behind ubuntu and why it is made by/for the people, every little aspect is heard and taken care off.

Nevertheless I still will continue to inprove the thread for those who want to stick with Jaunty OR if they have problems with karmic I guess I could add some info once I upgrade to it too. :guitar:

---

