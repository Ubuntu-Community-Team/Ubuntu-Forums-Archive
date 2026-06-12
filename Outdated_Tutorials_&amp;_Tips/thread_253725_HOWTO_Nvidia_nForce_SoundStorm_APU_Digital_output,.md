---
title: "HOWTO: Nvidia nForce SoundStorm APU: Digital output, Surround and Hardware mixing"
date: 2006-09-08
forum: Outdated Tutorials &amp; Tips
---

### Post by jocko on 2006-09-08
[SIZE=3][COLOR=Blue]**Note (March 5:th, 2010): My old desktop is nowadays enjoying a long deserved retirement (after six or seven years of faithful service). [SIZE=2]This means I have no reason to continue maintaining this thread, but if anyone feels up to it, you are very welcome to use, modify and distribute this thread and my  patches in any way you like.[/SIZE]**[/COLOR][/SIZE]



This howto is for those of you who have an nforce mobo with SoundStorm hardware and want to take better advantage of it's capabilities.
The open source alsa driver (intel8x0) is not capable of hardware mixing or dolby digital encoding.

In my experience nvidias closed source oss drivers work (almost) perfectly.
Note that these have not been developed at all since november '05, and nvidia have apparently decided that they will not provide any further linux nforce drivers, they just tell us to use the open source drivers. The main reason I wrote this howto was because I saw somewhere (forgot where) that nvidias drivers will not install on kernels 2.6.16 and later. I found a couple of hacks that works and decided to share them, together with everything else I do to get my sound work the way I want it.

My setup:
Motherboard:    Gigabyte GA-7NNXP (nForce2, mcp-t southbridge)
 Other:        Digital Output through SPDIF (both optical and rca cable works) to an external 5.1 reciever (never tried analog surround, but analog stereo works fine)

