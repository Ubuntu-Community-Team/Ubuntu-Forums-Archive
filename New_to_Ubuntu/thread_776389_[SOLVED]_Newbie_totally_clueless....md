---
title: "[SOLVED] Newbie totally clueless..."
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Nebelhom on 2008-04-30
Hi guys,

I only recently installed ubuntu hardy heron to test out ubuntu. (NOTE: I'm a complete greenhorn in terms of computers)

I encountered some problems on installation already (black screen on installation). I managed to maneuver my way past with the noapic nolapic approach. I'm just sayin this, in case this is important.

I have an intel dual core and a GeForce 7600 GS. I am still at the bit where I need to install the drivers. (I chose the amd64 hardy heron version if this is important)
The NVIDIA drivers are simply not working and I am running out of ideas.

what happened so far:

shortly after successful installation (only took me about 2 days ;) ) ubuntu notified me that there are drivers available so I said yes. once they were installed, it said they may not work properly (sorry, for the inexact wording but I can't get the message again)

so that was that.

afterwards I surfed the net for various answers (by the way, I have internet connection, a picture with very poor resolution, mouse and keyboard work, i.e I am doin this from ubuntu not windows):

the first one I tried was EnvyNG. that appeared to have done the job (first uninstall all drivers, restart, install drivers, restart), however, it encountered several error messages on the way and on restart I was notified that the graphics card is not working correctly. so I tried to find the right one but that didnt help.

I then decided to follow the following guide:

[http://www.lucioalbenga.com/2008/04/25/hardy-heron-nvidia-drivers/](http://www.lucioalbenga.com/2008/04/25/hardy-heron-nvidia-drivers/)

With this one I am able to download the driver from the nvidia website and put it into my home(very similar to windows ;) ), but I am unable to open it.
on typing into the terminal: 
sudo chmod +x NVIDIA-Linux-x86-169.12.pkg1.run

I get the following messages:

nebelhom@DualBootBonanza:~$ sudo chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
[sudo] password for nebelhom: 
chmod: cannot access `NVIDIA-Linux-x86-169.12.pkg1.run': No such file or directory

trying another approach:

nebelhom@DualBootBonanza:~$ sh NVIDIA-Linux-x86-173.08-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.08-pkg1.run

The apt-get approaches give me the following messages:

Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) 

or

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)

(Please note I do not understand the commands I typed in there. I just followed procedures given from various websites)

basically, I'm out of ideas and wherever I turn seems to be a dead end mostly because I don't know how to navigate. is it possible, that one of you could give me a pointer in the right direction like a link to a thread with a similar if not identical problem (or the answer to all my questions, but answer != 42)? I wanted to teach myself BASH slowly but I think without guidance I am jumping in at the deep end not knowing how to swim.
I checked various guides but they weren't any help, unfortunately. help would be very appreciated.

Thanks in advance

Nebelhom :guitar:

---

### Post by Nebelhom on 2008-04-30
System Details:

Intel Core2 CPU
6420 @ 2.13GHz
2.00 GB RAM

Onboard Sound
GeForce 7600 GS

Thanks again for any help/advice

---

### Post by Bothered on 2008-04-30
Have you managed to install and try out the drivers in the repositories, by checking the relevant box in System->Hardware Drivers?

It sounds like you have some package manager problem as well. Did you have another package manager open (e.g. synaptic) when you tried to run apt-get?

---

### Post by martrn on 2008-04-30
> **Nebelhom said:**
> Hi guys,

I only recently installed ubuntu hardy heron to test out ubuntu. (NOTE: I'm a complete greenhorn in terms of computers)

I encountered some problems on installation already (black screen on installation). I managed to maneuver my way past with the noapic nolapic approach. I'm just sayin this, in case this is important.

I have an intel dual core and a GeForce 7600 GS. I am still at the bit where I need to install the drivers. (I chose the amd64 hardy heron version if this is important)
The NVIDIA drivers are simply not working and I am running out of ideas.

what happened so far:

shortly after successful installation (only took me about 2 days ;) ) ubuntu notified me that there are drivers available so I said yes. once they were installed, it said they may not work properly (sorry, for the inexact wording but I can't get the message again)

so that was that.

afterwards I surfed the net for various answers (by the way, I have internet connection, a picture with very poor resolution, mouse and keyboard work, i.e I am doin this from ubuntu not windows):

the first one I tried was EnvyNG. that appeared to have done the job (first uninstall all drivers, restart, install drivers, restart), however, it encountered several error messages on the way and on restart I was notified that the graphics card is not working correctly. so I tried to find the right one but that didnt help.

I then decided to follow the following guide:

[http://www.lucioalbenga.com/2008/04/25/hardy-heron-nvidia-drivers/](http://www.lucioalbenga.com/2008/04/25/hardy-heron-nvidia-drivers/)

With this one I am able to download the driver from the nvidia website and put it into my home(very similar to windows ;) ), but I am unable to open it.
on typing into the terminal: 
sudo chmod +x NVIDIA-Linux-x86-169.12.pkg1.run

I get the following messages:

nebelhom@DualBootBonanza:~$ sudo chmod +x NVIDIA-Linux-x86-169.12.pkg1.run
[sudo] password for nebelhom: 
chmod: cannot access `NVIDIA-Linux-x86-169.12.pkg1.run': No such file or directory

trying another approach:

nebelhom@DualBootBonanza:~$ sh NVIDIA-Linux-x86-173.08-pkg1.run
sh: Can't open NVIDIA-Linux-x86-173.08-pkg1.run

The apt-get approaches give me the following messages:

Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable) 

