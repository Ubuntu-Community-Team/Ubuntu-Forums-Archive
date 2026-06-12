---
title: "Odd errors following fglrx install. Cannot remove."
date: 2014-04-01
forum: New to Ubuntu
---

### Post by Darrell_Wellsman on 2014-04-01
Ubuntu 12.04, been running it into the ground for about a month and a half.

So I've been trying to run a game in Wine (separate problem) and hit a wall with my graphics despite having fixed to what should have been a working point. I was getting an 'incompatible graphics card' message for my Radeon HD 5850, which I know isn't the case for the game in question, so I decided to get a new driver.

I look up guides on this and end up trying fglrx. First I try it through 'additional drivers', but that gets me an error feedback about dependencies. I update dependencies from terminal as per some guides I find online. then I get the .run file for catalyst from ati and use 
buildpkg Ubuntu/precise

to get these three .deb files. I try to run the first and get back a message about broken package lists. I try to purge
with sudo apt-get remove --purge xorg-driver-fglrx fglrx*
but that gets back a string of 'package XXXX is not installed so not removed' messages. I try reinstalling the default
open source drivers, but that goes nowhere fast. When I reboot I get a grey screen after I log in that takes a while to 
change into my desktop. At this point whenever I open my software centre, or even just randomly and for no reason at all
I get a message about broken package lists.

So I start using sudo rm -rf on anything and everything with fglrx in it (accompanied by the locate command). And that 
seems to do a whole lot of nothing. But after that I eventually get back 'radeon default' as a driver and my software
centre stops bugging me about package lists (tested installing something, it worked). 

However I still have the greyscreen on startup, when I locate fglrx I still can't purge it or rm it, my windows won't
autoform when I drag them to a scren edge (a feature I quite liked). And I still can't go back to my default open source
drivers. 

At this point I'm really not sure what to do. I've looked through documentation in a lot of places with people who have
had trouble with this sort of thing, but none of their solutions seem to work for me, and none of them got their systems
quite so FUBAR-ed. Any help to cleaning up my graphics drivers completely then working back up to a point of functionality:
preferably high functionality would be appreciated.

PS. am getting windows popping up with "Sorry the application unity_support_test has closed unexpectedly" and "System Problem Detected" frequently.

---

### Post by sotiris2 on 2014-04-01
Check [here](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx) for instructions on how to remove fglrx.  If you want to revert back to the open drivers it has a link to an additional process. 

If you want the amd drivers follow [these](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Before_you_start)

---

### Post by Darrell_Wellsman on 2014-04-01
Already tried the above guide for removing fglrx, it straight up did not work. These are the messages I get back:

ryakoth@Oracle:~$ sudo sh /usr/share/ati/fglrx-uninstall.sh
[sudo] password for ryakoth: 
sh: 0: Can't open /usr/share/ati/fglrx-uninstall.sh
ryakoth@Oracle:~$ sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'xorg-driver-fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-kernel-source' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx_*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-driver-dev' for regex 'fglrx_*'
Note, selecting 'xfree86-driver-fglrx' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle-experimental-12' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle-experimental-13' for regex 'fglrx_*'
Note, selecting 'fglrx-experimental-9-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle-experimental-9' for regex 'fglrx_*'
Note, selecting 'fglrx-experimental-12-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-updates' for regex 'fglrx_*'
Note, selecting 'fglrx-pxpress' for regex 'fglrx_*'
Note, selecting 'fglrx-control-qt2' for regex 'fglrx_*'
Note, selecting 'fglrx-updates-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-experimental-12' for regex 'fglrx_*'
Note, selecting 'fglrx-experimental-13' for regex 'fglrx_*'
Note, selecting 'fglrx-glx' for regex 'fglrx_*'
Note, selecting 'fglrx-modaliases' for regex 'fglrx_*'
Note, selecting 'fglrx-experimental-13-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-experimental-9' for regex 'fglrx_*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx_*'
Note, selecting 'fglrx-driver' for regex 'fglrx_*'
Note, selecting 'fglrx-control' for regex 'fglrx_*'
Note, selecting 'fglrx-amdcccle-updates' for regex 'fglrx-amdcccle*'
Note, selecting 'fglrx-amdcccle-experimental-12' for regex 'fglrx-amdcccle*'
Note, selecting 'fglrx-amdcccle-experimental-13' for regex 'fglrx-amdcccle*'
Note, selecting 'fglrx-amdcccle-experimental-9' for regex 'fglrx-amdcccle*'
Note, selecting 'fglrx-amdcccle' for regex 'fglrx-amdcccle*'
Note, selecting 'xorg-driver-fglrx-dev' for regex 'fglrx-dev*'
Note, selecting 'fglrx-dev' for regex 'fglrx-dev*'
Note, selecting 'xfree86-driver-fglrx-dev' for regex 'fglrx-dev*'
Package fglrx is not installed, so not removed
Package fglrx-amdcccle is not installed, so not removed
Package fglrx-amdcccle-experimental-12 is not installed, so not removed
Package fglrx-amdcccle-experimental-13 is not installed, so not removed
Package fglrx-amdcccle-experimental-9 is not installed, so not removed
Package fglrx-amdcccle-updates is not installed, so not removed
Package fglrx-dev is not installed, so not removed
Package fglrx-experimental-12 is not installed, so not removed
Package fglrx-experimental-12-dev is not installed, so not removed
Package fglrx-experimental-13 is not installed, so not removed
Package fglrx-experimental-13-dev is not installed, so not removed
Package fglrx-experimental-9 is not installed, so not removed
Package fglrx-experimental-9-dev is not installed, so not removed
Package fglrx-updates is not installed, so not removed
Package fglrx-updates-dev is not installed, so not removed
Package fglrx-pxpress is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