Make sure you know you have SoundStorm before you try any of this. It's only present in nforce 2 motherboards, and only if they have an mcp-t southbridge.
[COLOR=Blue] How can you check if you have SoundStorm?[/COLOR]
Check the result of running this command in a terminal:```
lspci | grep audio
```This is what I get:```
00:05.0 Multimedia audio controller: nVidia Corporation [COLOR=Blue]nForce Audio Processing Unit[/COLOR] (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
```You have SoundStorm only if you see "[COLOR=Blue]nForce Audio Processing Unit[/COLOR]"
[SIZE=3][COLOR=Red]** If you don't have SoundStorm, this howto will probably not help you in any way.**[/COLOR][/SIZE]
##########################################################################
**[SIZE=5]Step 1:[/SIZE]**
Get some dependencies ([COLOR=Red]if you run dapper or older: change *-generic* in the last two to match your kernel[/COLOR] (-k7/-686/-386, check the output of 'uname -r' if not sure):
```
sudo apt-get update
sudo apt-get install build-essential libqt3-mt linux[COLOR=Red]*-generic*[/COLOR] linux-headers[COLOR=Red]*-generic*[/COLOR]

```The last two are metapackages that make sure you always have the headers and restricted modules matching your kernel (-generic is instead of -k7 or -686 in edgy/feisty). libqt3-mt is necessary to get nvmixer working.
##########################################################################
[SIZE=5]**Step 2:**[/SIZE]
Add your user to the "audio" group. A few users have reported permission problems that prevents users that are not members of the audio group from using the sound card:
```
sudo adduser $USER audio
```Prevent intel8x0 from loading:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
``` Add the following line anywhere:```
blacklist snd_intel8x0
``` This will make sure nvmixer loads your saved settings on each boot: ```
gksudo gedit /etc/modprobe.d/nvsound.conf
``` Paste the following into it: ```
install nvsound /sbin/modprobe --ignore-install nvsound ; sleep 1; /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1 || :
remove nvsound { /usr/bin/nvmix-reg -f /etc/nvmixrc -S >/dev/null 2>&1 || : ; }; /sbin/modprobe -r --ignore-remove nvsound
``` [SIZE=4][COLOR=Blue]**Reboot** before you continue[/COLOR][/SIZE] to make sure intel8x0 is not loaded. It will prevent nvsound from loading properly.
##########################################################################
[SIZE=5]**Step 3:**[/SIZE]
Download nvidias driver package:
```
wget http://download.nvidia.com/XFree86/nforce/1.0-0310/NFORCE-Linux-x86-1.0-0310-pkg1.run

``` ##########################################################################
[SIZE=5]**Step 4:**[/SIZE]
Install the nvsound module:

[COLOR=Blue]**I. Kernels older than 2.6.16**[/COLOR] (got it to work in both [COLOR=Blue]**breezy and dapper**[/COLOR]):
```
sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run
``` If your internet connection is already working, you probably don't want to install nvnet.    
The installer should build the module for you.

**[COLOR=Blue]II. Kernel 2.6.16 or later[/COLOR]** needs some hacking before the module will build and load. This works in edgy, feisty, gutsy, and hardy (tested in alpha 3):

First unpack the installer files:
```
sh NFORCE-Linux-x86-1.0-0310-pkg1.run -x
```Download the attached file [nvsound-patch2.6.16-2.6.31.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=130521&stc=1&d=1254513615")   to your desktop and extract it to the folder that contains the extracted installer files:
```
mv ~/Desktop/nvsound-patch2.6.16-2.6.31.tar.gz ~/NFORCE-Linux-x86-1.0-0310-pkg1
cd  ~/NFORCE-Linux-x86-1.0-0310-pkg1
tar -xvvzf nvsound-patch2.6.16-2.6.31.tar.gz
```Apply the appropriate patches and start the installer:
[COLOR=Blue]**a) For kernels between 2.6.16 to 2.6.20 (Edgy and Feisty)**:[/COLOR]
```
./2.6.16-patch
sudo ./nforce-installer
```[COLOR=Blue]**b) For kernel 2.6.22 (Gutsy) or 2.6.24 (Hardy):**[/COLOR]
```
./2.6.24-patch
sudo ./nforce-installer
```[COLOR=Blue]**c) For kernel 2.6.27 **[/COLOR][COLOR=Blue]**(Intrepid)**[/COLOR][COLOR=Blue]** or 2.6.28 (Jaunty):**[/COLOR]
```
./2.6.27-patch
sudo ./nforce-installer
```[COLOR=Blue]**d) For kernel 2.6.31**[/COLOR][COLOR=Blue]** (Karmic development):**[/COLOR]
```
./2.6.31-patch
sudo ./nforce-installer
```The installer will build the module for you.
Make sure you [COLOR=Red]**do not try to build the nvnet module**[/COLOR], it will not work. 
To load the nvsound module without the need for reboot (as long as intel8x0 is not loaded):
```
sudo modprobe nvsound
```When this is done I can see "Dolby Digital" lighting up on my reciever and sound starts working.
##########################################################################
[SIZE=5]**Step 5:**[/SIZE]
**[COLOR=Blue]a) Change sound settings:[/COLOR]**
```
nvmixer

```I've set the speaker tab to 5.1 speakers and surround to clone, which means I get hardware encoded Dolby digital 5.1 output to my reciever (if the sound is only stereo the rear channels are just cloned from the front channels, and the center is not used). I get perfect passthrough of dolby surround and DTS from DVDs (using xine or mplayer)

[COLOR=Red] If you get this error:[/COLOR] "Nvsound: Unable to open the Mixer"; reboot and try again. If there was already a sound module loaded before you did step 4, nvmixer will not work unless you reboot.

[COLOR=Red] If you get this error:[/COLOR] "nvmixer: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory" (Happened to me in a gutsy tribe 5 fresh install, but not in gutsy final. Again in hardy alpha 3), run this:```
sudo ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
```**[COLOR=Blue]b) Save your new nvmixer settings (to keep your settings after shutdown / reboot):[/COLOR]**
```
sudo /usr/bin/nvmix-reg -f /etc/nvmixrc -S
```To manually load saved settings:
```
/usr/bin/nvmix-reg -f /etc/nvmixrc -L
``` ##########################################################################
[SIZE=5]**Step 6 (only gnome):**[/SIZE]
Get esd to play system sounds through oss instead of alsa (this is for Ubuntu/gnome, I don't think it is necessary in kubuntu/xubuntu):
```
killall esd
sudo apt-get update
sudo apt-get install esound esound-clients esound-common libesd0

``` [COLOR=Red]**Note****:**[/COLOR] This will uninstall the pulseaudio esd wrapper and the meta package Ubuntu-desktop, this should be safe but you'll probably want to **reinstall ubuntu-desktop before you upgrade to a new version of ubuntu**. 

Restart esd (from a "run application" dialog (Alt-f2), otherwise esd will die when the terminal is closed):
```
esd
```[SIZE=4][COLOR=Red][B]
WARNING: DON'T USE PULSEAUDIO IN HARDY OR later. It will cause your system to freeze as soon as it loads (but in gutsy it's ok).[/B][/COLOR][/SIZE]
(bugs have been reported but rejected by both the ubuntu and pulseaudio developers, the problem is probably in nvidia's code, which will never be fixed.)
**[SIZE=3][COLOR=Blue]Set all applications to use oss instead of alsa:[/COLOR][/SIZE]**
Run the following from a terminal and select oss in all menus. This will take care of many applications.
```
gstreamer-properties
``````
gnome-sound-properties
```Others, like mplayer and beep-media-player you'll need to set in the respective applications preferences.
Some applications, like gaim, does not have the option to use oss, but will work if you set it to use esd instead.
##########################################################################
[SIZE=5]**Step 7: (only gnome)**[/SIZE]
Get gdm to play sound through an oss capable player instead of aplay (this must be the least important step in this howto, it will only enable that silly little drum sound when the login screen is ready).
I got it working with mplayer (you'll of course need to install mplayer to get this working):
```
sudo gedit /usr/lib/gdmplay
``` make it look like this:```

#!/bin/sh
#/usr/bin/aplay -q -N $@ 2> /dev/null
mplayer -msglevel all=-1 -ao oss $@ 2> /dev/null
``` ##########################################################################

**[SIZE=4][COLOR=Red]Revert to your original settings:[/COLOR][/SIZE]**
```
sudo apt-get install libesd-alsa0 ubuntu-desktop
``` ```
sudo gedit /etc/modprobe.d/blacklist
```     delete or put a # before "blacklist snd_intel8x0"
```
sudo gedit /usr/lib/gdmplay
``` make it look like this:```

#!/bin/sh
/usr/bin/aplay -q -N $@ 2> /dev/null
#mplayer -msglevel all=-1 -ao oss $@ 2> /dev/null
```Manually uninstall the nforce drivers (the built-in uninstaller apparently does not work properly):
```
sudo rm -rf /usr/bin/nforce-installer /usr/bin/nforce-bug-report.sh /usr/bin/nvmixer /usr/bin/nvmix-reg /usr/local/lib/libnvopenal.a /usr/local/lib/libnvalut.a /lib/modules/`uname -r`/kernel/sound/oss/nvsound.ko /etc/modprobe.d/nvsound /usr/share/doc/nforce/ReleaseNotes.html /var/lib/nvidia-nforce/nforce_log_audio /var/lib/nvidia-nforce /var/log/nvidia-nforce-installer.log /etc/nvmixrc
```**[COLOR=Black]Reboot[/COLOR]**
#########################################################################
**Remaining problems:** Volume control does not work in any program, except those that have a software volume controller (but this may be because I use digital output through SPDIF, I remember having the same problem with some apps in windows if they were set to use SPDIF)
[B][SIZE=5]
[COLOR=Blue] Get sound to work with flash 9:[/COLOR][/SIZE]
[Check this post]("http://www.ubuntuforums.org/showpost.php?p=1716845&postcount=61") (Thanks to Pseudonym for sorting it out for us.)

Acknowledgements:[/B]
Some of the steps are directly ripped from other posts on these forums (thank you girls and boys). Other parts I figured out by trial and error with help of nvidias cryptic [release notes]("http://download.nvidia.com/XFree86/nforce/1.0-0310/ReleaseNotes.html"). The hack for making the module build properly on kernel 2.6.17 I ripped from post #3 in [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=72264") and the second hack to get the module to load without errors I figured out my self with some help from [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=69012").

---

### Post by re-negade on 2006-09-10
THANKS!!!  :) :D :biggrin: \\:D/ \\:D/ :KS

---

### Post by HAARP on 2006-09-13
In the name of a friend of mine who has Soundstorm: Thanks for this!!

---

### Post by jocko on 2006-09-17
I just realized a mistake in the install procedure for newer kernels. The howto is updated to correct that. (nvmixer only get installed from the installer, not by "make install").

---

### Post by jocko on 2006-09-18
Just one more update. Added one thing under "step 2" that is necessary to keep the settings after reboot. Hope this helps anyone.

---

### Post by mouse256 on 2006-09-21
Is this also working on kernel 2.6.18? I can't get it working with that kernel...

---

### Post by jocko on 2006-09-21
> **mouse256 said:**
> Is this also working on kernel 2.6.18? I can't get it working with that kernel...

I haven't tried it in 2.6.18. Do you get any error messages when you try to install it?

---

### Post by Hansi on 2006-09-23
Hello, 

I just realized this good Howto and I don't have any problems to install the Nvidia nForce SoundStorm APU. But, now I have a problem... I have a analog 5.1 input system sorround system, and I don't do activate de subwoofer... The wizard of the nvmixer don't work, and I don't turn on this option (to activate the 5.1 sorround sound) --> LFE Crossover Frequency. 

I using a ubuntu 6.0.6.1 LTS with 2.6.15-27-k7 kernel, and Nvidia GeForce 6800 installed on this. 

Any suggestions? 


PD: Sorry for my english...and thanks for the pacience to read this!  xD

---

### Post by jocko on 2006-09-24
> **Hansi said:**
> Hello, 

I just realized this good Howto and I don't have any problems to install the Nvidia nForce SoundStorm APU. But, now I have a problem... I have a analog 5.1 input system sorround system, and I don't do activate de subwoofer... The wizard of the nvmixer don't work, and I don't turn on this option (to activate the 5.1 sorround sound) --> LFE Crossover Frequency. 

I using a ubuntu 6.0.6.1 LTS with 2.6.15-27-k7 kernel, and Nvidia GeForce 6800 installed on this. 

Any suggestions? 


PD: Sorry for my english...and thanks for the pacience to read this!  xD

If I understood you correctly I have the same problem. Some of the options in nvmixer are greyed out, and not possible to change. The speaker wizard doesn't work, and there is no way to activate LFE or move the LFE slider.
I think one way to activate LFE would be to manually edit the file that contains the nvmixer settings.
Try this:
```
sudo gedit /etc/nvmixrc
```Find these two lines:
```
LfeSet:0
LfeSlider:0
```Try changing to:```

LfeSet:1
LfeSlider:200
```Save the file. To load the new settings:```
sudo /usr/bin/nvmix-reg -f /etc/nvmixrc -L >/dev/null 2>&1
```
NOTE: I don't know what value LfeSlider should have, you'll have to find it out by trial and error.

[COLOR=Red]Edit:[/COLOR] I've tried this myself, and the LFE slider actually works. However I do not notice that it actually does anything (but that may be because I use digital output?).
If it works, save the new settings of the slider by:
```
sudo /usr/bin/nvmix-reg -f /etc/nvmixrc -s >/dev/null 2>&1
```Let us know if it works

Good luck

---

### Post by pseudonym on 2006-09-25
Just wanted to say thanks for your great howto! I am now running a custom 2.6.17 kernel on Xubuntu Dapper, and the nvsound driver compiled without issues and is working perfectly.

Like you I only use S/PDIF output, and when I saw the Dolby Digital LED light up on my Creative 5.1 digital speakers, I was indeed a happy chappy!

I have an ASUS A7N8X Deluxe M/B which I don't plan on upgrading any time soon. Before I read your post I was resigned to switching to alsa when the next flavour of Ubuntu comes out, or when Debian Etch gets released (nothing against alsa, of course, just that it only half works with Soundstorm chips). Now I no longer have to.

Thanks again!

---

### Post by jocko on 2006-09-25
I'm glad I could help!:D

---

### Post by rickc on 2006-09-26
Hello, I'm trying to run this, but I can't seem to get the right headers. 
I used "uname -r" I'm running 2.6.12-10-386 but when I input

> sudo aptitude install build-essential libqt3-mt linux-2.6.12-10-386 linux-headers-2.6.12-10-386 I get this > Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
**Couldn't find any package whose name or description matched "linux-2.6.12-10-386"**
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done


Any ideas on why? thanks in advance RickC


**EDIT
 I tried > apt-get install build-essential

ad it sez "build-essential is already the newest version."
So why does it fail?
Maybe I fell apart before that, so I'll post the log.
> nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Tue Sep 26 19:26:41 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.12-10-386 (buildd@terranova) (gcc version
   3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Fri Sep 15
   16:31:49 UTC 2006
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.12-10-386/build'
-> Kernel output path: '/lib/modules/2.6.12-10-386/build'
-> Performing cc_version_check with CC="cc".
-> gcc-version-check failed:
   
   You appear to be compiling the NVIDIA kernel module with a different compile
   r than the one that was used to compile the running kernel.  This may be fin
   e, but there are cases where this can lead to instability.  The compiler use
   d to compile the kernel was gcc 3.4; the current compiler is gcc 4.0.
   
   If you know what you are doing and want to ignore the gcc version check, sel
   ect "No" to continue installation.  Otherwise, select "Yes" to abort install
   ation, set the CC environment variable to the name of the compiler used to c
   ompile your kernel, and restart installation.  Abort now? (Answer: Yes)
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).


Any ideas?
thanks in advance RickC

---

### Post by jocko on 2006-09-27
> **rickc said:**
> Hello, I'm trying to run this, but I can't seem to get the right headers. 
I used "uname -r" I'm running 2.6.12-10-386 but when I input

 I get this 

Any ideas on why? thanks in advance RickC


**EDIT
 I tried 
ad it sez "build-essential is already the newest version."
So why does it fail?
Maybe I fell apart before that, so I'll post the log.


Any ideas?
thanks in advance RickC


The packages you need to have are named "linux-386" and "linux-headers-386".
Those are meta packages that will make sure you have the latest kernel and headers.
From what I can see in the log you already have the correct headers for your kernel.

Installation seems to fail because you are using the wrong version of gcc.
The breezy kernel was built using gcc-3.4, but by some reason breezy had a higher version of gcc installed by default.
Try this:
```
sudo aptitude install build-essential libqt3-mt **linux-386 linux-headers-386** **gcc-3.4**
```(It will skip the packages you already have, so it doesn't hurt to include them all)

Then install by:```

[B]sudo CC=gcc-3.4
sudo export CC[/B]
sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run
```Good luck.

Let us know if it works.

---

### Post by rickc on 2006-09-27
I tried that too. I got this....

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done


yet when I try 
> sudo CC=gcc-3.4 
I get > sudo: CC=gcc-3.4: command not found


Not sure why... Hmmmm

---

### Post by mouse256 on 2006-09-27
Oh, I just want to notice I did got nvsound running on kernel 2.6.18 with these patches.  I'm not using ubuntu but archlinux, and it was a patch from archlinux that was added for kernel 2.6.16 that made it fail the first time.  Just adding these patches works perfectly, thanks :D

---

### Post by jocko on 2006-09-27
> **rickc said:**
> I tried that too. I got this....



yet when I try 
 
I get 

Not sure why... Hmmmm

Ok. I tried it myself, and it didn't work.
One thing that will work is this:```

sudo rm -rf /usr/bin/gcc && sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
sudo sh ~/NFORCE-Linux-x86-1.0-0310-pkg1.run
```

When it's done you can run the following to revert gcc to defaults:
```
sudo rm -rf /usr/bin/gcc && sudo ln -s /usr/bin/gcc-4.0 /usr/bin/gcc
```

I'll add this to the howto.

---

### Post by rickc on 2006-09-27
> **jocko said:**
> Ok. I tried it myself, and it didn't work.
One thing that will work is this:```

sudo rm -rf /usr/bin/gcc && sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc
sudo sh ~/NFORCE-Linux-x86-1.0-0310-pkg1.run
```

When it's done you can run the following to revert gcc to defaults:
```
sudo rm -rf /usr/bin/gcc && sudo ln -s /usr/bin/gcc-4.0 /usr/bin/gcc
```

I'll add this to the howto.

SWEET
Worked like a charm... Thanks JOCKO.... Now my Linux has REAL sound :D

---

### Post by the_glider_pilot on 2006-09-29
Hi

I really want this to work. But when I tried it it fails. I get to step 4. but the installer fails, this is the error I get.

ERROR: Unable to find the kernel source tree for the currently running
         kernel.  Please make sure you have installed the kernel source files
         for your kernel; on Red Hat Linux systems, for example, be sure you
         have the 'kernel-source' rpm installed.  If you know the correct
         kernel source files are installed, you may specify the kernel source
         path with the '--kernel-source-path' commandline option.


I am new to this linux thing, sorry if it is a stupid qouestion. but how do i resolve this?
I am running dapper, kernel 2.6.15-26-386

appreciate any help.


Edit: never mind... i fixed it

---

### Post by pseudonym on 2006-09-30
I noticed an issue which I had in previous Debian Sarge installations has just reappeared in Ubuntu, and I think it has something to do with the nvsound driver.

It appears that when I adjust the speaker configuration from 5.1 (my usual setup) to 2.0 , the stream that I am playing (usually digital TV or internet radio) will start constantly cutting out. But if I switch back to 5.1 mode and reboot, the problem goes away (I'm guessing it might also go away if I unload and reload nvsound, but I haven't tried that).

A bit more info about my setup -

Custom 2.6.17 kernel from kernel.org + 'ck' patches
nvsound as per this howto
all alsa modules/utilities disabled
nforce2 soundstorm
Creative DTT2500 5.1 Digital Speakers (primary output - S/PDIF))
stereo amp w/ 2 analogue speakers plugged into line out

Whenever I want to use the analogue speakers (usually for digital TV via TV-out) I have been changing the speaker setup in nvmixer to 2.0. This isn't strictly necessary, though, it's just a habit I've got into (I think now it's one I should get out of :) )

But the driver should be able to handle config changes on the fly, shouldn't it? The thing is, I don't see any helpful output in dmesg, other than the usual messages about upsampling or 'Unable to change the Channel, set back to Stereo', depending on the circumstances.

Maybe there is some verbose mode in the driver which could be turned on? If so, how?

Anyway, does anybody else notice this, know what's causing it, and/or know a way to fix it?

EDIT: Ignore this. The issue is not related to the nvsound driver. I haven't nailed it down 100% but it appears to be network/streaming related. It happened again recently when I was experimenting with getting some windows-designed web streams to run with various linux apps. Somehow my settings became corrupted and then my streams went into the constant rebuffering mentioned above. I couldn't be bothered spending time to troubleshoot it properly so I just reloaded my system from a partition image and was back to normal in no time. Lesson learned - download pod/vodcasts where possible instead of live streaming.

---

### Post by tux-gamer on 2006-09-30
I cann't compile it, under kernel 2.6.18, here the log:
1)On Mandriva2005
```
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sat Sep 30 15:42:44 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /root/tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86
-> Found package NVIDIA network driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> There appears to already be an audio driver installed on your system (versio
   n: 1.0-7).  As part of installing this driver (version: 1.0-7), the existing
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> /proc/version is Linux version 2.6.18 (root@localhost) (gcc version 3.4.3
   (Mandrakelinux 10.2 3.4.3-7mdk)) #1 Sat Sep 30 14:52:36 WIT 2006
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.18/source'
-> Kernel output path: '/lib/modules/2.6.18/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.18/source/Makefile | /bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.18/source
   SYSOUT=/lib/modules/2.6.18/build'...
   make -C /lib/modules/2.6.18/build \
   KBUILD_SRC=/usr/src/linux-2.6.18 \
   KBUILD_EXTMOD="/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-
   pkg1/nvsound/main" -f /usr/src/linux-2.6.18/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (         \
   echo;                                                                \
   echo "  ERROR: Kernel configuration is invalid.";            \
   echo "         include/linux/autoconf.h or include/config/auto.conf are miss
   ing.";       \
   echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.
   ";   \
   echo;                                                                \
   /bin/false)
   mkdir -p /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/n
   vsound/main/.tmp_versions
   rm -f /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvso
   und/main/.tmp_versions/*
   make -f /usr/src/linux-2.6.18/scripts/Makefile.build obj=/os/data-1/ftp/pub/
   SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvalinux.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandrake
   -linux-gnu/3.4.3/include -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-
   2.6.18/include -include include/linux/autoconf.h  -I/os/data-1/ftp/pub/Syste
   mDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msof
   t-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -ffrees
   tanding -I/usr/src/linux-2.6.18/include/asm-i386/mach-default -Iinclude/asm-
   i386/mach-default -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdecl
   aration-after-statement  -I/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x
   86-1.0-0310-pkg1/nvsound/main -O3 -Wall -march=athlon-xp -mtune=athlon-xp -W
   implicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wp
   ointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_RE
   MAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s
   )=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvalinux)"  -D"KBUILD_MODNAME=KBUILD_STR
   (nvsound)" -c -o /os/data-1
   /ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinu
   x.o /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsoun
   d/main/nvalinux.c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from include/linux/module.h:9,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvalinux.c:19:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvalinux.c:25:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvmixer.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandrake-
   linux-gnu/3.4.3/include -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2
   .6.18/include -include include/linux/autoconf.h  -I/os/data-1/ftp/pub/System
   DanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft
   -float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -ffreest
   anding -I/usr/src/linux-2.6.18/include/asm-i386/mach-default -Iinclude/asm-i
   386/mach-default -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdecla
   ration-after-statement  -I/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x8
   6-1.0-0310-pkg1/nvsound/main -O3 -Wall -march=athlon-xp -mtune=athlon-xp -Wi
   mplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpo
   inter-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_REM
   AP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvmixer)"  -D"KBUIL
   D_MODNAME=KBUILD_STR(nvsound)" -c -o /os/data-1/ftp/pub/SystemDanDriver/NFOR
   CE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmixer.o /os/data-1/ftp/pub/SystemD
   anDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmixer.c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:29,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmixer.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:564,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:35,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmixer.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvmain.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandrake-l
   inux-gnu/3.4.3/include -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.
   6.18/include -include include/linux/autoconf.h  -I/os/data-1/ftp/pub/SystemD
   anDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-
   float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -ffreesta
   nding -I/usr/src/linux-2.6.18/include/asm-i386/mach-default -Iinclude/asm-i3
   86/mach-default -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -Wdeclaration-after-statement  -I/os/data-1/ftp/pu
   b/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -O3 -Wall -mar
   ch=athlon-xp -mtune=athlon-xp -Wimplicit -Wreturn-type -Wswitch -Wformat -Wc
   har-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -
   Wno-cast-qual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_
   PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvmain)"
    -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /os/data-1/ftp/pub/SystemDanDr
   iver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.o /os/data-1/ftp/pub
   /SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from include/linux/module.h:9,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmain.c:27:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:564,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:35,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmain.c:29:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c: At top level:
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: error: syntax error before string constant
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: warning: type defaults to `int' in declaration of `MODULE_
   PARM'
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: warning: function declaration isn't a prototype
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: warning: data definition has no type or storage class
   make[4]: *** [/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-p
   kg1/nvsound/main/nvmain.o] Error 1
   make[3]: *** [_module_/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main] Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
```
2)On PClinuxOS-0.93a
```
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sat Sep 30 18:00:13 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : true
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /root/tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86
-> Found package NVIDIA network driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> Trying to remove loaded module nvsound
ERROR: An NVIDIA audio driver module 'nvsound' appears to already be loaded in
       your kernel, possibly because it is in use. Please be sure you have
       exited any audio applications and unloaded the driver before attempting
       to upgrade your driver.  If you have trouble unloading the driver, it is
       likely that an error has occured that has confused the usage count of
       the kernel module; the simplest remedy is to reboot your computer.
-> License accepted.
-> Skipping check for conflicting rpms.
-> Not probing for precompiled kernel interfaces.
-> Kernel source path: '/lib/modules/2.6.18/source'
-> Kernel output path: '/lib/modules/2.6.18/build'
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.18/source/Makefile | /bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.18/source
   SYSOUT=/lib/modules/2.6.18/build'...
   make -C /lib/modules/2.6.18/build \
   KBUILD_SRC=/os/linux/usr/src/linux-2.6.18 \
   KBUILD_EXTMOD="/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-
   pkg1/nvsound/main" -f /os/linux/usr/src/linux-2.6.18/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (         \
   echo;                                                                \
   echo "  ERROR: Kernel configuration is invalid.";            \
   echo "         include/linux/autoconf.h or include/config/auto.conf are miss
   ing.";       \
   echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.
   ";   \
   echo;                                                                \
   /bin/false)
   mkdir -p /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/n
   vsound/main/.tmp_versions
   rm -f /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvso
   und/main/.tmp_versions/*
   make -f /os/linux/usr/src/linux-2.6.18/scripts/Makefile.build obj=/os/data-1
   /ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvalinux.o.d  -nostdinc -isystem /usr/lib/gcc-lib/i586-mand
   rake-linux-gnu/3.3.1/include -D__KERNEL__ -Iinclude -Iinclude2 -I/os/linux/u
   sr/src/linux-2.6.18/include -include include/linux/autoconf.h  -I/os/data-1/
   ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -W
   undef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O
   2 -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march
   =i686 -ffreestanding -I/os/linux/usr/src/linux-2.6.18/include/asm-i386/mach-
   default -Iinclude/asm-i386/mach-default -fno-omit-frame-pointer -fno-optimiz
   e-sibling-calls  -I/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0
   310-pkg1/nvsound/main -O3 -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -
   Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD
   -Wno-cast-qual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR
   _PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvalinu
   x)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /os/data-1/ftp/pub/System
   DanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.o /os/data-1/
   ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux
   .c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from include/linux/module.h:9,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvalinux.c:19:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvalinux.c:25:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvmixer.o.d  -nostdinc -isystem /usr/lib/gcc-lib/i586-mandr
   ake-linux-gnu/3.3.1/include -D__KERNEL__ -Iinclude -Iinclude2 -I/os/linux/us
   r/src/linux-2.6.18/include -include include/linux/autoconf.h  -I/os/data-1/f
   tp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wu
   ndef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2
   -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i
   686 -ffreestanding -I/os/linux/usr/src/linux-2.6.18/include/asm-i386/mach-de
   fault -Iinclude/asm-i386/mach-default -fno-omit-frame-pointer -fno-optimize-
   sibling-calls  -I/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-031
   0-pkg1/nvsound/main -O3 -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wc
   har-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -
   Wno-cast-qual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_
   PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(
   nvmixer)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /os/data-1/ftp/pub/S
   ystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmixer.o /os/dat
   a-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmi
   xer.c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:29,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmixer.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:564,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:35,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmixer.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvmain.o.d  -nostdinc -isystem /usr/lib/gcc-lib/i586-mandra
   ke-linux-gnu/3.3.1/include -D__KERNEL__ -Iinclude -Iinclude2 -I/os/linux/usr
   /src/linux-2.6.18/include -include include/linux/autoconf.h  -I/os/data-1/ft
   p/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wun
   def -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 
   -pipe -msoft-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i
   686 -ffreestanding -I/os/linux/usr/src/linux-2.6.18/include/asm-i386/mach-de
   fault -Iinclude/asm-i386/mach-default -fno-omit-frame-pointer -fno-optimize-
   sibling-calls  -I/os/da
   ta-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -O3
   -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparenth
   eses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error
   -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUIL
   D_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvmain)"  -D"KBUILD_MODNAME=KBUIL
   D_STR(nvsound)" -c -o /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmain.o /os/data-1/ftp/pub/SystemDanDriver/NFORCE-
   Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from include/linux/module.h:9,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmain.c:27:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:564,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:35,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmain.c:29:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c: At top level:
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: error: syntax error before "int"
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: type defaults to `int' in declaration of `module_
   parm'
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: function declaration isn't a prototype
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: data definition has no type or storage class
   make[4]: *** [/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-p
   kg1/nvsound/main/nvmain.o] Error 1
   make[3]: *** [_module_/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main] Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.
```

I'am not using Ubuntu, I'am using Mandriva 2005 and PClinuxOS-0.93a.
In Mandriva 2005, i use gcc-3.4.3, but in PClinuxOS. I use gcc 3.3.1
My Motherboard using nforce2 mcp-t.

If you need more information, i will give you.

Please, help me to compile it.
Thanks before.

Best Regrads
Teguh


nb: Sory for my bad english.

---

### Post by tux-gamer on 2006-09-30
sory double post

---

### Post by Jason_25 on 2006-09-30
Check step #4 of this thread.

[http://www.ubuntuforums.org/showthread.php?t=253725&highlight=nvsound](http://www.ubuntuforums.org/showthread.php?t=253725&highlight=nvsound)

---

### Post by tux-gamer on 2006-10-01
That what i did, the problem is, when i change this line:
```
MODULE_PARM(vapu_enable, "i");
```
to:
```
module_param(vapu_enable, int, 0444);
```

I got this nforce-intaller.log:
```

   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c: At top level:
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: error: syntax error before "int"
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: type defaults to `int' in declaration of `module_
   parm'
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: function declaration isn't a prototype
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: data definition has no type or storage class
   make[4]: *** [/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-p
   kg1/nvsound/main/nvmain.o] Error 1

```

But, if i not change this line:
```
MODULE_PARM(vapu_enable, "i");
```

I got this nforce-installer.log:
```
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c: At top level:
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: error: syntax error before string constant
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: warning: type defaults to `int' in declaration of `MODULE_
   PARM'
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: warning: function declaration isn't a prototype
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: warning: data definition has no type or storage class
   make[4]: *** [/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-p
   kg1/nvsound/main/nvmain.o] Error 1
```

How to fix the Syntax error, or Any ideas.

edit: sSory, the nforce-installer.log on Mandriva 2005 in my first post, is wrong, this the right one:
```
 nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sat Sep 30 15:45:46 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /root/tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86
-> Found package NVIDIA network driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.18 (root@localhost) (gcc version 3.4.3
   (Mandrakelinux 10.2 3.4.3-7mdk)) #1 Sat Sep 30 14:52:36 WIT 2006
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.18/source'
-> Kernel output path: '/lib/modules/2.6.18/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.18/source/Makefile | /bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.18/source
   SYSOUT=/lib/modules/2.6.18/build'...
   make -C /lib/modules/2.6.18/build \
   KBUILD_SRC=/usr/src/linux-2.6.18 \
   KBUILD_EXTMOD="/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-
   pkg1/nvsound/main" -f /usr/src/linux-2.6.18/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (         \
   echo;                                                                \
   echo "  ERROR: Kernel configuration is invalid.";            \
   echo "         include/linux/autoconf.h or include/config/auto.conf are miss
   ing.";       \
   echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.
   ";   \
   echo;                                                                \
   /bin/false)
   mkdir -p /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/n
   vsound/main/.tmp_versions
   rm -f /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvso
   und/main/.tmp_versions/*
   make -f /usr/src/linux-2.6.18/scripts/Makefile.build obj=/os/data-1/ftp/pub/
   SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvalinux.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandrake
   -linux-gnu/3.4.3/include -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-
   2.6.18/include -include include/linux/autoconf.h  -I/os/data-1/ftp/pub/Syste
   mDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstric
   t-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msof
   t-float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -ffrees
   tanding -I/usr/src/linux-2.6.18/include/asm-i386/mach-default -Iinclude/asm-
   i386/mach-default -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdecl
   aration-after-statement  -I/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x
   86-1.0-0310-pkg1/nvsound/main -O3 -Wall -march=athlon-xp -mtune=athlon-xp -W
   implicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wp
   ointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_RE
   MAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s
   )=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvalinux)"  -D"KBUILD_MODNAME=KBUILD_STR
   (nvsound)" -c -o /os/data-1
   /ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinu
   x.o /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsoun
   d/main/nvalinux.c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from include/linux/module.h:9,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvalinux.c:19:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvalinux.c:25:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvmixer.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandrake-
   linux-gnu/3.4.3/include -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2
   .6.18/include -include include/linux/autoconf.h  -I/os/data-1/ftp/pub/System
   DanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict
   -prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft
   -float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -ffreest
   anding -I/usr/src/linux-2.6.18/include/asm-i386/mach-default -Iinclude/asm-i
   386/mach-default -fno-omit-frame-pointer -fno-optimize-sibling-calls -Wdecla
   ration-after-statement  -I/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x8
   6-1.0-0310-pkg1/nvsound/main -O3 -Wall -march=athlon-xp -mtune=athlon-xp -Wi
   mplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpo
   inter-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_REM
   AP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DM
   ODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvmixer)"  -D"KBUIL
   D_MODNAME=KBUILD_STR(nvsound)" -c -o /os/data-1/ftp/pub/SystemDanDriver/NFOR
   CE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmixer.o /os/data-1/ftp/pub/SystemD
   anDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmixer.c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:29,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmixer.c:14:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:564,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:35,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmixer.c:14:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/.nvmain.o.d  -nostdinc -isystem /usr/lib/gcc/i586-mandrake-l
   inux-gnu/3.4.3/include -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.
   6.18/include -include include/linux/autoconf.h  -I/os/data-1/ftp/pub/SystemD
   anDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-
   prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -O2 -pipe -msoft-
   float -mpreferred-stack-boundary=2 -fno-unit-at-a-time -march=i686 -ffreesta
   nding -I/usr/src/linux-2.6.18/include/asm-i386/mach-default -Iinclude/asm-i3
   86/mach-default -fno-omit-frame-pointer -f
   no-optimize-sibling-calls -Wdeclaration-after-statement  -I/os/data-1/ftp/pu
   b/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -O3 -Wall -mar
   ch=athlon-xp -mtune=athlon-xp -Wimplicit -Wreturn-type -Wswitch -Wformat -Wc
   har-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -
   Wno-cast-qual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_
   PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvmain)"
    -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /os/data-1/ftp/pub/SystemDanDr
   iver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.o /os/data-1/ftp/pub
   /SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c
   In file included from include/linux/list.h:8,
                    from include/linux/lockdep.h:12,
                    from include/linux/spinlock_types.h:12,
                    from include/linux/spinlock.h:78,
                    from include/linux/capability.h:45,
                    from include/linux/sched.h:44,
                    from include/linux/module.h:9,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmain.c:27:
   include/linux/prefetch.h: In function `prefetch_range':
   include/linux/prefetch.h:62: warning: pointer of type `void *' used in arith
   metic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:564,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvhw.h:35,
                    from /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmain.c:29:
   include/asm/io.h: In function `check_signature':
   include/asm/io.h:245: warning: wrong type argument to increment
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c: At top level:
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: error: syntax error before "int"
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: type defaults to `int' in declaration of `module_
   parm'
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: function declaration isn't a prototype
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: data definition has no type or storage class
   make[4]: *** [/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-p
   kg1/nvsound/main/nvmain.o] Error 1
   make[3]: *** [_module_/os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main] Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.

```

nb: Sory for my bad english.

---

### Post by jocko on 2006-10-01
> **tux-gamer said:**
> That what i did, the problem is, when i change this line:
```
**MODULE_PARM**(vapu_enable, "i");
```to:
```
**module_param**(vapu_enable, int, 0444);
```I got this nforce-intaller.log:
```

 /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: error: **syntax error before "int"**
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2191: warning: type defaults to `int' in declaration of [B]`module_
   parm'[/B]
   

```But, if i not change this line:
```
MODULE_PARM(vapu_enable, "i");
```I got this nforce-installer.log:
```
    /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: error: syntax error before string constant
   /os/data-1/ftp/pub/SystemDanDriver/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvmain.c:2190: warning: type defaults to `int' in declaration of [B]`MODULE_
   PARM'[/B]
   
```How to fix the Syntax error, or Any ideas.

It took me a while, but I managed to reproduce your error. Make sure you change the line in nvmain.c to **exactly** what the howto says. It should be '**module_param**', not 'module_parm' or 'MODULE_PARM'.

Good luck!

---

### Post by tux-gamer on 2006-10-01
Wow, thanks a lot. :D
Now i can compile it under PCLinuxOS-0.93a + kernel 2.6.18 and with gcc-3.3.1.
I will try compile it under Mandriva 2005 soon.

Many thanks to you. :D

Best regards.
Teguh

nb:Sory for my bad english.

---

### Post by tux-gamer on 2006-10-03
it work on My Mandriva2005 + kernel-2.6.18 + gcc-3.4.3. 
Thanks a lot JOCKO.

Best regrads,
Teguh.

nb: Sory for my bad english.

---

### Post by PRGUY85 on 2006-10-05
I am able to open nvmixer yet when I enter nvmixer on the terminal it displays lots of Unabke to open the Mixer messages.  I go into the NVMixer window and try to set the volumes but everytime I click something I get the following:

Volume Bit Failed

I am using Edgy Eft with kernel 2.6.17-10-386.  My motherboard is a Asus A7N8x-deluxe with Nvidia nforce2 soundstorm.  I followed the instructions word for word...

Any ideas?

---

### Post by PRGUY85 on 2006-10-05
Anyone?

---

### Post by jocko on 2006-10-05
> **PRGUY85 said:**
> Anyone?

Are you sure nvsound is loaded?
Check what output you get if you run ```
lsmod | grep nvsound
``` and ```
lsmod | grep intel8x0
``` in a terminal.

---

### Post by PRGUY85 on 2006-10-05
lsmod | grep nvsound output:

nvsound              1543224  0 
soundcore               9952  2 nvsound,snd

lsmod | grep intel8x0 output:

 lsmod | grep intel8x0
snd_intel8x0           33436  3 
snd_ac97_codec         96672  1 snd_intel8x0
snd_pcm                80520  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
snd                    55428  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer

---

### Post by jocko on 2006-10-05
> **PRGUY85 said:**
> 
 lsmod | grep intel8x0
snd_intel8x0           33436  3 
snd_ac97_codec         96672  1 snd_intel8x0
snd_pcm                80520  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_page_alloc         10504  2 snd_intel8x0,snd_pcm
snd                    55428  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer

Your problem is that you still have the intel8x0 module loaded.
Did you really do everything in my howto? Looks like you missed **step 2**, or maybe you did not **reboot**?

---

### Post by PRGUY85 on 2006-10-05
Yes I did both and just checked the two files edited on step 2 and they seem allright.  I rebooted many times already.  Any ideas?

---

### Post by jocko on 2006-10-05
> **PRGUY85 said:**
> Yes I did both and just checked the two files edited on step 2 and they seem allright.  I rebooted many times already.  Any ideas?

Weird... Could you show me the contents of your /etc/modprobe.d/blacklist?

---

### Post by PRGUY85 on 2006-10-05
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

blacklist snd_intel8x0


Also when I type sudo gedit /etc/modprobe.d/blacklist I get this on the terminal before getting gedit window:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'nForce2'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

---

### Post by jocko on 2006-10-05
> Also when I type sudo gedit /etc/modprobe.d/blacklist I get this on the terminal before getting gedit window:

ALSA lib confmisc.c:670:(snd_func_card_driver) cannot find card 'nForce2'
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:391:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1070:(snd_func_refer) error evaluating name
ALSA lib conf.c:3479:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3947:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2146:(snd_pcm_open_noupdate) Unknown PCM default

The file looks exactly like mine, so apparently something else is causing your problem. I'm not sure how to help you figure it out, I'm definetly not an expert.

I think the alsa errors are caused by the intel8x0 module (nvsound uses oss instead of alsa).

---

### Post by PRGUY85 on 2006-10-05
Fixed it.  I had a set Nvidia nforce 2 sound driver on my Sounds section of Ubuntu.  I put Autodetect on everything and now it works flawlessly.  Will this give true 5.1 sound on movies or will it just throw out same sound through all speakers?

Thanks a bunch.  Great guide.

---

### Post by jocko on 2006-10-05
> **PRGUY85 said:**
> Fixed it.  I had a set Nvidia nforce 2 sound driver on my Sounds section of Ubuntu.  I put Autodetect on everything and now it works flawlessly.  Will this give true 5.1 sound on movies or will it just throw out same sound through all speakers?

Thanks a bunch.  Great guide.

Cool.
I get true 5.1 sound if the audio track of the video is 5.1.

---

### Post by PRGUY85 on 2006-10-07
I am using a 5.1 DVD and getting same sound from all speakers.  I dont have a digital output to my speakers though since I dont have an external receiver or anything.

---

### Post by opticalia on 2006-10-07
I have DFI NFII U400SG-AGF motherboard

[http://us.dfi.com.tw/Product/product_search_result_us.jsp?PRODUCT_ID0B=3244&SITE=US]("http://us.dfi.com.tw/Product/product_search_result_us.jsp?PRODUCT_ID0B=3244&SITE=US")

does this have soundstorm support?
manual says "South bridge: nForce2 MCP GIG"
but not MCP-t :-k

---

### Post by jocko on 2006-10-07
> **opticalia said:**
> I have DFI NFII U400SG-AGF motherboard

[http://us.dfi.com.tw/Product/product_search_result_us.jsp?PRODUCT_ID0B=3244&SITE=US](http://us.dfi.com.tw/Product/product_search_result_us.jsp?PRODUCT_ID0B=3244&SITE=US)

does this have soundstorm support?
manual says "South bridge: nForce2 MCP GIG"
but not MCP-t :-k

Sorry, but I think you only have the AC'97 codec. According to DFI's [description]("http://us.dfi.com.tw/Product/xx_product_spec_details_r_us.jsp?PRODUCT_ID=3244&CATEGORY_TYPE=MB&SITE=US"):
> Audio
AC’97 CODEC
S/PDIF-in/out interface 
6-channel audio output


---

### Post by Icarosaurus on 2006-10-17
Thank you for the howto!
I'm using kubuntu Dapper with a 2.6.15-27 kernel and kde seems to autodetect the proper sound server without modifying any file as in Gnome.
It seems it doesn't need ESD too...
I have the rear speakers working for now, I just have to try some 5.1 DVD :)
Thank you again

---

### Post by Icarosaurus on 2006-10-17
I've got an analog 5.1 speaker system.
I have a strange problem...but I think I'm not the only one.

All the drivers I have installed under Windowz had the Center/LFE channell swapped to the Rear Channells.
So I just plugged my speakers' jacks reversed on the mainboard (Black plugged into orange, orange plugged into black), and all worked fine.
Maybe it's some bug in drivers or in the colours of the holes in the mainboard.

Now under my dapper when I play an mp3 I have the same situation, while when I play a 5.1 film I have to plug the jacks in the correct place 'cause I hear center in the left/rear channell.

Moreover when I unplug the center and rear jacks I hear a louder sound from the subwoofer while when I connect all the jacks the sound in the subwoofer seems to be less loud.
Changing the LfeSet and LfeSlider voices in /etc/nvmixrc doesn't seem to work :(

Anyone can help me?? ](*,)

---

### Post by daverab on 2006-10-19
Soundstorm+flash 9 = no workie for me.


Anyone have this issue out there. I know on my laptop it somehow muted the PCM control (a lil' important) and I'm wondering if that's the issue I'm having.

Also, gaim isn't generating sounds.

When I run firefox under terminal, I get this when trying to play a youtube vid....

```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
```

Over and over and over. Something's failing, and I don't know what.

---

### Post by jocko on 2006-10-20
> **daverab said:**
> Soundstorm+flash 9 = no workie for me.


Anyone have this issue out there. I know on my laptop it somehow muted the PCM control (a lil' important) and I'm wondering if that's the issue I'm having.

Also, gaim isn't generating sounds.

When I run firefox under terminal, I get this when trying to play a youtube vid....

```
ALSA lib confmisc.c:672:(snd_func_card_driver) cannot find card '0'
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_card_driver returned error: No such device
ALSA lib confmisc.c:392:(snd_func_concat) error evaluating strings
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_concat returned error: No such device
ALSA lib confmisc.c:1072:(snd_func_refer) error evaluating name
ALSA lib conf.c:3493:(_snd_config_evaluate) function snd_func_refer returned error: No such device
ALSA lib conf.c:3962:(snd_config_expand) Evaluate error: No such device
ALSA lib pcm.c:2102:(snd_pcm_open_noupdate) Unknown PCM default
ALSA lib pcm_hw.c:1305:(_snd_pcm_hw_open) Invalid value for card
```Over and over and over. Something's failing, and I don't know what.

soundstorm is an oss driver, not alsa. You have to make sure the apps are set to use either oss or ESD for sound. In gaim (at least 2.0beta3) go to tools-->settings-->sound and select esd.

I don't know how to fix sound in flash, but maybe [flash 9]("http://www.ubuntuforums.org/showthread.php?t=279990") is better than flash 7?
[COLOR=Red]Edit: [/COLOR]I just saw you posted this issue in a flash 9 thread, so I guess you've already tried everything.

---

### Post by mouse256 on 2006-10-20
> **daverab said:**
> Soundstorm+flash 9 = no workie for me.
...
Same problem here, downgraded back to flash 7.  I hope adobe will fix this or someone can find a patch...

---

### Post by daverab on 2006-10-20
Well thanks for the instruction on ESD jocko. That did work for gaim. Now only if I could figure out what the heck is going on with flash 9.

I so want it working on this machine because of the synching issue being fixed with audio.

---

### Post by Jason_25 on 2006-10-20
> **mouse256 said:**
> Same problem here, downgraded back to flash 7.  I hope adobe will fix this or someone can find a patch...
You may need to use the aoss wrapper.

---

### Post by metalfreak666 on 2006-10-21
Hi! When i do this howto on Edgy RC amd 64 i get  :
------------------
                   from /home/bart/NFORCE-Linux-x86_64-1.0-0310-pkg1/nvsound/m
   ain/nvmain.c:29:
   include/asm-generic/pci-dma-compat.h: In function ‘pci_map_page’:
   include/asm-generic/pci-dma-compat.h:49: warning: pointer of type ‘void *
   &#65533;&#65533; used in arithmetic
   /home/bart/NFORCE-Linux-x86_64-1.0-0310-pkg1/nvsound/main/nvmain.c: At top l
   evel:
   /home/bart/NFORCE-Linux-x86_64-1.0-0310-pkg1/nvsound/main/nvmain.c:2191: err
   or: expected ‘)’ before ‘int’
   make[4]: *** [/home/bart/NFORCE-Linux-x86_64-1.0-0310-pkg1/nvsound/main/nvma
   in.o] Error 1
   make[3]: *** [_module_/home/bart/NFORCE-Linux-x86_64-1.0-0310-pkg1/nvsound/m
   ain] Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).
------

:o(

---

### Post by daverab on 2006-10-21
> **Jason_25 said:**
> You may need to use the aoss wrapper.

So...use AOSS for the FIREFOX_DSP value? I've tried that myself without much luck.

---

### Post by mouse256 on 2006-10-21
> **metalfreak666 said:**
> Hi! When i do this howto on Edgy RC amd 64 i get  
...
Why would you do that? If you have amd 64 you'll have no nforce 2. As far as I know the nvsound drivers only have an advantage above the kernel drivers for use with nforce 2 with soundstorm.
I suggest to use the kernel intel_8x0 drivers with alsa

---

### Post by phoqueyoo on 2006-10-21
The flash 9 plugin is alsa only. I've tried using the aoss package to fix it with no luck so far. I'm also getting the alsa errors with gedit. BTW if anyone wants the get the nvnet module to work with 2.6.17 I can post what I did.

---

### Post by Icarosaurus on 2006-10-21
Sorry for repeating the question...
I have an Abit AN-7 Mobo, and I experience that center channells are swapped to rear channells while watching 5.1 films... no other has the same problem here??

---

### Post by jocko on 2006-10-22
> **Icarosaurus said:**
> Sorry for repeating the question...
I have an Abit AN-7 Mobo, and I experience that center channells are swapped to rear channells while watching 5.1 films... no other has the same problem here??

Sorry, I haven't got any idea what could be the cause of that. Does it happen in all movieplayers? According to [this]("http://www.nforcershq.com/forum/nvsound-installed-but-wrong-speakers-vt59748.html") there is (or was?) a bug in xine causing the same problem. If you use mplayer I guess you could find a workaround [here]("http://www.mplayerhq.hu/DOCS/HTML/en/advaudio.html") (there is a section about copying/moving sound channels).

---

### Post by Icarosaurus on 2006-10-22
Thank you very very much for your hints, Jocko.

On Windoz the problem is ALWAYS present: i have to stay all the time with jacks inverted and all works fine. I don't know if it's a bug of the AN7 Mobo, but I had a NF7-S and there was the same problem.

In my Kubuntu Dapper, the problem comes only when i play 5.1 streams even with MPLAYER...so I guess it's not a Xine bug.
With 2-channels I hear the rear speakers correctly WITH JACKS INVERTED on the MoBo.So I have to switch them for listening to a 5.1 stream.

I could try that work-around on Mplayer...but it's only a workaround: I'm afraid there's something wrong on NVIDIA drivers...

I could try with Gnome too: maybe there's something wrong in my kde setup...

Anyway I can't hear a loud subwoofer sound and I can't control it even enabling LFE slide in the configuration file.

](*,) 

I hope someone around the world solved the problem :-k

---

### Post by daverab on 2006-10-22
How do you revert back to the intel driver? I'm having issues following the directions. I followed everything, but I still only have capture on my volume control. I think I have to get rid of the actual NVidia driver, but I have no clue how to do so.


EDIT: Yeah, I got it back. There's some extra options if people just want 5.1 sound on the intel driver in the preferences. That's all I wanted from the nvidia driver, and now I don't really need it. Flash 9 works correctly.

For people trying to go back to the intel driver, and the originator of this thread, you might want to add the following to the steps, because it is required. Without it, the intel module won't load correctly and the nvsound one will override it.

```
sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run --uninstall
```

---

### Post by jocko on 2006-10-25
> **daverab said:**
> 
For people trying to go back to the intel driver, and the originator of this thread, you might want to add the following to the steps, because it is required. Without it, the intel module won't load correctly and the nvsound one will override it.

```
sudo sh NFORCE-Linux-x86-1.0-0310-pkg1.run --uninstall
```

Ok, I've added it to the end of my howto.

---

### Post by joincamp on 2006-10-28
> **jocko said:**
> Ok, I've added it to the end of my howto.

has anyone figured out how to get firefox's sound to work for this?  i tried uninstalling it at least to get firefox sound for a little bit, but it wont uninstall.  when i run the script with --uninstall i get:
```
There is no NVIDIA /objcopy driver currently installed.
```

---

### Post by pseudonym on 2006-10-30
> **joincamp said:**
> has anyone figured out how to get firefox's sound to work for this?  i tried uninstalling it at least to get firefox sound for a little bit, but it wont uninstall.  when i run the script with --uninstall i get:
```
There is no NVIDIA /objcopy driver currently installed.
```

It's common that this driver won't uninstall automatically. In this case, you need to delete all the files manually. On my system (and most probably yours if you followed this howto) the list of files is - ```
/usr/bin/nforce-installer
/usr/bin/nforce-bug-report.sh
/usr/bin/nvmixer
/usr/bin/nvmix-reg
/usr/local/lib/libnvopenal.a
/usr/local/lib/libnvalut.a
/usr/share/doc/nforce//ReleaseNotes.html
/lib/modules/<kernel-name>/kernel/sound/oss/nvsound.ko
/var/lib/nvidia-nforce
/var/lib/nvidia-nforce/nforce_log_audio
/var/log/nvidia-installer.log
/var/log/nforce-installer.log
/etc/modprobe.d/nvsound
``` Upon reboot, you should have ALSA back, but you will probably need to change your sound settings and/or some of your apps to use it.

---

### Post by pseudonym on 2006-10-30
I just installed the Flash 9 and hey, guess what? No sound! I knew the default support is for ALSA but I thought it would be easy to tell it to use OSS. But, apparently not. According to the [Adobe Labs website]("http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux"), OSS support in Flash 9 can only be enabled through the 'flashsupport' layer, which you need to build separately. And then it only mentions support for opensound.com drivers, not OSS Free (?) which AFAIK the nvsound module is.

Has anyone here managed to build the flashsupport library and got it working with Soundstorm?

---

### Post by joincamp on 2006-10-30
> **pseudonym said:**
> I just installed the Flash 9 and hey, guess what? No sound! I knew the default support is for ALSA but I thought it would be easy to tell it to use OSS. But, apparently not. According to the [Adobe Labs website]("http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux"), OSS support in Flash 9 can only be enabled through the 'flashsupport' layer, which you need to build separately. And then it only mentions support for opensound.com drivers, not OSS Free (?) which AFAIK the nvsound module is.

Has anyone here managed to build the flashsupport library and got it working with Soundstorm?

If you ever get this working or have any updates, please post about it in this thread.  Thanks.

---

### Post by pseudonym on 2006-11-05
OK, I've sorted out the Flash & OSS issue. It's very simple to build and install the flashsupport library, and it works well. I've tested it on a variety of websites with Flash audio content, and they all playback sound clearly (depending on the quality of the original source) and with no A/V sync issues. I do also notice that Flash sites seem to load quicker in Beta 9, although using the [Flashblock]("https://addons.mozilla.org/firefox/433/") Firefox extension no doubt helps.

I should also point out that I tested this on my Debian machine as my Ubuntu one is temporarily out of action. The necessary packages have the same names, though, so there shouldn't be any problems.

The flashsupport library will enable OSS support in Flash 9 Beta for users of the nvidia nforce-audio driver mentioned in this thread, as well as users using other OSS drivers for their sound hardware, such as those from [Opensound]("http://www.opensound.com/").

To build the flashsupport library, follow these steps (they closely follow the 'official' instuctions at the [Adobe Labs website]("http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux")). It is assumed that you already have the Beta installed as a Firefox/IceWeasel plugin. If you do not currently have Flash 9 Beta on your system, follow the instructions at the [Adobe Labs website]("http://labs.adobe.com/technologies/flashplayer9/") to install it first -

1. Verify that you have these packages installed - ```
build-essential; libicu34; libicu34-dev; libssl0.9.8; libssl-dev; linux-headers-<kernel name> package for your kernel (or unpacked and symlinked kernel source tree in /usr/src if you built your kernel from scratch)
```

2. Download the flashsupport source code from [here]("http://www.kaourantin.net/flashplayer/flashsupport.c") (right-click and 'Save-As' - the file you have should be called 'flashsupport.c').

3. (Optional) If you don't wish to enable the SSL or ICU support, you can just open up flashsupport.c in your favourite text editor and comment out the '#define OPENSSL" and '#define ICU" options near the top of the file, then save & exit.

4. Copy flashsupport.c to /tmp

5. Open up a terminal and issue these commands - ```
cd /tmp
cc -shared -O2 -Wall -Werror -licuuc -lssl flashsupport.c -o libflashsupport.so
ldd libflashsupport.so
``` Note that the file you create with the second command is 'libflashsupport.so' not 'libflashplayer.so', as per the [Adobe Labs website]("http://labs.adobe.com/wiki/index.php/Flash_Player:Additional_Interface_Support_for_Linux"). This is an error that has been pointed out in the 'Discussion' section of the flashsupport page but not yet updated on it as of this writing.

6. Now issue this command as sudo - ```
sudo cp libflashsupport.so /usr/lib
```

7. Shut down Firefox/IceWeasel if you have it running, then restart it. Browse to a Flash site with audio and enjoy sound in Flash 9 Beta!

NB. If someone wishes to copy or move this HOWTO to a separate thread, please feel free to do so.

---

### Post by jocko on 2006-11-05
Excellent! Thank you, pseudonym!
I'll put a link to it in my howto.

---

### Post by Darthash on 2006-11-08
[SIZE="4"]Hey everyone, 

I have a AN7 motherboard, and I am kinda having some trouble installing the  Nforce soundstream, I follow the howto to a tee, I get to the end of step 4,

Code:

cd ~/NFORCE-Linux-x86-1.0-0310-pkg1 sudo ./nforce-installer

And i received this error while it was trying to build the module.

ERROR: Unable to build the NVIDIA kernel module.

and when i go to the log I get this output,



[HTML]
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Wed Nov  8 00:34:40 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA network driver for Linux-x86 (1.0-13)
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA network driver for Linux-x86
-> Checking for loaded module nvnet
-> Checking for loaded module forcedeth
-> Trying to remove loaded module forcedeth
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.17-10-generic (root@vernadsky) (gcc
   version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct
   13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.17-10-generic/build'
-> Kernel output path: '/lib/modules/2.6.17-10-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.17-10-generic/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvnet.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvnet; make clean'...
   rm -f *.ko *mod.* *.cmd nvenet.o nvenetif.o nvnet.o *~ core
-> Building kernel module:
   executing: 'cd ./nvnet; make module SYSSRC=/lib/modules/2.6.17-10-generic/bu
   ild SYSOUT=/lib/modules/2.6.17-10-generic/build'...
   make -C /lib/modules/2.6.17-10-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.17-10-generic \
   	KBUILD_EXTMOD="/home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet" -f /usr/src/
   linux-headers-2.6.17-10-generic/Makefile modules
   mkdir -p /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/.tmp_versions
   rm -f /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/.tmp_versions/*
   make -f /usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.build obj=
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet
     cc -Wp,-MD,/home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/.nvenet.o.d  -no
   stdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D__KERNEL__ -Iinc
   lude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-generic/include -include 
   include/linux/autoconf.h  -I/home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -fno-stack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tab
   les -pipe -msoft-float -mpreferred-stack-boundary=2 -march=i586 -mtune=gener
   ic
    -mregparm=3 -ffreestanding -I/usr/src/linux-headers-2.6.17-10-generic/inclu
   de/asm-i386/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-after
   -statement -Wno-pointer-sign -DDRIVERVER=\"9999\"  -I/home/ash/NFORCE-Linux-
   x86-1.0-0310-pkg1/nvnet -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wc
   har-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -
   Wno-cast-qual -Wno-error -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KB
   UILD_STR(nvenet)"  -D"KBUILD_MODNAME=KBUILD_STR(nvnet)" -c -o /home/ash/NFOR
   CE-Linux-x86-1.0-0310-pkg1/nvnet/.tmp_nvenet.o /home/ash/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvnet/nvenet.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.
   h:20,
                    from /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.
   c:22:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:62: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.
   h:32,
                    from /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.
   c:22:
   include/asm/io.h: In function ‘check_signature’:
   include/asm/io.h:245: warning: wrong type argument to increment
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c: At top level:
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:217: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:220: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:223: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:226: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:229: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:232: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:235: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:238: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:241: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:244: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:247: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:250: error: expected
   ‘)’ before string constant
   /home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.c:336: warning: initia
   lization from incompatible pointer type
   make[4]: *** [/home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet/nvenet.o] Error
   1
   make[3]: *** [_module_/home/ash/NFORCE-Linux-x86-1.0-0310-pkg1/nvnet] Error 
   2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the network driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.17-10-generic (root@vernadsky) (gcc
   version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct
   13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Using the kernel source path '/lib/modules/2.6.17-10-generic/build' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/lib/modules/2.6.17-10-generic/build'
-> Using the kernel output path '/lib/modules/2.6.17-10-generic/build' as
   specified by the '--kernel-output-path' commandline option.
-> Kernel output path: '/lib/modules/2.6.17-10-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.17-10-generic/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   Makefile:53: *** extraneous `else'.  Stop.
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.17-10-gen
   eric/build SYSOUT=/lib/modules/2.6.17-10-generic/build'...
   Makefile:53: *** extraneous `else'.  Stop.
   make: *** [module] Error 2
-> Error.
ERROR: Unable to build the NVIDIA kernel module.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.


[/html]



So if anyone could help me, or direct me to some where that can, that would be awesome.. 


Thanks 


Ash
[/SIZE]

---

### Post by pseudonym on 2006-11-08
Hallo,

I can see two issues in your log -

1. You tried to build the nvnet module. Why? The nvidia onboard NIC is driven much better by the open-source 'forcedeth' module which, as you will note, was loaded when you ran the nforce-installer script (it comes as part of the Ubuntu kernel). nvnet errored out, probably because you also need to make similar edits to the installer files to get it to build on recent kernels (exactly which edits, I don't know, but there is no point in building this module anyway).

When you re-run the nforce-installer, make sure nvnet is unselected (highlight it and press either the space bar or return key, I can't remember which).

2. nvsound looks like it encountered something wrong in the makefile (an 'extraneous 'else''). What you need to do here is make doubly sure that you edit the makefile and nvmain.c (see the original howto) exactly as shown. A stray or misplaced character anywhere can break the whole process.

Hope this helps.

---

### Post by pseudonym on 2006-11-08
> **jocko said:**
> Excellent! Thank you, pseudonym!
I'll put a link to it in my howto. Hi jocko, 
Something else which may be worth adding in your 'known issues' is the list of installed files for the nforce-installer, mentioned in [this post]("http://www.ubuntuforums.org/showpost.php?p=1686729&postcount=58"). As you probably know, nvsound doesn't always uninstall automatically (in fact, it never has for me since kernel 2.6.15). It would therefore be helpful to users to include a step on how to remove all the files manually.

---

### Post by Icarosaurus on 2006-11-09
So...
This howto works great, but Nvidia drivers doesn't very much for me.

Nowadays I cannot listen to 5.1 streams with analog speakers using all the power of my soundstorm, as you can see in my posts :(
I experience channel inversions, can't control LFE and so on...

I tried to make ALSA work for 5.1 streams and it sounds fine: I can even better control volumes.
But I cannot use Hardware mixing and everything seems to be "made by software" instead of hardware.

Im so mad at NVIDIA! :evil: 
Why they don't release updated and working driver for us? [-( 
They think exclusively to immediate commercial gain, seen that they release updates only for linux distributions which they are interested in...

I'd like to use an ALSA driver with hardware capabilities so much... :-k 
Is it possible? Or I'm only a dreamer?

---

### Post by Icarosaurus on 2006-11-09
My little little contribute to this Howto :) 
When I'm in step 6:
```
killall esd
sudo aptitude update
sudo aptitude install libesd0
```
my Edgy doesn't uninstall **ubuntu-desktop** package.
So, I think the question mark after Edgy:
> (at least in breezy and dapper, but not in edgy?)
could be put off.

:D

---

### Post by jocko on 2006-11-10
> **pseudonym said:**
> Hi jocko, 
Something else which may be worth adding in your 'known issues' is the list of installed files for the nforce-installer, mentioned in [this post]("http://www.ubuntuforums.org/showpost.php?p=1686729&postcount=58"). As you probably know, nvsound doesn't always uninstall automatically (in fact, it never has for me since kernel 2.6.15). It would therefore be helpful to users to include a step on how to remove all the files manually.

Thanks for pointing this out. I've changed the uninstall method to a manual removal of all the files instead of using the uninstaller.

---

### Post by jocko on 2006-11-10
> **Icarosaurus said:**
> My little little contribute to this Howto :) 
When I'm in step 6:
```
killall esd
sudo aptitude update
sudo aptitude install libesd0
```my Edgy doesn't uninstall **ubuntu-desktop** package.
So, I think the question mark after Edgy:

could be put off.

:D

Yes, that's right. The only reason i had a question mark there was because edgy was still under development when I wrote it, so I didn't know if the dependencies of ubuntu-desktop would change again. I've removed the question mark.:)

---

### Post by Xarkam on 2006-11-10
Hi,
for me the compilation dont work.
I receive this message:
```

ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely because the kernel module was built using the wrong
         kernel source files.  Please make sure you have installed the kernel source files for your kernel; on Red Hat Linux systems,
         for example, be sure you have the 'kernel-source' rpm installed.  If you know the correct kernel source files are installed,  
         you may specify the kernel source path with the '--kernel-source-path' commandline option.

```
I installed the linux-headers-2.6.17-10, linux-headers-2.6.17-10-generic and the linux-source-2.6.17.
On command line i'm using the --kernel-source-path option on this:
```
 sudo ./nforce-installer --kernel-source-path /usr/src/linux-headers-2.6.17-10-generic/

```
My kernel used is: 
```
xarkam@HYKSOS:~/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1$ uname -a
Linux HYKSOS 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

```
The finality is always the same, the driver don't compile.

My nvidia-nforce-installer.log
```
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Fri Nov 10 09:33:51 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : /usr/src/linux-headers-2.6.17-10-generic/
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> There appears to already be an audio driver installed on your system (versio
   n: 1.0-7).  As part of installing this driver (version: 1.0-7), the existing
   driver will be uninstalled.  Are you sure you want to continue? ('no' will a
   bort installation) (Answer: Yes)
-> /proc/version is Linux version 2.6.17-10-generic (root@vernadsky) (gcc
   version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct
   13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Using the kernel source path '/usr/src/linux-headers-2.6.17-10-generic/' as
   specified by the '--kernel-source-path' commandline option.
-> Kernel source path: '/usr/src/linux-headers-2.6.17-10-generic/'
-> Kernel output path: '/lib/modules/2.6.17-10-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /usr/src/linux-headers-2.6.17-10-generic//Makefile | /usr/bin/cut -d " " -f
   3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/usr/src/linux-headers-2.6
   .17-10-generic/ SYSOUT=/lib/modules/2.6.17-10-generic/build'...
   make -C /lib/modules/2.6.17-10-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.17-10-generic \
   	KBUILD_EXTMOD="/home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/
   main" -f /usr/src/linux-headers-2.6.17-10-generic/Makefile modules
   mkdir -p /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.t
   mp_versions
   rm -f /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_
   versions/*
   make -f /usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.build obj=
   /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     cc -Wp,-MD,/home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/.nvalinux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/includ
   e -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-gener
   ic/include -include include/linux/autoconf.h  -I/home/xarkam/Desktop/NFORCE-
   Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-
   trigraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-f
   rame-p
   ointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-bou
   ndary=2 -march=i586 -mtune=generic -mregparm=3 -ffreestanding -I/usr/src/lin
   ux-headers-2.6.17-10-generic/include/asm-i386/mach-default -Iinclude/asm-i38
   6/mach-default -Wdeclaration-after-statement -Wno-pointer-sign  -I/home/xark
   am/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wimplicit -Wre
   turn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith 
   -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_CHANGE_PAGE_ATT
   R_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvalin
   ux)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /home/xarkam/Desktop/NFOR
   CE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_nvalinux.o /home/xarkam/Desktop
   /NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvalinux.c:19:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvalinux.c:25:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/.nvmixer.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include
   -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-generic
   /include -include include/linux/autoconf.h  -I/home/xarkam/Desktop/NFORCE-Li
   nux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-tr
   igraphs -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-fra
   me-pointer -fasynchronous-unwind-tables -pipe -msoft-float -mpreferre
   d-stack-boundary=2 -march=i586 -mtune=generic -mregparm=3 -ffreestanding -I/
   usr/src/linux-headers-2.6.17-10-generic/include/asm-i386/mach-default -Iincl
   ude/asm-i386/mach-default -Wdeclaration-after-statement -Wno-pointer-sign  -
   I/home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wim
   plicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoi
   nter-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_CHAN
   GE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD
   _STR(nvmixer)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /home/xarkam/De
   sktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_nvmixer.o /home/xarka
   m/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmixer.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvhw.h:29,
                    from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvmixer.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvhw.h:35,
                    from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvmixer.c:14:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     cc -Wp,-MD,/home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/.nvmain.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include 
   -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-generic
   /include -include include/linux/autoconf.h  -I/home/xarkam/Desktop/NFORCE-Li
   nux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wunde
   f -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -fno-s
   tack-protector -O2 -fomit-frame-pointer -fasynchronous-unwind-tables -pipe -
   msoft-float -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -mregpar
   m=3 -ffreestanding -I/usr/src/linux-headers-2.6.17-10-generic/include/asm-i3
   86/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-statemen
   t -Wno-pointer-sign  -I/home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/n
   vsound/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscrip
   ts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qua
   l -Wno-error -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(nvmain)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" 
   -c -o /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_
   nvmain.o /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nv
   main.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvmain.c:27:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvhw.h:35,
                    from /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvmain.c:29:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
   /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c: I
   n function &#8216;Nvaudio_mmap&#8217;:
   /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c:99
   1: warning: implicit declaration of function &#8216;remap_page_range&#8217;
     ld -m elf_i386 -m elf_i386 -d -r -o /home/xarkam/Desktop/NFORCE-Linux-x86-
   1.0-0310-pkg1/nvsound/main/nvsound.o /home/xarkam/Desktop/NFORCE-Linux-x86-1
   .0-0310-pkg1/nvsound/main/mcpmain.o /home/xarkam/Desktop/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvalinux.o /home/xarkam/Desktop/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main/nvmixer.o /home/xarkam/Desktop/NFORCE-Linux-x86-1.0
   -0310-pkg1/nvsound/main/nvmain.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.17-10-generic/scripts/Makefile.modpos
   t
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.17-10-generic/Modu
   le.symvers -I /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/Modules.symvers -o /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/Modules.symvers /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/nvsound.o
   WARNING: could not find /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/
   nvsound/main/.mcpmain.o.cmd for /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-03
   10-pkg1/nvsound/main/mcpmain.o
   WARNING: "remap_page_range" [/home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-
   pkg1/nvsound/main/nvsound.ko] undefined!
     cc -Wp,-MD,/home/xarkam/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/.nvsound.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/inc
   lude -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-ge
   neric/include -include include/linux/autoconf.h -I/usr/src/linux-headers-2.6
   .17-10-generic/ -I -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-str
   ict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasy
   nchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2 -mar
   ch=i586 -mtune=generic -mregparm=3 -ffreestanding -I/usr/src/linux-headers-2
   .6.17-10-generic/include/asm-i386/mach-default -Iinclude/asm-i386/mach-defau
   lt -Wdeclaration-after-statement -Wno-pointer-sign  -D"KBUILD_STR(s)=#s" -D"
   KBUILD_BASENAME=KBUILD_STR(nvsound)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)"
   -DMODULE -c -o /home/xarkam/Desktop/NFORCE
   -Linux-x86-1.0-0310-pkg1/nvsound/main/nvsound.mod.o /home/xarkam/Desktop/NFO
   RCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvsound.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /home/xarkam/Desktop/NFORCE-Linux-x86-1.0
   -0310-pkg1/nvsound/main/nvsound.ko /home/xarkam/Desktop/NFORCE-Linux-x86-1.0
   -0310-pkg1/nvsound/main/nvsound.o /home/xarkam/Desktop/NFORCE-Linux-x86-1.0-
   0310-pkg1/nvsound/main/nvsound.mod.o
-> done.
-> Kernel module compilation complete.
-> Testing kernel module:
-> Copying test module ./nvsound/main/nvsound.ko to
   /lib/modules/2.6.17-10-generic/kernel/sound/oss/nvsound.ko
ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: FATAL: Error inserting nvsound
   (/lib/modules/2.6.17-10-generic/kernel/sound/oss/nvsound.ko): Unknown symbol
   in module, or unknown parameter (see dmesg)
-> Testing completed.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.
```

The dmesg error:
```

[17179890.728000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9629  Wed Nov  1 19:30:07 PST 2006
[17179999.568000] nvsound: Unknown symbol remap_page_range
[17180074.080000] nvsound: Unknown symbol remap_page_range

```

	
an idea?

---

### Post by Xarkam on 2006-11-10
I found my error.
I comment this line in Makefile.kbuild :
```

        EXTRA_CFLAGS += -DNV_REMAP_PFN_RANGE_PRESENT

```
All work fine :)

---

### Post by Larrxi on 2006-11-12
I just decided to change my motherboard because of my fails to get sound working when i run over this guide. 
The sound is now working on my Abit NF7-S 2.0.

Thanks!

---

### Post by Icarosaurus on 2006-11-12
Larrxi,
I own an AN7 that should be a "sister" of your MoBo (I owned a NF7S MoBo too).
Are you able to listen to 5.1 streams correctly?
I have some problems...se my other posts:

[http://ubuntuforums.org/showthread.php?t=253725&page=6&highlight=icarosaurus]("http://ubuntuforums.org/showthread.php?t=253725&page=6&highlight=icarosaurus") 
[http://ubuntuforums.org/showthread.php?t=253725&page=5&highlight=icarosaurus]("http://ubuntuforums.org/showthread.php?t=253725&page=5&highlight=icarosaurus")

bye

---

### Post by techstop on 2006-11-16
Hi there. Still can't get any sound from my soundstorm SPDIF...

When running nvmixer from the terminal, I get these errors;

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

The application runs though, and on the information page it says I am using MCP-T, soundstorm etc. However, no sound!

The display on my home theater amp indicates a DTS signal though.

EDIT: This could be a PEBKAC. I will check my HT amp settings....

Any pointers? I am getting desperate here, I may have to go back to Windows Media Center! ](*,) ](*,) ](*,)

---

### Post by Elcoco on 2006-11-16
hi, ive tried everything mentioned in this post to get this to work, i have a n nforce 4 and 2.6.17-10 kernel, ive made sure the two files i needed to change have been changed but it still dosnt find my kernel source path and if i put it in manually it complains about the output path. 
this is my .log
```
nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Thu Nov 16 12:13:38 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.17-10-386 (root@vernadsky) (gcc version
   4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40
   UTC 2006 (Ubuntu 2.6.17-10.33-386)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
ERROR: Unable to find the kernel source tree for the currently running kernel. 
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.

```

---

### Post by techstop on 2006-11-16
> **Elcoco said:**
> hi, ive tried everything mentioned in this post to get this to work, i have a n nforce 4

I guess your problems arise from the fact this is a HOWTO for nForce Soundstorm, and you have an nForce 4, which does not have Soundstorm. Soundstorm was only in nForce 2.


As per the HOWTO, post #1;

> Make sure you know you have SoundStorm before you try any of this. Afaik it's only present in nforce 2 motherboards, and only if they have an mcp-t southbridge. Check your motherboard manual or the manufacturers homepage. If you don't have SoundStorm, this howto will probably not help you in any way.

---

### Post by jocko on 2006-11-18
> **techstop said:**
> Hi there. Still can't get any sound from my soundstorm SPDIF...

When running nvmixer from the terminal, I get these errors;

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```The application runs though, and on the information page it says I am using MCP-T, soundstorm etc. However, no sound!

The display on my home theater amp indicates a DTS signal though.

EDIT: This could be a PEBKAC. I will check my HT amp settings....

Any pointers? I am getting desperate here, I may have to go back to Windows Media Center! ](*,) ](*,) ](*,)

The errors you see does not affect nvmixer in any way. They probably happen every time you start a program from a terminal. You can get rid of that annoyance by inactivating support for wacom devices in /etc/X11/xorg.conf (remove three "InputDevice" sections that refer to wacom devices and three lines under "server layout" referring to the same devices, unless you actually use any of those devices).

I find it more probable that the fact that your amp indicates a dts signal is the cause of the problem. Soundstorm hardware is capable of encoding dolby digital, but not dts (as far as I know anyway). But it will pass an already encoded dts signal on to an external amp.
Are you sure you don't have any other sound drivers loaded? Check the output of 'lsmod' that snd_intel8x0 (or any other snd_..) is not loaded.

---

### Post by jocko on 2006-11-18
> **Elcoco said:**
> hi, ive tried everything mentioned in this post to get this to work, i have a n nforce 4 and 2.6.17-10 kernel, ive made sure the two files i needed to change have been changed but it still dosnt find my kernel source path and if i put it in manually it complains about the output path. 

First of all I think if you have nforce 4 there is probably no point installing nvsound, since your hardware is not capable of anything else than ac'97 anyway. So my advice to you is to stay with the open source alsa drivers.

But I still think it is possible to install nvsound on nforce 4, and probably you will get them working. You will just not gain any extra functionality or quality, as far as I know.

It seems to me that the installer fails because you don't have the kernel headers for your running kernel installed.
I see in your log that you are running a -386 kernel. That means you need to have 'linux-headers-386' installed before you try to install (if you decide to try it anyway).

---

### Post by techstop on 2006-11-18
> **jocko said:**
> The errors you see does not affect nvmixer in any way. They probably happen every time you start a program from a terminal. You can get rid of that annoyance by inactivating support for wacom devices in /etc/X11/xorg.conf (remove three "InputDevice" sections that refer to wacom devices and three lines under "server layout" referring to the same devices, unless you actually use any of those devices).

I find it more probable that the fact that your amp indicates a dts signal is the cause of the problem. Soundstorm hardware is capable of encoding dolby digital, but not dts (as far as I know anyway). But it will pass an already encoded dts signal on to an external amp.
Are you sure you don't have any other sound drivers loaded? Check the output of 'lsmod' that snd_intel8x0 (or any other snd_..) is not loaded.

Ahh, no, I can confirm a PEBKAC. I turned my HT amp off and then on again, it went back to Dolby Digital and I had sound. I don't know what I did. But, it works! Cheers, I will comment out those devices from xorg.conf anyway.

---

### Post by etamax on 2006-11-24
Hi to all!
I am new to the linux world.
I have a DFI Lanparty NF4 Ultra-D and the integrated audio soundcard is a Realtek ALC850. My system is Kubuntu Edgy.
I have followed the How-To but I am stuck at Step 6.
```
killall esd
``` did not work because esd was not loaded already. When I installed libesd0, it removed libesd-alsa.
But now, when I try to launch esd via Alt+F2, it says to me that esd cannot be found.
What should I do?



Another thing: 
In Step 5, when I launch nvmixer, I cannot set the sorround to clone in my 5.1 system because I cannot select the button.
What I did wrong?



Thank you for your answers

Massimo

---

### Post by jocko on 2006-11-24
> **etamax said:**
> Hi to all!
I am new to the linux world.
I have a DFI Lanparty NF4 Ultra-D and the integrated audio soundcard is a Realtek ALC850. My system is Kubuntu Edgy.
I have followed the How-To but I am stuck at Step 6.
```
killall esd
``` did not work because esd was not loaded already. When I installed libesd0, it removed libesd-alsa.
But now, when I try to launch esd via Alt+F2, it says to me that esd cannot be found.
What should I do?



Another thing: 
In Step 5, when I launch nvmixer, I cannot set the sorround to clone in my 5.1 system because I cannot select the button.
What I did wrong?



Thank you for your answers

Massimo


1. Kubuntu does not use esd, it uses aRts instead (correct me if I'm wrong). I don't know how to set that up to get it working with oss sound drivers.
2. Nforce 4 motherboards only have realtek ac'97, which does not support dolby digital encoding (=no way to set parameters for encoding if you don't have the hardware to do it, no matter which drivers you use). This feature was only present in the SoundStorm chipset in some nforce 2 motherboards.

My advice to you is to stay with the open source alsa drivers, since they have full support for your hardware (as far as I know).

---

### Post by Janusz11 on 2006-12-15
Just one question: do you have sound from more than 2 or 4 speakers? 

I'm personally pretty happy with ALSA's snd-intel8x0 driver- and I do can play multiple sound sources at once, like for example listening to MP3s and sound from Flash on Internet pages. I even prefer ALSA's sound quality over nVidia's.

I only tried nVidia's nForce driver for Linux once when I tried to play games on Linux and wanted to have 5.1 sound. However, I was never able to chose a 5.1 speaker set within nvmixer like in Windows. And I never had sound from more than 2 or 4 speakers (duplicating the front stereo source onto the back speakers).

---

### Post by eddj on 2006-12-15
For those of you who have errors when running the ./nforce-installer or sudo make that amount to errors in mvmix.c on lines 2003 and 2004 (nvmix.c:2003 nvmix.c:2004), you can correct by performing the following...

delete the entry nvmix.c from line 2003 (basically delete the entire line) and add ; to the end of line 2002 and now it should make and install fine.

I apologise for not being able to show the whole error as I did not save it at the time.

This error was found on Edgy 6.10 on the 15th of December 2006 and solved as above

---

### Post by VooDooTom on 2006-12-16
Hello,

thanks for this good tutorial. I did manage to install the nvsound drivers in my Xubuntu. Then I wanted to install OSS which went fine also (except that there is no esd - I don't know if this is important). But then I wanted to try something and removed the drivers completly (as you wrote) - but now I can't get the module compiled anymore. Do you have any idea of where the problem could lie?

Here is my nvidia-install log file:

```

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Sat Dec 16 19:25:46 2006

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.17-10-386 (root@vernadsky) (gcc version
   4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 Fri Oct 13 18:41:40
   UTC 2006 (Ubuntu 2.6.17-10.33-386)
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.17-10-386/build'
-> Kernel output path: '/lib/modules/2.6.17-10-386/build'
-> Performing cc_version_check with CC="gcc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.17-10-386/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.17-10-386
   /build SYSOUT=/lib/modules/2.6.17-10-386/build'...
   make -C /lib/modules/2.6.17-10-386/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.17-10-386 \
   	KBUILD_EXTMOD="/home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n" -f /usr/src/linux-headers-2.6.17-10-386/Makefile modules
   mkdir -p /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_
   versions
   rm -f /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_ver
   sions/*
   make -f /usr/src/linux-headers-2.6.17-10-386/scripts/Makefile.build obj=/hom
   e/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     gcc -Wp,-MD,/home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/
   .nvalinux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include 
   -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-386/inc
   lude -include include/linux/autoconf.h  -I/home/tom/Install/NFORCE-Linux-x86
   -1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs
   -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-point
   er -fasynchronous-unwind-tables -
   pipe -msoft-float -mpreferred-stack-boundary=2 -march=i486 -mtune=generic -m
   regparm=3 -ffreestanding -I/usr/src/linux-headers-2.6.17-10-386/include/asm-
   i386/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-after-statem
   ent -Wno-pointer-sign  -I/home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscript
   s -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual
   -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT -DMODU
   LE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvalinux)"  -D"KBUILD_
   MODNAME=KBUILD_STR(nvsound)" -c -o /home/tom/Install/NFORCE-Linux-x86-1.0-03
   10-pkg1/nvsound/main/.tmp_nvalinux.o /home/tom/Install/NFORCE-Linux-x86-1.0-
   0310-pkg1/nvsound/main/nvalinux.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvalinux.c:19:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvalinux.c:25:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     gcc -Wp,-MD,/home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/
   .nvmixer.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -
   D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-386/incl
   ude -include include/linux/autoconf.h  -I/home/tom/Install/NFORCE-Linux-x86-
   1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs 
   -fno-strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-point
   er -fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundar
   y=2 -march=i486 -mtun
   e=generic -mregparm=3 -ffreestanding -I/usr/src/linux-headers-2.6.17-10-386/
   include/asm-i386/mach-default -Iinclude/asm-i386/mach-default -Wdeclaration-
   after-statement -Wno-pointer-sign  -I/home/tom/Install/NFORCE-Linux-x86-1.0-
   0310-pkg1/nvsound/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wch
   ar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar -Werror -O -MD -W
   no-cast-qual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_P
   RESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvmixer)"
    -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /home/tom/Install/NFORCE-Linux
   -x86-1.0-0310-pkg1/nvsound/main/.tmp_nvmixer.o /home/tom/Install/NFORCE-Linu
   x-x86-1.0-0310-pkg1/nvsound/main/nvmixer.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvhw.h:29,
                    from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvmixer.c:14:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvhw.h:35,
                    from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvmixer.c:14:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     gcc -Wp,-MD,/home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/
   .nvmain.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/include -D
   __KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-386/inclu
   de -include include/linux/autoconf.h  -I/home/tom/Install/NFORCE-Linux-x86-1
   .0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -
   fno
   -strict-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -
   fasynchronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2 
   -march=i486 -mtune=generic -mregparm=3 -ffreestanding -I/usr/src/linux-heade
   rs-2.6.17-10-386/include/asm-i386/mach-default -Iinclude/asm-i386/mach-defau
   lt -Wdeclaration-after-statement -Wno-pointer-sign  -I/home/tom/Install/NFOR
   CE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wimplicit -Wreturn-type -Wswi
   tch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar 
   -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_C
   HANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBU
   ILD_STR(nvmain)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /home/tom/Ins
   tall/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_nvmain.o /home/tom/Ins
   tall/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c
   In file included from include/linux/list.h:7,
                    from include/linux/wait.h:22,
                    from include/asm/semaphore.h:41,
                    from include/linux/sched.h:57,
                    from include/linux/module.h:9,
                    from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvmain.c:27:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   In file included from include/linux/dmapool.h:14,
                    from include/linux/pci.h:559,
                    from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvhw.h:35,
                    from /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsou
   nd/main/nvmain.c:29:
   include/asm/io.h: In function &#8216;check_signature&#8217;:
   include/asm/io.h:245: warning: wrong type argument to increment
     ld -m elf_i386 -m elf_i386 -d -r -o /home/tom/Install/NFORCE-Linux-x86-1.0
   -0310-pkg1/nvsound/main/nvsound.o /home/tom/Install/NFORCE-Linux-x86-1.0-031
   0-pkg1/nvsound/main/mcpmain.o /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pk
   g1/nvsound/main/nvalinux.o /home/tom/I
   nstall/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmixer.o /home/tom/Insta
   ll/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.o
     Building modules, stage 2.
   make -rR -f /usr/src/linux-headers-2.6.17-10-386/scripts/Makefile.modpost
     scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.17-10-386/Module.s
   ymvers -I /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/Modu
   les.symvers -o /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
   /Modules.symvers /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/ma
   in/nvsound.o
   WARNING: could not find /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvs
   ound/main/.mcpmain.o.cmd for /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg
   1/nvsound/main/mcpmain.o
     gcc -Wp,-MD,/home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/
   .nvsound.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.2/inclu
   de -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.17-10-386/
   include -include include/linux/autoconf.h -I/usr/src/linux-headers-
   2.6.17-10-386/ -I -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-stri
   ct-aliasing -fno-common -fno-stack-protector -O2 -fomit-frame-pointer -fasyn
   chronous-unwind-tables -pipe -msoft-float -mpreferred-stack-boundary=2 -marc
   h=i486 -mtune=generic -mregparm=3 -ffreestanding -I/usr/src/linux-headers-2.
   6.17-10-386/include/asm-i386/mach-default -Iinclude/asm-i386/mach-default -W
   declaration-after-statement -Wno-pointer-sign  -D"KBUILD_STR(s)=#s" -D"KBUIL
   D_BASENAME=KBUILD_STR(nvsound)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -DMO
   DULE -c -o /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvs
   ound.mod.o /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvs
   ound.mod.c
     ld -m elf_i386 -m elf_i386 -r -o /home/tom/Install/NFORCE-Linux-x86-1.0-03
   10-pkg1/nvsound/main/nvsound.ko /home/tom/Install/NFORCE-Linux-x86-1.0-0310-
   pkg1/nvsound/main/nvsound.o /home/tom/Install/NFORCE-Linux-x86-1.0-0310-pkg1
   /nvsound/main/nvsound.mod.o
-> done.
-> Kernel module compilation complete.
-> Testing kernel module:
-> Copying test module ./nvsound/main/nvsound.ko to
   /lib/modules/2.6.17-10-386/kernel/sound/oss/nvsound.ko
ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: FATAL: Error inserting nvsound
   (/lib/modules/2.6.17-10-386/kernel/sound/oss/nvsound.ko): Unknown symbol in
   module, or unknown parameter (see dmesg)
-> Testing completed.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.


```

As I am told to use dmesg, here it is:

```

nvsound: Unknown symbol unregister_sound_mixer
[17179761.040000] nvsound: Unknown symbol register_sound_dsp
[17179761.040000] nvsound: Unknown symbol remap_page_range
[17179761.040000] nvsound: Unknown symbol unregister_sound_dsp
[17179761.040000] nvsound: Unknown symbol register_sound_mixer
[17180372.032000] nvsound: version magic '2.6.17-10-386 mod_unload 486 REGPARM gcc-3.4' should be '2.6.17-10-386 mod_unload 486 REGPARM gcc-4.1'
[17180388.016000] nvsound: Unknown symbol unregister_sound_mixer
[17180388.016000] nvsound: Unknown symbol register_sound_dsp
[17180388.016000] nvsound: Unknown symbol remap_page_range
[17180388.016000] nvsound: Unknown symbol unregister_sound_dsp
[17180388.016000] nvsound: Unknown symbol register_sound_mixer
[17180718.768000] nvsound: Unknown symbol unregister_sound_mixer
[17180718.768000] nvsound: Unknown symbol register_sound_dsp
[17180718.768000] nvsound: Unknown symbol unregister_sound_dsp
[17180718.772000] nvsound: Unknown symbol register_sound_mixer
[17180991.440000] nvsound: Unknown symbol unregister_sound_mixer
[17180991.440000] nvsound: Unknown symbol register_sound_dsp
[17180991.440000] nvsound: Unknown symbol unregister_sound_dsp
[17180991.440000] nvsound: Unknown symbol register_sound_mixer
[17181882.600000] nvsound: Unknown symbol unregister_sound_mixer
[17181882.600000] nvsound: Unknown symbol register_sound_dsp
[17181882.600000] nvsound: Unknown symbol unregister_sound_dsp
[17181882.600000] nvsound: Unknown symbol register_sound_mixer
[17182035.112000] nvsound: Unknown symbol unregister_sound_mixer
[17182035.112000] nvsound: Unknown symbol register_sound_dsp
[17182035.112000] nvsound: Unknown symbol unregister_sound_dsp
[17182035.112000] nvsound: Unknown symbol register_sound_mixer
[17186789.708000] nvsound: Unknown symbol unregister_sound_mixer
[17186789.708000] nvsound: Unknown symbol register_sound_dsp
[17186789.708000] nvsound: Unknown symbol unregister_sound_dsp
[17186789.708000] nvsound: Unknown symbol register_sound_mixer

```

This does not look very well I guess.

uname -r:
```
2.6.17-10-386
```

I really have no idead whre the problem could lie.
I have an nForce2 bord and I managed to get it to work this morning, but after I deinstalled it I could not get it to work again.

thanks in advance

---

### Post by jocko on 2006-12-17
@Janusz11:
Yes I have sound from all my speakers if i enable dolby digital 5.1 encoding. The sound quality with nvsound is absolutely perfect, while sound with the alsa drivers is like an old scratchy vinyl (I got the same huge difference between nvidia SoundStorm drivers and realtek ac'97 drivers in windows). Are you sure you have SoundStorm? Do you get hardware encoded dolby digital 5.1 output in windows, or do you just get pass-through of pre-encoded sound?

@eddj:
I can't find any nvmix.c anywhere. Are you sure you got the file name correct? There is a 'nvsound/main/nvmixer.c', but that only has 318 lines.

---

### Post by jocko on 2006-12-17
@VooDooTom:
I'm not sure about those errors, but what if you try to start from the absolute beginning?
Delete your 'NFORCE-Linux-x86-1.0-0310-pkg1/' (or whatever you named it) directory and follow my instructions at the end of the howto for manual uninstall of everything related to nvsound.

Next start from the beginning of the howto and make sure you follow the steps for kernel 2.6.16 or later EXACTLY as in my howto. Hopefully you just had a typo (or forgot to make the changes?) in Makefile.kbuild or nvmain.c.

---

### Post by Janusz11 on 2006-12-17
> **jocko said:**
> @Janusz11:
Yes I have sound from all my speakers if i enable dolby digital 5.1 encoding. The sound quality with nvsound is absolutely perfect, while sound with the alsa drivers is like an old scratchy vinyl (I got the same huge difference between nvidia SoundStorm drivers and realtek ac'97 drivers in windows). Are you sure you have SoundStorm? Do you get hardware encoded dolby digital 5.1 output in windows, or do you just get pass-through of pre-encoded sound?

Yeah, I'm absolutely sure that I have a SoundStorm APU. :) I'm on a MSI K7N2 Delta ILSR nForce2 MCP2-T board here. The MCP2-**T** is the chip that provides the SoundStorm APU capable of encoding Dolby Digital (AC3) on the fly. So, yeah, I use the SoundStorm software and have a hardware encoded AC3 stream in Windows.

About my experience that ALSA's sound quality sounds better to me than that of nVidia's original driver, well, as we know, this is a pretty subjective matter. 

One reason however, why ALSA sound a tad better (to me) may be because, as we know, AC3 is a lossy audio compression. And if I feed the original and "raw" Stereo signal to my receiver instead of having it encoded in AC3 may be the reason why it sounds better (to me).

But you wrote that you have sound from all your speakers. Now, this is interesting because, as I've already stated, I was never able to achieve that. Of course, this is absolutely uninteresting for listening to music (Stereo) or playing DVDs (I use pass-through for that). But for playing games, this is something different.

Have you done anything to get sound from all your speakers, edited some file maybe, or did it work right "out of the box"? Also, can you choose different speaker sets (2, 4, 4 + Dolby Digital encoding, 5.1, 5.1 + Dolby Digital encoding) with the nvmixer software like one can in Windows? And can you turn on and off Dolby Digital encoding "on the fly"?

Thanks in advance.

---

### Post by jocko on 2006-12-17
> **Janusz11 said:**
> Yeah, I'm absolutely sure that I have a SoundStorm APU. :) I'm on a MSI K7N2 Delta ILSR nForce2 MCP2-T board here. The MCP2-**T** is the chip that provides the SoundStorm APU capable of encoding Dolby Digital (AC3) on the fly. So, yeah, I use the SoundStorm software and have a hardware encoded AC3 stream in Windows.

About my experience that ALSA's sound quality sounds better to me than that of nVidia's original driver, well, as we know, this is a pretty subjective matter. 

One reason however, why ALSA sound a tad better (to me) may be because, as we know, AC3 is a lossy audio compression. And if I feed the original and "raw" Stereo signal to my receiver instead of having it encoded in AC3 may be the reason why it sounds better (to me).

But you wrote that you have sound from all your speakers. Now, this is interesting because, as I've already stated, I was never able to achieve that. Of course, this is absolutely uninteresting for listening to music (Stereo) or playing DVDs (I use pass-through for that). But for playing games, this is something different.

Have you done anything to get sound from all your speakers, edited some file maybe, or did it work right "out of the box"? Also, can you choose different speaker sets (2, 4, 4 + Dolby Digital encoding, 5.1, 5.1 + Dolby Digital encoding) with the nvmixer software like one can in Windows? And can you turn on and off Dolby Digital encoding "on the fly"?

Thanks in advance.

It works pretty much out of the box, at least after going through the steps in my howto.
My "speaker" options in nvmixer are: "headphone", "2 speakers", "4 speakers", "5.1 speakers" and "7.1 speakers". Whatever I choose I always get dolby digital (seems like they have left out the option to turn it off?). In "surround settings" I can choose "clone" to get sound in my rear speakers if the source is only stereo (this is excellent for listening to music). I'm not sure of games, I don't have any games with 5.1 sound so I haven't been able to test that.

---

### Post by Janusz11 on 2006-12-17
Thanks jocko!

---

### Post by Nx2 on 2006-12-25
Thanks a lot for this great tutorial, Jocko, even as a total linux-newbie, i managed to install my soundstorm system correct and now i have another reason not to switch back to windows, great work!

---

### Post by pseudonym on 2006-12-26
> **jocko said:**
> I'm not sure of games, I don't have any games with 5.1 sound so I haven't been able to test that.
Just to clarify that, SoundStorm 5.1 Dolby Digital works fine in games. In Doom 3 and Quake 4 you get 6-channel output - just make sure to disable cloning (ie. choose 'none' for the encoding option).

The only quirk I noticed with it was that the fading of voices to your rear seemed to come out of the front speakers rather than the surround speakers. The voices faded OK as you moved further away, just not quite in the right position. But I don't know whether that was the fault of the driver, my motherboard, or my speakers.

On a side note, I recently upgraded to an AMD64 machine and ebayed my nforce2 system. The new board has 7.1 Realtek ALC883 audio via optical SPDIF out, and it sounds pretty good with ALSA. But I can honestly say that I do miss the crisp Dolby Digital of Soundstorm, and even prefer it over this new audio solution. Not bad for a 3-year-old sound chip which used a driver that hasn't been developed for more than a year! :)

---

### Post by dustoashes on 2007-01-13
Hi,
I've followed this and it seems things have installed normally but as previously without the nvidia drivers, I can't get to manage the subwoofer to work.

WHen accessing nvmixer I get this

> X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Nvmixer does open but I can't access the Speaker Wizard and cannot enable LFE Crossover frequency in Surround setting.

---

### Post by jocko on 2007-01-14
> **dustoashes said:**
> Hi,
I've followed this and it seems things have installed normally but as previously without the nvidia drivers, I can't get to manage the subwoofer to work.

WHen accessing nvmixer I get this



Nvmixer does open but I can't access the Speaker Wizard and cannot enable LFE Crossover frequency in Surround setting.

Afaik there is no speaker wizard. They probably didn't care to remove that button when they ported nvmixer from the windows version.
I can't enable LFE crossover frequency either, or change the subwoofer volume from nvmixer. Luckily my external reciever handles the subwoofer perfectly anyway, so I have no need for those functions.

Do you have an external reciever, or are your speakers connected directly to your computer?

I actually found a way to enable the LFE crossover option and get the slider working, but it doesn't seem to make any difference in the sound. [http://www.ubuntuforums.org/showpost.php?p=1538077&postcount=9](http://www.ubuntuforums.org/showpost.php?p=1538077&postcount=9)
Try it and let me know if it works or not, but my guess is that it does not work.

The errors you get in the terminal is in no way related to nvmixer (try starting some other program from the terminal and you'll see the same).

---

### Post by dustoashes on 2007-01-14
> **jocko said:**
> 
Do you have an external reciever, or are your speakers connected directly to your computer?


Yes my speakers (5.1) are directly connected to the PC. I didn't try the HowTo you directed me to, since I already uninstalled what I've done in this guide. I tried the comprehensive sound guide that's somewhere around here.. but it doesn't seem to fix my subwoofer problem.

---

### Post by Icarosaurus on 2007-01-15
> **dustoashes said:**
> Yes my speakers (5.1) are directly connected to the PC. I didn't try the HowTo you directed me to, since I already uninstalled what I've done in this guide. I tried the comprehensive sound guide that's somewhere around here.. but it doesn't seem to fix my subwoofer problem.

Yes, it doesn't seem to fix the subwoofer problem, for me too...I have **analog speakers directly attached** and can't get my sound card work perfectly as I want...

> **pseudonym said:**
> Just to clarify that, SoundStorm 5.1 Dolby Digital works fine in games. In Doom 3 and Quake 4 you get 6-channel output - just make sure to disable cloning (ie. choose 'none' for the encoding option).

The only quirk I noticed with it was that the fading of voices to your rear seemed to come out of the front speakers rather than the surround speakers. The voices faded OK as you moved further away, just not quite in the right position. But I don't know whether that was the fault of the driver, my motherboard, or my speakers.


I have a big problem with this...
I have an **Abit AN7** Motherboard and slides of the speakers' volume in the NVmixer panel seems to be "mixed" when I listen to 5.1 streams...
They appear in the panel as:
  * Left Rear -- Left -- Center --Sub woofer -- Right -- Right Rear*
But I set them moving as they were:
 * Center -- Left -- Left Rear -- Right Rear -- Right -- Sub Woofer *
When I set Cloning on... I hear Rear Channels in Center/Sub when listening to Stereo (MP3).
When I'm under Windows, everything works fine with Center/Sub (Black) and Rear (Orange) jacks **reversed**
Everything seems to work fine in linux when I listen to 5.1 streams...but I cannot have cloning...(well, I should switch the audio jacks everytime).
Crazy, isn't it? :-)

How can we solve the LFE problem?
Anyone here has my same "reverse problem" ?

---

### Post by dustoashes on 2007-01-28
Ok, I've tried this again. The sound works but the subwoofer still doesn't. If i rearrange the cords of the speakers to the PC, i can get it working - but then again, that combination doesn't work when i'm in XP. 

Any idea?

EDIT: I missed Icarosaurus's post above. The problem seems to be identical to mine.

---

### Post by Icarosaurus on 2007-01-30
Well...it seems both windows and linux drivers are bugged...
but in windows they are bugged in such a way that the things work fine if you reverse two jacks...
In linux they seem to be "half-bugged" ..so they cause some problem...
So crazy ](*,)

---

### Post by Inot on 2007-02-02
I've been following this thread - It is very informative.
I have a question and a help request.

Question - Will this how-to work with a virtualized Linux running on
                an XP machine with VmWare workstation?

Help request - I have a FIC AU13 with soundstorm. I have had no problems
                     running 5.1 into a Klipsh digital/analog/Dolby sound system
                     in Windows (98se or Xp pro). I have read in the post's about
                     front/rear cable swapping, but when I run the 5.1 audio test,
                     all the sounds come from the correct speakers. So no problem
                     there.
                     My request is - Does anyone know about the A73 audio bracket
                     that comes with the AU13 and also I believe with the DFI lanparty
                     Ultra B.  My bracket has no RCA digital IN, but has the pads for
                     adding the components. If anyone has hacked their own RCA
                     digital IN for this bracket (know the values of the components
                     to add, I would greatly appreciate any info). My guess is 
                     an input resistor of 75ohms, a 10nf cap, and then there are
                     2 resistors (a divider I think) - and those are the ones I 
                     need to know.

---

### Post by Icarosaurus on 2007-02-08
> **Inot said:**
>  I have read in the post's about
                     front/rear cable swapping, but when I run the 5.1 audio test,
                     all the sounds come from the correct speakers. So no problem
                     there.

I experience center/rear swapping with an Abit N7F-S and an Abit AN7... but I'm not sure it's a hardware or a driver fault.
I guess you have the -GT or -ST version of your motherboard model, with soundstorm, so thank you for information: maybe It's a my Manufacturer's fault...
I experience channel swapping using ALSA too.

Sorry, I cannot answer you technical-electronical questions...I'm not so expert :)

I'm running Wintendo using VMWARE, and I cannot tell you if things go well running Linux under Windows, but I suppose there's no problem...
Anyway running linux alone is better :)

---

### Post by jocko on 2007-02-08
> **Inot said:**
> 
Question - Will this how-to work with a virtualized Linux running on
                an XP machine with VmWare workstation?

As far as I know, an os running in a vmware virtual machine does not see your actual hardware. It will only see a virtual soundcard, so I do not think you'll get the nforce drivers working under vmware.

---

### Post by Icarosaurus on 2007-02-10
Yes...I was wrong telling it should work.
VMWARE runs under a virtual machine, so it installs a virtual soundcard (typically a Soundblaster).

---

### Post by Icarosaurus on 2007-02-10
Hey Guys!
I've heard about a petition for asking Nvidia to release code and hardware specifications of Soundstorm to linux community.
Has anyone signed it ?

---

### Post by dnns on 2007-02-15
I'd sign it! Can you provide us with a link?

---

### Post by Icarosaurus on 2007-02-15
Well, I remember I've seen it surfing somewhere in the net, but I've not been able to find it again, so... I was just asking 8-[ .

There's a famous petition for asking Nvidia to reintroduce their APU in the Nforce4 chipset, 'cause it wasn't mounted in the Nforce3 one.
In fact it seems that Nforce4 will have a "Soundstorm 2".

I've told this just for saying that I'm not very optimistic on the possibility that Nvidia will develop better drivers for linux: they aren't interested in Nforce2 anymore.

But... let's see the other face: Nvidia could help the linux community to develop a better open source (see ALSA) driver releasing codes and specifications just because Nforce2 is not being produced anymore...

What do you think about setting up a new **[B]Petition for Nvidia**[/B]?
Naturally, if we cannot find that it already exists...

EDIT: click [here]("http://www.nforcershq.com/forum/1-vt36337.html?postdays=0&postorder=asc&&start=0") or [here]("http://forums.gentoo.org/viewtopic.php?p=664706#664706") : there is an "email campaign" but it's a bit old (2003). Anyway you can find there some interesting informations about why the APU is a sore point for Nvidia.

---

### Post by Icarosaurus on 2007-03-17
I tried to make it go in Feisty (2.6.20-11-generic kernel).
Compilation went fine... so it seems to work under a 2.6.20 kernel too
But I get this error in the log:

ERROR: Kernel configuration is invalid

And then something related to autoconf.h

Is this a problem?

---

### Post by jocko on 2007-03-18
> **Icarosaurus said:**
> I tried to make it go in Feisty (2.6.20-11-generic kernel).
Compilation went fine... so it seems to work under a 2.6.20 kernel too
But I get this error in the log:

ERROR: Kernel configuration is invalid

And then something related to autoconf.h

Is this a problem?

I have it working fine in 2.6.20-11-generic. I don't see any errors in the log, but I see this:
```
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (           \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)

```
I think this just shows a script that is being run to check if there are files named 'autoconf.h' or 'auto.conf' in the kernel headers. If those files would be missing compilation would fail and show the three messages in quotes after the 'echo' commands and otherwise compilation would continue. So if this is what you see I think you don't have any problem.

---

### Post by Icarosaurus on 2007-03-18
Thank you :)

---

### Post by noorigin on 2007-03-29
so i followed this tutorial (thanks by the way) and finally got sound from spdif on my abit NF7-s. BUT... the sound is that digitzed pulse test tone noise! it sounds like the test tones that nvmixer uses for speaker setup under MSwindows. i cant get any other sounds. and its constant. from the moment xubuntu loads till i shutdown. play a song or video and it just garbles or amplifies the tone. i feel i am so close to getting this to work! ARRRGH! anyone have any ideas? how can i fix this?

---

### Post by adam_ac on 2007-03-29
Hi, 

Greats tutorial, i got it working on opensuse 10.2 but with some quirks,

First, its only work when i logon as root. When i logon as user, xine automaticaly show an error dialog telling me it cannot find a soundcard. Can anyone explain this ?

Secondly, i was unable to blacklist snd_intel8x0 by adding blacklist snd_intel8x0 to /etc/modprobe.d/blacklist. My workaround was by deleting it from yast. What is the right way to blacklist module ?

Any help is greatly appreciated,
Adam

---

### Post by jocko on 2007-04-09
> **noorigin said:**
> so i followed this tutorial (thanks by the way) and finally got sound from spdif on my abit NF7-s. BUT... the sound is that digitzed pulse test tone noise! it sounds like the test tones that nvmixer uses for speaker setup under MSwindows. i cant get any other sounds. and its constant. from the moment xubuntu loads till i shutdown. play a song or video and it just garbles or amplifies the tone. i feel i am so close to getting this to work! ARRRGH! anyone have any ideas? how can i fix this?

I have never had this problem, so I'll probably not be able to help. Do you mean you get a clean tone, or is it more like the digital to analog conversion noise you get from a modem or fax?
How have you connected your speakers? Digital or analog output? External amplifier?

> **adam_ac said:**
> Hi, 

Greats tutorial, i got it working on opensuse 10.2 but with some quirks,

First, its only work when i logon as root. When i logon as user, xine automaticaly show an error dialog telling me it cannot find a soundcard. Can anyone explain this ?

Secondly, i was unable to blacklist snd_intel8x0 by adding blacklist snd_intel8x0 to /etc/modprobe.d/blacklist. My workaround was by deleting it from yast. What is the right way to blacklist module ?

Any help is greatly appreciated,
Adam

I'm not sure I can help here either, I've never tried opensuse.
Have you set xine to use oss instead of alsa for audio output? This would have to be set for all your users.
As for the blacklisting, I have no idea what is the "correct" way to do it in opensuse, but if deleting it from yast prevents it from being loaded, I guess it's a good way to do it.

---

### Post by noorigin on 2007-04-20
yea the sound is like a digital to analog sort of. constant fast pulse with lots of distortion in the background. teh speakers are a 2.1 set that have internal power and internal DAC. they connect to the pc via a single RCA to a spdif out from the board.

---

### Post by jocko on 2007-04-21
> **noorigin said:**
> yea the sound is like a digital to analog sort of. constant fast pulse with lots of distortion in the background. teh speakers are a 2.1 set that have internal power and internal DAC. they connect to the pc via a single RCA to a spdif out from the board.

I sounds to me like you send a digital signal to an analog speaker speaker system.

I'm not sure if it's possible to send an analog signal through spdif.
Have you tried to connect through analog output?

---

### Post by 5ar on 2007-04-23
First thanks for this great HOWTO!
I'm new to Ubuntu, using 7.04.
I done everything and it worked ... for 2 restarts. Same thou i did not have sound from subwoofer.
Now i have the same problem like noorigin!
Don't know what to do ... now every sound is a mess!\

My motherborad is ASUS A7N8X-E Deluxe.
Genius 5.1 speakers: SW-HF 5.1 5000

P.S.
Sorry for bad english!

---

### Post by 5ar on 2007-04-24
Reinstalled it and now it works!

But still no sound from subwoofer.

---

### Post by mouse256 on 2007-05-07
Kernel 2.6.21 will give a compilation error, I created a patch which works fine for me:

[http://aur.archlinux.org/packages/nforce-nvsound/nforce-nvsound/kernel-2.6.21.patch](http://aur.archlinux.org/packages/nforce-nvsound/nforce-nvsound/kernel-2.6.21.patch)

Have fun

---

### Post by noorigin on 2007-05-09
> **jocko said:**
> I sounds to me like you send a digital signal to an analog speaker speaker system.

I'm not sure if it's possible to send an analog signal through spdif.
Have you tried to connect through analog output?


no. its all hooked up tight. teh speakers are a boston accoustics set. they ONLY accept a digital connection. no analog inputs. but your description of sound is right on. like i sent a digi signal to analog components. if youve ever set up sondstorm in windows you know the sound im talking about. its that pulsed digi test tone nvidia uses to determine which speakers are connected. my problem is the test tone never goes away.

---

### Post by jocko on 2007-05-10
@noorigin:
Ok. I probably misunderstood you. I have no idea how that sound can appear...
5ar (a few posts up) says he solved the same problem by reinstalling.

If you decide to try that, follow the last section of the howto to manually remove all files created during the install, but skip reverting the blacklist file.
After a reboot you should not have any sound and no sound driver loaded.
If you still have the unpacked installer (the "NFORCE-Linux-x86-1.0-0310-pkg1" folder), remove it to make sure you start with fresh files.
Then follow the howto again to set it up.
If it doesn't work, I have no clue how to help you, and if it works I have no idea what went wrong to begin with...
Good luck

---

### Post by ezrollers on 2007-05-11
I'm using Kubuntu 7.04.

I've followed the very helpful howto.

Sound works fine, but I can't run nvmixer

I get this error 

```
nvmixer: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

I checked and I have libstdc++ 6 installed but not 5

I would have imagined that v6 would be a superset of v5

edit:

Guess I was I wrong. Installed libstdc++ 5 and nvmixer works sort of
Any ideas?

TIA

---

### Post by finchy on 2007-05-16
Hi Guys

I'm using Kubuntu 7.04 and I have this message while running installation of drivers and testing new module:


ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely
         because the kernel module was built using the wrong kernel source
         files.  Please make sure you have installed the kernel source files
         for your kernel; on Red Hat Linux systems, for example, be sure you
         have the 'kernel-source' rpm installed.  If you know the correct
         kernel source files are installed, you may specify the kernel source
         path with the '--kernel-source-path' commandline option.

Mouse256 did you have same error before applying the patch? I was trying to change this one but still driver cannot be installed. Or maybe I'm patching it in a wrong way? Anyone know what can be done with that?

Cheers

---

### Post by Janusz11 on 2007-05-21
I have exactly the same problem as finchy. 

Ubuntustudio and 2.6.20-15-lowlatency kernel here.

---

### Post by jocko on 2007-05-22
> **finchy said:**
> Hi Guys

I'm using Kubuntu 7.04 and I have this message while running installation of drivers and testing new module:


ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely
         because the kernel module was built using the wrong kernel source
         files.  Please make sure you have installed the kernel source files
         for your kernel; on Red Hat Linux systems, for example, be sure you
         have the 'kernel-source' rpm installed.  If you know the correct
         kernel source files are installed, you may specify the kernel source
         path with the '--kernel-source-path' commandline option.

Mouse256 did you have same error before applying the patch? I was trying to change this one but still driver cannot be installed. Or maybe I'm patching it in a wrong way? Anyone know what can be done with that?

Cheers

> **Janusz11 said:**
> I have exactly the same problem as finchy. 

Ubuntustudio and 2.6.20-15-lowlatency kernel here.

1. Check that you have the correct kernel headers (they have to match your running kernel).

2. Make sure you make the changes to nvmain.c and Makefile.kbuild **exactly** as they are written in the howto (if you don't make the change in Makefile.kbuild or if you make a typo you'll get exactly the error you're getting).

3. Don't apply Mouse256's patch unless you use kernel 2.6.21 (or later).

---

### Post by Icarosaurus on 2007-05-22
Any hint on how to play midi streams?

---

### Post by Janusz11 on 2007-05-23
Thanks jocko. Did everything again step by step and then it worked. Must have had a typo somewhere or something. 

I'm still not so sure though what to use: ALSA or OSS/nVidia. The latter of course is better for hardware mixing (I use Ubuntustudio and want to digitize some old MCs). However, I also experienced some problems with OSS (for example with Flash in websites).

Anyways, thanks again for you help and for this great How-to!

---

### Post by tux-gamer on 2007-06-05
> **mouse256 said:**
> Kernel 2.6.21 will give a compilation error, I created a patch which works fine for me:

[http://aur.archlinux.org/packages/nforce-nvsound/nforce-nvsound/kernel-2.6.21.patch](http://aur.archlinux.org/packages/nforce-nvsound/nforce-nvsound/kernel-2.6.21.patch)

Have fun

Thanks, it's work on kernel-2.6.21.3
I Use PCLinuxOS 2007.

I don't know how to patch, so i just edit file "nvaioctl-old.h" line 218
from:
```

enum device_type{

```

to
```

enum dev_type{

```

---

### Post by jocko on 2007-06-10
I just made some changes to the howto.
Instead of manually making the changes needed to get the installer to work on newer kernels, I managed to figure out how to make some patch files and a simple script to apply them.
It should work with kernel 2.6.21 now (thanks to mouse256), but I haven't tested it.

---

### Post by xMachina on 2007-06-17
Thanks for the great guide.

One little note: I am running a fairly vanilla Feisty installation, Kernel 2.6.20-16, and I had to run

sudo aptitude install build-essential libqt3-mt linux-386 linux-headers-386

to get the nforce-installer to recognise my Kernel (ie substiting '386' for where the HOWTO says
'generic' for Feisty)

Other than that, worked fine, thanks again!

---

### Post by jocko on 2007-06-18
> **xMachina said:**
> Thanks for the great guide.

One little note: I am running a fairly vanilla Feisty installation, Kernel 2.6.20-16, and I had to run

sudo aptitude install build-essential libqt3-mt linux-386 linux-headers-386

to get the nforce-installer to recognise my Kernel (ie substiting '386' for where the HOWTO says
'generic' for Feisty)

Other than that, worked fine, thanks again!

Yep, that's right. If you have downgraded to a -386 kernel, you need the headers for that...

---

### Post by grazhoppa on 2007-06-21
I followed the steps, and I it works - finally hardware mixing! :)

BUT

I use the digital-out to be hooked up to an old Sony MiniDisc player. Then I listen to music through the headphone jack on the MiniDisc player.  The MiniDisc player is flashing ¨Cannot Copy¨ when it´s in record mode using the optical digital-in as input.

 does it have to do with sample rate? Or maybe it&#347; outputting a 5.1 pass-through signal instead of a stereo signal...

If it´s sample rate for the digital-out, where may I start looking to change it?
If it´s a matter of getting a stereo signal out of the digital-out, I can´t find how to do that!

The Windows version of Nvidia´s audio driver had a neat check box to put a stereo signal out of the digital port :)

---

### Post by jocko on 2007-06-21
> **grazhoppa said:**
> 
 does it have to do with sample rate? Or maybe it&#347; outputting a 5.1 pass-through signal instead of a stereo signal...

If it´s sample rate for the digital-out, where may I start looking to change it?
If it´s a matter of getting a stereo signal out of the digital-out, I can´t find how to do that!

The Windows version of Nvidia´s audio driver had a neat check box to put a stereo signal out of the digital port :)

I'm guessing there is no way to output anything but dolby digital through the spdif with the linux soundstorm drivers. You're stuck with dolby digital;).
Have you tried analog output? there should be a "line-out" that should output an analog stereo signal if you select "2 speakers" in nvmixer.

---

### Post by callit on 2007-06-28
Just wanted to toss in my thanks for getting this all working an posting it.  Things are working great now on my DFI Infinity NF2.  No more choppy sound, multiple outputs at once.\\:D/

---

### Post by rastiman on 2007-07-22
Hi, here was my post with description of my problem. In short I was trying to run nvsound on oss4.0 but now I know that is impossible :)

Regards

---

### Post by MPiece on 2007-08-01
Outstanding! Thanks a lot for this how-to. It works like a charm. At least on kernel 2.6.21.x. 

But the kernel module fails to build with kernel 2.6.22.1 on an Asus A7N8X-E DeLuxe motherboard. Are others experiencing the same thing?

---

### Post by thinkdude on 2007-08-01
I confirm that it doesn't compile when using the 2.6.22 kernel on an asus a7n8x-e.  Any ideas on how to patch for 2.6.22?

---

### Post by jocko on 2007-08-02
> **thinkdude said:**
> I confirm that it doesn't compile when using the 2.6.22 kernel on an asus a7n8x-e.  Any ideas on how to patch for 2.6.22?

Nope... I just noticed this problem myself...
I have no knowledge whatsoever in programming.
I hope someone can figure out what changes are needed.
I attach the nvidia installer logfile, just in case someone can see a way to fix it.

---

### Post by röd on 2007-08-02
Smoking HOW-TO! Can confirm the same problem with A7N8X-e.

---

### Post by jocko on 2007-08-02
[SIZE=4][COLOR=Blue][B]Good news! It now works with kernel 2.6.22!
[/B][SIZE=2][COLOR=Black]I just found a fix in this thread on [nvnews.net]("http://nvnews.net/vbulletin/showthread.php?t=94864&highlight=nvsound")
I managed to include those fixes in my patches (now attached in the [howto]("http://ubuntuforums.org/showpost.php?p=1478381&postcount=1")).
Now we can have excellent sound in gutsy as well...
Repeat the relevant steps under step 4 in my [howto]("http://ubuntuforums.org/showpost.php?p=1478381&postcount=1").
Make sure you start with fresh, unpatched files.
(i.e remove any previosly extracted files and extract them from the installer again)

Let me know if it works.
[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by thinkdude on 2007-08-07
Hey,


Thanks a lot  , that works perfectly.  Was wondering, does anyone know how to use this driver with pulseaudio?   Is it even possible?

---

### Post by nduanetesh on 2007-08-17
Thanks very much for this HOWTO, but (of course) I have a small issue...

My system sounds are super loud (as are some others, like video played from within firefox) and I was wondering about that....and tonight I remembered that I had problems during the "run esd and set everything to us OSS" step.

Whenever I type "esd" into the alt-f2 box, nothing happens.  I mean, nothing noticeable.  If I check the system monitor, there is a process named "esd", but there is no window or any sort of dialog box where I can change anything.  If I run "esd" in a terminal window, I get a very loud series of beeps, but once again no dialog box or window where I can change any settings.  Anybody have any ideas? Just to be sure, I already attempted to reinstall the libesd package, and it said that the package was already installed.

Thanks for any help,

ND

---

### Post by jocko on 2007-08-18
Esd is just a sound deamon running in the background to give you system sounds and sound from some applications thet use esd instead of oss. If you see the process, it is running. 
If your sound is too loud, use nvmixer to lower the volume (step 5 in the howto).
By some reason my volume controls in nvmixer or the default gnome volume control does nothing (I think it's because I only use digital output), so I have to use the surround settings under the "Speaker" tab to adjust the volume of the individual channels. I've set all speakers to 80% and use my external amplifier when I need to adjust the volume.

---

### Post by killer_tank on 2007-09-29
ok everything seemed to work but my rear speakers are my front ones as far as surrond sound goes and center and subwoofer are reversed.

anyone know the fix for this ?

i have to reverse all of this in windows too but the speaker wizard does it all for me which doesn't run in linux..

---

### Post by Icarosaurus on 2007-09-30
> **killer_tank said:**
> ok everything seemed to work but my rear speakers are my front ones as far as surrond sound goes and center and subwoofer are reversed.

anyone know the fix for this ?

i have to reverse all of this in windows too but the speaker wizard does it all for me which doesn't run in linux..

I have the same problem.. I didn't find any solution...
See one of my posts [here]("http://ubuntuforums.org/showpost.php?p=2015788&postcount=95")

---

### Post by dcj on 2007-10-05
I followed your guide exactly, but here is where I run into trouble.
################################################## ########################
Step 5:
Change sound settings:
Code:

nvmixer

When I tried to run nvmixer It responded with the following error:

nvmixer: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: no such file or directory.

What can I do to fix this, as I currently have no sound. I'm running Feisty Fawn 2.6.20-16. (I did have it working out 2 speakers only before I tried this, I have 5.1)

---

### Post by dcj on 2007-10-05
I actually managed to run nvmixer by reinstalling the libqt part at the beginning. However, when I run nvmixer, I get the following messages in the command window:

helmut@davo:~$ nvmixer
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

Some options, such as the speaker wizard, are also greyed out in the nvmixer window.

---

### Post by sebasbari on 2007-10-05
Hello
I have NVidia nForce SounStorm (motherboard ASUS A7n8x - deluxe)

I want sound hardware-mixing, is there possible? 

by the way, I have download:
Version: 1.23
Release Date: June 25, 2007
Download V 1.23

Supported Distributions:

    * SLES 10 (2.6.16.21)
    * RHEL 3 UP7 (2.4.21-40)
    * RHEL 4 UP4 (2.6.9-42)
    * RHEL 4 UP5 (2.6.9-55)
    * Fedora Core 5 (2.6.15-1)
    * RHEL 3 UP8 (2.4.21-47)
    * SuSE 10.2 (2.6.18.2)
    * RHEL 5 (2.6.18-1)

from [http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

I have kubuntu, so I don't know what to do with this.

thanks in advance for the answer, and thanks to jocko for the HOWTO.

sorry my english :(

---

### Post by Icarosaurus on 2007-10-05
yes, it's possible...
just follow step by step the Howto in the first post of this thread.
You don't need to do anything else: the drivers you downloaded don't support Ubuntu and are closed source (**EDIT**: this is not true: they are open source and, of course, support Ubuntu because they're ALSA drivers,but don't support hardware mixing),,, so unfortunately you'll have to download an older version (**EDIT**: OSS drivers supporting hardware mixing) following the howto.

---

### Post by sebasbari on 2007-10-05
Thanks again for the answer.

I read the entire thread. I follow the instructions and the sound works (almost) fine. I can hear 5.1 sound on analog output. The post is very fine. (thanks jocko).

But the mixing is made by software. so when I have high duty of CPU, the sounds does not work fine. ( it sounds "cutted") (suena entre cortado).

That's the point why I want hardware mixing.

---

### Post by jocko on 2007-10-06
> **sebasbari said:**
> Hello
I have NVidia nForce SounStorm (motherboard ASUS A7n8x - deluxe)

I want sound hardware-mixing, is there possible? 

by the way, I have download:
Version: 1.23
Release Date: June 25, 2007
Download V 1.23

Supported Distributions:

    * SLES 10 (2.6.16.21)
    * RHEL 3 UP7 (2.4.21-40)
    * RHEL 4 UP4 (2.6.9-42)
    * RHEL 4 UP5 (2.6.9-55)
    * Fedora Core 5 (2.6.15-1)
    * RHEL 3 UP8 (2.4.21-47)
    * SuSE 10.2 (2.6.18.2)
    * RHEL 5 (2.6.18-1)

from [http://www.nvidia.com/object/linux_nforce_1.23.html](http://www.nvidia.com/object/linux_nforce_1.23.html)

I have kubuntu, so I don't know what to do with this.

thanks in advance for the answer, and thanks to jocko for the HOWTO.

sorry my english :(

What you downloaded (V 1.23) is the open source alsa driver (intel8x0), which is already installed in ubuntu by default.
It does NOT support hardware mixing (as it only use the crippled ac'97 part of the sound card).
If you follow my howto you will get hardware mixing using nvidias old closed source oss driver, which is the only driver capable of using the audio processing unit (SoundStorm).

> **sebasbari said:**
> Thanks again for the answer.

I read the entire thread. I follow the instructions and the sound works (almost) fine. I can hear 5.1 sound on analog output. The post is very fine. (thanks jocko).

But the mixing is made by software. so when I have high duty of CPU, the sounds does not work fine. ( it sounds "cutted") (suena entre cortado).

That's the point why I want hardware mixing.

If you did everything as described in the howto, you should have hardware mixing, and you should have better sound quality than with the alsa driver.
Some of the instructions in the howto (step 6 and 7) are only applicable to gnome, so if you use kde you should skip them.

---

### Post by sebasbari on 2007-10-18
Ok, I follow the howto again just to be sure.
I use KUBUNTU, and I don't know what to do at STEP 6. I don't have ESD (I guess).  I am using oss. I found a process called artsd ( /usr/bin/artsd ) and it has the ghost icon. See the image attached.
I don't know if it has any relation.

Sory my english again.

SebasBari

EDIT: I forgot a question. Is there any way to confirm that every is ok ?

---

### Post by jocko on 2007-10-18
> **sebasbari said:**
> Ok, I follow the howto again just to be sure.
I use KUBUNTU, and I don't know what to do at STEP 6. I don't have ESD (I guess).  I am using oss. I found a process called artsd ( /usr/bin/artsd ) and it has the ghost icon. See the image attached.
I don't know if it has any relation.

Sory my english again.

SebasBari

EDIT: I forgot a question. Is there any way to confirm that every is ok ?

The problem with esd in gnome is that the standard install can only output sound to alsa, so if I want to have gnome system sounds through oss I have to remove one package (libesd-alsa0) and replace it with another package (libesd0).
I think aRts can output to both sound systems (alsa and oss), so you can skip that step (and also skip step 7, as you don't have gdm).
How to confirm that everything is ok?
If you get sound, everything should be ok.

---

### Post by sebasbari on 2007-10-18
Thanks again Jocko for your time.

I skip Step 6 and 7. I have sound.

which sound system should I choose? the available options are:
Auto detect
Advance Linux Sound Architecture
Enlightened sound server
network sound system
no input/output audio
Open sound system     <---- ( this is actually choosed )
Open sound system multi thread

(the names could be a little distinct, because these are translations from Spanish)

which is the best sound system? 

Remember I have Kubuntu.

Thanks in advice

SebasBari

---

### Post by jocko on 2007-10-19
> **sebasbari said:**
> which is the best sound system?

If you have followed my howto, OSS (Open Sound System) is the _only_ sound system. The drivers don't support anything else.

---

### Post by oCfuu on 2007-10-25
Hi there. Just installed a fresh copy of gutsy.
I have used this patch before in feisty, and everything worked flawless. But now, when I get to the "use alt+f2 to restart esd" it tells me, that it can't find esd.
when i check in the terminal i get this output:
> The program 'esd' can be found in the following packages:
 * pulseaudio-esound-compat
 * esound
Try: sudo apt-get install <selected package>
bash: esd: command not found

What to do?

---

### Post by jocko on 2007-10-26
> **oCfuu said:**
> Hi there. Just installed a fresh copy of gutsy.
I have used this patch before in feisty, and everything worked flawless. But now, when I get to the "use alt+f2 to restart esd" it tells me, that it can't find esd.
when i check in the terminal i get this output:


What to do?

esd isn't that important. It was installed by default in previous versions of ubuntu, and had to be restarted to unload libesd-alsa0 and load libesd0 after the install to get system sounds to work without a reboot.
Now I'm not sure, I have esd installed because I found a nice way of getting my laptop to send sound to the esd server on my desktop, [COLOR=Gray]but I think I get system sounds even without starting esd[/COLOR].
[COLOR=Red]**EDIT:**[/COLOR] I tested, and could not get system sounds without esd running. If you want login/logout sounds and sounds on different gnome events, you'll need to install esound (or figure out how to get pulseaudio working).
[COLOR=Gray] Do you get system sounds (maybe a reboot is required after you have installed libesd0)?[/COLOR]
If you don't need esd because of some specific program that cannot send sound directly to OSS, you can probably skip it without any problem.
If you find you need it, just install "esound" from synaptic or apt-get/aptitude.

I'll probably do a fresh install soon just to test some things out, so I'll try to remember to see if esd is needed or not and update the howto accordingly ([COLOR=Red]**EDIT**[/COLOR]: done this).

---

### Post by Bakon Jarser on 2007-10-29
not sure if it's just me but I had to reboot before launching nvmixer.  Didn't have to do this in Feisty but I just did a clean install of Gutsy.  I think this is because the new driver is considered a restricted driver.  Might want to add an edit that a reboot may be required at the end of step 4.  Thanks for the how to.

---

### Post by sp0onman on 2007-10-30
hi i followed the guide and in the restricted drivers think it says the nvsound driver is installed and in use. but when i try to start nvmixer i get this error in terminal:
Nvsound: Unable to open the Mixer 
 
but the nvmixer opens although i cant get into speaker wizard or surround settings. and in the information tab the boxes are there but nothing is in them. i am using 7.10. i am getting sound but all i want is the digital out to work. anybody know how to fix this? oh and my mobo is a asus a7n8x e deluxe if that helps.

---

### Post by jocko on 2007-10-30
> **Bakon Jarser said:**
> not sure if it's just me but I had to reboot before launching nvmixer.  Didn't have to do this in Feisty but I just did a clean install of Gutsy.  I think this is because the new driver is considered a restricted driver.  Might want to add an edit that a reboot may be required at the end of step 4.  Thanks for the how to.

A reboot is required at **some** point to unload the alsa driver (snd_intel8x0).
If you reboot after you have blacklisted snd_intel8x0 (step 2), you do not have to reboot after installing nvsound, as it can be loaded with modprobe (last part of step 4).
And once nvsound is loaded, nvmixer will work fine without a reboot (just tested with a clean install).


> **sp0onman said:**
> hi i followed the guide and in the restricted drivers think it says the nvsound driver is installed and in use. but when i try to start nvmixer i get this error in terminal:
Nvsound: Unable to open the Mixer 
 
but the nvmixer opens although i cant get into speaker wizard or surround settings. and in the information tab the boxes are there but nothing is in them. i am using 7.10. i am getting sound but all i want is the digital out to work. anybody know how to fix this? oh and my mobo is a asus a7n8x e deluxe if that helps.

Are you sure snd_intel8x0 isn't loaded? Check the output of these commands:
```
lsmod | grep snd
lsmod | grep nvsound
```If all is as it should, only the second command should give an output.
If you get an output from the first, you need to check that snd_intel8x0 is blacklisted (first part of step 2), and then reboot and everything should be fine.

---

### Post by sp0onman on 2007-10-30
lsmod | grep snd output is:
[PHP]snd_mpu401              9640  0 
snd_mpu401_uart         9600  1 snd_mpu401
snd_pcm_oss            44672  0 
snd_pcm                80388  1 snd_pcm_oss
snd_page_alloc         11400  1 snd_pcm
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54660  10 snd_mpu401,snd_mpu401_uart,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  3 snd,nvsound[/PHP]


and lsmod | grep nvsound output is:
[PHP]nvsound              1543992  1 
soundcore               8800  3 snd,nvsound[/PHP]

---

### Post by sp0onman on 2007-10-30
heh sorry all i had to do was restart now the digital out is working, yet to test proper 5.1 with a dvd but music sounds great through it. gotta love my new free logitech z5300e's running through my creative inspire digital 5500 decoder box. thanks alot for this guide!

---

### Post by Bakon Jarser on 2007-11-01
> **sp0onman said:**
> heh sorry all i had to do was restart now the digital out is working, yet to test proper 5.1 with a dvd but music sounds great through it. gotta love my new free logitech z5300e's running through my creative inspire digital 5500 decoder box. thanks alot for this guide!

looks like for some of us a restart is required.  i had the same problem he had until i restarted.

---

### Post by jocko on 2007-11-01
> **sp0onman said:**
> heh sorry all i had to do was restart now the digital out is working, yet to test proper 5.1 with a dvd but music sounds great through it. gotta love my new free logitech z5300e's running through my creative inspire digital 5500 decoder box. thanks alot for this guide!

> **Bakon Jarser said:**
> looks like for some of us a restart is required.  i had the same problem he had until i restarted.

Yes, it looks like if you have any "snd" modules loaded before you install nvsound (step 4), you may need to reboot to unload those..

---

### Post by sp0onman on 2007-11-03
havin a little trouble getting sound to work in flash. i dont know how to install the packages mentioned in step 1 here: [http://ubuntuforums.org/showpost.php?p=1716845&postcount=61](http://ubuntuforums.org/showpost.php?p=1716845&postcount=61)
btw im running gutsy itf that makes a difference

---

### Post by sp0onman on 2007-11-05
anybody?

---

### Post by jocko on 2007-11-06
> **sp0onman said:**
> anybody?

Have you tried searching in synaptic?
Another way is to type ```
sudo apt-get install build-essential libicu36 libicu36-dev libssl0.9.8 libssl-dev linux-headers-generic
``` in a terminal.

---

### Post by sp0onman on 2007-11-06
yea ta, i already just did it through synaptic, had trouble cause i didn't(silly me) realise that those versions were old.

---

### Post by MastaDaDesasta on 2007-11-15
Hello, 
I'm owner of a Nforce 2 Ultra 400 with Soundstorm onboard. I've got an Optical SPDIF-IN which I like to use but the neither the  Ubuntu default driver nor the nvsound nvidia driver recognize the Optical SPDIF-In anyone an idea to activate the port and output the optical-in sound through the speakers?

---

### Post by tux-gamer on 2007-11-21
> **jocko said:**
> [SIZE=4][COLOR=Blue][B]Good news! It now works with kernel 2.6.22!
[/B][SIZE=2][COLOR=Black]I just found a fix in this thread on [nvnews.net]("http://nvnews.net/vbulletin/showthread.php?t=94864&highlight=nvsound")
I managed to include those fixes in my patches (now attached in the [howto]("http://ubuntuforums.org/showpost.php?p=1478381&postcount=1")).
Now we can have excellent sound in gutsy as well...
Repeat the relevant steps under step 4 in my [howto]("http://ubuntuforums.org/showpost.php?p=1478381&postcount=1").
Make sure you start with fresh, unpatched files.
(i.e remove any previosly extracted files and extract them from the installer again)

Let me know if it works.
[/COLOR][/SIZE][/COLOR][/SIZE]
Your patch for 2.6.22 is work for kernel-2.6.22-9
Thank's a lot, i use Mandriva 2008.0 with deafult kernel ( 2.6.22-9 )

---

### Post by bferd on 2007-12-16
Ok, I now need some help. After struggling with this for about four hours I've got my analog 5.1 speakers, and my SPDIF/out to work. The only problem is my rear channels and my center/LFE are switched. Not a big deal for my 5.1 speakers as I can just swap plugs, but for my SPDIF/out it's a pain. Is there some way I can fix this? Is there a configuration file where I can map the outputs.

I have only been using Ubuntu for about 4 months and I'm still learning.

I have an ASUS A7N8X Deluxe motherboard.

---

### Post by jocko on 2007-12-16
> **bferd said:**
> Ok, I now need some help. After struggling with this for about four hours I've got my analog 5.1 speakers, and my SPDIF/out to work. The only problem is my rear channels and my center/LFE are switched. Not a big deal for my 5.1 speakers as I can just swap plugs, but for my SPDIF/out it's a pain. Is there some way I can fix this? Is there a configuration file where I can map the outputs.

I have only been using Ubuntu for about 4 months and I'm still learning.

I have an ASUS A7N8X Deluxe motherboard.

Unfortunately, that seems to be a problem in some motherboards ([see this post]("http://ubuntuforums.org/showpost.php?p=2015788&postcount=95")).
I don't know if there is any solution to re-map the channels system-wide, but it should be possible to map the output from mplayer (check the [manual]("http://www.mplayerhq.hu/DOCS/HTML/en/advaudio.html#advaudio-channels-copying") for help, it may require some trial and error to figure it out).

---

### Post by Maurolic on 2007-12-28
Hi
I have a nforce chipset and after the steps read in this post now work very well, but now I ahve a  new problem.

I cannot record from any source.

Any clue?

thx

---

### Post by Icarosaurus on 2008-01-19
Anyone got the driver working on the Hardy Heron Kernel?
The module fails to build with 2.6.24 kernel using the 2.6.22 patch :(
These are the last lines of my [B]/var/log/nvidia-nforce-installer.log
[/B]
```

  In file included from /home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/nvalinux.c:49:
   /home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.h: At top l
   evel:
   /home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.h:46: error
   : conflicting types for &#8216;uintptr_t&#8217;
   include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was
   here
   make[4]: *** [/home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalin
   ux.o] Error 1
   make[3]: *** [_module_/home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n] Error 2
   make[2]: *** [sub-make] Error 2
-> Error.

```
Is there a simple solution for this? I hope so :)

---

### Post by jocko on 2008-01-20
> **Icarosaurus said:**
> Anyone got the driver working on the Hardy Heron Kernel?
The module fails to build with 2.6.24 kernel using the 2.6.22 patch :(
These are the last lines of my [B]/var/log/nvidia-nforce-installer.log
[/B]
```

  In file included from /home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/nvalinux.c:49:
   /home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.h: At top l
   evel:
   /home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.h:46: error
   : conflicting types for &#8216;uintptr_t&#8217;
   include/linux/types.h:40: error: previous declaration of &#8216;uintptr_t&#8217; was
   here
   make[4]: *** [/home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalin
   ux.o] Error 1
   make[3]: *** [_module_/home/icaro/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n] Error 2
   make[2]: *** [sub-make] Error 2
-> Error.

```Is there a simple solution for this? I hope so :)



I may have found a fix to get it to build against a 2.6.24 kernel in a virtual machine. I haven't tested if it works all the way, but I got the compilation to work.

Try to do it this way:
1: Apply my patch for 2.6.22.
2:```
gedit ~/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.h
```Find line 46:
```
    typedef unsigned int     uintptr_t;
```[SIZE=3][COLOR=Red]Delete the entire line[/COLOR][/SIZE].
3:```
gedit ~/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c
```
[SIZE=3][COLOR=Red]Find "SA_SHIRQ" (without quotes, lines 2091 and 2197), replace with "IRQF_SHARED" (again, without the quotes)[/COLOR][/SIZE].
4. If it works, reply and let me know, and I will try to figure out how to include it in my patches. If it doesn't, reply with any errors you encounter.

---

### Post by Icarosaurus on 2008-01-21
Thank you for your quick and precise reply, Jocko.
The module seems to build without errors using your suggestions.
Unfortunately I had to reinstall the whole distribution 'cause I messed up a lot of things :p
I'll try to build again and check if everything works in the next hours... thanks again!

---

### Post by Icarosaurus on 2008-01-21
Ok, your solution seems to work without problems, Q.C. PASSED :-D
I have three notes:
1) Hardy Heron doesn't use esd anymore. It uses pulseaudio and a "pulseaudio esd wrapper" behaves just like esd.
So, the esd command works anyway. You don't need to install esound as you do in gutsy, cause it will cause pulseaudio to be removed.
2)At the moment, gstreamer autodetection fails... forcing oss in gstreamer-properties works fine.
3)I didn't test flash yet.

---

### Post by jocko on 2008-01-21
> **Icarosaurus said:**
> Ok, your solution seems to work without problems, Q.C. PASSED :-D
I have three notes:
1) Hardy Heron doesn't use esd anymore. It uses pulseaudio and a "pulseaudio esd wrapper" behaves just like esd.
So, the esd command works anyway. You don't need to install esound as you do in gutsy, cause it will cause pulseaudio to be removed.
2)At the moment, gstreamer autodetection fails... forcing oss in gstreamer-properties works fine.
3)I didn't test flash yet.

That's excellent news. I'll make sure to update the howto when I find time to upgrade to hardy myself.
For now I'll just link to this page for those that are eager to try out hardy and still want to use their soundstorm.

---

### Post by jocko on 2008-01-21
Edit: Nevermind. I thougt I had figured out how to get pulseaudio working, but I was just lucky... can't repeat it...

---

### Post by Icarosaurus on 2008-01-22
Well, I installed pulseaudio under Gutsy and it worked without problems... it just substitutes esd with its own wrapper, so the change is practically transparent to user ;)

---

### Post by jocko on 2008-01-22
> **Icarosaurus said:**
> Well, I installed pulseaudio under Gutsy and it worked without problems... it just substitutes esd with its own wrapper, so the change is practically transparent to user ;)

Not for me... The problem for me was that I needed to tell pulseaudio which modules to load at startup, otherwise it would just say it "couldn't find any sink" or something similar (the same on my desktop with nvsound/OSS and my laptop with snd_hda_intel/ALSA).
I managed to fix it last night by editing /etc/pulse/default.pa to make sure the correct modules are loaded, just took a little bit of trial and error to figure out what to load and what not to load.
Now I understand why they decided to drop esound in favour of pulseaudio... the sound quality seems much better (no stuttering, crackling or delay anymore, not even when I send the sound from my laptop to my desktop...)

Just in case anyone else have problems with getting pulseaudio working, this is what I did:
1. Install pulseaudio and some plugins and tools```
sudo apt-get install pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-hal pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils libgstreamer-plugins-pulse0.10-0 padevchooser paman paprefs pavucontrol pavumeter
```
Some of these can probably be left out if all you want is system sounds, and some of them may already be installed.
2. Add your user and the user "pulse" to the groups pulse, pulse-rt, pulse-access and audio (don't know if this is necessary, probably not for basic functionality, I picked it up from a tutorial somewhere):
```
sudo adduser *username* pulse
sudo adduser *username* pulse-rt
sudo adduser *username* pulse-access
sudo adduser *username* audio
sudo adduser pulse pulse
sudo adduser pulse pulse-rt
sudo adduser pulse pulse-access
sudo adduser pulse audio
```
3. ```
sudo gedit /etc/pulse/default.pa
```
Find and uncomment (remove the "#") these lines:
```
load-module module-oss device="/dev/dsp" sink_name=output source_name=input
add-autoload-sink output module-oss device="/dev/dsp" sink_name=output source_name=input
load-module module-native-protocol-unix
set-default-sink output
set-default-source input
load-sample x11-bell /usr/share/sounds/gtk-events/activate.wav
load-sample-dir-lazy /usr/share/sounds/*.wav
load-module module-x11-bell sample=x11-bell
```
Not all of these are necessary (I guess), but I needed the lines containing "module-oss" to get anything at all to work...

---

### Post by Icarosaurus on 2008-01-22
Honestly, I don't remember how I made pulseaudio to work before my fresh install of Hardy, because it was just a try, but I found it simpler.
As far as I remember, I installed some configuration tools available into repositories, and I had to answer some questions during the packages installation.
Anyway, the driver works pretty good in Hardy, without further modifications and file editing, just using your howto and your solution for Hardy, as I tried 5.1 streams and installed libflashsupport.so
Thanks :)

---

### Post by Icarosaurus on 2008-01-24
:( Things worked with pulseaudio because I didn't use it :P
I keep selected OSS in the sound preferences panel, but when i select pulseaudio I have an error message.
So I tried to configure pulseaudio by activating the oss module...but my computer freezes when using it.
I searched on the internet and it looks like the oss module and the whole pulseaudio  is still under development and full of bugs...
So I prefere disabling the pulseaudio oss module and specify oss in applications for now ... I don't have gnome sounds, but I can listen to mp3 and movies normally.

---

### Post by Icarosaurus on 2008-01-25
libflashsupport.so present in Hardy's official repositories doesn't support OSS but it's supposed to support pulseaudio.
I reported this bug to Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/186060 ]("https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/186060")

---

### Post by jocko on 2008-01-25
> **Icarosaurus said:**
> libflashsupport.so present in Hardy's official repositories doesn't support OSS but it's supposed to support pulseaudio.
I reported this bug to Launchpad:
[https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/186060 ]("https://bugs.launchpad.net/ubuntu/+source/libflashsupport/+bug/186060")

I hope they put oss support back in flashsupport before the final release.
I'll add a comment to your bug report later (if I manage to sign up on launchpad).


I have updated my patches so that they should work on kernel 2.6.24 (and the same patches also works for 2.6.22).
Hopefully it will still work when hardy is released.

---

### Post by jocko on 2008-01-26
> **Icarosaurus said:**
> .
So I tried to configure pulseaudio by activating the oss module...but my computer freezes when using it.

I installed hardy and ran into the same thing.
I submitted a [bug report]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/186133").

---

### Post by Icarosaurus on 2008-02-23
Compiling the 0.9.6 version of Pulseaudio works fine...
EDIT: microphone doesn't work with 0.9.6

So I confirm the problem is any bug starting from 0.9.7 (I tested it too).

I'm using compiz now and when computer is busy doing i.e. cube rotations, sound seems to be a little corrupted (I hear it crackling).
This happens with or without pulseaudio (maybe it's more with pulseaudio).

Do you know any solution to this? (i.e. incrementing some buffer)

Bye

---

### Post by ealderman on 2008-02-25
Awesome, simply awesome.

---

### Post by jocko on 2008-02-28
> **Icarosaurus said:**
> Compiling the 0.9.6 version of Pulseaudio works fine...
EDIT: microphone doesn't work with 0.9.6

So I confirm the problem is any bug starting from 0.9.7 (I tested it too).

I'm using compiz now and when computer is busy doing i.e. cube rotations, sound seems to be a little corrupted (I hear it crackling).
This happens with or without pulseaudio (maybe it's more with pulseaudio).

Do you know any solution to this? (i.e. incrementing some buffer)

Bye

Yeah, I also tested some different versions of pulseaudio and came to the same conclusion.
It seems my bug report in launchpad was rejected (I was told to report it to nvidia, but that would be quite pointless...).
So I try my luck with the pulseaudio developers instead ([[SIZE=2]Ticket #249[/SIZE]]("http://www.pulseaudio.org/ticket/249#")).
Hopefully someone will at least try to have a look at it..

I have noticed some corruption, but heavy cpu usage is not enough to cause it. At the same time X (or perhaps Xgl) becomes almost unresponsive (the screen updates only a few times per second or so). So for me it's not just the sound that stutters, it's the graphics as well (or the entire system?)
I have no Idea what causes it, but I have a feeling firefox is involved as I haven't noticed it without firefox running. Perhaps pulseaudio is also involved, but I haven't found any way to reproduce the stuttering,

---

### Post by SR_ELPIRATA on 2008-03-03
Hello All:

Jocko, thanks for the great how to, I was about to pull some hair out (I may still though) and it was quite pleasing finding a guide for this. Im having some problems, and Im kind of new to Linux/Ubuntu.

Im using Ubuntu 7.10 btw.

In step 1 after:

sudo apt-get install build-essential libqt3-mt linux-generic linux-headers-generic

I get asked to put the ubuntu CD, which I do put on my DVD (only drive) and it keeps asking me to put the CD (/media/cdrom) but whenever I hit enter it keeps asking for the CD. I noted that when I put the ubuntu CD it loads in media/ubuntu instead of media/cdrom )no matter 0 or 1). So I cant get past this.

I also tried via Synaptic, not sure if can be done from there, this part specially, but when I went to search for the

libqt3-mt linux-generic linux-headers-generic

It basically said I had it installed, (shown with green square), or thats what I inferr.

Did steps 2 and 3 without problems, and at the moment I have no audio, which is what the steps asked for, disabling the intel8x0. Then on step 4, I unpacked the nforce driver, then downloaded the nvsound patch which I extracted into the prior folder (where it had extracted the files),

Then, went for the:

./2.6.24-patch
sudo ./nforce-installer

On the 2nd line I got the installer to work, selected the audio driver ONLY and this is the nforce log:

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Mon Mar  3 02:35:26 2008

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.22-14-generic (buildd@terranova) (gcc
   version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb
   12 07:42:25 UTC 2008
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.22-14-generic/build'
-> Kernel output path: '/lib/modules/2.6.22-14-generic/build'
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).

What can I do?

Thanks in advance....

---

### Post by SR_ELPIRATA on 2008-03-03
Following a recommnedation of a friend, I disabled the ubuntu CD as a software source and this allowed me to complete the step 1, also, when I did the nforce installer again, this time went further but I got a new set of errors:

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Mon Mar  3 05:08:38 2008

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA network driver for Linux-x86
-> Found package NVIDIA audio driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.22-14-generic (buildd@terranova) (gcc
   version 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)) #1 SMP Tue Feb
   12 07:42:25 UTC 2008
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.22-14-generic/build'
-> Kernel output path: '/lib/modules/2.6.22-14-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.22-14-generic/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.22-14-gen
   eric/build SYSOUT=/lib/modules/2.6.22-14-generic/build'...
   make -C /lib/modules/2.6.22-14-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.22-14-generic \
   	KBUILD_EXTMOD="/home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main" 
   -f /usr/src/linux-headers-2.6.22-14-generic/Makefile modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_ver
   sions
   rm -f /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_versio
   ns/*
   make -f /usr/src/linux-headers-2.6.22-14-generic/scripts/Makefile.build obj=
   /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     cc -Wp,-MD,/home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.nva
   linux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.1.3/include -D__
   KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.22-14-generic/inc
   lude -include include/linux/autoconf.h  -I/home/elpirata/NFORCE-Linux-x86-1.
   0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -f
   no-strict-aliasing -fno-common -O2 -pipe -msoft-float -mregparm=3 -freg-stru
   ct-return -mpreferred-stack-boundary=2 -march=i586 -mtune=generic -ffreestan
   ding -maccumulate-outgoing-args -I/usr/src/linux-headers-2.6.22-14-generic/i
   nclude/asm-i386/mach-default -Iinclude/asm-i386/mach-default -fomit-frame-po
   inter -g -fno-stack-protector -Wdeclaration-after-statement -Wno-pointer-sig
   n  -I/home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wimpl
   icit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpoint
   er-arith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_CHANGE
   _PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_S
   TR(nvalinux)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /home/elpirata/N
   FORCE-Linux-x86-1.0-0310-pkg1/n
   vsound/main/.tmp_nvalinux.o /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nv
   sound/main/nvalinux.c
   In file included from include/linux/list.h:8,
                    from include/linux/module.h:10,
                    from /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/
   main/nvalinux.c:19:
   include/linux/prefetch.h: In function &#8216;prefetch_range&#8217;:
   include/linux/prefetch.h:62: warning: pointer of type &#8216;void *&#8217; used in a
   rithmetic
   /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c: In fu
   nction &#8216;AosFpuSave&#8217;:
   /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:181: e
   rror: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:191: e
   rror: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:214: e
   rror: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c: In fu
   nction &#8216;AosFpuRestore&#8217;:
   /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:234: e
   rror: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   /home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:235: e
   rror: &#8216;struct task_struct&#8217; has no member named &#8216;thread_info&#8217;
   make[4]: *** [/home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nva
   linux.o] Error 1
   make[3]: *** [_module_/home/elpirata/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/
   main] Error 2
   make[2]: *** [modules] Error 2
-> Error.
ERROR: The NVIDIA kernel module was not created.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at [www.nvidia.com](www.nvidia.com).

ELP

---

### Post by jocko on 2008-03-03
@SR_ELPIRATA:

It looks like you used the wrong patch, or that the patch failed. Or maybe you tried to patch twice?
Try this:
1. Delete the entire directory where you unpacked the nforce installer.
2. Repeat step 4. Make sure you only use the correct patch set (2.6.24-patch). Notice if the patches succeds or fails.

---

### Post by SR_ELPIRATA on 2008-03-03
Yep, I remember doing the windows fatality move.. (clicking on the file 2.6.24-patch) instead of running on a terminal. I noted that it said now patched files, did the other step and this time I got the success mesage.

Tried the sudo modprobe nvsound but it didnt work. I'm going to restart the system just in case. At this moment... I guess I should be saying that Im using the analog connections...... not the SPDIF, I use a cheapo solution with 3 amps, each doing 2 channels work, which works great under Windows, is just that I want to finally leave that side of my life.

BRB I hope

SR_ELP

---

### Post by SR_ELPIRATA on 2008-03-03
Not sure if anyone else menioned it, but the LFE slider is the frequence cutover. I got me an Infinity sub, a monstruosity, I noticed it works better at 63hz, which is what I just set mine to.

Im going to keep looking, but so far I havent found the 'clone front' so that music sounds with 4 speakers.

Now for the tests...

---

### Post by Icarosaurus on 2008-03-04
An alternatve way to solve the libstdc++ problem in Hardy is simply to do: 
```

sudo aptitude install libstdc++5

```

---

### Post by aulismedia on 2008-03-05
That is wonderful! First time in my life I hear sounds via digital output in Linux! Man, you are really good at it! Spasibo!

---

### Post by SR_ELPIRATA on 2008-03-05
Well, bad news, I can listen to 2 channel audio no problem. I put a DVD and while VLC is set to force 5.1 auto detection all I get is totally mute sound. I have to manually change to left channel, then right and then I can use Stereo but Surround dont appear no more.

The Clone to back doesnt appear either.

Any other options I may try?

ELP

---

### Post by jocko on 2008-03-05
> **SR_ELPIRATA said:**
> Well, bad news, I can listen to 2 channel audio no problem. I put a DVD and while VLC is set to force 5.1 auto detection all I get is totally mute sound. I have to manually change to left channel, then right and then I can use Stereo but Surround dont appear no more.

The Clone to back doesnt appear either.

Any other options I may try?

ELP
As you said a couple of posts ago you only use the analog output.
My guess is that vlc just passes the digital audio through spdif instead of decoding it into analog signals. I don't use vlc, so I have no idea how to make vlc decode digital audio into analog output, but you have to make sure it's using the liba52 codec instead of direct passthrough, otherwise you'll just get complete silence from your analog speakers. Is there any setting in vlc where you can set it to not use spdif?

To see the "clone to back" option, run nvmixer, go to the "speaker" tab, select "5.1 speakers" (or anything else than "2 speakers" or "headphone").
Then you can click the "surround settings" button.
Not sure if that would help you in any way, as I think that it would only affect dolby digital encoding (which of course will not work as you only use analog output).

---

### Post by Icarosaurus on 2008-03-06
Try using Xine and set 5.1 speakers in it.
5.1 streams with analogue output work nice for me.

---

### Post by SR_ELPIRATA on 2008-03-08
@Jocko: VLC can use the A52 but with SPDIF. Gonna download/install mplayer and xine and see what happens as well.

About the speaker wizard and surround buttons, I can't click on them, they both appear blank. I can click fine the one that selects from headphones to 5.1 but nothing else appears that I can click on.

ELP

---

### Post by SR_ELPIRATA on 2008-03-08
Ok, found mplayer stuff on the packages but I get "NON AUTHENTICATED" as a warning... would I want to install something that is not marked 'safe' for public consumption?

I had gxine installed, but iits giving me trouble to play some stuff, and can't open DVD's with it. I still have teh DVD problem in which I can't find what its path is, is not either /media/cdrom nor /media/cdrom0, its just /media/currentdvdlabel, and somehow it never runs apropiately.

Running out of options...

ELP

---

### Post by jocko on 2008-03-09
> **SR_ELPIRATA said:**
> @Jocko: VLC can use the A52 but with SPDIF. Gonna download/install mplayer and xine and see what happens as well.

About the speaker wizard and surround buttons, I can't click on them, they both appear blank. I can click fine the one that selects from headphones to 5.1 but nothing else appears that I can click on.

ELP

The speaker wizard button does nothing (there is no speaker wizard, but by some reaon they still put the button there).
The fact that you can't access the surround button tells me that your hardware probably don't have soundstorm. 
In that case you should be better off using the alsa drivers.


> **SR_ELPIRATA said:**
> Ok, found mplayer stuff on the packages but I get "NON AUTHENTICATED" as a warning... would I want to install something that is not marked 'safe' for public consumption?

I had gxine installed, but iits giving me trouble to play some stuff, and can't open DVD's with it. I still have teh DVD problem in which I can't find what its path is, is not either /media/cdrom nor /media/cdrom0, its just /media/currentdvdlabel, and somehow it never runs apropiately.

Running out of options...

ELP

The "unauthenticated" warning when you try to install mplayer should not be there. This may simply mean that you have added an extra repo to your softwere sources without installing the authentication key for that repo. Have a look in your /etc/apt/sources.list and see which repos you have. If you only have repos from ubuntu.com I'm sure you can trust them even if you get authentication errors.

But again: [COLOR=Blue]If your soundcard don't have soundstorm, there's no point in using this driver.[/COLOR]
What makes this driver better than the open source driver is the ability to use hardware mixing and real-time dolby digital encoding capabilities in soundstorm cards.
If your card don't have those capabilities, you will not gain anything compared to the alsa driver.

---

### Post by Icarosaurus on 2008-03-10
The module fails to install in the 2.6.24-12 kernel just updated from repositories... :(

These are the last lines of /var/log/nvidia-nforce-installer.log:

```

-> Copying test module ./nvsound/main/nvsound.ko to
   /lib/modules/2.6.24-12-generic/kernel/sound/oss/nvsound.ko
ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: FATAL: Error inserting nvsound
   (/lib/modules/2.6.24-12-generic/kernel/sound/oss/nvsound.ko): Unknown symbol
   in module, or unknown parameter (see dmesg)
-> Restoring backup /lib/modules/2.6.24-12-generic/kernel/sound/oss/nvsound.ko
-> Testing completed.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.

```

and this is what dmesg says:

```

[  232.355411] warning: process `nforce-installe' used the deprecated sysctl system call with 1.23.
[  232.356128] warning: process `nforce-installe' used the deprecated sysctl system call with 1.23.
[  238.725298] nvsound: Unknown symbol unregister_sound_dsp
[  238.725347] nvsound: Unknown symbol unregister_sound_mixer
[  238.725451] nvsound: Unknown symbol register_sound_mixer
[  238.725584] nvsound: Unknown symbol register_sound_dsp
[  257.153842] warning: process `nforce-installe' used the deprecated sysctl system call with 1.23.

```

The module installed nice with the -11 kernel...

---

### Post by jocko on 2008-03-10
> **Icarosaurus said:**
> The module fails to install in the 2.6.24-12 kernel just updated from repositories... :(

These are the last lines of /var/log/nvidia-nforce-installer.log:

```

-> Copying test module ./nvsound/main/nvsound.ko to
   /lib/modules/2.6.24-12-generic/kernel/sound/oss/nvsound.ko
ERROR: Unable to load the kernel module 'nvsound.ko'.  This is most likely
       because the kernel module was built using the wrong kernel source files.
       Please make sure you have installed the kernel source files for your
       kernel; on Red Hat Linux systems, for example, be sure you have the
       'kernel-source' rpm installed.  If you know the correct kernel source
       files are installed, you may specify the kernel source path with the
       '--kernel-source-path' commandline option.
-> Kernel module load error: FATAL: Error inserting nvsound
   (/lib/modules/2.6.24-12-generic/kernel/sound/oss/nvsound.ko): Unknown symbol
   in module, or unknown parameter (see dmesg)
-> Restoring backup /lib/modules/2.6.24-12-generic/kernel/sound/oss/nvsound.ko
-> Testing completed.
ERROR: Installation of the audio driver has failed.  Please see the file
       '/var/log/nvidia-nforce-installer.log' for details.  You may find
       suggestions on  fixing installation problems in the README available on
       the Linux driver download page at www.nvidia.com.

```and this is what dmesg says:

```

[  232.355411] warning: process `nforce-installe' used the deprecated sysctl system call with 1.23.
[  232.356128] warning: process `nforce-installe' used the deprecated sysctl system call with 1.23.
[  238.725298] nvsound: Unknown symbol unregister_sound_dsp
[  238.725347] nvsound: Unknown symbol unregister_sound_mixer
[  238.725451] nvsound: Unknown symbol register_sound_mixer
[  238.725584] nvsound: Unknown symbol register_sound_dsp
[  257.153842] warning: process `nforce-installe' used the deprecated sysctl system call with 1.23.

```The module installed nice with the -11 kernel...

I think I've managed to track that down to a mistake in the kernel build... they have apparently left out both alsa and oss from 2.6.24-12.19, so no sound at all will work... A newer version (2.6.24-12.20) is up on the main server now. I'll try it and see if it works.

**Edit: Yep. It's fixed now.** If you're impatient, just switch your software sources to the main server and update.

---

### Post by Icarosaurus on 2008-03-11
Thank you!

---

### Post by dcj on 2008-03-14
This has been a great help; I've been frustrated with surround sound problems for a long time (have NForce 2 chipset, logitech 5.1 surround through analogue output).

However, I'd like to know what options should be checked in the advanced options in NVMixer. The options are:
Swap options:
MIC TO CENTERLFE
LINE TO SURROUND LR
CENTER AND LFE

currently I've ticked all three. It seems to be working, but just playing music won't test the center channel.

Is there an easy way on ubuntu gutsy to test the sound output of each individual speaker?

Also, why is the 'speaker wizard' option greyed out in the NVMixer?

---

### Post by jocko on 2008-03-14
> **dcj said:**
> This has been a great help; I've been frustrated with surround sound problems for a long time (have NForce 2 chipset, logitech 5.1 surround through analogue output).

However, I'd like to know what options should be checked in the advanced options in NVMixer. The options are:
Swap options:
MIC TO CENTERLFE
LINE TO SURROUND LR
CENTER AND LFE

currently I've ticked all three. It seems to be working, but just playing music won't test the center channel.

Is there an easy way on ubuntu gutsy to test the sound output of each individual speaker?

Also, why is the 'speaker wizard' option greyed out in the NVMixer?

I don't think there is any easy way to test the sound of each speaker, other than playing a file or dvd with surround sound and see if it works.

There is no speaker wizard, that's why the button is greyed out.
I have no idea why they put the button there, maybe they just copied the nvmixer interface from the windows version and didn't care to remove it.

---

### Post by dcj on 2008-03-15
I get sound out of 4 speakers (but not center channel) when playing MP3's, which is what I expected as it does the same thing in windows. Haven't tried DVD's yet.

One problem I am having is watching youtube videos - I get no sound at all now.

---

### Post by jocko on 2008-03-15
> **dcj said:**
> One problem I am having is watching youtube videos - I get no sound at all now.

[This post]("http://ubuntuforums.org/showpost.php?p=1716845&postcount=61") explains how to get sound in flash.

---

### Post by Loacoon on 2008-03-29
Hi,

It sounds like you know this driver well here. First thanks for your patches, it was more than helpfull ;).

Here is my problem : When I use my S/PDIF out, and listen to a 5.1 stream, the voices (normally the central channel) are displayed in the rear speakers.
I guess it's a driver problem, but the devs didn't even answer to the message I posted on Nvnews... Do you have any idea how to fix this?

---

### Post by Loacoon on 2008-03-29
It sounds like there is still a problem with kernel 2.6.24. Here is my console output using "dmesg" :

```
WARNING: at arch/x86/kernel/pci-dma_32.c:66 dma_free_coherent()
Pid: 3261, comm: artsd Tainted: P        2.6.24-1-686 #1
 [<c010819c>] dma_free_coherent+0x5a/0x97
 [<f0c1343b>] AosMemoryFreePhysical+0xe8/0x110 [nvsound]
 [<f0b709e1>] _Z18AosListRemoveEntryP8NVA_LISTP14NVA_LIST_ENTRY+0x85/0x90 [nvsound]
 [<f0b703ec>] _ZdlPv+0x38/0x50 [nvsound]
 [<f0bc0050>] _ZN8CNvVoiceD0Ev+0x160/0x168 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0bb45f1>] _ZN9CNvStream12FinalReleaseEv+0x57/0x68 [nvsound]
 [<f0b70c14>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x2a/0x48 [nvsound]
 [<f0c08ccb>] _ZN9CNvStream7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bfc0ad>] _ZN13CApuStreamPciD0Ev+0x47/0xd6 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0c09e53>] _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bf6098>] Nv_FreeNewstream+0x2c/0x38 [nvsound]
 [<f0c14a09>] Nvfree_wave_device+0x51/0xd6 [nvsound]
 [<f0c14b5a>] Nvaudio_release+0xcc/0xdd [nvsound]
 [<c01792bd>] __fput+0x96/0x14c
 [<c0176b41>] filp_close+0x51/0x58
 [<c0177cd8>] sys_close+0x62/0x96
 [<c0103e5e>] sysenter_past_esp+0x6b/0xa1
 =======================
WARNING: at arch/x86/kernel/pci-dma_32.c:66 dma_free_coherent()
Pid: 3261, comm: artsd Tainted: P        2.6.24-1-686 #1
 [<c010819c>] dma_free_coherent+0x5a/0x97
 [<f0c1343b>] AosMemoryFreePhysical+0xe8/0x110 [nvsound]
 [<f0b703ec>] _ZdlPv+0x38/0x50 [nvsound]
 [<f0bb0940>] _ZN9CNvStreamD0Ev+0x1c0/0x1c8 [nvsound]
 [<f0bb45f1>] _ZN9CNvStream12FinalReleaseEv+0x57/0x68 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0c08ccb>] _ZN9CNvStream7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bfc0ad>] _ZN13CApuStreamPciD0Ev+0x47/0xd6 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0c09e53>] _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bf6098>] Nv_FreeNewstream+0x2c/0x38 [nvsound]
 [<f0c14a09>] Nvfree_wave_device+0x51/0xd6 [nvsound]
 [<f0c14b5a>] Nvaudio_release+0xcc/0xdd [nvsound]
 [<c01792bd>] __fput+0x96/0x14c
 [<c0176b41>] filp_close+0x51/0x58
 [<c0177cd8>] sys_close+0x62/0x96
 [<c0103e5e>] sysenter_past_esp+0x6b/0xa1
 =======================
WARNING: at arch/x86/kernel/pci-dma_32.c:66 dma_free_coherent()
Pid: 3261, comm: artsd Tainted: P        2.6.24-1-686 #1
 [<c010819c>] dma_free_coherent+0x5a/0x97
 [<f0c1343b>] AosMemoryFreePhysical+0xe8/0x110 [nvsound]
 [<f0c13148>] AosSpinLockAcquire+0x10/0x19 [nvsound]
 [<f0b703ec>] _ZdlPv+0x38/0x50 [nvsound]
 [<f0bfc136>] _ZN13CApuStreamPciD0Ev+0xd0/0xd6 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0c09e53>] _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bf6098>] Nv_FreeNewstream+0x2c/0x38 [nvsound]
 [<f0c14a09>] Nvfree_wave_device+0x51/0xd6 [nvsound]
 [<f0c14b5a>] Nvaudio_release+0xcc/0xdd [nvsound]
 [<c01792bd>] __fput+0x96/0x14c
 [<c0176b41>] filp_close+0x51/0x58
 [<c0177cd8>] sys_close+0x62/0x96
 [<c0103e5e>] sysenter_past_esp+0x6b/0xa1
 =======================
WARNING: at arch/x86/kernel/pci-dma_32.c:66 dma_free_coherent()
Pid: 3261, comm: artsd Tainted: P        2.6.24-1-686 #1
 [<c010819c>] dma_free_coherent+0x5a/0x97
 [<f0c1343b>] AosMemoryFreePhysical+0xe8/0x110 [nvsound]
 [<f0b709e1>] _Z18AosListRemoveEntryP8NVA_LISTP14NVA_LIST_ENTRY+0x85/0x90 [nvsound]
 [<f0b703ec>] _ZdlPv+0x38/0x50 [nvsound]
 [<f0bc0050>] _ZN8CNvVoiceD0Ev+0x160/0x168 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0bb45f1>] _ZN9CNvStream12FinalReleaseEv+0x57/0x68 [nvsound]
 [<f0b70c14>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x2a/0x48 [nvsound]
 [<f0c08ccb>] _ZN9CNvStream7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bfc0ad>] _ZN13CApuStreamPciD0Ev+0x47/0xd6 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0c09e53>] _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bf6098>] Nv_FreeNewstream+0x2c/0x38 [nvsound]
 [<f0c14a09>] Nvfree_wave_device+0x51/0xd6 [nvsound]
 [<f0c14b5a>] Nvaudio_release+0xcc/0xdd [nvsound]
 [<c01792bd>] __fput+0x96/0x14c
 [<c0176b41>] filp_close+0x51/0x58
 [<c0177cd8>] sys_close+0x62/0x96
 [<c0103e5e>] sysenter_past_esp+0x6b/0xa1
 =======================
WARNING: at arch/x86/kernel/pci-dma_32.c:66 dma_free_coherent()
Pid: 3261, comm: artsd Tainted: P        2.6.24-1-686 #1
 [<c010819c>] dma_free_coherent+0x5a/0x97
 [<f0c1343b>] AosMemoryFreePhysical+0xe8/0x110 [nvsound]
 [<f0b703ec>] _ZdlPv+0x38/0x50 [nvsound]
 [<f0bb0940>] _ZN9CNvStreamD0Ev+0x1c0/0x1c8 [nvsound]
 [<f0bb45f1>] _ZN9CNvStream12FinalReleaseEv+0x57/0x68 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0c08ccb>] _ZN9CNvStream7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bfc0ad>] _ZN13CApuStreamPciD0Ev+0x47/0xd6 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0c09e53>] _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bf6098>] Nv_FreeNewstream+0x2c/0x38 [nvsound]
 [<f0c14a09>] Nvfree_wave_device+0x51/0xd6 [nvsound]
 [<f0c14b5a>] Nvaudio_release+0xcc/0xdd [nvsound]
 [<c01792bd>] __fput+0x96/0x14c
 [<c0176b41>] filp_close+0x51/0x58
 [<c0177cd8>] sys_close+0x62/0x96
 [<c0103e5e>] sysenter_past_esp+0x6b/0xa1
 =======================
WARNING: at arch/x86/kernel/pci-dma_32.c:66 dma_free_coherent()
Pid: 3261, comm: artsd Tainted: P        2.6.24-1-686 #1
 [<c010819c>] dma_free_coherent+0x5a/0x97
 [<f0c1343b>] AosMemoryFreePhysical+0xe8/0x110 [nvsound]
 [<f0c13148>] AosSpinLockAcquire+0x10/0x19 [nvsound]
 [<f0b703ec>] _ZdlPv+0x38/0x50 [nvsound]
 [<f0bfc136>] _ZN13CApuStreamPciD0Ev+0xd0/0xd6 [nvsound]
 [<f0b70c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<f0c09e53>] _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
 [<f0bf6098>] Nv_FreeNewstream+0x2c/0x38 [nvsound]
 [<f0c14a09>] Nvfree_wave_device+0x51/0xd6 [nvsound]
 [<f0c14b5a>] Nvaudio_release+0xcc/0xdd [nvsound]
 [<c01792bd>] __fput+0x96/0x14c
 [<c0176b41>] filp_close+0x51/0x58
 [<c0177cd8>] sys_close+0x62/0x96
 [<c0103e5e>] sysenter_past_esp+0x6b/0xa1
 =======================

```

I never had this kind of messages before. It wouldn't be a problem for me, if it didn't cause some kernel panics, and disabled my network... :(

EDIT : It could be a clue of the problem, here is a part of the nforce-installer.log :

```
   /home/loacoon/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1-MOD/nvsound/main/nvmain
   .c: In function &#8216;Nvaudio_probe&#8217;:
   /home/loacoon/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1-MOD/nvsound/main/nvmain
   .c:2077: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible 
   pointer type
   /home/loacoon/Desktop/NFORCE-Linux-x86-1.0-0310-pkg1-MOD/nvsound/main/nvmain
   .c:2166: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible 
   pointer type
```

---

### Post by jocko on 2008-03-29
> **Loacoon said:**
> Hi,

It sounds like you know this driver well here. First thanks for your patches, it was more than helpfull ;).

Here is my problem : When I use my S/PDIF out, and listen to a 5.1 stream, the voices (normally the central channel) are displayed in the rear speakers.
I guess it's a driver problem, but the devs didn't even answer to the message I posted on Nvnews... Do you have any idea how to fix this?

There are other people with the same problem as you, but as far as I know, noone has found any fix.
I'm not sure if it's a driver problem or a hardware problem, but I don't have it.
Nvidia quit developing the driver in 2005, so they will not release any fix.

---

### Post by Loacoon on 2008-03-29
Great....... I'll have to do with it...

Could you see the message I posted after that please? It's a bigger problem for me.

Thanks anyway, sorry for bothering you.

---

### Post by jocko on 2008-03-29
I get the same output in my nvidia-nforce-installer.log, but I don't see any of those dmesg messages. Is there any actual problem?

---

### Post by Loacoon on 2008-03-29
Yes, 2 kernel panics and my network disabled (I had to reinstall the sound driver for my network to work again).
For now it works but I have those strange outputs.

---

### Post by Icarosaurus on 2008-04-01
I compiled Pulseaudio 0.9.10
Good news: The system doesn't freeze when uncommenting the oss module in default.pa
Bad News: selecting pulseaudio in the audio preferences and testing gives this message:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

---

### Post by jocko on 2008-04-02
> **Icarosaurus said:**
> I compiled Pulseaudio 0.9.10
Good news: The system doesn't freeze when uncommenting the oss module in default.pa
Bad News: selecting pulseaudio in the audio preferences and testing gives this message:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument
```

Interesting. I tried 0.9.10 yesterday, and as soon as I loaded module-oss the system froze up completely...
Are you sure the module actually loads?

---

### Post by Icarosaurus on 2008-04-03
Oh no, the module is not loaded... so, no good news for now :p

---

### Post by russ18uk on 2008-04-03
Hi, I used your guide on Gutsy using my A7N8X-Deluxe and sound works beautifully. No more crackles :guitar:

Anyway, I can't get sound to work in WINE. I know about the Flash issue, and I'll go back and patch that and get that to work, just been breezing through this thread to see if there was anything that may work and you say OSS is the only thing to use? 

I'll go around and make sure everything is using OSS; I did try all the available sound drivers in the WINE config and none would work so I'm not certain that would indeed work. Any ideas?

---

### Post by jocko on 2008-04-03
> **Icarosaurus said:**
> Oh no, the module is not loaded... so, no good news for now :p

Just as I guessed then. Unfortunately the pulseaudio developers told me they won't even try to fix it, they think it's a bug in the nvsound module, so pulseaudio is a no-go for us...

> **russ18uk said:**
> Hi, I used your guide on Gutsy using my A7N8X-Deluxe and sound works beautifully. No more crackles :guitar:

Anyway, I can't get sound to work in WINE. I know about the Flash issue, and I'll go back and patch that and get that to work, just been breezing through this thread to see if there was anything that may work and you say OSS is the only thing to use? 

I'll go around and make sure everything is using OSS; I did try all the available sound drivers in the WINE config and none would work so I'm not certain that would indeed work. Any ideas?

Well, for me sound in wine works just fine if I set winecfg to use oss or esd... Start up winecfg, set it to oss only, restart winecfg and test it by pressing the "test sound" button.

---

### Post by russ18uk on 2008-04-04
Thanks for the response. I've tried on all :P

[http://img256.imageshack.us/img256/5414/winenosoundrf7.jpg]("http://img256.imageshack.us/img256/5414/winenosoundrf7.jpg")

Any guesses? Don't get sound in any games either. kconfigure is set to use OSS and has no issues, nor do any apps like mplayer/amarok/kaffeine.

---

### Post by dustoashes on 2008-04-13
Ok, once again I've tried this HOWTO on Ubuntu 7.10. I can't change volume in Nvmixer ("volume set failed") nor can I run the surround wizard or anything. 

The only problem I've had in following the guide was here:

> 
Save your new nvmixer settings (to keep your settings after shutdown / reboot):

Code:
```
sudo /usr/bin/nvmix-reg -f /etc/nvmixrc -S
```

To manually load saved settings:

Code:
```
/usr/bin/nvmix-reg -f /etc/nvmixrc -L
```

At both I get 

> nvmixer:mixer opening error

Notably, the woofer is not working. I'm using a 5.1 system of speakers. 

Also, in the Gnome-volume-control the only option for choosing "device and track to control" is nvidia nforce2 (alsa mixer).

---

### Post by jocko on 2008-04-13
> **dustoashes said:**
> Ok, once again I've tried this HOWTO on Ubuntu 7.10. I can't change volume in Nvmixer ("volume set failed") nor can I run the surround wizard or anything. 

The only problem I've had in following the guide was here:



At both I get 



Notably, the woofer is not working. I'm using a 5.1 system of speakers. 

Also, in the Gnome-volume-control the only option for choosing "device and track to control" is nvidia nforce2 (alsa mixer).

That's because you are still using the alsa drivers. You need to blacklist them (first part of step 2 of the howto) and then unload every alsa module before you load nvsound. The easiest way is by rebooting after step 2.

The "surround settings" button will work once the nvsound module is installed and loaded in the kernel, as long as there are no alsa modules loaded.

---

### Post by dustoashes on 2008-04-14
Thanks, you were right, I overlooked the reboot, now I can configure in nvmixer. However, the option "LFE crossover frequency" is still disabled in the Surround Setting. That option enables, or, boosts my woofer up to a normal level in WinXP. Any idea how to get it going here?

Also do I need to edit the Advanced options (Swap options) for any effects?

---

### Post by jocko on 2008-04-14
> **dustoashes said:**
> Thanks, you were right, I overlooked the reboot, now I can configure in nvmixer. However, the option "LFE crossover frequency" is still disabled in the Surround Setting. That option enables, or, boosts my woofer up to a normal level in WinXP. Any idea how to get it going here?

Also do I need to edit the Advanced options (Swap options) for any effects?

Unfortunately I don't think the LFE crossover slider does anything.
I think they just copied the nvmixer interface from an old windows version and never bothered to remove some buttons and sliders.
I know nothing about the swap options, as I only use digital output. Maybe someone else knows.

---

### Post by dustoashes on 2008-04-14
I wish the woofer would work, anyway :(

EDIT: I re-arranged the cords and it seems to work fine (well, at least 80% of it :)). I suppose it won't be a problem, since I'll be using Ubuntu for multimedia from now on...

---

### Post by SR_ELPIRATA on 2008-04-19
Hey Jocko:

As you pointed out, seems that my board doenst have SoundStorm though is confusing because from what I read all NF7-S Abit boards came with it. Some days ago I was visiting the nforcershq site and came up with a nvmixer picture of somebody else and then I noticed it.

Its odd because I know mine dont say SoundStorm but everything else looks the same, even Ubuntu tells me I can choose from Nvidia to Realtek, so in a way perhaps I have it, otherwise I shouldnt have this option to come up.

[IMG]http://www.stormraider.net/nvmixers.jpg[/IMG]

When I go to Volume Control Preferences, on the top I can chose between:

- NVidia CK8 (Alsa Mixer) (as Ive uninstalled the nforce drivers)
- Realtek AL658D (OSS Mixer) - I have never tried it, if its a software solution I dont want it.

Doing lspci -v I got this:

```
00:06.0 Multimedia audio controller: nVidia Corporation MCP2S AC'97 Audio Controller (rev a1)
        Subsystem: ABIT Computer Corp. Unknown device 1c08
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at d000 [size=256]
        I/O ports at d400 [size=128]
        Memory at e8005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
```

This is what is odd to me, movies sound great under windows, and Id wish it worked here as well. Anyways, Im so decided to switch that Ill go get me a 5.1 card that Ubuntu 7.10 can use, I was thinking on the Audigy ES (goes for $30 or so) but if you can recommend something better that doesnt go beyond $70.... :)

Anyways.... thanks for all the help.

ELP

---

### Post by jocko on 2008-04-20
@SR_ELPIRATA:
If you had soundstorm 'lspci' would report two different audio controllers (blue is soundstorm, red is realtek ac97):

```
[COLOR=Blue]00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev a2)
        Subsystem: nVidia Corporation Unknown device 0c11
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at ea000000 (32-bit, non-prefetchable) [size=512K]
        Capabilities: [44] Power Management version 2[/COLOR]

[COLOR=Red]00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
        Subsystem: nVidia Corporation Unknown device 4144
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 17
        I/O ports at dc00 [size=256]
        I/O ports at e000 [size=128]
        Memory at ea084000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2[/COLOR]
``` The fact that you see both an alsa mixer and an oss mixer have nothing to do with soundstorm. That's just alsa's oss emulation, which is there to provide a way to use applications that can not use alsa.

I know very little about sound cards, but I'd guess an audigy would work fine. I don't think there is any card that provides dolby digital live in linux, though (I hope someone could tell me I'm wrong here, 'cause if I new of a card with good driver support that could do what I can do with my old soundstorm I wouldn't think it would be the end of the world when I can no longer manage to find out how to make nvsound work for every new kernel...).

---

### Post by dustoashes on 2008-04-20
Concerning sound in FLash - I'm having problems with getting these two files:

```
libicu34; libicu34-dev
``` 

I've tried Synaptic, but can't find them there. Can someone help me out, I'm pretty new with Ubuntu Gutsy also... :)

---

### Post by jocko on 2008-04-20
> **dustoashes said:**
> Concerning sound in FLash - I'm having problems with getting these two files:

```
libicu34; libicu34-dev
```I've tried Synaptic, but can't find them there. Can someone help me out, I'm pretty new with Ubuntu Gutsy also... :)


In gutsy they are named libicu36 and libicu36-dev.

---

### Post by SR_ELPIRATA on 2008-04-20
Jocko:

Would lspci -v be affected by the absence of nforce drivers in my case? since I removed them sometime ago.

ELP

---

### Post by SR_ELPIRATA on 2008-04-20
I dont know if this is something that would shed some light in what you said about dolby digital.. but maybe this link will help you. You most probably will understand a lot more than I do.

[http://www.alsa-project.org/main/index.php/A52_plugin](http://www.alsa-project.org/main/index.php/A52_plugin)

ELP

---

### Post by jocko on 2008-04-21
> **SR_ELPIRATA said:**
> Jocko:

Would lspci -v be affected by the absence of nforce drivers in my case? since I removed them sometime ago.

ELP

No, what driver you have does not affect which hardware is visible to lspci.

> **SR_ELPIRATA said:**
> I dont know if this is something that would shed some light in what you said about dolby digital.. but maybe this link will help you. You most probably will understand a lot more than I do.

[http://www.alsa-project.org/main/index.php/A52_plugin](http://www.alsa-project.org/main/index.php/A52_plugin)

ELP
Thanks. What I was thinking about was the built-in ability of many soundcards to take any sound signal and convert it to dolby digital, *without* the need for any software encoder (which will use the computers cpu and memory instead of the audio processor in the soundcard).
But as dolby labs don't want to give away their secrets, there is no way to get open source linux drivers which are capable of activating this function of the soundcards.

---

### Post by dustoashes on 2008-04-26
Ok, I've managed Flash w/ sound. So all is good. Many thank yous to the useful HOWTOs.

P.S. Any plugins that would enhance the sound quality, make it a bit more bassy, etc.?

---

### Post by jocko on 2008-04-26
> **dustoashes said:**
> Ok, I've managed Flash w/ sound. So all is good. Many thank yous to the useful HOWTOs.

P.S. Any plugins that would enhance the sound quality, make it a bit more bassy, etc.?

I'm not sure what you mean with plugins?
There is no graphical equalizer in nvmixer, but the file where nvmixer stores it's values does contain values for an equalizer.
You could try by manually editing the file:
```
sudo gedit /etc/nvmixrc
```Find these lines:
```
GlobalEQ:0
EQPreset:18
CustomBand0:0.000000
CustomBand1:0.000000
CustomBand2:0.000000
CustomBand3:0.000000
CustomBand4:0.000000
CustomBand5:0.000000
CustomBand6:0.000000
CustomBand7:0.000000
CustomBand8:0.000000
```Setting "GlobalEQ" to 1 activates the equalizer, and the "CustomBand#" lines acts as an equalizer with the lowest frequencies in CustomBand0 and the highest in CustomBand8. It seems like the valid values are between -20 to (+)10. I have no idea what the EQPreset variable does...
After you have changed something and saved the file, load the new setting with:
```
/usr/bin/nvmix-reg -f /etc/nvmixrc -L
```

---

### Post by dustoashes on 2008-04-26
Ok, but finding out a good sound configuration with this is an issue. Is there anything I could use, for example, in Amarok to enhance the sound quality?

---

### Post by jocko on 2008-04-26
> **dustoashes said:**
> Ok, but finding out a good sound configuration with this is an issue. Is there anything I could use, for example, in Amarok to enhance the sound quality?

I'm not that familiar with amarok but I installed it just to see how it works.
It has it's own equalizer (under Tools --> Equalizer), and there's a bunch of presets you could try. Is that what you mean by enhance sound quality?
I think you should also set it to use oss output (Settings --> configure amarok -->Interface --> Output plugin).

---

### Post by simpleharmonics on 2008-06-20
Is there an update for the 2.6.25 and higher kernels?  When I try to build the module I am getting this error:

  cc -Wp,-MD,/home/salvador/builds/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.nvalinux.o.d  -nostdinc -isystem /usr/lib/gcc/i686-pc-linux-gnu/4.3.1/include -D__KERNEL__ -Iinclude  -include include/linux/autoconf.h -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -O2  -fno-stack-protector -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boundary=2  -march=i686 -mtune=generic -ffreestanding -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Iinclude/asm-x86/mach-default -fomit-frame-pointer -Wdeclaration-after-statement -Wno-pointer-sign   -I/home/salvador/builds/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wimplicit -Wreturn-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith  -Wno-multichar  -Werror -O -MD   -Wno-cast-qual -Wno-error  -DNV_REMAP_PFN_RANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(nvalinux)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)" -c -o /home/salvador/builds/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.o /home/salvador/builds/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c
In file included from include/linux/list.h:8,
                 from include/linux/module.h:9,
                 from /home/salvador/builds/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:19:
include/linux/prefetch.h: In function ‘prefetch_range’:
include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in arithmetic
In file included from include/asm/dma-mapping_32.h:5,
                 from include/asm/dma-mapping.h:2,
                 from include/linux/dma-mapping.h:52,
                 from include/asm-generic/pci-dma-compat.h:7,
                 from include/asm/pci.h:90,
                 from include/linux/pci.h:945,
                 from /home/salvador/builds/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:29:
include/linux/scatterlist.h: In function ‘sg_virt’:
include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used in arithmetic
In file included from /home/salvador/builds/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:37:
include/linux/highmem.h: In function ‘zero_user_segments’:
include/linux/highmem.h:134: warning: pointer of type ‘void *’ used in arithmetic

and so on.  I've applied the 2.6.24 patch to no avail.  Any ideas?

---

### Post by jocko on 2008-06-21
> **simpleharmonics said:**
> Is there an update for the 2.6.25 and higher kernels?  When I try to build the module I am getting this error:
...
I've applied the 2.6.24 patch to no avail.  Any ideas?

I'm not sure I see any error in there... If there is an error, you should see the word "error" with a short description after it. I saw at least some of those messages/warnings on 2.6.24 and earlier, even when the compilation worked.
Can you post the entire contents in your /var/log/nvidia-nforce-installer.log?
It may give some clue...
I haven't tried it on 2.6.25, but on 2.6.26 I got LOTS of errors. I managed to get rid of some of them, but some others I could not solve.
If you show me the log from your failure on 2.6.25, maybe I can figure it out with some googling... Or, if you manage to solve it yourself, please share your solution...

---

### Post by timmio87 on 2008-07-06
Hey I'm having problems patching the extracted nvidia driver, after running the following code

```
./2.6.24-patch
sudo ./nforce-installer
```

i get the following error message

```
tim@Bill:~/NFORCE-Linux-x86-1.0-0310-pkg1$ ./2.6.24-patch
./2.6.24-patch: 2: patch: not found
./2.6.24-patch: 3: patch: not found
./2.6.24-patch: 4: patch: not found
./2.6.24-patch: 5: patch: not found
./2.6.24-patch: 6: patch: not found
```

does anyone have ideas, as I've read all of this thread and no ones had a similar problem so I must be doing something wrong?

---

### Post by jocko on 2008-07-06
> **timmio87 said:**
> Hey I'm having problems patching the extracted nvidia driver, after running the following code

```
./2.6.24-patch
sudo ./nforce-installer
```i get the following error message

```
tim@Bill:~/NFORCE-Linux-x86-1.0-0310-pkg1$ ./2.6.24-patch
./2.6.24-patch: 2: patch: not found
./2.6.24-patch: 3: patch: not found
./2.6.24-patch: 4: patch: not found
./2.6.24-patch: 5: patch: not found
./2.6.24-patch: 6: patch: not found
```does anyone have ideas, as I've read all of this thread and no ones had a similar problem so I must be doing something wrong?

EDIT: Found the problem (I think):
Did you really follow my instructions exactly as they are written?
It looks to me that you don't have the program "patch" installed, which means you have not installed **build-essential**, so you skipped step 1 in the howto...

---

### Post by simpleharmonics on 2008-07-16
> **jocko said:**
> I'm not sure I see any error in there... If there is an error, you should see the word "error" with a short description after it. I saw at least some of those messages/warnings on 2.6.24 and earlier, even when the compilation worked.
Can you post the entire contents in your /var/log/nvidia-nforce-installer.log?
It may give some clue...
I haven't tried it on 2.6.25, but on 2.6.26 I got LOTS of errors. I managed to get rid of some of them, but some others I could not solve.
If you show me the log from your failure on 2.6.25, maybe I can figure it out with some googling... Or, if you manage to solve it yourself, please share your solution...

sorry I haven't checked back, I ended up keeping the .24 kernel for now.  basically running the installer gives the warnings about pointers and fails to build the module.  I will post the install log when i get home later tonight.

I think it has something to do with gcc 4.3 (or later), but I'm talking from memory, will have more info later.

Has anyone else had success with the .25+ kernels and the nforce-nvsound module?

---

### Post by thewarlord on 2008-07-17
hi folks,

many thanks for this great how to!

only when i will play some games my sound didnt work.


It says:

3D EGO Shooter Sauerbraten gives me:
> ALSA lib pcm_direct.c:1492:(_snd_pcm_direct_get_slave_ipc_offset) Invalid value for card

or some other games like secret maryo chronicles

ALSA lib pcm_direct.c:1492:(_snd_pcm_direct_get_slave_ipc_offset) Invalid value for card
Last known SDL Error : No available audio device



Is it possible that I receive this error message from everything witch uses ALSA??

Anyone an idea?

---

### Post by jocko on 2008-07-17
> **thewarlord said:**
> Is it possible that I receive this error message from everything witch uses ALSA??

Anyone an idea?

Yes, that's it. Anything that tries to use alsa will fail. If there is no way to tell the application to use oss instead ther is no easy way to fix it.
In Gutsy it's possible to set alsa to use a pulseaudio plugin, which redirects alsa to oss through pulseaudio, but unfortunately a NASTY bug in pulseaudio (which the pulseaudio developers claim is in the nvsound driver...) makes the entire system freeze up completely whenever you try to combine nvsound with pulseaudio...
So if you use gutsy, it's relatively easy to fix, while in hardy it probably impossible...

---

### Post by simpleharmonics on 2008-07-17
[edit: forgot to add this ONLY works with 2.6.25 kernel - I have not tested with other kernels, so YMMV, and you might have to edit the patch file manually.  I am also using arch-linux, so I was using the 2.6.24 patches posted on the first page, plus the changes I made to create the patch file, so again YMMV]

For those of you (the two or three of us left :) ) having problems building the binary driver, here's what I've determined.  The nvsound module was not being build because of the similar problem described for the nvidia graphics module as seen here:
[http://www.nvnews.net/vbulletin/showthread.php?t=107144](http://www.nvnews.net/vbulletin/showthread.php?t=107144)
A patch for the nvidia graphics driver was posted in page 4, and several revisions thereafter:
[http://www.nvnews.net/vbulletin/showthread.php?t=107144&page=4](http://www.nvnews.net/vbulletin/showthread.php?t=107144&page=4)

I didn't really go into the revisions too much, but that first patch led me to believe the same problem that the graphics driver is having was happening here, mainly an issue with a call to the (now-defunct in the kernel) init_mm function, and other functions associated with it (change_page_attr() and global_flush_tlb()).

Soooooo..  based on that patch, I created a new one that replaces the same functions by ones that "work", but because of the way nvsound is set up on the source files available, what ends up happening is that, unlinke the graphic driver, we will not have a memory flush function in the sound driver.  But it builds, and it works, and so far (I built and installed the module last night) I haven't had any problems.  

I'm thinking the lack of flushing of ram/cpu or whatever the "global_flush_tlb() function did *might* cause a crash eventually, due to some memory error or cpu register error.  my log files indicate that something bad might be happening :confused:  but so far no crashes, and the kernel seems to be clearing out the problems itself:

```
Jul 17 11:14:28 anonymous WARNING: at arch/x86/kernel/pci-dma_32.c:66 dma_free_coherent+0x80/0x90()
Jul 17 11:14:28 anonymous Modules linked in: nvsound(P) soundcore nvidia(P) xt_tcpudp ipt_REJECT nf_conntrack_ipv4 xt_state nf_conntrack iptable_filter ip_tables x_tables asb100 hwmon_vid psmouse serio_raw shpchp pci_hotplug pcspkr ohci_hcd ehci_hcd i2c_nforce2 i2c_core usbcore nvidia_agp agpgart sg evdev thermal processor fan button battery ac skge sk98lin rtc_cmos rtc_core rtc_lib ext3 jbd mbcache sr_mod cdrom sd_mod pata_acpi sata_sil ata_generic pata_amd libata scsi_mod dock [last unloaded: soundcore]
Jul 17 11:14:28 anonymous Pid: 10578, comm: amarokapp Tainted: P         2.6.25-ARCH #1
Jul 17 11:14:28 anonymous [<c0128e9f>] warn_on_slowpath+0x5f/0xa0
Jul 17 11:14:28 anonymous [<c0125a26>] hrtick_set+0xc6/0x140
Jul 17 11:14:28 anonymous [<c03058ff>] schedule+0x3af/0x850
Jul 17 11:14:28 anonymous [<c012365d>] try_to_wake_up+0x6d/0x140
Jul 17 11:14:28 anonymous [<c0140d04>] enqueue_hrtimer+0x74/0x100
Jul 17 11:14:28 anonymous [<f9629341>] AosInterruptStatePop+0x10/0x1b [nvsound]
Jul 17 11:14:28 anonymous [<f961eeef>] _ZN8CNvAudio20VoiceProcLockReleaseEv+0x25/0x34 [nvsound]
Jul 17 11:14:28 anonymous [<c0109910>] dma_free_coherent+0x80/0x90
Jul 17 11:14:28 anonymous [<f96294ff>] AosMemoryFreePhysical+0xe4/0x108 [nvsound]
Jul 17 11:14:28 anonymous [<f95869e1>] _Z18AosListRemoveEntryP8NVA_LISTP14NVA_LIST_ENTRY+0x85/0x90 [nvsound]
Jul 17 11:14:28 anonymous [<f95863ec>] _ZdlPv+0x38/0x50 [nvsound]
Jul 17 11:14:28 anonymous [<f95d6050>] _ZN8CNvVoiceD0Ev+0x160/0x168 [nvsound]
Jul 17 11:14:28 anonymous [<f9586c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
Jul 17 11:14:28 anonymous [<f95ca5f1>] _ZN9CNvStream12FinalReleaseEv+0x57/0x68 [nvsound]
Jul 17 11:14:28 anonymous [<f9586c14>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x2a/0x48 [nvsound]
Jul 17 11:14:28 anonymous [<f961eccb>] _ZN9CNvStream7ReleaseEv+0x17/0x1c [nvsound]
Jul 17 11:14:28 anonymous [<f96120ad>] _ZN13CApuStreamPciD0Ev+0x47/0xd6 [nvsound]
Jul 17 11:14:28 anonymous [<f9586c20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
Jul 17 11:14:28 anonymous [<f961fe53>] _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
Jul 17 11:14:28 anonymous [<f960c098>] Nv_FreeNewstream+0x2c/0x38 [nvsound]
Jul 17 11:14:28 anonymous [<f962ab49>] Nvfree_wave_device+0x51/0xd6 [nvsound]
Jul 17 11:14:28 anonymous [<f962aca2>] Nvaudio_release+0xd4/0xe5 [nvsound]
Jul 17 11:14:28 anonymous [<c0186136>] __fput+0x96/0x160
Jul 17 11:14:28 anonymous [<c0182ce9>] filp_close+0x49/0x80
Jul 17 11:14:28 anonymous [<c0182d99>] sys_close+0x79/0xd0
Jul 17 11:14:28 anonymous [<c01050d8>] sysenter_past_esp+0x6d/0xa5
Jul 17 11:14:28 anonymous =======================
Jul 17 11:14:28 anonymous ---[ end trace b4e207752bffd14f ]---                                    
```

[edit 3: the log shows nvsound is unloaded, but I've experienced no loss of sound while watching movies or playing sounds - YMMV]

so here's the patch, the way I got it to work was extracting the NFORCE-xxx.run file, cd to the NFORCE dir, then run
patch -p1 < ../nforce-nvsound.patch
by the way, this patch takes into account any previous patches already made, so this should be the only patch you need to apply.  The only changes i made were to nvavm.h and conftest.sh.  once you run the nforce-install script (on the NFORCE-xxx dir) it should build the sound module and install it properly.

[edit 2: It's sad that there are no open-source drivers for this motherboard/soundcard combo, considering it's been discontinued and nVidia doesn't support it anymore.  And with more changes to future kernels, we'll probably have no choice but to stop using the soundstorm chip (other than with alsa/oss and the dreaded intel8x0 which has not been really satisfactory to my ears).  so we can probably expect more things to break with newer kernels]

---

### Post by jocko on 2008-07-17
> **simpleharmonics said:**
> ...I created a new one that replaces the same functions by ones that "work", ...
Excellent work. I was trying something similar a couple of weeks back, also partially based on patches I found for the nvidia graphics driver, but I gave up after a while because I just got other errors after I solved the first ones, and my attempts to fix those errors resulted in more errors and so on... that was with a 2.6.26 kernel, though...
I think I will try to use your patch on 2.6.26 and see if I can get any further.
In that case I'll probably add your patches (or modifications of it that works with 2.6.26) to the howto...

** Edit:** Just tried, and it errors out with:
```
/home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c: In function &#8216;AosFpuSave&#8217;:
   /home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:189: error: &#8216;struct thread_struct&#8217; has no member named &#8216;i387&#8217;
   /home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:193: error: &#8216;struct thread_struct&#8217; has no member named &#8216;i387&#8217;
   /home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:187: error: invalid lvalue in asm output 0
   /home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:191: error: invalid lvalue in asm output 0
   make[4]: *** [/home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.o] Error 1
   make[3]: *** [_module_/home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main] Error 2
   make[2]: *** [sub-make] Error 2
-> Error.
```So I guess there's more to do... I'll see what Google tells me...
** Edit 2:** Google isn't helpful today... Hope someone else have an idea...

---

### Post by simpleharmonics on 2008-07-17
> **jocko said:**
> Excellent work. I was trying something similar a couple of weeks back, also partially based on patches I found for the nvidia graphics driver, but I gave up after a while because I just got other errors after I solved the first ones, and my attempts to fix those errors resulted in more errors and so on... that was with a 2.6.26 kernel, though...
Thanks.  I've been looking for a solution since 2.6.25 came out and haven't found one, so I was doing searches for the specific errors and saw the nvidia graphics driver had a similar issue.

> **jocko said:**
> I think I will try to use your patch on 2.6.26 and see if I can get any further.
In that case I'll probably add your patches (or modifications of it that works with 2.6.26) to the howto...

** Edit:** Just tried, and it errors out with:
```
/home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c: In function &#8216;AosFpuSave&#8217;:
   /home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:189: error: &#8216;struct thread_struct&#8217; has no member named &#8216;i387&#8217;
   /home/jocko/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:193: error: &#8216;struct thread_struct&#8217; has no member named &#8216;i387&#8217;

Well, try this patch.  This only contains the changes I made to the two files nvavm.h and conftest.sh, so apply the patch on this thread's first page (or any that you've created since) and then this one using 

[code]patch -p1 ../nvsound-mini.patch
```

Maybe you can find something I edited out or changed that might have affected it.  Maybe something changed in 2.6.26?
From the error message the file affected was one changed by the original patches on the first page, either the nvalinux.c-patch or nvalinux.h-patch.  When I build I only get a warning at that point.

If you are using new patches and adding mine works, could you post the file here? either individual patches or all-in-one, I want to make sure when I get the 2.6.26 kernel I have something ready to test for it.

---

### Post by jocko on 2008-07-17
> **simpleharmonics said:**
> Thanks.  I've been looking for a solution since 2.6.25 came out and haven't found one, so I was doing searches for the specific errors and saw the nvidia graphics driver had a similar issue.



Well, try this patch.  This only contains the changes I made to the two files nvavm.h and conftest.sh, so apply the patch on this thread's first page (or any that you've created since) and then this one using 

```
patch -p1 ../nvsound-mini.patch
```Maybe you can find something I edited out or changed that might have affected it.  Maybe something changed in 2.6.26?
From the error message the file affected was one changed by the original patches on the first page, either the nvalinux.c-patch or nvalinux.h-patch.  When I build I only get a warning at that point.

If you are using new patches and adding mine works, could you post the file here? either individual patches or all-in-one, I want to make sure when I get the 2.6.26 kernel I have something ready to test for it.

I couldn't get your mini-patch to apply (some malformed lines around line 47), but I manually edited the files according to what I guess the malformed lines should look like. It builds fine on 2.6.24, but not on 2.6.26 (same errors as in my post above).
So I guess the problem is caused by a difference between the 2.6.25 and .26 kernels...

**EDIT:** I think I may have found a fix (googled for the offending functions "thread.i387.fxsave" and "thread.i387.fsave" and found how these functions were replaced in 2.6.26-rc9, and did the same changes in nvalinux.c...).
It now seems to build fine (in a virtual machine, so I haven't actually tested that the driver works).

I attach an [updated patch collection here]("http://ubuntuforums.org/attachment.php?attachmentid=78093&stc=1&d=1216332241"), in case anyone feels like testing it on a real machine with a 2.6.26 kernel before I have time to get an intrepid livecd to test with...
To apply the patches, just follow the relevant steps (3 and 4) of the main howto, but apply the correct patches and install like this [instead of step 4 -II a) or b)]:
```
./2.6.26-patch
sudo ./nforce-installer
```

---

### Post by ppurka on 2008-07-31
> **jocko said:**
> I attach an [updated patch collection here]("http://ubuntuforums.org/attachment.php?attachmentid=78093&stc=1&d=1216332241"), in case anyone feels like testing it on a real machine with a 2.6.26 kernel before I have time to get an intrepid livecd to test with...Excellent patch! It [works well]("http://omploader.org/vbjR3")! At least on my gentoo system ;)
Thanks!

---

### Post by jocko on 2008-08-01
> **ppurka said:**
> Excellent patch! It [works well]("http://omploader.org/vbjR3")! At least on my gentoo system ;)
Thanks!
Thanks for the testing and info.
I haven't come around to test it on an itrepid alpha install yet.
It appears to work on a livecd session, at least I get dolby digital output when I load the module, the mixer fails to start but I guess it will work after a reboot on a real install...

---

### Post by thewarlord on 2008-08-16
In order to use OSS with games like Sauerbraten you need to install package:

libsdl1.2debian-oss and remove libsdl1.2debian-alsa.

hope that help people like me how had problem with this...

---

### Post by fspade on 2008-08-28
please skip to next post :(

---

### Post by fspade on 2008-08-28
Hi guys,

I have tried to follow the HOWTO, but got stuck at step 4.II.b: [PHP]ERROR: ... include/linux/autoconf.h or include/config/auto.conf are missing.[/PHP]I did [PHP]sudo make oldconfig && sudo make prepare && sudo make modules[/PHP]
I still get the same errors, even though include/linux/autoconf.h and include/config/auto.conf exist!

Since I don't really know what I am doing here and don't want to get into more trouble then necessary, I would appreciate somebody telling me how to proceed.

This is under ubuntu 8.04 (2.6.24-19-server). I have the 2.6.24-16-generic and 2.6.24-19-generic headers installed.

When I went back and redid [PHP]sudo ./2.6.24-patch
[/PHP] I got the following errors:[PHP]patching file nvsound/main/Makefile.kbuild
Reversed (or previously applied) patch detected!  Assume -R? [n] y
patching file nvsound/main/nvmain.c
Reversed (or previously applied) patch detected!  Assume -R? [n] y
Hunk #3 FAILED at 2191.
Hunk #4 FAILED at 2208.
2 out of 4 hunks FAILED -- saving rejects to file nvsound/main/nvmain.c.rej
patching file nvsound/main/nvaioctl.h
patching file nvsound/main/nvalinux.c
Hunk #1 succeeded at 71 (offset 8 lines).
Hunk #2 succeeded at 75 (offset 8 lines).
patching file nvsound/main/nvalinux.h
Reversed (or previously applied) patch detected!  Assume -R? [n] y
[/PHP]I did answer y for every question. The reject file looks like this:[PHP]***************
*** 2191
- module_param(vapu_enable, int, 0444);
--- 2191 -----
+ MODULE_PARM(vapu_enable, "i");
***************
*** 2208
-     ret = ret = pci_register_driver(&Nvaudio_pci_driver);
--- 2208 -----
+     ret = pci_module_init(&Nvaudio_pci_driver);[/PHP]
I am lost ... please help.

Kind regards,

Frank

---

### Post by jocko on 2008-09-20
From what I see, you had already applied the patch, so when you tried again it tried to reverse the patch instead (restore it to it's original form, which will not work).
Delete the folder where you unpacked the installer (~/NFORCE-Linux-x86-1.0-0310-pkg1) and start over from the beginning.
When did you see the error about missing autoconf.h or auto.conf?
Did the installer quit with that error or did you just see it in the log file on a line starting with "echo" (which is normal and not a problem)?
If you have the kernel and headers and apply the correct patch to the nvsound files it will work (I have never tried it on a server kernel, but I can't see why it wouldn't work).

And, by the way: I see you used the patch with sudo. Don't. The commands in the howto that does not have "sudo" in front of them should NOT be run with sudo (the installer files should be unpacked in your home directory, with you as the owner. After you apply the patches, the patched files should still be yours.). You may mess up the permission on the files in ~/NFORCE-Linux-x86-1.0-0310-pkg1, making every other step fail unless you run everything else with sudo.

Sorry for not answering sooner (just moved to a new town, new job and have been stuck without an internet connection at home for the last month...).

---

### Post by laiclair on 2008-09-21
Works for me using debian lenny 2.6.26-1-686.
5.1 Analogic creative.
Asus A7n8x dl.

ThX for this really good souuuuunnnndddd

---

### Post by Icarosaurus on 2008-09-23
The patch for 2.6.26 kernel works for 2.6.27 too. Thank you.

---

### Post by Icarosaurus on 2008-10-04
I'm able to listen Gnome system sounds using esd!
Well... yes, I wasn't able to listen to system sound using a fresh 8.04 and the Jocko's guide.
I just used the following guide till the "Building OSS" step.
I didn't need to build my own OSS, in fact.

[https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound")

---

### Post by xMachina on 2008-10-04
Hi guys - just a note that you might want to install a little tool called "oss-preserve" which will save your OSS mixer and volume settings when you log off. Otherwise, I found the volume was always reset to 100% on restart, which was really annoying.

Just "sudo apt-get install oss-preserve" as per usual.

Worth adding to the HOWTO on the front page?

---

### Post by jocko on 2008-10-06
> **xMachina said:**
> Hi guys - just a note that you might want to install a little tool called "oss-preserve" which will save your OSS mixer and volume settings when you log off. Otherwise, I found the volume was always reset to 100% on restart, which was really annoying.

Just "sudo apt-get install oss-preserve" as per usual.

Worth adding to the HOWTO on the front page?

For me it works fine without it. It should be taken care of by the /etc/modprobe.d/nvsound file that is included in the howto, which loads the saved nvmixer settings on boot.

---

### Post by eriktenburen on 2008-10-31
Hey Jocko and the rest.

I was wondering if I can do a clean install of 8.10? Does your howto still work with the new Ubuntu release? I can't/won't loose my DD5.1 soundstorm crystal clear sound!:)

Thanx for your support!

---

### Post by jocko on 2008-11-01
> **eriktenburen said:**
> Hey Jocko and the rest.

I was wondering if I can do a clean install of 8.10? Does your howto still work with the new Ubuntu release? I can't/won't loose my DD5.1 soundstorm crystal clear sound!:)

Thanx for your support!

It should work now. I added my latest patches to the main howto a couple of minutes ago, I haven't tested them myself in the current intrepid kernel (2.6.27), but according to Icorasaurus' post above it does work.
Just make sure you don't use pulseaudio (or at least don't load pulseaudio's "module-oss" module), as it will most likely cause your system to freeze.

---

### Post by jocko on 2008-11-01
> **Icarosaurus said:**
> I'm able to listen Gnome system sounds using esd!
Well... yes, I wasn't able to listen to system sound using a fresh 8.04 and the Jocko's guide.
I just used the following guide till the "Building OSS" step.
I didn't need to build my own OSS, in fact.

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Ok. I just added the relevant instructions to the howto (install esound, which was replaced by a pulseaudio wrapper in hardy...)

---

### Post by Icarosaurus on 2008-11-05
I'm still using hardy, but I tested the driver with the intrepid kernel for few days.
I confirm it worked.

---

### Post by brundlfly on 2008-11-07
Hi- the link in the how-to for nvsound-patch2.6.16-2.6.24.tar.gz seems to be broken and I don't see it anywhere else (but I did find your crosslink in nV news. Help please?

---

### Post by Icarosaurus on 2008-11-07
Go to this post:
[http://ubuntuforums.org/showpost.php?p=5406130&postcount=244](http://ubuntuforums.org/showpost.php?p=5406130&postcount=244)

---

### Post by jocko on 2008-11-08
> **brundlfly said:**
> Hi- the link in the how-to for nvsound-patch2.6.16-2.6.24.tar.gz seems to be broken and I don't see it anywhere else (but I did find your crosslink in nV news. Help please?
Sorry. I changed the tar.gz to one that includes patches for kernel 2.6.27, but forgot to change the link in the text (the correct one was still attached at the bottom of the howto). It's fixed now. Here's the correct link: [nvsound-patch2.6.16-2.6.27.tar.gz]("http://ubuntuforums.org/attachment.php?attachmentid=90526&d=1225519160")

---

### Post by SyL on 2008-11-09
Thanks Dude!!
I got now my sound working on my old asus a7n8x deluxe under 8.10!!

:-)

---

### Post by fok on 2008-11-13
I get the following warning, over and over:

[PHP]Nov 13 14:41:53 fok kernel: [18969.979545] WARNING: at /build/buildd/linux-2.6.27/arch/x86/kernel/pci-dma.c:376 dma_free_coherent+0x88/0x90()
Nov 13 14:41:53 fok kernel: [18969.979548] Modules linked in: af_packet container pci_slot sbs wmi battery sbshc video output iptable_filter ip_tables x_t
ables ac parport_pc lp parport evdev psmouse serio_raw nvidia(P) pcspkr button nvsound(P) i2c_nforce2 soundcore i2c_core nvidia_agp shpchp pci_hotplug agp
gart ext3 jbd mbcache sr_mod cdrom pata_acpi sd_mod crc_t10dif sg pata_amd sata_sil ata_generic libata skge scsi_mod dock ohci_hcd ehci_hcd forcedeth usbc
ore thermal processor fan fbcon tileblit font bitblit softcursor fuse
Nov 13 14:41:53 fok kernel: [18969.979583] Pid: 9987, comm: winamp.exe Tainted: P        W 2.6.27-7-generic #1
Nov 13 14:41:53 fok kernel: [18969.979585]  [<c037c406>] ? printk+0x1d/0x1f
Nov 13 14:41:53 fok kernel: [18969.979590]  [<c0131de9>] warn_on_slowpath+0x59/0x90
Nov 13 14:41:53 fok kernel: [18969.979594]  [<c018916e>] ? get_pageblock_flags_group+0xe/0x80
Nov 13 14:41:53 fok kernel: [18969.979598]  [<c018916e>] ? get_pageblock_flags_group+0xe/0x80
Nov 13 14:41:53 fok kernel: [18969.979603]  [<c018abdf>] ? free_hot_page+0xf/0x20
Nov 13 14:41:53 fok kernel: [18969.979606]  [<c018afa7>] ? __free_pages+0x37/0x40
Nov 13 14:41:53 fok kernel: [18969.979610]  [<c0108171>] ? dma_free_coherent+0x71/0x90
Nov 13 14:41:53 fok kernel: [18969.979614]  [<f8c4d5c9>] ? AosMemoryFree+0x46/0x4e [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979657]  [<f8c4d5c9>] ? AosMemoryFree+0x46/0x4e [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979700]  [<f8c4d707>] ? AosMemoryFreePhysical+0xfa/0x107 [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979743]  [<c0108188>] dma_free_coherent+0x88/0x90
Nov 13 14:41:53 fok kernel: [18969.979748]  [<f8c4d6f7>] AosMemoryFreePhysical+0xea/0x107 [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979791]  [<f8bb326b>] ? _ZN20CStreamingAciChannelD0Ev+0x75/0x7c [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979825]  [<f8baa3ec>] _ZdlPv+0x38/0x50 [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979857]  [<f8c342eb>] _ZN13CAciStreamPciD0Ev+0xd1/0xd8 [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979903]  [<f8baac20>] _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979936]  [<f8c43cd3>] _ZN13CAciStreamPci7ReleaseEv+0x17/0x1c [nvsound]
Nov 13 14:41:53 fok kernel: [18969.979981]  [<f8c30098>] Nv_FreeNewstream+0x2c/0x38 [nvsound]
Nov 13 14:41:53 fok kernel: [18969.980012]  [<f8c4ed70>] Nvfree_wave_device+0xa2/0xd8 [nvsound]
Nov 13 14:41:53 fok kernel: [18969.980012]  [<f8c4ee82>] Nvaudio_release+0xdc/0xee [nvsound]
Nov 13 14:41:53 fok kernel: [18969.980012]  [<c01b3490>] __fput+0xb0/0x190
Nov 13 14:41:53 fok kernel: [18969.980012]  [<c01b358f>] fput+0x1f/0x30
Nov 13 14:41:53 fok kernel: [18969.980012]  [<c01afe8e>] filp_close+0x4e/0x80
Nov 13 14:41:53 fok kernel: [18969.980012]  [<c02147d8>] ? cap_file_ioctl+0x8/0x10
Nov 13 14:41:53 fok kernel: [18969.980012]  [<c01aff3f>] sys_close+0x7f/0xd0
Nov 13 14:41:53 fok kernel: [18969.980012]  [<c0103f7b>] sysenter_do_call+0x12/0x2f
Nov 13 14:41:53 fok kernel: [18969.980012]  =======================
Nov 13 14:41:53 fok kernel: [18969.980012] ---[ end trace c351670e487632d8 ]---
[/PHP]

dmesg bit:
[PHP]
[   12.845480] nvsound: module license 'NVIDIA' taints kernel.
[   12.846307] Symbol init_mm is marked as UNUSED, however this module is using it.
[   12.846310] This symbol will go away in the future.
[   12.846313] Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting y
our code for inclusion.
[   12.886893] Nvsound: Nvidia Audio Init Module, 11:29:30 Nov 12 2008 version 1.0-7
[   12.888666] ACPI: PCI Interrupt Link [APCI] enabled at IRQ 21
[   12.888675] nforce_audio 0000:00:05.0: PCI INT A -> Link[APCI] -> GSI 21 (level, high) -> IRQ 21
[   12.888682] nforce_audio 0000:00:05.0: setting latency timer to 64
[   12.888689] Nvsound:  NVIDIA nForce2 Controller Mem 0xe5000000 and IRQ 15
[   12.889029] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[   12.889034] nforce_audio 0000:00:06.0: PCI INT A -> Link[APCJ] -> GSI 20 (level, high) -> IRQ 20
[   12.889039] nforce_audio 0000:00:06.0: setting latency timer to 64
[   12.889046] Nvsound: NVIDIA nForce2 Audio aci 0xd400 and ac97 0xd000, IRQ 14
[   12.928248] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[   12.944031] ACPI: Power Button (FF) [PWRF]
[   12.944172] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input3
[   12.960024] ACPI: Power Button (CM) [PWRB]
[   13.169304] Nvsound: DEV MIXER 0 DEV AUDIO 3
[   13.195621] input: PC Speaker as /devices/platform/pcspkr/input/input4
[   15.643009] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   15.643022] nvidia 0000:03:00.0: PCI INT A -> Link[APC4] -> GSI 19 (level, high) -> IRQ 19
[   15.643490] NVRM: loading NVIDIA UNIX x86 Kernel Module  173.14.12  Thu Jul 17 18:11:36 PDT 2008
[/PHP]

I have an Asus A7N8X-e Deluxe running a Xubuntu 8.10 with linux kernel version 2.6.27-7. Albeit sound seems to work, the system hangs some times but I could not find out exactly why and I think it might be related. Any tips to eliminate the warning above will be appreciated. I can provide more info if you need.

---

### Post by jocko on 2008-11-13
> **fok said:**
> I get the following warning, over and over:

...

I have an Asus A7N8X-e Deluxe running a Xubuntu 8.10 with linux kernel version 2.6.27-7. Albeit sound seems to work, the system hangs some times but I could not find out exactly why and I think it might be related. Any tips to eliminate the warning above will be appreciated. I can provide more info if you need.

I don't see anything strange in that output... looks normal to me.
The only warning there is about something different ([COLOR=#000000][COLOR=#0000BB][/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]build[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]buildd[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]linux[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]2.6.27[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]arch[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]x86[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]kernel[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000BB]pci[/COLOR][COLOR=#007700]-[/COLOR][COLOR=#0000BB]dma[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000BB]c[/COLOR][/COLOR] whatever that is...)

One thing that can hang your system is if you use pulseaudio together with nvsound (but that would still require that you actively set pulseaudio to use oss output before it happens...).
Otherwise I don't think your problem is connected to your sound driver at all...

---

### Post by Sav on 2008-11-23
Hi, thanks for this how-to.
I followed every step, but I'm unable to access the oss sound module only by the root user.
For example:

launching "nvmixer": Nvsound: Unable to open the Mixer

launching "sudo nvmixer": perfect

launching mplayer (audio setted to oss): could not initialize audio device

launching "sudo mplayer": perfect

launching "gnome-sound-properties": I'm unable to test the oss module

launching "sudo gnome-sound-properties": I can set everything.

How can I solve this permission problem?

---

### Post by azzkickr on 2008-11-24
Hello there Gentlemen,

I have an old MSI K7N420 Pro with nForce 1 on board.

```
lspci | grep audio
```

Returns:

```
00:05.0 Multimedia audio controller: nVidia Corporation nForce Audio Processing Unit (rev c2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce AC'97 Audio Controller (rev c2)
```

Up to point 4 everything was fine and as expected. My speaker system (Logitech ZX-5400) showed [DIGITAL] on coaxial input but problems started when I ran 
```
nvmixer
```
I got 
```
$ nvmixer
Nvsound: Unable to open the Mixer 
Nvsound: Unable to open the Mixer 
Nvsound: Unable to open the Mixer 
Nvsound: Unable to open the Mixer
```
For like 50 lines. The the nvmixer opens with four tabs.
On the speaker tab Speaker Wizard and Surround Settings are inactive. Changing the default speakers - Headphones - to anything, it works until i close the application. Bu it works I mean it shows different speaker picture. That's it.

Running gstreamer-properties ends with:
```
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Error running pipeline 'OSS - Open Sound System': Could not open audio device for playback. You don't have permission to open the device. [gstosssink.c(423): gst_oss_sink_open (): /GstPipeline:pipeline0/GstOssSink:osssink2:
system error: Permission denied]

```

Crash.

Same with gnome-sound-properties
```
~$ gnome-sound-properties 
(gnome-sound-properties:15762): sound-properties-DEBUG: setting theme ubuntu
sound-properties-Message: Error running pipeline 'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink': Could not open audio device for playback. You don't have permission to open the device. [gstosssink.c(423): gst_oss_sink_open (): /GstBin:bin0/GstOssSink:osssink0:
system error: Permission denied]

```

Thanks in advance for any ideas...

---

### Post by jocko on 2008-11-25
Are you sure you don't have any alsa driver loaded?
Check the output of:
```
lsmod | grep snd_
```
If you get any output an alsa driver is still loaded, which prevents the nvsound driver from working.
If that's the case, make sure you did everything in the first part of step 2 correctly (= blacklist the alsa driver. Check your spelling and remember that linux is case sensitive). Reboot and try again.

---

### Post by azzkickr on 2008-11-25
I did all the steps very carefully.

```
lsmod | grep snd_
```
returns nothing.

My speakers do show digital input, there's no sound coming out and every time I try to play a sound I get:

```
Could not open audio device for playback. You don't have permission to open the device.
```

---

### Post by Xune on 2008-12-11
Hey Jocko et al. I've followed the steps laid out here and now have audio working nicely through the Soundstorm on my A7n8x Deluxe. Thank you very much.

I have one rather annoying problem at them moment that I'd appreciate guidance with though and that is that the settings are not being loaded between system shutdowns/restarts. I've setup an alias for /usr/bin/nvmix-reg -f /etc/nvmixrc -L, nvload, but when I run it I am give the following output:

Nvsound: RegSettings - File Stat failed 
nvmixer:mixer opening error

My alias for sudo /usr/bin/nvmix-reg -f /etc/nvmixrc -S, nvsave, works a-ok.

The only way I can reload settings is by manually inputting it into a terminal everytime the system is booted up.

I've checked that the nvsound file in modprobe.d is present and owned by root, so I'm a bit stumped as to why the settings aren't loading, either through this file or using the alias command.

---

### Post by jocko on 2008-12-11
> **Xune said:**
> Hey Jocko et al. I've followed the steps laid out here and now have audio working nicely through the Soundstorm on my A7n8x Deluxe. Thank you very much.

I have one rather annoying problem at them moment that I'd appreciate guidance with though and that is that the settings are not being loaded between system shutdowns/restarts. I've setup an alias for /usr/bin/nvmix-reg -f /etc/nvmixrc -L, nvload, but when I run it I am give the following output:

Nvsound: RegSettings - File Stat failed 
nvmixer:mixer opening error

My alias for sudo /usr/bin/nvmix-reg -f /etc/nvmixrc -S, nvsave, works a-ok.

The only way I can reload settings is by manually inputting it into a terminal everytime the system is booted up.

I've checked that the nvsound file in modprobe.d is present and owned by root, so I'm a bit stumped as to why the settings aren't loading, either through this file or using the alias command.

That's weird... I tried adding this to my ~/.bashrc:
```
alias nvload='/usr/bin/nvmix-reg -f /etc/nvmixrc -L'
```and it works fine, but if i change the spelling of the file name (/etc/nvmixrc), I get the same error as you, so it seems your save command did not save the file with the same name as you are trying to load...
Check that the file /etc/nvmixrc is really there, and that you have spelled it the same way (and the same case) in both of your aliases.

As a side note, I've noticed lately that the settings are not loaded on every boot, so I sometimes need to load them manually (which is much easier with an alias... thanks for the idea).

---

### Post by Xune on 2008-12-11
Gah. Sure enough, the alias had a typo in it. Thanks for looking.

Another handy alias is:

```
alias nvtweak='sudo gedit /etc/nvmixrc'
```

I find the graphical interface of the nvmixer too fiddly to get the balance of my speakers just right and this makes it a heck of a lot easier to fine tune levels without the guesswork.

---

### Post by Icarosaurus on 2008-12-13
Hi all,
Since I switched from Hardy to Intrepid I'm not able to get the driver to work.
As far as I remember, it worked in Intrepid Beta. No errors appear when installing the driver through the patched installer.

I was thinking it was something related to the new way Gnome is planning to manage sound, so I installed Xubuntu, with Xfce, but the result is the same.

When I try to open nvmixer, several "Unable to Open Mixer" messages appear, but the mixer window shows, even if not working.

**sudo nvmixer works, as other users here noticed, so I think it's a problem related to permissions**

This is my dmesg:
[http://pastebin.com/f736e8630]("http://pastebin.com/f736e8630")

This is my /var/log/nvidia-nforce-installer.log
[http://pastebin.com/f2833a84]("http://pastebin.com/f2833a84")

This is what I get in dmesg when rmmod/modprobe the module:
```

[ 2362.946336] Nvsound: Audio getting removed 00000000 
[ 2362.946351] Nvsound: Audio getting removed f7851d00 
[ 2363.165770] KERN_INFO Nvsound: Release DEV MIXER 0 
[ 2369.299735] Symbol init_mm is marked as UNUSED, however this module is using it.
[ 2369.299752] This symbol will go away in the future.
[ 2369.299755] Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting your code for inclusion.
[ 2369.305142] Nvsound: Nvidia Audio Init Module, 22:09:42 Dec 13 2008 version 1.0-7 
[ 2369.306375] nforce_audio 0000:00:05.0: setting latency timer to 64
[ 2369.306388] Nvsound:  NVIDIA nForce2 Controller Mem 0xe4000000 and IRQ 14
[ 2369.306818] nforce_audio 0000:00:06.0: setting latency timer to 64
[ 2369.306829] Nvsound: NVIDIA nForce2 Audio aci 0xd400 and ac97 0xd000, IRQ 16
[ 2370.017453] Nvsound: DEV MIXER 0 DEV AUDIO 3 

```

---

### Post by Icarosaurus on 2008-12-13
Problem solved.
Simply set the current user to "use audio devices" in the users/groups management. It looks like they forgot in the latest Ubuntu releases :p

I hope this can help many people having the same problem

---

### Post by TheAlteredState on 2008-12-23
hey guys,

I'm having the same problem, no sound at all... but with an ASUS M2N32-SLI Deluxe. Will this work with it too?

> root@thealteredstate:/home/tazz# lspci | grep audio
root@thealteredstate:/home/tazz# lsmod | grep snd_
snd_hda_intel         489264  6 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  3 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79432  20 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm


---

### Post by jocko on 2008-12-25
> **TheAlteredState said:**
> hey guys,

I'm having the same problem, no sound at all... but with an [COLOR=Red]ASUS M2N32-SLI Deluxe[/COLOR]. Will this work with it too?

No. you don't have an nvidia soundstorm chip, so this driver will not in any way help you. The sound chip in your motherboard is intel hda, which should work well with the snd-hda-intel driver that you're already using.
Make sure nothing is muted in alsamixer and that pulseaudio is working (assuming you use gnome).

---

### Post by leiflundgren on 2009-01-10
Hi,

I have an Ubuntu 8.04 system.
Yesterday newer kernel-versions got pushed out, now 2.6.24-23. 

And after reboot I found that I no longer had any sound.

After some digging it turns out that nsound-installer produces the "wrong" version. 
**dmesg:**
  [INDENT] [ 1517.418146] warning: process `nforce-installe' used the deprecated sysctl system call with 1.23.
   [ 1518.207292] nvsound: disagrees about version of symbol struct_module[/INDENT]
[B]
Error in GUI:
[/B][INDENT]Unable to load the kernel module 'nvsound.ko'. This is most likely because the kernel module was built using the wrong kernel source files.  Please make sure you have installed the kernel source files for your kernel; on Red Hat Linux systems, for example, be sure you have the 'kernel-source' rpm installed.  If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' commandline option.[/INDENT]

I've tried to download the linux-souce and specify it, but then it turned out that the "default" source wasn't configured like the 8.04 kernel, so nforce-installer refused to use it.

Note: uname -r :  2.6.24-23-386


Anyone got the same experience with new 2.6.24-23 kernel?

Regards
Leif

---

### Post by jocko on 2009-01-10
> **leiflundgren said:**
> I've tried to download the [COLOR=Red]linux-souce[/COLOR] and specify it, but then it turned out that the "default" source wasn't configured like the 8.04 kernel, so nforce-installer refused to use it.

Note: uname -r :  2.6.24-23-386


Anyone got the same experience with new 2.6.24-23 kernel?

Regards
Leif

1. You don't need to configure the source, just make sure the correct kernel headers are installed:
```
sudo apt-get install linux-headers-386
```2. Why do you have a -386 kernel installed? If you have a motherboard with an nforce2 chipset, I'm convinced that your processor is modern enough to run a -generic kernel.
-386 is for VERY old processors (older than pentium II, which was outdated 10 years ago...)
Unless you have a good reason for running a -386 kernel, my advice is to run this:
```
sudo apt-get install linux-generic
sudo apt-get install linux-headers-generic
```Reboot (make sure to hit Esc to get to the grub menu and make sure you boot the -generic kernel).
Run the nvidia installer again:
```
cd  ~/NFORCE-Linux-x86-1.0-0310-pkg1
sudo ./nforce-installer
```And, once you have seen that everything works: uninstall the -386 kernel (just search for -386 in synaptic).

---

### Post by leiflundgren on 2009-01-10
Thanks, you got it!

By some reason the 386-flavor had become default on my system although I had headers for the generic-flavor installed.

After changing default-image in grub, a reboot and re-installation my SoundStorm kicked back in.

Cheers!

---

### Post by pipik on 2009-02-04
nvsound module dont load with kernel 2.6.28 & 2.6.28.3

2.6.28* Kernel config is almost the same that 2.6.27 that works flawlessly (make oldconfig).


```
# modprobe nvsound
FATAL: Error inserting nvsound (/lib/modules/2.6.28.3/kernel/sound/oss/nvsound.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```

[QUOTE="dmesg"]nvsound: Unknown symbol unregister_sound_dsp
nvsound: Unknown symbol unregister_sound_mixer
Symbol init_mm is marked as UNUSED, however this module is using it.
This symbol will go away in the future.
Please evalute if this is the right api to use and if it really is, submit a rep                                                                                                                        ort the linux kernel mailinglist together with submitting your code for inclusio                                                                                                                        n.
nvsound: Unknown symbol register_sound_mixer
nvsound: Unknown symbol register_sound_dsp
[/QUOTE]

---

### Post by jocko on 2009-02-05
> **pipik said:**
> nvsound module dont load with kernel 2.6.28 & 2.6.28.3

2.6.28* Kernel config is almost the same that 2.6.27 that works flawlessly (make oldconfig).


```
# modprobe nvsound
FATAL: Error inserting nvsound (/lib/modules/2.6.28.3/kernel/sound/oss/nvsound.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
Probably some function in the kernel has been renamed or replaced with another one. If we're lucky it's possible to find a workaround or some dirty hack to get it working...

I may look into it if I get bored some weekend, until then I hope someone else have any ideas.

In case someone likes to give it a try:
The last time a kernel upgrade broke the nvsound module (somewhere between 2.6.24 and 2.6.26 or .27), I looked through the kernel changelogs ([kernel.org]("http://kernel.org/")) to find what happened to the function that gave the error in that case. In this case a good start would be to find out what "register_sound_mixer" and "register_sound_dsp" have been replaced with and make the corresponding changes in NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c (lines 2134 and 2143). After that there may be new similar errors that may be solved in a similar way...

---

### Post by celenhein on 2009-02-15
My NforceSoundStorm APU work verry nice on SPDIF in dolby digital with kaffeine or vlc, totem, etc , but i dont have sound in FIREFOX or SEAMONKEY on youtube.com or similar sites build on flash video.
Is there a chance to work flash sound on SPDIF output ?

I am running UBUNTU 8.04

Thanks.

---

### Post by jocko on 2009-02-15
> **celenhein said:**
> My NforceSoundStorm APU work verry nice on SPDIF in dolby digital with kaffeine or vlc, totem, etc , but i dont have sound in FIREFOX or SEAMONKEY on youtube.com or similar sites build on flash video.
Is there a chance to work flash sound on SPDIF output ?

I am running UBUNTU 8.04

Thanks.
First make sure you *don't* have the libflashsupport package installed (search in synaptic, and mark it for complete removal if it's installed). That's a crippled version of flashsupport where they by some stupid reason stripped out oss support.
Then follow the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=1716845&postcount=61") to install the real flashsupport (but note that some of the packages listed in that post may have different version numbers, so instead of libicu34 you may have to install libicu36 and so on... search for them in synaptic.

---

### Post by celenhein on 2009-02-19
> **jocko said:**
> First make sure you *don't* have the libflashsupport package installed (search in synaptic, and mark it for complete removal if it's installed). That's a crippled version of flashsupport where they by some stupid reason stripped out oss support.
Then follow the instructions in [this post]("http://ubuntuforums.org/showpost.php?p=1716845&postcount=61") to install the real flashsupport (but note that some of the packages listed in that post may have different version numbers, so instead of libicu34 you may have to install libicu36 and so on... search for them in synaptic.

Thanks. I will tryto do  what you say above.

---

### Post by celenhein on 2009-02-19
> **celenhein said:**
> Thanks. I will tryto do  what you say above.

Thanks.

It works even with Adobe Flash Player 10 plugin

:guitar:

---

### Post by jocko on 2009-03-08
Just an update for the problem with kernel 2.6.28:
The problem was that one of my patch files were slightly malformatted (a couple of tabs where there should only have been spaces). I don't understand why it worked on 2.6.27 with this error, but now it's fixed.
Just download the new patches from the first post and repeat everything under step 4 of the howto to get it working...
So SoundStorm is still alive... :guitar:

---

### Post by mintochris on 2009-04-01
I'm having some trouble on a fresh jaunty install, where the patching fails on nvalinux.c, and the build process then fails. I've included the relevant errors (i think!) so any advice anyone can offer would be greatly appreciated (I've had this working on gutsy, hardy, and intrepid, so I don't think I'm making any stupid mistakes - I hope.)

```

~/NFORCE-Linux-x86-1.0-0310-pkg1$ ./2.6.27-patch
patching file nvsound/main/Makefile.kbuild
patching file nvsound/main/nvmain.c
patching file nvsound/main/nvaioctl.h
patching file nvsound/main/nvalinux.c
Hunk #3 FAILED at 189.
Hunk #4 FAILED at 193.
2 out of 4 hunks FAILED -- saving rejects to file nvsound/main/nvalinux.c.rej
patching file nvsound/main/nvalinux.h
patching file nvsound/main/conftest.sh
patching file nvsound/main/nvavm.h

```
```

ERROR: The NVIDIA kernel module was not created.

```
```

nforce-installer log file '/var/log/nvidia-nforce-installer.log'
creation time: Wed Apr  1 19:00:39 2009

option status:
  license pre-accepted      : false
  expert                    : false
  uninstall                 : false
  driver info               : false
  no precompiled interface  : false
  no ncurses color          : false
  no questions              : false
  silent                    : false
  Installer install prefix  : /usr
  kernel source path        : (not specified)
  net kernel install path   : (not specified)
  audio kernel install path : (not specified)
  proc mount point          : /proc
  ui                        : (not specified)
  tmpdir                    : /tmp

Using: nvidia-installer ncurses user interface
-> Found package NVIDIA audio driver for Linux-x86
-> Found package NVIDIA network driver for Linux-x86
-> Please select packages for installation:
   Selections:
   NVIDIA audio driver for Linux-x86 (1.0-7)
-> Starting install of NVIDIA audio driver for Linux-x86
-> Checking for loaded module nvsound
-> Checking for loaded module nvaudio
-> License accepted.
-> Skipping check for conflicting rpms.
-> /proc/version is Linux version 2.6.28-11-generic (buildd@palmer) (gcc
   version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #37-Ubuntu SMP Mon Mar 23 16:40:23
   UTC 2009
-> No precompiled kernel interface was found to match your kernel; this means
   that the installer will need to compile a new kernel interface.
-> Kernel source path: '/lib/modules/2.6.28-11-generic/build'
-> Kernel output path: '/lib/modules/2.6.28-11-generic/build'
-> Performing cc_version_check with CC="cc".
-> running command /bin/grep "^PATCHLEVEL ="
   /lib/modules/2.6.28-11-generic/build/Makefile | /usr/bin/cut -d " " -f 3
-> Kernel module filename is nvsound.ko
   Cleaning kernel module build directory.
   executing: 'cd ./nvsound/main; make clean'...
   rm -f *.ko *mod.* *.cmd nv*.o *~ core
-> Building kernel module:
   executing: 'cd ./nvsound/main; make module SYSSRC=/lib/modules/2.6.28-11-gen
   eric/build SYSOUT=/lib/modules/2.6.28-11-generic/build'...
   make -C /lib/modules/2.6.28-11-generic/build \
   	KBUILD_SRC=/usr/src/linux-headers-2.6.28-11-generic \
   	KBUILD_EXTMOD="/home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main" -f 
   /usr/src/linux-headers-2.6.28-11-generic/Makefile \
   	modules
   test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
   	echo;								\
   	echo "  ERROR: Kernel configuration is invalid.";		\
   	echo "         include/linux/autoconf.h or include/config/auto.conf are mis
   sing.";	\
   	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it
   .";	\
   	echo;								\
   	/bin/false)
   mkdir -p /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_versio
   ns ; rm -f /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_vers
   ions/*
   make -f /usr/src/linux-headers-2.6.28-11-generic/scripts/Makefile.build obj=
   /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
     cc -Wp,-MD,/home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.nvalin
   ux.o.d  -nostdinc -isystem /usr/lib/gcc/i486-linux-gnu/4.3.3/include -D__KER
   NEL__ -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-he
   aders-2.6.28-11-generic/include -I/usr/src/linux-headers-2.6.28-11-generic/a
   rch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/sr
   c/linux-headers-2.6.28-11-generic/ubuntu/include  -I/home/chris/NFORCE-Linux
   -x86-1.0-0310-pkg1/nvsound/main -Wall -Wundef -Wstrict-prototypes -Wno-trigr
   aphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration 
   -O2 -m32 -msoft-float -mregparm=3 -freg-struct-return -mpreferred-stack-boun
   dary=2 -march=i586 -mtune=generic -Wa,-mtune=generic32 -ffreestanding -pipe 
   -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse
   2 -mno-3dnow -I/usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm
   /mach-default -Iarch/x86/include/asm/mach-default -fno-stack-protector -fno-
   omit-frame-pointer -fno-optimize-sibling-calls -Wdeclaration-after-statement
   -Wno-pointer-sign  -I/home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main
   -Wall -Wimplicit -Wreturn-type -Wswi
   tch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-arith -Wno-multichar 
   -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_REMAP_PFN_RANGE_PRESENT -DNV_C
   HANGE_PAGE_ATTR_PRESENT -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBU
   ILD_STR(nvalinux)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)"  -c -o /home/chri
   s/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.tmp_nvalinux.o /home/chris/NF
   ORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c
   In file included from include/linux/bitops.h:17,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/cpufeature.h:166,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/processor.h:16,
                    from include/linux/prefetch.h:14,
                    from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/nvalinux.c:19:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘set_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:60: w
   arning: pointer of type ‘void *’ used in arithmetic
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h: In f
   unction ‘clear_bit’:
   /usr/src/linux-headers-2.6.28-11-generic/arch/x86/include/asm/bitops.h:97: w
   arning: pointer of type ‘void *’ used in arithmetic
   In file included from include/linux/list.h:6,
                    from include/linux/module.h:9,
                    from /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/nvalinux.c:19:
   include/linux/prefetch.h: In function ‘prefetch_range’:
   include/linux/prefetch.h:57: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/dma-mapping.h:9,
                    from include/linux/dma-mapping.h:57,
                    from include/asm-generic/pci-dma-compat.h:7,
                    from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/pci.h:94,
                    from include/linux/pci.h:1002,
                    from /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/nvalinux.c:29:
   include/linux/scatterlist.h: In function ‘sg_virt’:
   include/linux/scatterlist.h:199: warning: pointer of type ‘void *’ used 
   in arithmetic
   In file included from include/linux/smp_lock.h:5,
                    from include/linux/hardirq.h:5,
                    from include/linux/interrupt.h:12,
                    from /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/nvalinux.c:30:
   include/linux/sched.h: In function ‘object_is_on_stack’:
   include/linux/sched.h:2025: warning: pointer of type ‘void *’ used in ar
   ithmetic
   In file included from /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/nvalinux.c:37:
   include/linux/highmem.h: In function ‘zero_user_segments’:
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:136: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   include/linux/highmem.h:139: warning: pointer of type ‘void *’ used in a
   rithmetic
   In file included from /usr/src/linux-headers-2.6.28-11-generic/arch/x86/incl
   ude/asm/i387.h:15,
                    from /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n/nvalinux.c:47:
   include/linux/regset.h: In function ‘user_regset_copyout’:
   include/linux/regset.h:230: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h:233: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h:237: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h: In function ‘user_regset_copyin’:
   include/linux/regset.h:255: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h:258: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h:262: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h: In function ‘user_regset_copyout_zero’:
   include/linux/regset.h:287: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h:291: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h: In function ‘user_regset_copyin_ignore’:
   include/linux/regset.h:312: warning: pointer of type ‘void *’ used in ar
   ithmetic
   include/linux/regset.h:314: warning: pointer of type ‘void *’ used in ar
   ithmetic
   /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c: In funct
   ion ‘AosFpuSave’:
   /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:189: erro
   r: ‘struct thread_struct’ has no member named ‘i387’
   /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:193: erro
   r: ‘struct thread_struct’ has no member named ‘i387’
   /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:187: erro
   r: invalid lvalue in asm output 0
   /home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalinux.c:191: erro
   r: invalid lvalue in asm output 0
   make[4]: *** [/home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvalin
   ux.o] Error 1
   make[3]: *** [_module_/home/chris/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/mai
   n] Error 2
   make[2]: *** [sub-make] Error 2
-> Error.

```

---

### Post by jocko on 2009-04-02
> **mintochris said:**
> I'm having some trouble on a fresh jaunty install, where the patching fails on nvalinux.c, and the build process then fails. I've included the relevant errors (i think!) so any advice anyone can offer would be greatly appreciated (I've had this working on gutsy, hardy, and intrepid, so I don't think I'm making any stupid mistakes - I hope.)

```

~/NFORCE-Linux-x86-1.0-0310-pkg1$ ./2.6.27-patch
patching file nvsound/main/Makefile.kbuild
patching file nvsound/main/nvmain.c
patching file nvsound/main/nvaioctl.h
patching file nvsound/main/nvalinux.c
Hunk #3 FAILED at 189.
Hunk #4 FAILED at 193.
2 out of 4 hunks FAILED -- saving rejects to file nvsound/main/nvalinux.c.rej
patching file nvsound/main/nvalinux.h
patching file nvsound/main/conftest.sh
patching file nvsound/main/nvavm.h

```
Hmmm... I thought I had fixed that problem a couple of weeks ago. The problem is that the file nvalinux.c contains tabs in stead of normal spaces on lines 185 and 189 (which will be 189 to 193 after another of my patches have added four lines to the file). The patch command seems to have a problem with the tabs, causing it to just skip these lines.

Maybe I will need to find out another way of patching those lines.
In the meantime, there's always the manual method:
1. Run my patch script from the howto (don't run it again if you have already done this):
```
./2.6.27-patch
```(this will fail to change the two problematic lines, but all the other necessary changes will be successful).
2. Edit the nvalinux.c file manually:
```
gedit nvsound/main/nvalinux.c
```Find lines 189 to 193, change them from:
```
                                [COLOR=Red]:"=m"(currenttask->thread.i387.fxsave) );[/COLOR]
        } else {
            __asm__ __volatile__( "fnsave %0\n"
                            "fwait"
                            [COLOR=Red]:"=m"(currenttask->thread.i387.fsave) );[/COLOR]
```To:
```
                                [COLOR=Blue]:"=m"(currenttask->thread.xstate->fxsave) );[/COLOR]
        } else {
            __asm__ __volatile__( "fnsave %0\n"
                            "fwait"
                            [COLOR=Blue]:"=m"(currenttask->thread.xstate->fxsave) );[/COLOR]
```(only change the highlighted text)
Save, exit gedit and run the installer:
```
sudo ./nforce-installer
```

---

### Post by mintochris on 2009-04-02
thanks, that resolved it. Good on you for keeping soundstorm alive :D

---

### Post by jocko on 2009-04-03
And now I found an easier solution (I hope). The new, updated patch scripts in the howto should apply successfully without any need for manual editing...

---

### Post by MadCityGuy on 2009-04-08
> **jocko said:**
> Are you sure you don't have any alsa driver loaded?
Check the output of:
```
lsmod | grep snd_
```
If you get any output an alsa driver is still loaded, which prevents the nvsound driver from working.
If that's the case, make sure you did everything in the first part of step 2 correctly (= blacklist the alsa driver. Check your spelling and remember that linux is case sensitive). Reboot and try again.

Hi, I'm new at this, too. I followed your instructions with Intrepid but don't have sound from speakers attached to my A7N8X Deluxe board (except that funny drum sound at startup). I notice that grepping snd_ I apparently have an alsa driver loaded, but I don't see instructions in step 2 in how to blacklist it (step 2 only seems to blacklist the intel8x0). When I try to run NVMIXER I get the "Nvsound: Unable to open the Mixer" error. I checked and the intel8x0 is not loaded (When I do a "lsmod | grep intel8x0" nothing comes back).

Please tell me how to blacklist the alsa driver.

---

### Post by jocko on 2009-04-08
> **MadCityGuy said:**
> Hi, I'm new at this, too. I followed your instructions with Intrepid but don't have sound from speakers attached to my A7N8X Deluxe board (except that funny drum sound at startup). I notice that grepping snd_ I apparently have an alsa driver loaded, but I don't see instructions in step 2 in how to blacklist it (step 2 only seems to blacklist the intel8x0). When I try to run NVMIXER I get the "Nvsound: Unable to open the Mixer" error. I checked and the intel8x0 is not loaded (When I do a "lsmod | grep intel8x0" nothing comes back).

Please tell me how to blacklist the alsa driver.
The "alsa driver" IS intel8x0. If it is not loaded, no other alsa modules should be loaded when you reboot.
What is your output of:
```
lsmod | grep snd_
```
To manually unload any alsa modules that are loaded, try this:
```
sudo alsa force-unload
sudo modprobe nvsound
```

---

### Post by MadCityGuy on 2009-04-08
> **jocko said:**
> The "alsa driver" IS intel8x0. If it is not loaded, no other alsa modules should be loaded when you reboot.
What is your output of:
```
lsmod | grep snd_
```
To manually unload any alsa modules that are loaded, try this:
```
sudo alsa force-unload
sudo modprobe nvsound
```

Thanks! the sudo also force-unload succesfully unloaded the also modules (they were loaded even though intel8x0 was NOT loaded). I also had a permissions problem - my account didn't have rights to audio.  I think I'm almost there; all I need to do is to figure out codecs.

Thank you very much for your help.

---

### Post by ppurka on 2009-04-30
> **jocko said:**
> Probably some function in the kernel has been renamed or replaced with another one. If we're lucky it's possible to find a workaround or some dirty hack to get it working...

I may look into it if I get bored some weekend, until then I hope someone else have any ideas.

In case someone likes to give it a try:
The last time a kernel upgrade broke the nvsound module (somewhere between 2.6.24 and 2.6.26 or .27), I looked through the kernel changelogs ([kernel.org]("http://kernel.org/")) to find what happened to the function that gave the error in that case. In this case a good start would be to find out what "register_sound_mixer" and "register_sound_dsp" have been replaced with and make the corresponding changes in NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvmain.c (lines 2134 and 2143). After that there may be new similar errors that may be solved in a similar way...
Hi,
were you able to determine the change in 2.6.28? The patches work fine and the compilation runs through fine, but it is the loading of the nvsound module that fails. Same messages essentially:
```
nvsound: Unknown symbol unregister_sound_dsp
nvsound: Unknown symbol unregister_sound_mixer
Symbol init_mm is marked as UNUSED, however this module is using it.
This symbol will go away in the future.
Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting your code for inclusion.
nvsound: Unknown symbol register_sound_mixer
nvsound: Unknown symbol register_sound_dsp

```I looked through the kernel changes for 2.6.28_rc* to 2.6.28 but do not see anything which has changed the register_sound_* functions. However, doing the following does not produce any output. ```
cd /usr/src/linux/arch/x86/include
grep -r register * | grep sound
```
Again these functions are present in /usr/src/linux/sound, so I am completely at a loss on what has changed. :confused:

---

### Post by jocko on 2009-05-03
> **ppurka said:**
> Hi,
were you able to determine the change in 2.6.28? The patches work fine and the compilation runs through fine, but it is the loading of the nvsound module that fails. Same messages essentially:
```
nvsound: Unknown symbol unregister_sound_dsp
nvsound: Unknown symbol unregister_sound_mixer
Symbol init_mm is marked as UNUSED, however this module is using it.
This symbol will go away in the future.
Please evalute if this is the right api to use and if it really is, submit a report the linux kernel mailinglist together with submitting your code for inclusion.
nvsound: Unknown symbol register_sound_mixer
nvsound: Unknown symbol register_sound_dsp

```I looked through the kernel changes for 2.6.28_rc* to 2.6.28 but do not see anything which has changed the register_sound_* functions. However, doing the following does not produce any output. ```
cd /usr/src/linux/arch/x86/include
grep -r register * | grep sound
```Again these functions are present in /usr/src/linux/sound, so I am completely at a loss on what has changed. :confused:
I get no such errors on 2.6.28. It all works fine with my new (4 weeks ago), fixed patch script. The older version of the script was too strict, and ignored a couple of lines in the file main/nvalinux.c that contained tabs instead of spaces. The driver compiled fine even without those changes, but the module failed to load with the errors:```
nvsound: Unknown symbol register_sound_mixer
nvsound: Unknown symbol register_sound_dsp
```
Start from the beginning with fresh files (delete the old NFORCE-Linux-x86-1.0-0310-pkg1 directory and extract the installer again), and make sure you use my new patch files ([from here]("http://ubuntuforums.org/attachment.php?attachmentid=108554&d=1238790712")).

---

### Post by ppurka on 2009-05-05
> **jocko said:**
> I get no such errors on 2.6.28. It all works fine with my new (4 weeks ago), fixed patch script. The older version of the script was too strict, and ignored a couple of lines in the file main/nvalinux.c that contained tabs instead of spaces. The driver compiled fine even without those changes, but the module failed to load with the errors:```
nvsound: Unknown symbol register_sound_mixer
nvsound: Unknown symbol register_sound_dsp
```
Start from the beginning with fresh files (delete the old NFORCE-Linux-x86-1.0-0310-pkg1 directory and extract the installer again), and make sure you use my new patch files ([from here]("http://ubuntuforums.org/attachment.php?attachmentid=108554&d=1238790712")).That is wierd. I just did a diff between your link and the tar.gz file I download a couple of days ago from the first post in this thread. There is no difference.

I had a quick look at the 2.6.27.patch file. I noticed that you are using ```
patch -bl
```to patch the files. This means that it will ignore all whitespace problems. To try it out, I replaced that with ```
patch -b --dry-run
``` and sure enough the patch failed exactly as described in an [earlier post #288]("http://ubuntuforums.org/showpost.php?p=6998637&postcount=288") of yours!

I think you uploaded the old patch files :P If that is true, then I am saved. I will try the solution you provided in post #288 and hopefully the module will load successfully :D

**EDIT:** Unfortunately, the above didn't work. :(
Could this be because I have linux-headers from 2.6.27 instead of 2.6.28

**EDIT 2:** I tried the same after installing linux-headers 2.6.28. It still gives the same error. I guess I will stay with 2.6.27. Thank you for all your help and the patches,- it works in 2.6.27 absolutely fine :)
I forgot to mention earlier: this is on a gentoo system. Maybe the ubuntu kernels have some additional patches which help you somewhere. So, I guess I shouldn't waste your time any more. :/

---

### Post by jocko on 2009-05-06
> **ppurka said:**
> That is wierd. I just did a diff between your link and the tar.gz file I download a couple of days ago from the first post in this thread. There is no difference.

I had a quick look at the 2.6.27.patch file. I noticed that you are using ```
patch -bl
```to patch the files. This means that it will ignore all whitespace problems. To try it out, I replaced that with ```
patch -b --dry-run
``` and sure enough the patch failed exactly as described in an [earlier post #288]("http://ubuntuforums.org/showpost.php?p=6998637&postcount=288") of yours!

I think you uploaded the old patch files :P If that is true, then I am saved. I will try the solution you provided in post #288 and hopefully the module will load successfully :D

**EDIT:** Unfortunately, the above didn't work. :(
Could this be because I have linux-headers from 2.6.27 instead of 2.6.28

**EDIT 2:** I tried the same after installing linux-headers 2.6.28. It still gives the same error. I guess I will stay with 2.6.27. Thank you for all your help and the patches,- it works in 2.6.27 absolutely fine :)
I forgot to mention earlier: this is on a gentoo system. Maybe the ubuntu kernels have some additional patches which help you somewhere. So, I guess I shouldn't waste your time any more. :/
The patch script with "patch -bl" is the new one (that I uploaded 4 or 5 weeks ago, the old one actually failed on 2.6.27 as well, I just did not notice it as I installed with the version that I had patched manually when I made the fix for the 2.6.27 kernel).
You need to have the exact same version of kernel headers as your running kernel, otherwise it will never compile. If you compile the driver against the 2.6.27 kernel it will only work when you run a 2.6.27 kernel.

---

### Post by ppurka on 2009-05-07
> **jocko said:**
> The patch script with "patch -bl" is the new one (that I uploaded 4 or 5 weeks ago, the old one actually failed on 2.6.27 as well, I just did not notice it as I installed with the version that I had patched manually when I made the fix for the 2.6.27 kernel).
You need to have the exact same version of kernel headers as your running kernel, otherwise it will never compile. If you compile the driver against the 2.6.27 kernel it will only work when you run a 2.6.27 kernel.Actually, the following is what I have tried:
linux-headers-2.6.27  + linux-2.6.27: it compiles and loads
linux-headers-2.6.27  + linux-2.6.28: it compiles but fails to load
linux-headers-2.6.28  + linux-2.6.28: it compiles but fails to load

Moreover, in gentoo you always need some kernel source file to be present in /usr/src (because most of the time you will be compiling your own kernel) and the log of the nvsound compilation have -I<include directory> which points to the headers in /usr/src/linux-<version>. For example, this is one of the compilation lines```
  cc -Wp,-MD,/tmp/selfgz5701/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/.nv
   sound.mod.o.d  -nostdinc -isystem /usr/lib/gcc/i686-pc-linux-gnu/4.3.2/inclu
   de -D__KERNEL__ -Iinclude -Iinclude2 -I/usr/src/linux-2.6.28-gentoo-r5/inclu
   de -I/usr/src/linux-2.6.28-gentoo-r5/arch/x86/include -include include/linux
   /autoconf.h  -I/tmp/selfgz5701/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -
   Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-co
   mmon -Werror-implicit-function-declaration -Os -m32 -msoft-float -mregparm=3
   -freg-struct-return -mpreferred-stack-boundary=2 -march=athlon -Wa,-mtune=ge
   neric32 -ffreestanding -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pip
   e -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-s
   se2 -mno-3dnow -I/usr/src/linux-2.6.28-gentoo-r5/arch/x86/include/asm/mach-d
   efault -Iarch/x86/include/asm/mach-default -fno-stack-protector -fomit-frame
   -pointer -Wdeclaration-after-statement -Wno-pointer-sign -fwrapv  -I/tmp/sel
   fgz5701/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main -Wall -Wimplicit -Wretur
   n-type -Wswitch -Wformat -Wchar-subscripts -Wparentheses -Wpointer-ar
   ith -Wno-multichar -Werror -O -MD -Wno-cast-qual -Wno-error -DNV_REMAP_PFN_R
   ANGE_PRESENT -DNV_CHANGE_PAGE_ATTR_PRESENT  -D"KBUILD_STR(s)=#s" -D"KBUILD_B
   ASENAME=KBUILD_STR(nvsound.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(nvsound)"  -D
   MODULE -c -o /tmp/selfgz5701/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvs
   ound.mod.o /tmp/selfgz5701/NFORCE-Linux-x86-1.0-0310-pkg1/nvsound/main/nvsou
   nd.mod.c

``` In my 5 yrs of running gentoo, I haven't found any problems with linux-headers being a different version from the actual kernel I am running. Anyway, since I am on a different distribution, I don't want to bother you too much :P

---

### Post by MadCityGuy on 2009-05-07
Delete question - I didn't notice that you've updated the instructions to include Jaunty.

---

### Post by pipik on 2009-05-09
> **ppurka said:**
> 
......
**EDIT:** Unfortunately, the above didn't work. :(
Could this be because I have linux-headers from 2.6.27 instead of 2.6.28

**EDIT 2:** I tried the same after installing linux-headers 2.6.28. It still gives the same error. I guess I will stay with 2.6.27. Thank you for all your help and the patches,- it works in 2.6.27 absolutely fine :)
I forgot to mention earlier: this is on a gentoo system. Maybe the ubuntu kernels have some additional patches which help you somewhere. So, I guess I shouldn't waste your time any more. :/
......


Well I got similar problems with 2.6.28 & 2.6.29, I tried to solve them but I fail :/

With both versions I got it worked without the error:

```
nvsound: Unknown symbol register_sound_mixer
nvsound: Unknown symbol register_sound_dsp
```

but the system freezes when the nvsound module is loaded :/

What I tried (if I dont remember bad :) ):
**2.6.28**: replace the new linux-2.6.28/sound/sound_core.c for the oldone (2.6.27)

**2.6.29**: Patch linux-2.6.29/arch/x86/kernel/init_task.c and add 
```
EXPORT_UNUSED_SYMBOL(init_mm); /* will be removed in 2.6.26 */
```
And patch other files related to this one (.h) that I dont remember in this moment.

That was my "fast attempts" :) 'cause I havent enough free time to try to find a solution :(

PS: Seems that the ubuntu version of the 2.6.28 kernel works (I dont probe it). Download the sources package and try it ;)

---

### Post by jocko on 2009-05-11
> **pipik said:**
> ]but the system freezes when the nvsound module is loaded :/

I hope you are not trying to load nvsound with pulseaudio. That will cause a complete system freeze.

---

### Post by gilson585 on 2009-05-18
many thanks for the how-to
man i spent a long time trying to figure out what i did wrong at first, may i suggest changing the line "Running "gstreamer-properties" and "gnome-sound-properties" from a terminal and selecting oss in all menus will take care of many applications." to something more noticeable. maybe like
Run the following from a terminal and select oss in all menus. This will take care of many applications.
  ```
gstreamer-properties
gnome-sound-properties
```

---

### Post by jocko on 2009-06-12
> **gilson585 said:**
> many thanks for the how-to
man i spent a long time trying to figure out what i did wrong at first, may i suggest changing the line "Running "gstreamer-properties" and "gnome-sound-properties" from a terminal and selecting oss in all menus will take care of many applications." to something more noticeable. maybe like
Run the following from a terminal and select oss in all menus. This will take care of many applications.
  ```
gstreamer-properties
gnome-sound-properties
```

Done that + added patches to fix breakage with kernel 2.6.30...

---

### Post by eriktenburen on 2009-06-12
Hey jocko!

Still using soundtorm here! bt i know have kernel 2.6.28 but it seems there is no patch for it...? Do i miss something?

Help appriciated thanks!

---

### Post by jocko on 2009-06-13
> **eriktenburen said:**
> Hey jocko!

Still using soundtorm here! bt i know have kernel 2.6.28 but it seems there is no patch for it...? Do i miss something?

Help appriciated thanks!

The patch for 2.6.28 is named "2.6.27-patch", because it works for both .27 and .28.
> **jocko said:**
> [COLOR=Blue]**c) For kernel 2.6.27 **[/COLOR][COLOR=Blue]**(Intrepid)**[/COLOR][COLOR=Blue]** or 2.6.28 (Jaunty):**[/COLOR]
```
./2.6.27-patch
sudo ./nforce-installer
```

---

### Post by eriktenburen on 2009-06-13
Thanks Jocko!

Did that yesterday but it wasn't working. But I got it up and running again.

---

### Post by ppurka on 2009-06-23
> **jocko said:**
> Done that + added patches to fix breakage with kernel 2.6.30...Hey Jocko! Many many thanks for the patches! I have been able to figure out finally why the nvsound module wasn't loading for me with the newer kernels. It seems all the functions *register_sound_** have been put under a ```
#ifdef CONFIG_SOUND_OSS_CORE
...
#endif
```statement. I hadn't noticed this earlier. In 2.6.30, I just enabled the Sound and then enabled OSS as modules (I had never enabled OSS earlier in <=2.6.27). This enabled the functions register_sound_* to be visible to nvsound and it promptly loaded :D
Now, thanks to your patches, I am enjoying nvsound in 2.6.30 :popcorn:

---

### Post by osxuser on 2009-07-10
Wow, I haven't attempted to use Linux in quite some time and this was really helpful.  Thanks!

---

### Post by osxuser on 2009-07-10
When I try to play music with Rhythmbox I get this garbled mess.  What could be causing that?

---

### Post by PhantomPholly on 2009-08-01
Deleted - fixed in another thread.

---

### Post by PhantomPholly on 2009-08-02
One small note - after following these directions on a clean install of Ubuntu 9.04, I had to go to "System" / "Administration" / Users and Groups, then select my user and select "Unlock" in order to grant privileges to "Use Audio Devices" for that user.  Until I did that it would not show any sound devices in "System" / "Preferences" / "Sound."

Edit:  reading back in this thread I see others had this issue, too.  Jocko, would you please add this note to the main instructions for those who have this issue after installing (and are as slow as I am)?

---

### Post by jocko on 2009-08-02
> **PhantomPholly said:**
> One small note - after following these directions on a clean install of Ubuntu 9.04, I had to go to "System" / "Administration" / Users and Groups, then select my user and select "Unlock" in order to grant privileges to "Use Audio Devices" for that user.  Until I did that it would not show any sound devices in "System" / "Preferences" / "Sound."

Edit:  reading back in this thread I see others had this issue, too.  Jocko, would you please add this note to the main instructions for those who have this issue after installing (and are as slow as I am)?
I've read your other post, but can't see why you would have that problem. I've never had to add my user to the audio group to get it working, so unless someone else confirms that the problem exists, I won't add anything more to the howto.
Those errors you see when you run gstreamer-properties are perfectly normal, and does not indicate any problem. They are caused by the fact that some gstreamer plugins are not normally installed in ubuntu, as ubuntu doesn't use arts, esd, glimage, sdl *etc*.

---

### Post by PhantomPholly on 2009-08-02
While I'm new to Ubuntu, I'm not new to posting - as I inferred in my post I noted at least two other posters in the last 8 pages (both this year) of this thread who said they had exactly the same experience before I suggested it.  Since I'm new you'll probably suggest I should go back through the posts yet again and post the cross links, but unfortunately I don't have the time to do that.

Please don't think me ungrateful - your post was tremendously helpful!

:D

---

### Post by jocko on 2009-08-03
> **PhantomPholly said:**
> While I'm new to Ubuntu, I'm not new to posting - as I inferred in my post I noted at least two other posters in the last 8 pages (both this year) of this thread who said they had exactly the same experience before I suggested it.  Since I'm new you'll probably suggest I should go back through the posts yet again and post the cross links, but unfortunately I don't have the time to do that.

Please don't think me ungrateful - your post was tremendously helpful!

:D
I looked through the last 10 pages, and found a couple of posts that seems to indicate that there may be permission problems that prevents some people from accessing the sound card. Thank you for pointing this out, I'll add a step to the howto.

---

### Post by ppurka on 2009-09-27
On recent kernels 2.6.30 and 2.6.31 I had been getting errors like this:```
irq event 21: bogus return value c0460000
Pid: 0, comm: swapper Tainted: P        W  2.6.30-gentoo-r1 #3
Call Trace:
 [<c013953e>] ? __report_bad_irq+0x2b/0x69
 [<c0139663>] ? note_interrupt+0xe7/0x13c
 [<c0139bb3>] ? handle_fasteoi_irq+0x85/0xba
 [<c010406f>] ? handle_irq+0x17/0x1c
 [<c0103d77>] ? do_IRQ+0x2b/0x63
 [<c0102e69>] ? common_interrupt+0x29/0x30
 [<c01071a4>] ? default_idle+0x25/0x38
 [<c0101ba1>] ? cpu_idle+0x23/0x52
 [<c04628cd>] ? start_kernel+0x253/0x256
handlers:
[<c0294fc6>] (usb_hcd_irq+0x0/0x58)
[<e2cb2e42>] (Nvapu_interrupt+0x0/0x6a [nvsound])
Disabling IRQ #21
```After this happens, the sound would have a lot of static. 

To fix this, I reverted the patch to nvsound/main/nvhw.h and instead changed line 127 of nvsound/main/nvhw.h to 
```
#ifndef IRQ_RETVAL
```
So, the new patch for nvhw.h is:```
--- nvhw.h.orig	2005-10-21 21:59:44.000000000 -0400
+++ nvhw.h	2009-09-26 19:26:45.000000000 -0400
@@ -124,7 +124,7 @@
 #define PLAY_STREAM  1
 #define REC_STREAM   2
 
-#ifndef IRQ_HANDLED
+#ifndef IRQ_RETVAL
 typedef void irqreturn_t;
 #define IRQ_HANDLED
 #define IRQ_NONE
```
I have tested this with 2.6.31 but I think it should work with 2.6.30 too. This seems to be working fine for about a day now. I will report back if there is some other problem.

---

### Post by jocko on 2009-09-28
> **ppurka said:**
> On recent kernels 2.6.30 and 2.6.31 I had been getting errors like this:```
irq event 21: bogus return value c0460000
Pid: 0, comm: swapper Tainted: P        W  2.6.30-gentoo-r1 #3
Call Trace:
 [<c013953e>] ? __report_bad_irq+0x2b/0x69
 [<c0139663>] ? note_interrupt+0xe7/0x13c
 [<c0139bb3>] ? handle_fasteoi_irq+0x85/0xba
 [<c010406f>] ? handle_irq+0x17/0x1c
 [<c0103d77>] ? do_IRQ+0x2b/0x63
 [<c0102e69>] ? common_interrupt+0x29/0x30
 [<c01071a4>] ? default_idle+0x25/0x38
 [<c0101ba1>] ? cpu_idle+0x23/0x52
 [<c04628cd>] ? start_kernel+0x253/0x256
handlers:
[<c0294fc6>] (usb_hcd_irq+0x0/0x58)
[<e2cb2e42>] (Nvapu_interrupt+0x0/0x6a [nvsound])
Disabling IRQ #21
```After this happens, the sound would have a lot of static. 

To fix this, I reverted the patch to nvsound/main/nvhw.h and instead changed line 127 of nvsound/main/nvhw.h to 
```
#ifndef IRQ_RETVAL
```So, the new patch for nvhw.h is:```
--- nvhw.h.orig    2005-10-21 21:59:44.000000000 -0400
+++ nvhw.h    2009-09-26 19:26:45.000000000 -0400
@@ -124,7 +124,7 @@
 #define PLAY_STREAM  1
 #define REC_STREAM   2
 
-#ifndef IRQ_HANDLED
+#ifndef IRQ_RETVAL
 typedef void irqreturn_t;
 #define IRQ_HANDLED
 #define IRQ_NONE
```I have tested this with 2.6.31 but I think it should work with 2.6.30 too. This seems to be working fine for about a day now. I will report back if there is some other problem.
Thanks!
I'll try it out and update the patches in my howto if it works. Last time I tried it on 2.6.30 my sound was fine for a few minutes but became more and more choppy with time (and lots of dmesg output, probably similar to yours when that happened). I was just kind of waiting for someone else to notice and have any idea how to fix it...
If this works I can finally get everything I want in an up-to-date distro again (after gutsy the quality of the available ati graphics drivers were so poor that I chose not to upgrade, and now I thought I was finally going to be forced to give up on my excellent sound quality if I wanted to leave gutsy and upgrade to karmic...).

---

### Post by ppurka on 2009-09-30
> **jocko said:**
> Thanks!
I'll try it out and update the patches in my howto if it works. Last time I tried it on 2.6.30 my sound was fine for a few minutes but became more and more choppy with time (and lots of dmesg output, probably similar to yours when that happened). I was just kind of waiting for someone else to notice and have any idea how to fix it...
If this works I can finally get everything I want in an up-to-date distro again (after gutsy the quality of the available ati graphics drivers were so poor that I chose not to upgrade, and now I thought I was finally going to be forced to give up on my excellent sound quality if I wanted to leave gutsy and upgrade to karmic...).

The other kind of dmesg errors that you get is like this:```
include/asm/dma-mapping.h:132 AosMemoryFreePhysical+0xf5/0x144 [nvsound]()
Hardware name: A7N8X-E
Modules linked in: nvsound(P) nvidia(P) sg parport_pc parport nvidia_agp soundcore agpgart [last unloaded: nvsound]
Pid: 10817, comm: firefox Tainted: P        W  2.6.31-gentoo #1
Call Trace:
 [<c101c3a2>] ? warn_slowpath_common+0x5e/0x8a
 [<c101c3d8>] ? warn_slowpath_null+0xa/0xc
 [<e26a554e>] ? AosMemoryFreePhysical+0xf5/0x144 [nvsound]
 [<e2652050>] ? _ZN8CNvVoiceD0Ev+0x160/0x168 [nvsound]
 [<e26023ec>] ? _ZdlPv+0x38/0x50 [nvsound]
 [<e2642940>] ? _ZN9CNvStreamD0Ev+0x1c0/0x1c8 [nvsound]
 [<e26465f1>] ? _ZN9CNvStream12FinalReleaseEv+0x57/0x68 [nvsound]
 [<e2602c20>] ? _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<e269accb>] ? _ZN9CNvStream7ReleaseEv+0x17/0x1c [nvsound]
 [<e268e0ad>] ? _ZN13CApuStreamPciD0Ev+0x47/0xd6 [nvsound]
 [<e2602c20>] ? _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<e269be53>] ? _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
 [<e2688098>] ? Nv_FreeNewstream+0x2c/0x38 [nvsound]
 [<e26a6d5e>] ? Nvfree_wave_device+0x55/0x123 [nvsound]
 [<e26a6f21>] ? Nvaudio_release+0xf5/0x106 [nvsound]
 [<c1065fed>] ? __fput+0xc0/0x17a
 [<c1063672>] ? filp_close+0x4e/0x54
 [<c10636e5>] ? sys_close+0x6d/0xb7
 [<c10027f4>] ? sysenter_do_call+0x12/0x26