or

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)

(Please note I do not understand the commands I typed in there. I just followed procedures given from various websites)

basically, I'm out of ideas and wherever I turn seems to be a dead end mostly because I don't know how to navigate. is it possible, that one of you could give me a pointer in the right direction like a link to a thread with a similar if not identical problem (or the answer to all my questions, but answer != 42)? I wanted to teach myself BASH slowly but I think without guidance I am jumping in at the deep end not knowing how to swim.
I checked various guides but they weren't any help, unfortunately. help would be very appreciated.

Thanks in advance

Nebelhom :guitar:

Grepping through my logs I have come up with this.

Remove all trace of your nvidia drivers....
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get uninstall --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
sudo apt-get remove --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
```

Then visit this site and look at the nvidia manual.
[https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual")

Then download the nvidia drivers again from nvidia : [http://www.nvidia.com/object/unix.html]("http://www.nvidia.com/object/unix.html")
Make sure you save it to /home/yourusername where your username is your user name that you use to log on.

Find out your kernel, you are using, download the kernel header files, build tools and disable.

```
uname -r
sudo apt-get update
sudo apt-get install build-essential gcc
sudo apt-get build-dep
sudo apt-get install linux-image-$(uname -r)
sudo apt-get install linux-headers-`uname -r`
sudo apt-get upgrade
```

Then try :-
```
kdesu kate /etc/default/linux-restricted-modules-common
kdesu kate /etc/X11/xorg.conf
```

and find the line:


> DISABLED_MODULES=""

replace it with:

> DISABLED_MODULES="nv nvidia_new"

now we chang Section/Device/Driver
```
sudo /etc/init.d/gdm stop
```

Then run the shell script downloaded from nvidia
cd ~
cd /home/username
sudo sh NVIDIA*

*** NOTE ***** note that "....Could not get lock /var/lib/dpkg/loc..." means you didn't sudo it (run it as root) and that ..."....No such file or directory...."... means the file is not in the current directory or you didn't save the file to /home/username  so go back to downloading the nvidia drivers again..... Or just make sure you know the directory where you saved the nvidia shell script / drivers......

then
```
sudo /etc/init.d/gdm start
```
or 
```
sudo reboot
```


___________________________________________________________________
___________________________________________________________________

NOTE : This is not the recommended way to install nvidia drivers I found it works every time, but if you do get stuck in the shell type ```
sudo dpkg-reconfigure xserver-xorg
``` and set it to reconfigure X11 to use the nv driver, and you are back into graphical mode.

---

### Post by Nebelhom on 2008-05-01
thanks A LOT you two!!! I will try that.

> *** NOTE ***** note that "....Could not get lock /var/lib/dpkg/loc..." means you didn't sudo it (run it as root) and that ..."....No such file or directory...."... means the file is not in the current directory or you didn't save the file to /home/username so go back to downloading the nvidia drivers again..... Or just make sure you know the directory where you saved the nvidia shell script / drivers......

I think I took all that into account cos it seems common sense to me. Maybe I missed out a small snippet and that makes the difference.

Thanks a lot. will post again to give feedback whether it worked or not, but for now, back to work :(

Rock on, boys :guitar:

P.S. quick question at the side about BASH:

is there a quick guide to navigating in BASH (I found a tutorial that I will hit once I finished teaching myself the rudimentary basics of python)? is it like DOS where you can enter into certain folders and run things from there or is it completely different and I shouldn't ask these questions as they only represent tomfoolery?

---

### Post by Bothered on 2008-05-01
BASH is a shell, and hence has some elements in common with the DOS command line (or DOS shell). e.g. "cd [directory]" will change directory, "dir" will list files (although "ls" is more commonly used).

Try a quick google of "beginners guide to bash". The two commands I found most useful when starting on the linux command line are "man" and "apropos". Execute "man man" and "man apropos" for more information.

---

### Post by sp3ctum on 2008-05-01
> **Nebelhom said:**
> P.S. quick question at the side about BASH:

is there a quick guide to navigating in BASH (I found a tutorial that I will hit once I finished teaching myself the rudimentary basics of python)? is it like DOS where you can enter into certain folders and run things from there or is it completely different and I shouldn't ask these questions as they only represent tomfoolery?

I'm new to ubuntu/linux/unix myself, but I'd say it's not very different from dos. The commands are a little different, but the idea is the same, I guess.:)

I found one thing helpful: it's that when you're typing names of files or folders, you can type the beginning of the name and hit tab for autocompletion. 
In some cases when you're navigating into folders, you can for example type cd /home/yourusername/ and hit tab twice, and it will show a list of all the folders there without interrupting your string.

---

### Post by Nebelhom on 2008-05-01
Hi,

I followed the procedures as outlined by martrn (thanks by the way. it got me a little better understanding of the materia). however, it seems that the problem is a bit more deeply rooted. I will give you the error messages that I got so far when going through the instructions and then hopefully someone will understand more of this.
Thanks in advance already. I do apologise for the length of the post, I just wanted to put in as much info as poss so that people can work with it.

The following error repeats itself over and over again. starting on the command to remove all previous nvidia drivers. please note the line and the ones following where it says 1 not fully installed or removed. I get this error from then onwards every single time.
another thing at the side is the question of autoremove. I did not do this as i wasn't sure whether this would remove more than the files that I don't need. if someone could answer this one that would be a good thing to know at the side ;).

> nebelhom@DualBootBonanza:~$ sudo apt-get remove --purge nvidia-glx nvidia-glx-legacy nvidia-glx-new nvidia-settings
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx is not installed, so not removed
Package nvidia-glx-legacy is not installed, so not removed
Package nvidia-settings is not installed, so not removed
The following packages were automatically installed and are no longer required:
  debhelper libpthread-stubs0 libgl1-mesa-dev po-debconf libtimedate-perl
  intltool-debian x11proto-kb-dev mesa-common-dev xtrans-dev gettext
  x11proto-input-dev libxcb-xlib0-dev libglu1-mesa-dev libxau-dev dpkg-dev
  html2text libx11-dev patch libxcb1-dev x11proto-core-dev dpatch
  libxdmcp-dev libpthread-stubs0-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  nvidia-glx-new
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 28.3MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 97947 files and directories currently installed.)
Removing nvidia-glx-new ...
dpkg-divert: error checking `/usr/lib32/libGL.so.1': No such file or directory
dpkg: error processing nvidia-glx-new (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx-new
E: Sub-process /usr/bin/dpkg returned an error code (1)


Then I downloaded the most recent nvidia driver which is fine. kernel, update etc was fine as well apart from the constant notification of 1 not fully installed or removed. and the (Y/N) question.

then the kdesu commands were just mix ups between kubuntu and ubuntu I noticed (this is for the benefit of people who have the same problem and this procedure may work) I googled and typed in:

> gksudo gedit /etc/default/linux-restricted-modules-common
gksudo gedit /etc/X11/xorg.conf

if it is any help the following are the text documents I received. I noticed that it still says "Driver: 'vesa'"
> 
# This file is sourced from the linux-restricted-modules-common init
# script and is used to disable the link-on-boot feature, one module
# at a time.  This can be useful if you want to use hand-compiled
# versions of one or more modules, but keep linux-restricted-modules
# installed on your system, or just to disable modules you don't use
# and speed up your boot process by a second or two.
#
# Use a space-separated list of modules you wish to not have linked
# on boot.  The following example shows a (condensed) list of all
# modules shipped in the linux-restricted-modules packages:
#
# DISABLED_MODULES="ath_hal fc fglrx ltm nv"
#
# Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
# ltmodem and ltserial, and "nv" disables the three nvidia drivers.
# You can also name each module individually, if you prefer a subset.

DISABLED_MODULES="nv nvidia_new"

> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
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
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:2:0:0"
	Driver		"vesa"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #        
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:2:0:0"
	Driver		"vesa"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" #        
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" #        
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
Section "Extensions"
EndSection

The next step, I got completely stuck in:

> sudo /etc/init.d/gdm stop

This, stops the graphical interface, correct? if it should not have, then it has done something wrong.
Anyhow, this brings me to a black screen with the following writing at the beginning:

> * starting anac(h)ronistic cron anacron                [OK]
* starting deferred execution scheduler crond          [OK]
* checking battery state                               [OK]
* running local boot scripts (/etc/rc.local)           [OK]

then there is a free cursor with no prefix. by prefix I mean a prompt, for example in DOS you would see e.g C:\\ or python has >>>. but this has none which confused me a bit.
typing then in the commands seemed to not make any difference. as a consequence I couldnt get back into graphics mode either no matter what I did and I could only do it via reset button.

I hope one of you can help me out with one or two of these problems that I have. I am not sure what this tells me but probably the first thing to do would be to get rid of the 1 not fully installed or deleted item.

I would not mind reinstalling hardy if that would make things easier, but yet again, I do not know how :). again sorry for the lengthy post and thanks again for helping me out.