For the removal commands
And
ryakoth@Oracle:~$ sudo apt-get remove --purge xserver-xorg-video-ati xserver-xorg-video-radeon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xserver-xorg-video-ati is not installed, so not removed
Package xserver-xorg-video-radeon is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libc6-i386 lib32gcc1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ryakoth@Oracle:~$ sudo apt-get install xserver-xorg-video-ati
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 xserver-xorg-video-ati : Depends: xorg-video-abi-11
                          Depends: xserver-xorg-core (>= 2:1.10.99.901)
E: Unable to correct problems, you have held broken packages.
ryakoth@Oracle:~$ sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx : Depends: libglapi-mesa (= 8.0.4-0ubuntu0.7)
E: Unable to correct problems, you have held broken packages.
ryakoth@Oracle:~$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
mv: cannot stat `/etc/X11/xorg.conf': No such file or directory
ryakoth@Oracle:~$ sudo rm -rf /etc/ati
ryakoth@Oracle:~$ 
For the reinstall attempt.

I tried what is located here [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver). As well as searching previous threads on the fglrx topic before asking for help. If standard purge/remove/uninstall commands worked I wouldn't be asking for help.

---

### Post by sotiris2 on 2014-04-01
Try this one.

 ```
sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core 
```



EDIT: BEFORE THAT do 

```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
```

---

### Post by Darrell_Wellsman on 2014-04-01
ryakoth@Oracle:~$ sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core
[sudo] password for ryakoth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx : Depends: libglapi-mesa (= 8.0.4-0ubuntu0.7)
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 8.0.4-0ubuntu0.7)
E: Unable to correct problems, you have held broken packages.
ryakoth@Oracle:~$ 



Is there any way to do a scan/repair on 'broken packages' systemwide, because it looks like I have some pretty deeply ingrained here. 

Half a day away from just backing up my files and reinstalling ubuntu entirely... again. (likely to break it again while trying to get wine graphics to work).

---

### Post by sotiris2 on 2014-04-01
Try the purge i suggested above. Also disable any extra repositories if you have and try again.

---

### Post by Darrell_Wellsman on 2014-04-01
ryakoth@Oracle:~$ sudo apt-get remove --purge xorg-driver-fglrx fglrx*
[sudo] password for ryakoth: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'fglrx' for regex 'fglrx*'
Note, selecting 'fglrx-glx' for regex 'fglrx*'
E: Unable to locate package xorg-driver-fglrx

Is what I got for the purge, then I got the same error back as listed above when I retried the reinstall. 

When you say to disable extra repositories do you mean to check off all of the boxes in software sources other than 'main'. Or is there something else I need to do here?

---

### Post by sotiris2 on 2014-04-01
Uncheck everything in the "Other Software" tab. Btw you still have graphics?

then 

```
sudo apt-get update
```

and try 

```
sudo apt-get install purge libglapi-mesa:i386 libglapi-mesa:amd64
```

```
sudo apt-get install libglapi-mesa:i386 libglapi-mesa:amd64
```

then IF the second one succeeds try again 

```
sudo apt-get install --reinstall libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64 libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 xserver-xorg-core
```

---

### Post by Darrell_Wellsman on 2014-04-01
Yeah for some reason have had graphics this entire time, though slow loading graphics with glitches and greyscreens during lag. I think my motherboard or graphics card might have some sort of internal minimal driver. i know that my motherboard has that ASUS expressgate packet that comes with splashtop, so I assumed that was what I was reverting to here.... not actually sure how it works. 

That last thing seemed to work. I'm going to try rebooting then get back to thread on how it went. Either way, thanks for the help, and sorry if I've been a bit impatient/tempermental.

---

### Post by Darrell_Wellsman on 2014-04-01
So update. I did what you told me and upon rebooting got to the ubuntu screen, then suffered blackscreen. I tried plugging my monitor directly into my motherboard, still blackscreen. So I popped in my ubuntu boot cd and am currently running in 'try ubuntu' mode. Thus my problem is no longer mad crazy drivers defeating me, my problem is finding out how to back up files and bookmarks from an OS that I can't boot into. 

Once I get my files into thumb drives I'm up in the air about whether to get Windows 7 from my laptop and set up a duel boot, thus removing my tine problems or continuing to bash my head against wine based driver problems for all of eternity. (I currently have complete graphical failure after an attempt at installing a fairly basic game, no working printer driver [I hate you canon] and really don't want to reconfigure my wireless again... ever.]

---

### Post by sotiris2 on 2014-04-01
Can't you get a terminal with Ctrl+Alt+f1? 
If you can 

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
```

and finally:

```
sudo apt-get install xserver-xorg-video-ati
```

should get you up and running. Provided ofcourse that libglapi did install correct since that was the problem.

---