---[ end trace 94f160b26cd3b606 ]---

```It is different from the one I gave in the previous post. This is just a warning and it doesn't do anything pro-actively. I tried to find out what is giving such warnings and it seems this has to do with some assembly code in the nvsound sources. I am not much of a programmer, so fixing this is completely beyond my reach. 

The patch I gave in my earlier post has been working pretty fine till now :P
Without the patch above, you can run the following in the terminal to detect when your sound gets corrupted:```
while ! dmesg | grep -w '21'; do
sleep 10
done;
```Essentially, what is happening is that IRQ_HANDLED and IRQ_NONE are defined as enums in the newer kernels (see **/usr/src/linux/include/linux/irqreturn.h**). In the nvsound sources, these are redefined into some weird hexadecimal numbers. If you read the kernel sources, you will come across this comment in **/usr/src/linux/kernel/irq/spurious.c**```
/*
 * If 99,900 of the previous 100,000 interrupts have not been handled
 * then assume that the IRQ is stuck in some manner. Drop a diagnostic
 * and try to turn the IRQ off.
 *
 * (The other 100-of-100,000 interrupts may have been a correctly
 *  functioning device sharing an IRQ with the failing one)
 *
 * Called under desc->lock
 */

```So, the kernel waits till it has received more than 99,900 bogus IRQ_HANDLED or IRQ_NONE, and then it disables the IRQ. That is when the sound gets "choppy" or full of "static". This is what my patch tries to fix.

---

### Post by jocko on 2009-10-02
> **ppurka said:**
> The other kind of dmesg errors that you get is like this:```
include/asm/dma-mapping.h:132 AosMemoryFreePhysical+0xf5/0x144 [nvsound]()
Hardware name: A7N8X-E
Modules linked in: nvsound(P) nvidia(P) sg parport_pc parport nvidia_agp soundcore agpgart [last unloaded: nvsound]
Pid: 10817, comm: firefox Tainted: P        W  2.6.31-gentoo #1
Call Trace:
 [<c101c3a2>] ? warn_slowpath_common+0x5e/0x8a
 [<c101c3d8>] ? warn_slowpath_null+0xa/0xc
 [<e26a554e>] ? AosMemoryFreePhysical+0xf5/0x144 [nvsound]
 [<e2652050>] ? _ZN8CNvVoiceD0Ev+0x160/0x168 [nvsound]
 [<e26023ec>] ? _ZdlPv+0x38/0x50 [nvsound]
 [<e2642940>] ? _ZN9CNvStreamD0Ev+0x1c0/0x1c8 [nvsound]
 [<e26465f1>] ? _ZN9CNvStream12FinalReleaseEv+0x57/0x68 [nvsound]
 [<e2602c20>] ? _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<e269accb>] ? _ZN9CNvStream7ReleaseEv+0x17/0x1c [nvsound]
 [<e268e0ad>] ? _ZN13CApuStreamPciD0Ev+0x47/0xd6 [nvsound]
 [<e2602c20>] ? _ZN10NvaUnknown20NondelegatingReleaseEv+0x36/0x48 [nvsound]
 [<e269be53>] ? _ZN13CApuStreamPci7ReleaseEv+0x17/0x1c [nvsound]
 [<e2688098>] ? Nv_FreeNewstream+0x2c/0x38 [nvsound]
 [<e26a6d5e>] ? Nvfree_wave_device+0x55/0x123 [nvsound]
 [<e26a6f21>] ? Nvaudio_release+0xf5/0x106 [nvsound]
 [<c1065fed>] ? __fput+0xc0/0x17a
 [<c1063672>] ? filp_close+0x4e/0x54
 [<c10636e5>] ? sys_close+0x6d/0xb7
 [<c10027f4>] ? sysenter_do_call+0x12/0x26