Nebelhom

---

### Post by Bothered on 2008-05-01
Cntl+Alt+F[1-6] will bring up terminals. Ctnl+Alt+F[>7] are (I think, but am not sure) usually used for graphical display - X is usually running on Ctnl+Alt+F7 (but sometimes higher). It sounds like you shut down the display manager from within the GUI.

Try pressing Cntl+Alt+F1, logging in on that terminal, and shutting down X from there. If you then press Cntl+Alt+F7 there should be no graphical display. You can then return with Cntl+Alt+F1, and when you're ready restart X with "sudo gdm start". You can return to the GUI by pressing Cntl+Alt+F7.

EDIT: Also, you should remember to log out of the ttys when you're done.

---

### Post by Nebelhom on 2008-05-01
> EDIT: Also, you should remember to log out of the ttys when you're done.

Sorry for this innocent question but what is a ttys and how would I log out of it.

---

### Post by Bothered on 2008-05-01
I refer to the login screens on Cntl+Alt+F[1-6] as the ttys as they're numbered tty[1-6]. I don't know what they're actually called.

If you don't remember to log out of one and, say, walk away (having logged out of GNOME) then a passer by can still access your login from the appropriate terminal.

EDIT: Oh, and you log out with "logout"
EDIT2: Press Cntl+Alt+F1 and you'll see what I mean - remember you can return to the GUI on Cntl+Alt+F7 (or maybe +F[8 or 9 or etc.])

