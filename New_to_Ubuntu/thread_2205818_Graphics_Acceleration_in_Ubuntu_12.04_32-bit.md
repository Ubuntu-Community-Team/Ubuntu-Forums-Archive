---
title: "Graphics Acceleration in Ubuntu 12.04 32-bit"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by Alyx_Mazerov on 2014-02-16
I'm very new to using Ubuntu.  I recently had boot issues with Windows 7 (freezing during boot) and just happend to have an Ubuntu 32 bit disk laying around that a friend gave me years ago.   I loaded that on a partition, updated it to 12.04 and was able use it to retrieve my data.  Long story short, I haven't been able to fix Windows 7 or get my boot disk to load to reformat and reinstall.  Since it all seems to work fine with the Ubuntu I have I've given up on windows 7.  I just want to leave well enough alone.  
My guilty pleasure is playing Farmville 2.  When I go to the Zynga site to play I get the message "You are playing FarmVille 2 without graphics acceleration..."  And it's so slow I can't play.  I got the latest version of flash so that isn't the problem.  
I have a Nvidia GeForce GTS450 graphics card.  I think my problem is that I don't have a proper driver installed to maximize my graphics potential or it could be a 32bit vs 64bit issue.   I've also looked at the available Nvidia drivers in the software center and am not sure if any of these will fix my problem.  After reading bad reviews, that I don't really understand, for the NVidia binary X.Org driver ('current' driver) I'm afraid of just trying something out and hoping for the best.  The last thing I want to do is crash my system.
Any advice would be much appreciated.

---

### Post by wiremoons on 2014-02-16
Hi Alyx_Mazerov

Ubuntu 12.04 normally uses the opensource 'nouveau' drivers [1] for Nvidia graphics cards which is probably not supporting the graphics acceleration you need for FarmVille 2.

You should be able to swap to use the actual Nvidia provided drivers instead - to activate the full feature set of your graphics card. The easiest way I have found to do this is to open the "Ubuntu Software Center" application, and search for the application called:  " Additional Drivers "

If you install this program it will check what drivers you are using, and offer appropriate drivers that match you hardware, that are available from the manufacture (ie Nvidia) - as opposed to the open sources only drivers such as nouveau. The drivers it offers should include those in the Ubuntu software repository - so have been tested with Ubuntu for you.

That should be 'safer' option that downloading the latest driver from the NVidia web site, and installing them yourself. However, there are lots of tutorials and articles on the internet available, if you feel the need to go down this route in the future.

Hope that helps.


[1] nouveau drivers info: [http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)
[2] additional driver app info: [https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/](https://apps.ubuntu.com/cat/applications/precise/jockey-gtk/)

---

### Post by mastablasta on 2014-02-16
have a look: [http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers](http://askubuntu.com/questions/47506/how-do-i-install-extra-drivers)

jockey should already be included and these additional drivers should be safe and stable

---

### Post by Alyx_Mazerov on 2014-02-16
I installed a new driver via the Additional Drivers application but it didn't fix my problem.  I'll continue to do reasearch and see if I can find a solution.  Thanks for your help.

---

### Post by monkeybrain20122 on 2014-02-16
Hardware acceleration for flash is not enabled by default. You can enable it as follows
```
cd /etc
sudo mkdir adobe
cd adobe
gksudo gedit mms.cfg
```
the last command creates a new document mms.cfg, enter in it
```
EnableLinuxHWVideoDecode=1
OverrideGPUValidation=1
```
save and restart Firefox.

It may work for you, but in my experience flash crashes almost every time with hardware acceleration enabled and it doesn't work for most flash sites (it seems to work only on Youtube if it doesn't crash). If that happens just remove the folder /etc/adobe. I have made a script to switch between hardware acceleration enabled and disabled but pretty much leave it disabled.

**EDITED**: There is another type of hardware acceleration for playing videos called vdpau for Nvidia. To enable it you need to install extra packages: libvdpau1 and vdpau-va-driver. 

mplayer and XBMC support hardware decoding with vdpau. For mplayer use any of the guis (gnome-mplayer or Smplayer) and set output to vdpau. Vlc also supports it since 2.1.1 but not sure if it is enabled in any of the Ubuntu builds including ppas (ffmpeg in ubuntu is too old). vpdau has nothing to do with your original question but just mention it since  you have a Nvidia card.

---

### Post by Alyx_Mazerov on 2014-02-17
Thanks monkeybrain.  I tried it and it's still not fast enough.  Though it seemed slightly faster.  (If that is even possible, it might be all in my head.)  I'm starting to wonder if my problem is related to flash.  Adobe no longer supports flash for linux and the latest flash avalible is out of date.  If that is the case then I might be SOL.

---

### Post by mastablasta on 2014-02-17
it could be. however if it works it is probably not Flash. 
it could also be drivers are not good for the GPU. or that GPu is not that good.

one thing you could try is to add a lighter desktop environemnt and seeif that helps. are you using default Unity interface? try gnome classic or inity 2D. perhaps the desktop is eatign the GPU power. Unity desktop is 3D accelerated and is utilising the GPU to render the desktop itself.

---

### Post by monkeybrain20122 on 2014-02-17
> **Alyx_Mazerov said:**
> Thanks monkeybrain.  I tried it and it's still not fast enough.  Though it seemed slightly faster.  (If that is even possible, it might be all in my head.)  I'm starting to wonder if my problem is related to flash.  Adobe no longer supports flash for linux and the latest flash avalible is out of date.  If that is the case then I might be SOL.

You can get up to date flash with chrome. Just go to its website and pick the .deb for your architecture, download and install it (right click and the software centre will come up, but I prefer using gdebi, so you can install it first) After that it will create a repository and chrome will be updated along with other software.

Chrome bundles with it the latest flash, but I am not sure how to get hardware acceleration working. Google "hardware acceleration pepper flash Linux" and see if you can find anything.

Not sure if this would help with your problem, but it doesn't hurt to try.

---

### Post by Alyx_Mazerov on 2014-02-18
I tried Chrome and saw no difference.  Also there wasn't a noticeable difference when I switched to 2D.  Haven't tried Classic yet.  I'm pretty sure my GPU is good enough since it worked just fine in Windows 7.

---

### Post by mastablasta on 2014-02-18
ok so it's not flash then it is probably the drivers. i am not familiar with nvidia.

btw radeon 9200 works fine in windows xp but lags in linux (you tube videos) due to bad drivers (i think they are not doing full HD acceleration) as well as poor flash for linux :-/

---

### Post by mastablasta on 2014-02-18
ok so it's not flash then it is probably the drivers. i am not familiar with nvidia.

btw radeon 9200 works fine in windows xp but lags in linux (you tube videos) due to bad drivers (i think they are not doing full HD acceleration) as well as poor flash for linux :-/

---