---[ end trace 94f160b26cd3b606 ]---

```It is different from the one I gave in the previous post. This is just a warning and it doesn't do anything pro-actively. I tried to find out what is giving such warnings and it seems this has to do with some assembly code in the nvsound sources. I am not much of a programmer, so fixing this is completely beyond my reach. 

The patch I gave in my earlier post has been working pretty fine till now :P
Without the patch above, you can run the following in the terminal to detect when your sound gets corrupted:```
while ! dmesg | grep -w '21'; do
sleep 10
done;
```Essentially, what is happening is that IRQ_HANDLED and IRQ_NONE are defined as enums in the newer kernels (see **/usr/src/linux/include/linux/irqreturn.h**). In the nvsound sources, these are redefined into some weird hexadecimal numbers. If you read the kernel sources, you will come across this comment in **/usr/src/linux/kernel/irq/spurious.c**```
/*
 * If 99,900 of the previous 100,000 interrupts have not been handled
 * then assume that the IRQ is stuck in some manner. Drop a diagnostic
 * and try to turn the IRQ off.
 *
 * (The other 100-of-100,000 interrupts may have been a correctly
 *  functioning device sharing an IRQ with the failing one)
 *
 * Called under desc->lock
 */

```So, the kernel waits till it has received more than 99,900 bogus IRQ_HANDLED or IRQ_NONE, and then it disables the IRQ. That is when the sound gets "choppy" or full of "static". This is what my patch tries to fix.
Your patch seems to work perfectly (better than my ugly hack which is probably what caused the stuttering/static in the first place...).
I have no idea what causes the remaining dmesg output, but it seems to have been around for a while without causing any problems that I know of (there are some posts in this thread where the same happened in kernel 2.6.24). But it would be nice if someone had any idea how to fix it.

---

### Post by Spindoctor on 2010-01-05
Hi!

First I have to say, this is a great instruction!
For years I had the problem, that my computer produced a silent humming noise driving me insane. Now this noise is gone - that makes me happy.

Still, I have a problem that makes me unhappy: not only the humming noise is gone, but the whole sound :-)

I'm using Ubuntu 9.10. I think my problem is somewhere in step 6.
When I type "gstreamer-properties in my console, I can click on the "test"-button. I hear a loud noise then.
Typing "gnome-sound-properties" however gives me "command not found". Well, I think this command was replaced by "gnome-control-center", right?

When I go to the audio settings by clicking right on the speaker symbol, the tab "Hardware" is empty.

What can I do?

Thank you!

Spin

**[edit]**
... Finally got it running, using this tutorial:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Sorry for bothering, Jocko and thanks for this great guide!

---

### Post by jocko on 2010-01-08
> **Spindoctor said:**
> Hi!

First I have to say, this is a great instruction!
For years I had the problem, that my computer produced a silent humming noise driving me insane. Now this noise is gone - that makes me happy.

Still, I have a problem that makes me unhappy: not only the humming noise is gone, but the whole sound :-)

I'm using Ubuntu 9.10. I think my problem is somewhere in step 6.
When I type "gstreamer-properties in my console, I can click on the "test"-button. I hear a loud noise then.
Typing "gnome-sound-properties" however gives me "command not found". Well, I think this command was replaced by "gnome-control-center", right?

When I go to the audio settings by clicking right on the speaker symbol, the tab "Hardware" is empty.

What can I do?

Thank you!

Spin

**[edit]**
... Finally got it running, using this tutorial:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Sorry for bothering, Jocko and thanks for this great guide!

The reason gnome-volume-control does not detect any sound card when you use the nvsound driver is that pulseaudio does not work with nvsound, so all applications have to be set to use oss instead (but since gnome now-days is hard-coded to use pulseaudio, there is no way to get system sounds).

I actually don't use nvsound anymore. I kept gutsy with working pulseaudio and nvsound until karmic was released, and now I'm actually happy with the quality of the sound with the alsa driver and pulseaudio. I'm missing the real-time re-encoding to dolby digital, but I can live without it as long as the sound is clear and smooth...
So I'm not sure if I will keep trying to find ways to get this old driver working in any more kernel releases...

But, out of curiosity and in case it will help someone else: When you say you solved it by following the OpenSound guide, did you follow the whole guide and installed OSSv4 (which means you don't use the nvsound driver or the soundstorm chipset), or did you just follow part of the guide without installing OSSv4 (which means you still use soundstorm and nvsound)?

---

### Post by Spindoctor on 2010-01-08
I want to use the Nvidia-Driver as for some strange reason my speakers make a silent but hearable buzzing noise (but only in 5.1 mode) all the time, when my computer is turned on. This was driving me insane. When I had Windows installed before, this sound stopped after booting to Windows.

> **jocko said:**
> But, out of curiosity and in case it will help someone else: When you say you solved it by following the OpenSound guide, did you follow the whole guide and installed OSSv4 (which means you don't use the nvsound driver or the soundstorm chipset), or did you just follow part of the guide without installing OSSv4 (which means you still use soundstorm and nvsound)?

Oh, I also installed OSSv4. I didn't understand that I was replacing nvsound with that(it was really late yesterday). :(

But, as far as I remember, I think it also worked just before I installed OSSv4.

Hmm, in my opinion the buzzing noise got even more silent and less disturbing using OSSv4, but turning up the volume (on my speakers) I realize that it is still there.

I'd like to give nvsound a try... how can I replace the "native" OSSv4-driver with nvsound?


Thank you once more!

Spin

---

### Post by jocko on 2010-01-08
> **Spindoctor said:**
> I want to use the Nvidia-Driver as for some strange reason my speakers make a silent but hearable buzzing noise (but only in 5.1 mode) all the time, when my computer is turned on. This was driving me insane. When I had Windows installed before, this sound stopped after booting to Windows.



Oh, I also installed OSSv4. I didn't understand that I was replacing nvsound with that(it was really late yesterday). :(

But, as far as I remember, I think it also worked just before I installed OSSv4.

Hmm, in my opinion the buzzing noise got even more silent and less disturbing using OSSv4, but turning up the volume (on my speakers) I realize that it is still there.

I'd like to give nvsound a try... how can I replace the "native" OSSv4-driver with nvsound?


Thank you once more!

Spin
You can't replace the OSSv4 driver with nvsound. Nvsound was written for OSSv3 (which is still in the linux kernel) and nvidia quit developing it long before OSSv4 was released and returned to open source (and anyway, if they would have continued developing it they would probably have switched it to alsa instead, as that's what was being used at the time).
How do you connect your sound? Digital output through s/pdif with rca cable? Optical s/pdif? Analog output? The only thing I can think of which can cause the noise you describe is electrical interference from some other component in the computer, but I think that should only affect analog output...

---

### Post by Spindoctor on 2010-01-08
> **jocko said:**
> You can't replace the OSSv4 driver with nvsound. Nvsound was written for OSSv3 (which is still in the linux kernel) and nvidia quit developing it long before OSSv4 was released and returned to open source (and anyway, if they would have continued developing it they would probably have switched it to alsa instead, as that's what was being used at the time).
Okay, in this case I would have to try to uninstall the OSS4-packages, I've installed following the guide, right?
> How do you connect your sound? Digital output through s/pdif with rca cable? Optical s/pdif? Analog output? The only thing I can think of which can cause the noise you describe is electrical interference from some other component in the computer, but I think that should only affect analog output...
I connect my speakers with Analog output. My amplifier only has analog input (new amplifier would be more expansive than a new 5.1 soundcard ;-) )
I'm not sure if the noise is really comming from electrical interferences as it is
[LIST=1]
[*]not there in Windows
[*]not there if I play an (empty) sound file
[*]not there when i install nvsound (although Gnome had problems with nvsound as discribed)
[*](at least with OSSv4 - I can't tell for ALSA at the moment) not there when the computer is "doing something" - for example the noise stops while im scrolling websites
[/LIST]

I'm not an expert, but I have two approaches for my problem. One was to install the nvidia driver (but now I'm not sure if this is advantegous). The second would be to have a process running that keeps the sound chip "initialised" all the time (but I don't know how to do that).

Thank you once more.

---

### Post by ppurka on 2010-01-10
I had to revert to alsa a few days back. FYI, I am using gentoo. 

I updated the whole system recently and the nvsound drivers had been acting up. Really badly. Basically, the module needed to be modprobe'd at some specific time (usually as early as possible) on boot, otherwise the kernel would hang (SysRq wouldn't work). I have tried many different kernels from 2.6.30 - 2.6.32, and it used to modprobe successfully only with 2.6.32-zen kernel.  On top of that it somehow affected DMA on hard disk. I was getting anywhere between 8MBps to 40MBps speed on running "hdparm -t /dev/sda" depending on whether some sound was being played or not (lower when sound was being played).

It appears that the nvsound drivers have finally :( become incompatible with the latest linux system. I don't know anything about the inner workings of the kernel or userspace apps to even attempt to fix it.

---

### Post by raphen on 2010-01-14
> **jocko said:**
> 
To apply the patches, just follow the relevant steps (3 and 4) of the main howto, but apply the correct patches and install like this [instead of step 4 -II a) or b)]:
```
./2.6.26-patch
sudo ./nforce-installer
```

where are these steps?

---

### Post by jocko on 2010-01-16
> **raphen said:**
> where are these steps?
Just follow the howto (first post in this thread). The post you quoted was only relevant for a couple of days 1.5 years ago, until I updated the actual howto...

---

### Post by jocko on 2010-03-05
Sadly, my old desktop decided to become old and demented (severe instability, random crashes, freezes, segfaults and data losses, probably caused by a couple of bulging and visibly leaking capacitors on the motherboard), so I've decided to let it retire after long and faithful service.
This means there is no longer any real reason for me to continue maintaining this thread, except for the occasional fun of solving a problem that is in no way related to my day job (basic research in evolution and bacterial genetics).

If anyone else wants to take up the torch and continue providing patches for the nvsound driver for future kernel releases, you are very welcome to use, modify and distribute this thread and my patches in any way you like.

---

### Post by irvotheturbo on 2010-03-06
Thanks a lot for your work jocko, has worked perfectly in the past and still does! :)
Most of us will probably get an upgrade too - I know I will this year!

---

### Post by andree_b on 2010-05-19
Yeah thanks Jocko for this thread.

Some update wrt  ubuntu 10.04:
Stills works with the 2.6.30 patch, but i have to use "noirqdebug" kernel parameter since there seem to be some quirks with irq-handling which make the kernel disable the irq for the apu after some time --> choppy sound. With "noirqdebug" the irq doesnt get disabled and might cause some other problems - but for me it foxes the sound...  

May be someone finds this useful:
To use soundstorms hw-ac3 encoding for 6 channel aac material with mplayer use the following parameters: 
mplayer -channels 6 -af resample=40000,channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3 filename.mkv

The "channels=6:6:0:0:1:1:2:4:3:5:4:2:5:3" part will order the channels to their correct positions
"resample=40000" will resample the sound to 40k - you might not need it but on my system the sound gets choppy if i use higher sample rates like the default 48k... dont know really why.

(I am using just digital connection to my amplifier - but the channel reordering is probably needed for analog output too)

---

### Post by zoso75 on 2010-10-12
Thank you jocko for your good job ...
I'm a new linux user but unfortunately  I' m running Ubuntu 10.04.1 LTS (Linux Version 2.6.32-25-generic) so your good guide need a little update ... The steps are clear, it's all corrects (including the exceptions like "if you get this error do this etc...", great!!!) but probably some stuffs are missing :( ...
I have the 5. 1 Dolby digital led turned on on my apmplifier, I can hear the sound test by "gstreamer-properties" but no card is detected in the Hardware Audio Settings ... So any ideas ???
I have A7N8X-E Deluxe ...
I would appreciate any help you can give me

---

### Post by jocko on 2010-10-14
> **zoso75 said:**
> Thank you jocko for your good job ...
I'm a new linux user but unfortunately  I' m running Ubuntu 10.04.1 LTS (Linux Version 2.6.32-25-generic) so your good guide need a little update ... The steps are clear, it's all corrects (including the exceptions like "if you get this error do this etc...", great!!!) but probably some stuffs are missing :( ...
I have the 5. 1 Dolby digital led turned on on my apmplifier, I can hear the sound test by "gstreamer-properties" but no card is detected in the Hardware Audio Settings ... So any ideas ???
I have A7N8X-E Deluxe ...
I would appreciate any help you can give me

Sorry, my old computer is now dead, so there is no way I can test it... but gnome's audio hardware setting only apply to pulseaudio+alsa.
The instructions in this howto only works with oss (old oss, not the new oss4), so those settings will not help you in any way. You have to set every program to use oss instead of pulseaudio or alsa (and don't even try to force pulseaudio to start after you have followed this guide. It will cause a complete system freeze.

---

### Post by The Eight-Bit Link on 2011-06-18
Do you think you could make one last patch or give a suggestion for the new kernel? I keep getting an error that it can't build the module.
I would be grateful if you were to help, I can't afford a new computer.

---

### Post by jocko on 2011-06-20
> **The Eight-Bit Link said:**
> Do you think you could make one last patch or give a suggestion for the new kernel? I keep getting an error that it can't build the module.
I would be grateful if you were to help, I can't afford a new computer.
Sorry, I don't have the hardware to try it on, so it would be very hard for me to get anything working. If you post the error you get, maybe someone else can help you...

---

