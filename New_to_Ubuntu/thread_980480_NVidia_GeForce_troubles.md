---
title: "NVidia GeForce troubles"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by SalsaShark on 2008-11-12
I'm trying to get my NVidia GeForce 8400M G drivers running and I'm having some difficulty.  I follow the steps in here:
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```
(taken from [http://ubuntuforums.org/newreply.php?do=newreply&p=5086971](http://ubuntuforums.org/newreply.php?do=newreply&p=5086971))

but at step 9, I accept the license, and then it doesn't work.  The log reports this:

[I]-> License accepted.
-> No precompiled kernel interface was found to match your kernel; would you li
   ke the installer to attempt to download a kernel interface for your kernel f
   rom the NVIDIA ftp site ([ftp://download.nvidia.com)?](ftp://download.nvidia.com)?) (Answer: Yes)
-> No matching precompiled kernel interface was found on the NVIDIA ftp site;
   this means that the installer will need to compile a kernel interface for
   your kernel.[/I]

And then there's a whole bunch of code that will make this post way too long, and then finally:

[I]ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at [www.nvidia.com](www.nvidia.com).[/I]

So, is there anything I'm missing here?

---

### Post by sharkster2007 on 2008-11-12
Hello I have a Nvidia 6600GT and this worked for me and was very easy to set up my thread is here: [http://ubuntuforums.org/showthread.php?t=973038](http://ubuntuforums.org/showthread.php?t=973038)

Hope it helps you out :-)

PS: That .run thing's a pain in the rear end, I gave up on it the (pre-packaged ubuntu).deb files are much easier (just double click, select install for all 3files, then activate)

---

### Post by SalsaShark on 2008-11-12
So how do I know which one to get, the 173 or the 177?

---

### Post by sharkster2007 on 2008-11-12
Sorry the 177 is the latest one recommended by ubuntu 8.10 (as listed on Hardware drivers menu).

The 173 is an older version, but also compatible (both worked on mine, I but later upgraded to 177 version,as it was newer) :-)

---

### Post by nhasian on 2008-11-12
just out of curiosity, how come you dont use the restricted drivers in the repository?  I used to download the latest drivers from nVidia but every time there was a kernel update, i would have to reinstall the nvidia driver.  it was kinda a pain...

---

### Post by sharkster2007 on 2008-11-12
> just out of curiosity, how come you dont use the restricted drivers in the repository? I used to download the latest drivers from nVidia but every time there was a kernel update, i would have to reinstall the nvidia driver. it was kinda a pain...

The website's in my thread are the official ubuntu website ones, the "restricted drivers" are the 177 & 173 versions.

I worked my way out because my PC is not internet connected, but have access to a windows one that is, so I manually downloaded the required files on that one, then installed via the ubuntu desktop :-)

---

### Post by SalsaShark on 2008-11-12
So I just installed them, but they don't appear in the hardware drivers menu...

---

### Post by sharkster2007 on 2008-11-12
I didn't have this problem:
 > SYSTEM>ADMINISTRATION>HARDWARE DRIVERS select NVIDIA ACCELERATED GRAPHICS DRIVER VERSION 173 (or VERSION 177 if installed this instead) click enable, an arrow should appear asking you to restart your system.

There were 2 options on a menu below one for the 173 and another for the 177 driver, I selected one, clicked enable, it came up with a blue arrow, i restarted my machine and that was it. :-(

---

### Post by SalsaShark on 2008-11-12
I recall them being there before I did the stuff in my original post.  Does anyone know how to undo that stuff I did in the code?

---