---

### Post by Nebelhom on 2008-05-01
Thanks man! This allowed me to follow the procedure until the end. Unfortunately it didnt help my resolution ;(

while following the instructions till the end, there were more error messages during the driver install:

it could not find a suitable kernel and configured it itself.

afterwards when installing the OpenGL.libraries there was the following error:

> WARNING: Unable to perform the runtime configuration check for library 'libGL.so.1' ('/usr/lib32/libGL.so.162.12'); assuming successful installation.

after it finished, my login into ubuntu GUI is smaller but when logged on it is still the same and the resolution cannot be changed to anything but 640x480.

any thoughts? I would like to remove this 1 not fully installed or removed package, just to have a clean sheet, but I am not sure how to go about this.

any help is really appreciated. strangely enough I am learning more about ubuntu than if everything were going to plan \\:D/

---

### Post by martrn on 2008-05-01
I think you might be in the new safe mode (bullet proof x mode) I don't know.  Normally at this point point you just type, sudo dpkg-reconfigure xserver-xorg & configure your monitor.  But according to [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia") # In hardy you could have a problem with X going into failsafe mode and the /var/log/Xorg.0.log telling you something or other.

You don't normally need envy, we have already done what envy asked us to...  I would follow the but where it says trouble shooting at the bottom....

If you are under Gnome install envyng by typing ```
sudo apt-get install envyng-gtk
``` with your favorite package manager.Then ```
sudo envyng
``` or sudo apt-get envng-gtk.  Usually you keep your xorg.conf file, but it appears bullet-proof x is over-righting things.  envyng looks at the moment as it is the only way to install the nvidia drivers.... ?????

I don't know why ????

---

### Post by martrn on 2008-05-01
where it is telling you to remove packages eg...
The following packages were automatically installed and are no longer required: .... Use 'apt-get autoremove' to remove them.

Cut and paste what it is telling you to remove.  Do not autoremove them, just to be on the safe side.

Ask whoever wrote envy how it works. ??
I do not know anything about bullet-proofx, kdm doesn't use it. (gdm is only just begging to use it with hardy.)

---

### Post by howlingmadhowie on 2008-05-01
have you installed the nvidia-settings software?

---

### Post by martrn on 2008-05-01
Go to here and install envy-ng

```
http://www.albertomilone.com/nvidia_scripts1.html
```

or install nvy via apt-get.
Its just a script that does the same as listed here.  I don't think think ubuntu want anyone at the command line in hardy. :-?

---

### Post by Zralou on 2008-05-01
I had a similar problem when I first installed 8.04 back when it was still in Beta.  I ended up having to manually edit my xorg.conf file with the correct horz + vert refresh settings for my monitor.
I found them by googling my monitor make and model, then entered the setting into xorg.conf, worked fine after that (if you can access the rear of your monitor, it should be on a label there somewhere too).

Sara Lou

---

### Post by Nebelhom on 2008-05-02
Hi,

unfortunately I still have no joy, but the problem changed which I think is a good sign.

right, here is what I've done. I followed again (without much hope) down the envyng path.
and lo and behold I had a better resolution. still not what I know the graphics card can usually do but better (800x600 instead of 640x480, i.e. the firefox page fits on the screen)
I carry on trying using ubuntus-own troubleshoot and farting around with the xserver (> [http://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](http://help.ubuntu.com/community/BinaryDriverHowto/Nvidia))
just before I could do any major changes (I was about to run sudo nvidia-xconfig) my screen goes kinda black and says "out of range".

this is fine as it tells me that the drivers are acting now... I think, but the refresh rates of my monitor is not keeping up with the ones it is getting sent.

oh yea one strange thing is that I have sound now where before I didnt have any but no picture now... if anyone hasan explanation for that, I'd be glad to hear it ;)

now I tried to get into xorg.conf as Zralou suggested but I just can't seem to figure it out ;(.
So far what I've done is, once > "out of range" hits (that is once the login comes, I know this cos it does a stupid bongo bongo noise that seems to mock me with every reboot) I change to tty1 and run > sudo nano /etc/X11/xorg.conf
I know the refresh rates for my monitor I just have to implement them somehow. and once I am there i would like to make ubuntu understand that my graphics card is far better than ubuntu gives it credit (typical case of napoleon syndrome if you ask me)

it gives me various sections as a file but I am a bit at a loss how to enter into the subsections (say for example "monitor" or the "graphics display" to improve my resolution (if that is possible) and change something so that my GUI gives me a picture again.

again thanks guys. once (if) this works, I'll probably name my monitor in your honor ;)

thanks

Nebelhom

---

### Post by Zralou on 2008-05-02
Once in xorg.conf, change the horzsync and vertrefresh (or something along those terms, i'm on XP just now so I can't check the right terminology) to what your monitor settings should be.

Sara Lou

---

### Post by Nebelhom on 2008-05-03
hmmm...

ok I have now restored the intial settings I think via the fixvideoresolutionhowto on

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

section: undetected monitor specs

The file that I got was this (Zralou that will also explain why I wasnt sure how to do your suggestion. there were now values)

I was looking for values like horz and ver but there wasnt anything like that. and when the howto suggested to add my resolutions in the section "display" I couldnt even find that section. I'm a bit confused now :confused:
also note that the driver is now again "vesa" which makes me assume it is not the nvidia driver anymore (for obvious reasons). NOTE: I put xorg.conf at the bottom of post

so far the ubuntu adventure hasn't been exactly easy but strangely enough I dont mind that, cos in windows I would have just got wizards, assistants and all sorts to sort me out without telling me what's going on. I think I already know more about that little part of ubuntu than I will ever learn about windows ;). Am I strange?

Again, thanks for helping me out with suggestions:

As a summary for this last step:

When using envyng, it installs the necessary drivers but on load up of ubuntu the drivers grip and the monitor cannot handle it it seems (black screen and "out of range" error message; in manual that means adjust your resolution)
following ubuntu.help.Fix... it restores back to "vesa"
strangely, no values in xorg.conf and sound is gone again.

what to do?

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
	Driver		"vesa"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by Zralou on 2008-05-03
Not strange at all, I got the same 'buzz' when I fixed my own problem in Ubuntu, it's a great feeling fixing a problem in an OS you are totally new to.

When I had the same problem (my thread about it ended up 13 pages long!!), I used EnvyNG to uninstall the drivers, then re-install.  Upon reboot, I had the nvidia drivers, but 640x480 screen.
I then opened the xorg.conf file with 'kdesu kate' (I think its 'sudo gedit' in Ubuntu, I use Kubuntu), then scroll down till I found the h+v settings and changed them to the correct values that I found online for my monitor.

The xorg.config file you've posted is showing the 'vesa' drivers are in use, so try Envy again, but remember to uninstall all drivers first, then re-install, then hopefully you can re-boot into a GUI and adjust the monitor settings.

Sara Lou

---

### Post by Nebelhom on 2008-05-04
right guys,

down below is my xorg.conf now. as you see I managed to install the nvidia drivers (YAY!), but I still "only" have 800x600 resolution and my monitor works by plug'n'play (I don't know if that is a hindrance, I think it would be the right thing, as all other LCD monitors have too high refresh rates. I have a VideoSeven screen E17PS, if that is any help to anyone. It's one of those noname brands. I thought on purchase: 'What difference does a monitor make... I guess, now I've been told :lolflag:)
Now, I need to add into the file the new resolutions I'd like to have and my refresh rates.
Looking on the net I can't find anything and the manual doesnt tell anything either, but when I go into the menu of the screen I get the following values:

Horizontal Frequency 37.7 KHz
Vertical Frequency 60.0 Hz

I know the frequencies are usually given as an interval of numbers. is it bad, if I just type in the number? I can't modify them to see what the bandwidth is for these values ;(

could one of you tell me where to put what, cos last time I put the refresh rates into the > section "monitor" # and the whole thing just went balloonies on me and I ended up having to go into tty1 to restore everything back to normal ;(

Thanks guys, you've been amazing help so far. I think I'm almost finished with this problem. I feel it ;)



> # xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"uk"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:2:0:0"
	Driver		"nv"
	Screen	0
	Vendorname	"NVIDIA"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	640	480
		Modes		"640x480@60"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"NVIDIA GeForce 7 Series"
	Busid		"PCI:2:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"NVIDIA"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection

---

### Post by Nebelhom on 2008-05-04
Oh one other thing;

once I managed to get it all set up, do you know of a way of testing the drivers for performance? I mean quite clearly this is different to windows, so I am assuming that the performances in comparison could vary as well... or better said the driver may act differently... and obviously if it doesn't work then I know that there is still something fishy going on.

---

### Post by Nebelhom on 2008-05-04
Right. as of now, I, suddenly, only have 640x480 resolution (with the above xorg.conf), but I have shed loads of resolutions to choose from that are lower than 640x480.

could that be an update that took place recently? this is strange because when I put the changes in all was peachy, then today I got a black screen again and couldnt change tty. on leaving it and switching PC on after about 3 hours (watched donnie brasco... that'd be about 3 hours), I got the above config...

I followed the guide on [http://ubuntuforums.org/showpost.php?p=454217&postcount=1](http://ubuntuforums.org/showpost.php?p=454217&postcount=1)

but that just gave me the now quite familiar "out of range" error. I have the feeling that for some reason my monitor is not up to the task once ubuntu is used, but I don't know enough about that to make any meaningful changes.

...right playing around a little more with some german ubuntu guides that had a different approach still to no avail ;(

any ideas? slowly but surly I am going kerazy

Thanks guys

---

### Post by Zralou on 2008-05-04
This is all I can find on your monitor:
> 
&#8226; Resolutions supported 1024 x 768 &#8226; 1280 x 1024 &#8226; 640 x 480 &#8226; 800 x 600
&#8226; Synchronization Range - Vertical 56 - 76 Hz
&#8226; Synchronization Range - Horizontal 30 - 82 kHz

Sara Lou

---

### Post by Zralou on 2008-05-04
One thing I notice about your xorg file, it has been generated by:
> # This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.  It should be generated by nvidia.

Sara Lou

---

### Post by Zralou on 2008-05-04
Ok, I found my old thread about this, and this section is what I changed to fix my problem:

> Section "Monitor"
    Identifier         "Configured Monitor"
    Horizsync       31.5-70.0
    Vertrefresh     50-120
EndSection

Section "Screen"
    Identifier "Default Screen"
    Monitor "Configured Monitor"
    Device "Configured Video Device"
    Option "AddARGBGLXVisuals" "True"
    Defaultdepth    24
    SubSection "Display"
        Depth   24
        Modes "1024x768" "1280x1024"
    EndSubSection
EndSection

Hope it helps some.
Sara Lou

---

### Post by Nebelhom on 2008-05-05
thanks Zralou.

I am pretty sure I now know the problem. every time I have the right settings for my graphics card, I reload and the monitor goes off on one, which then makes hardy go into failsafe mode (800x600) and the mode is "vesa".

What I am going to try next is get all the new configs for nvidia via envyng, then before restart load xorg.conf and paste my monitors details.

It seems my monitor is a german make with a british cable which explains why I couldn't find anything in english threads about it ;)

thanks for your help. I'll keep trying.

party on, wayne :guitar:

---

### Post by Nebelhom on 2008-05-05
I found this code on the german ubuntu webpage.

The guy has a slightly newer graphics card and the same monitor. once I install the nvidia drivers I put everything the same as him apart from where it says identifier, I have "configured video device". is that important, i.e. my pc doesnt really know that it is an nvidia or is that just the way GeForce 7 series are displayed?

```
Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection 
```

---

### Post by Nebelhom on 2008-05-09
@Zralou: huge big thanks to you. your idea was right. in the end I managed (if interested see [http://ubuntuforums.org/showthread.php?t=785963&page=2](http://ubuntuforums.org/showthread.php?t=785963&page=2) )

I can see a whole picture without having to scroll now :)

---

### Post by darkerlink on 2008-05-09
> **Nebelhom said:**
> ...

I have an intel dual core and a GeForce 7600 GS. I am still at the bit where I need to install the drivers. (I chose the amd64 hardy heron version if this is important)
The NVIDIA drivers are simply not working and I am running out of ideas.
...

Not sure why this has not been mention yet but why would you choose AMD64 Hardy Heron version if you have an Intel Dual Core Processor?

---

### Post by Nebelhom on 2008-05-09
Because apparently an Intel Dual core is a 64-bit processor.

I double checked this a couple of times with folk because I wasnt sure myself, but people mostly agree on this.

the amd64 is misleading and means all 64 bit processors. at least this is the gist I got.

---

