---
title: "[SOLVED] Can't Install NVIDIA Driver"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by anachronon on 2008-05-22
This is a problem that I have been fighting for some time, through three different installations of Ubuntu.  The process is always the same.  From what I have read, it seems fairly common.  Yet, I have not found an answer that will work for me.  Right now, I am running Ubuntu Studio 8.04.

First, I download the driver from the NVIDIA website.  I have a P4 processor and Ge-Force 5200 chipset, so I assume this is the proper page:

[http://www.nvidia.com/object/linux_display_ia32_169.12.html](http://www.nvidia.com/object/linux_display_ia32_169.12.html)

From experience, I learned to use the Grub Loader to log in as root (no desktop, "runlevel 1").  This seems the easiest.  From there, I run the driver install, and get the error message saying that I need the "libc header files".

After running "apt-get install build-essential" (I don't need "sudo", as I am still in root), I run the NVIDIA install again.  This time I get the error message:

"Unable to find kernel source tree for the currently running kernel.  Please make sure you have installed the kernel source files for your kernel and that they are properly configured; on Red Hat Linux systems, for example, be sure to have the 'kernel source' or 'kernel-devel' RPM installed.  If you know the correct kernel source files are installed, you may specify the kernel source path with '--kernel-source-path' command line option"

So, what do I do now.  Of all the threads I could find on this issue, this was the farthest any seemed to get.

Is there a better way?  I am trying to use a wide screen monitor with 1280x800 native resolution.  Right now, I can't get better than 800x600, and I am forced to choose between images either terribly stretched or horribly squished.  I have read a number of other methods, but I'm not sure which to try.

---

### Post by ErusGuleilmus on 2008-05-22
Do the Drivers that Ubuntu recommends not work for what you need? You can go to System -> Administration -> Restricted Drivers (I think, using OpenBox right now.) That should enable you to install the required drivers.

---

### Post by yochaigal on 2008-05-22
What does envy say?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by oedha on 2008-05-22
just enable your nvidia on Hardware Drivers ( previously named restricted drivers )
it will automatically download and install the driver

---

### Post by anachronon on 2008-05-23
> **ErusGuleilmus said:**
> Do the Drivers that Ubuntu recommends not work for what you need? You can go to System -> Administration -> Restricted Drivers (I think, using OpenBox right now.) That should enable you to install the required drivers.
Thanks for replying.  I tried to use the proprietary driver that came with the installation, but it didn't work.  That one limited me to a resolution of 640x480, worse than what I have now.  I even went to add/remove, to install the NVIDIA "legacy" driver.  According to the screen, it installed.  But it doesn't show up as an option on the "drivers" page.

---

### Post by anachronon on 2008-05-23
> **yochaigal said:**
> What does envy say?

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
I don't know about "envy", but I used the command, "sudo lspci | grep -i nvidia", and it returned: "nvidia geforce 5200 (nv34)".  That is the right chipset.

---

### Post by anachronon on 2008-05-23
> **oedha said:**
> just enable your nvidia on Hardware Drivers ( previously named restricted drivers )
it will automatically download and install the driver
Thanks for replying. I tried that, but it didn't help. That one limited me to a resolution of 640x480, worse than what I have now. I even went to add/remove, to install the NVIDIA "legacy" driver. According to the screen, it installed. But it doesn't show up as an option on the "drivers" page.

---

### Post by Shazaam on 2008-05-23
Run this in terminal......
```
sudo apt-get install linux-headers-$(uname -r)
```
Then re-run the driver install.

---

### Post by ubuntu-freak on 2008-05-23
You should use the Ubuntu supplied driver. You can change the resolution with "gksudo nvidia-settings" or "gksudo displayconfig-gtk". Type either of those into the terminal, or press Alt F2 and type it there. Don't play with anything but the resolution options in displayconfig-gtk though.
 
You should report/confirm a bug at [Launchpad](launchpad.com) as well, cos' your hardware wasn't autodetected properly.
 
Nathan

---

### Post by yochaigal on 2008-05-24
envy is a program that will install and configure the appropriate nvidia/ati driver for ubuntu....

---

### Post by anachronon on 2008-05-24
> **reassuringlyoffensive said:**
> You should use the Ubuntu supplied driver. You can change the resolution with "gksudo nvidia-settings" or "gksudo displayconfig-gtk". Type either of those into the terminal, or press Alt F2 and type it there. Don't play with anything but the resolution options in displayconfig-gtk though.
 
You should report/confirm a bug at [Launchpad](launchpad.com) as well, cos' your hardware wasn't autodetected properly.
 
Nathan
Tried "gksudo nvidia-settings" in both terminal and alt-F2, but it did nothing.  Got "gksudo displayconfig-gtk" to work, but it wouldn't give me any more than the limited set of screen resolutions that I have now.

Also, went to Launchpad, but only got a screen saying "coming soon".

---

### Post by anachronon on 2008-05-24
> **Shazaam said:**
> Run this in terminal......
```
sudo apt-get install linux-headers-$(uname -r)
```
Then re-run the driver install.
I may need a little help with this command, before I try to run it.  Where it says "uname", does that mean that I type in my user name there?  Do I include the parentheses?  Also while I'm on the subject, what does the "-r" option do?  Finally, I'm familiar with the "$" modifier, but I have never seen it used this way.

---

### Post by Shazaam on 2008-05-24
No need to change it, run it as is. Here is a loose (modified) quote I grabbed from the help.ubuntu.com page.....

"The construct `uname -r` will evaluate to the version of the running kernel, e.g. 2.6.22-14 or higher (may vary on your system)".

---

### Post by anachronon on 2008-05-25
> **Shazaam said:**
> No need to change it, run it as is. Here is a loose (modified) quote I grabbed from the help.ubuntu.com page.....

"The construct `uname -r` will evaluate to the version of the running kernel, e.g. 2.6.22-14 or higher (may vary on your system)".
Well, I ran that command, and the nvidia driver was able to install.  Thanks.  However, it switched the screen resolution to one not supported by my monitor, so now, I had no picture.  With no desktop, I now had no way to switch the resolution to one that was supported.

Fianlly, I had to boot into Recovery Mode, and use the option to repair the xconfig file.  However, that put me back to where I was originally, before installing the driver. I'm still stuck with the wrong resoltion, and I cannot still find a way to change it to the right one, or activate the driver that I just installed.  So, what do I do now?

---

### Post by oedha on 2008-05-25
1. enable nvidia on hardware drivers
2. open terminal type :==> glxinfo | grep render
     if the output is :==> direct rendering: Yes
     it means your driver is installed and your 3d runs
3. since you are always failed......what if you edit the xorg.conf manually
    open terminal type :==> sudo gedit /etc/X11/xorg.conf
    then edit the resolution to your new resolution
    save it and quit
    restart your desktop / reboot

I actually didnt really recommend this way.........but this worked for me when i stucked on nvidia 7000m on gutsy last time

---

### Post by anachronon on 2008-05-26
> **oedha said:**
> 1. enable nvidia on hardware drivers
2. open terminal type :==> glxinfo | grep render
     if the output is :==> direct rendering: Yes
     it means your driver is installed and your 3d runs
3. since you are always failed......what if you edit the xorg.conf manually
    open terminal type :==> sudo gedit /etc/X11/xorg.conf
    then edit the resolution to your new resolution
    save it and quit
    restart your desktop / reboot

I actually didnt really recommend this way.........but this worked for me when i stucked on nvidia 7000m on gutsy last time
Well, I reenabled the driver in the Hardware Drivers section, so now I am stuck with 640x480.

Anyway, I ran the "glxinfo" command, and got a "yes".  But, there seems to be nothong in the xorg.conf file that I can change.  There are no lists of resolutions.  Here is what I found:

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

---

### Post by ubuntu-freak on 2008-05-26
You have the proprietary driver working now yeah? Well, nvidia-settings should be installed along with it, if not:
 
**sudo apt-get install nvidia-settings**
 
I'm surprised displayconfig-gtk didn't let you change it though. Sometimes you have to select different monitors in the list before you see the correct res.
 
Nathan

---

### Post by anachronon on 2008-05-26
There is one other possibility that might be worth exploring.  Earlier, I was able to get the driver downloaded from nVidia to install.  But, it switched my resolution to one not supported by the monitor, so I just got a blue screen.  That was probably because I had to run the installation with the desktop switched off.  The driver may have been working, but I could not see the desktop to find out.

That made me wonder, is there a way to handle that blindly?  Without being able to see the desktop, is there a keyboard command that I could use to switch to a terminal screen (runlevel 1)?  Once I had the text-only screen, is there I terminal command that I could use to set the desktop resolution?  I could then return to the desktop, to see if it works.  If not, back to the terminal screen.  I might be able to get what I need by trial and error.

---

### Post by oedha on 2008-05-26
press ctrl + alt +F2 to get into a terminal ( login and work in CLI )
back to gdm :==> ctrl + alt + F7

---

### Post by anachronon on 2008-05-27
> **reassuringlyoffensive said:**
> You have the proprietary driver working now yeah? Well, nvidia-settings should be installed along with it, if not:
 
**sudo apt-get install nvidia-settings**
 
I'm surprised displayconfig-gtk didn't let you change it though. Sometimes you have to select different monitors in the list before you see the correct res.
 
Nathan
Well, I tried that, and again, I lost my desktop.  Had to reboot into recovery again, to fix the xconfig.

I finally got displayconfig-gtk to let me select the monitor by description, rather than make and model.  It seems to have a mind of its own on that.  But, I still can't get the 1280x800 resolution that I need.

Perhaps, I should ask, is there anyone out there who HAS Linux running in 1280x800, or some other wide-screen resolution?

---

### Post by anachronon on 2008-05-27
> **oedha said:**
> press ctrl + alt +F2 to get into a terminal ( login and work in CLI )
back to gdm :==> ctrl + alt + F7
OK, I got that to switch me in and out of the desktop.  Now, is there any way that I can use the command line to set the desktop resolution, while I am in the text-only format?

---

### Post by oedha on 2008-05-27
i am still using sudo dpkg-reconfigure server-xorg
( although there is a new sysntax...which i never use yet ) :)

---

### Post by ubuntu-freak on 2008-05-28
This should fix you up:
     
**sudo xrandr -s 1280x800**
 
Hope that ends your troubles.
 
Nathan

---

### Post by anachronon on 2008-05-28
> **reassuringlyoffensive said:**
> This should fix you up:
     
**sudo xrandr -s 1280x800**
 
Hope that ends your troubles.
 
Nathan
Well, everything now is installed and supposedly running properly.  But I still can't get the proper resolution for my monitor.  The command "xrandr -s" helped me to get my screen going, but it claims that 1280x800 is not among the options.  i had to settle for 1024x768, which is better, but still distorted.

Could my problem be that I am using many different parts from different machines?  I researched everything carefully beforehand, and all of the parts have the right compatibility (voltages, bus speeds, etc).  Also, nVidia's specs on the video card say that it supports 1280x800, and the booklet with the monitor says that it's native resolution is 1280x800.  So, could the software simply be confused by all of the different parts?

---

### Post by ubuntu-freak on 2008-05-28
That's incredible. I don't know what's going on to be honest. You should report a bug.
 
Try "gksudo displayconfig-gtk" again and see if any of the monitor choices allow you to use 1280x800.
 
Nathan

---

### Post by anachronon on 2008-05-28
> **reassuringlyoffensive said:**
> That's incredible. I don't know what's going on to be honest. You should report a bug.
 
Try "gksudo displayconfig-gtk" again and see if any of the monitor choices allow you to use 1280x800.
 
Nathan
I tried a few other choices, and was able to get options for greater screen resolutions with some.  But, all of the wide-screen monitors were limited to 1024x768.

However, as an experiment, I tried using the 640x400 resolution, which is now an option.  It is exactly half of the 1280x800 that I need, which should have filled the screen.  The monitor even recognized it as 1280x800 (from the on-screen menu).  Yet, it still did not fill the screen.  In fact, it was even more distorted.  But then, the 720x400 resolution used by the terminal DOES fill the screen!

Could the problem be the monitor?  It is actually a 15" flat-screen TV, that can accept direct VGA input.  It was given to me by an in-law.  He no longer needed it, and he saw that I needed a monitor.  It's much nicer than anything that I could afford on my own, much nicer than the funky, 10-year-old, ready-to-catch-fire CRT that I was going to use.  I really wanted to get it to work.  Now, I have to ask if that is possible.  Has anyone else had experience along these lines?

Also, seeing that I got the driver installed and working, should I close this thread (mark as "solved"), and open a new thread to address the monitor and configuration issues?

---

### Post by ubuntu-freak on 2008-05-28
Yeah, a new thread might be good.
 
Has your monitor ever displayed 1280x800 in GNU/Linux? It's a shame you can't force what you know is right.
 
The command "sudo xrandr -q" will display what xrandr thinks your screen can handle.
 
Nathan

---

### Post by anachronon on 2008-05-29
First of all, I would like to thank everyone who helped me with this problem.  I finally got it all working!  However, the final result was by trial-and-error, and far from intuitive.  Here is what worked after getting the driver installed:

I needed to get a resolution of 1280x800.  Using "gksudo displayconfig-gtk", I set my monitor type to 1280x800.  However, for some reason that option would not give me that resolution. ???  So, I set the monitor type to 1280x1024.  This gave me the option of 1280x960.  Believe it or not, the monitor accepted that resolution with balking.

From there, I used "sudo xrandr -q" to get a list of resolution options.  This command now listed 1280x800 as an option, whereas, "displayconfig" did not.  So, I then used "sudo xrandr -s 1280x800" to set my resolution manually.  And, the rest is history.

I also noticed that, sometimes, trick or commands that did not work on the first try, might work on the second or third try.

I still have a slight screen-width problem though.  But, that is the topic of a new thread: "Screen Width Problem".

---

### Post by ubuntu-freak on 2008-05-29
You're welcome.
 
Strange how it took both displayconfig-gtk and xrandr to fix your screen resolution issue.
 
Regrading the screen width, the monitors menu button options should allow you to increase/decrease the width/height.
 
Nathan

---

### Post by anachronon on 2008-05-29
> **reassuringlyoffensive said:**
> You're welcome.
 
Strange how it took both displayconfig-gtk and xrandr to fix your screen resolution issue.
 
Regrading the screen width, the monitors menu button options should allow you to increase/decrease the width/height.
 
Nathan
Oh, thanks for reminding me.  I forgot to mention in the other post that the width is adjusted all the way out.

---

