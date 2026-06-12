---
title: "packages not updated"
date: 2014-11-12
forum: New to Ubuntu
---

### Post by marchello_lippi2 on 2014-11-12
Hi all, 

got warning during executing command: 

$ sudo apt-get upgrade

[sudo] password for user1: 
Reading packages list... Done
Building dependencies tree 
Reading information about state... Done 
Calculating updates... Done 
Packages left unchanged: 
  easytag gir1.2-rb-3.0 gir1.2-totem-1.0 libavcodec-extra-54
  librhythmbox-core8 libtotem-plparser18 libva1 libvlc5 libvlccore7
  libvncserver0 mplayer rhythmbox rhythmbox-data rhythmbox-mozilla
  rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune rhythmbox-plugins
  totem totem-common totem-mozilla totem-plugins vlc vlc-data vlc-nox
  vlc-plugin-notify vlc-plugin-pulse
updated 0, installed 0 new, 0 marked for deleting and 26 not updated. 

What is it and how to solve? And do I need to solve it?

---

### Post by pfeiffep on 2014-11-12
> **marchello_lippi2 said:**
> Hi all, 

got warning during executing command: 

$ sudo apt-get upgrade

<snip>

What is it and how to solve? And do I need to solve it?
Did you enter the command ```
sudo apt-get update
```prior  upgrade?
If not try update followed by upgrade

---

### Post by marchello_lippi2 on 2014-11-12
pfeiffep, 

sorry I didn't mention it before, but yes, I always perform 

sudo apt-get update 

before 

sudo apt-get upgrade 

So my question is still open.

---

### Post by pfeiffep on 2014-11-12
There are more knowledgeable folks participating on this forum than me, with that caveat I'll attempt to answer to your dilemma.

Please read about the command [apt-get dist-upgrade]("http://linux.die.net/man/8/apt-get") prior to executing.
 [Another resource]("http://askubuntu.com/questions/222348/what-does-sudo-apt-get-update-do")

---

### Post by ian-weisser on 2014-11-12
I can think of only four reasons why a package wouldn't be upgraded by 'apt-get upgrade' in Ubuntu.
1) It's a kernel package, and requires dist-upgrade.
2) It's been apt-pinned. (You would know if you did that - you would need to look up how to do it)
3) It's a package or dependency from a non-Ubuntu source (like a PPA). One of the non-Ubuntu packages in that chain has a poorly-chosen version number on it, or has the wrong files in it.
4) It's a package that's from Debian or from a different version of Ubuntu.

#3 is the most likely issue that pops up in these forums. People forget where they installed applications from.
Did you install Rhythmbox, Totem, or VLC from a PPA or other non-Ubuntu source?

---

### Post by marchello_lippi2 on 2014-11-12
*Did you install Rhythmbox, Totem, or VLC from a PPA or other non-Ubuntu source?*

Well, actually it is possible. Some packages I've installed from different PPA than official ubuntu source. 

What now? Does it mean that these packages will not be upgraded at all? 
How to solve? Should I reinstall my ubuntu system from the beginning or there is easier decision? 
Thanks ahead.

---

### Post by marchello_lippi2 on 2014-11-12
I decided just to remove those packages. I don't use vlc, totem, rhythmbox anyway...

---

### Post by ian-weisser on 2014-11-12
> **marchello_lippi2 said:**
> I decided just to remove those packages. I don't use vlc, totem, rhythmbox anyway...

A wise decision.
If they were from non-Ubuntu sources, then uninstalling them was what I would have recommended anyway.

Glad to see that you seem to have it sorted.

---

### Post by marchello_lippi2 on 2014-11-12
Well, only one package left to be discussed. 

It is **libva1**, I can't just remove it, because it wants to remove also 

  audacious audacious-plugins clementine dolphin ffmpegthumbnailer
  gecko-mediaplayer gnome-mplayer gstreamer1.0-libav gstreamer1.0-plugins-bad
  guvcview libavcodec54 libavformat54 libbaloowidgets4 libchromaprint0
  libffmpegthumbnailer4 libkfilemetadata4 libopencv-contrib2.4
  libopencv-highgui2.4 libopencv-legacy2.4 libopencv-objdetect2.4 libva-glx1
  libva-x11-1 libva1 libxine1-ffmpeg libxine1-plugins lubuntu-desktop mencoder
  mplayer2 xbmc xbmc-bin

(I use audacious, dolphin, lubuntu-desktop). 

So what should I do now? 
Thanks ahead.

---

### Post by ian-weisser on 2014-11-12
Please show us the complete result of:
```
apt-cache policy libva1
```
This will show us which repository the current version came from, and which repository the not-updated version is in.

After you uninstalled those applications you were not using, did you happen to go into Software & Updates and disable those PPAs? Some people forget to do that.

---

### Post by marchello_lippi2 on 2014-11-12
$ sudo apt-cache policy libva1
[sudo] password for user1: 
libva1:
  Installed: 1.3.0-2
  Candidate:    1.4.0~trusty
  Version table:
     1.4.0~trusty 0
        500 [http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/](http://ppa.launchpad.net/mc3man/trusty-media/ubuntu/) trusty/main i386 Packages
 *** 1.3.0-2 0
        500 [http://ua.archive.ubuntu.com/ubuntu/](http://ua.archive.ubuntu.com/ubuntu/) trusty/universe i386 Packages
        100 /var/lib/dpkg/status

---

### Post by ian-weisser on 2014-11-12
Yep, that's a problem. The Ubuntu version is installed; the system wants to upgrade to the PPA version...which is apparently incompatible with some other software.

1) Disable that PPA.
2) Refresh your package cache (sudo apt-get update)

Then see if the problem goes away.

---

### Post by marchello_lippi2 on 2014-11-12
> **ian-weisser said:**
> Yep, that's a problem. The Ubuntu version is installed; the system wants to upgrade to the PPA version...which is apparently incompatible with some other software.

1) Disable that PPA.
2) Refresh your package cache (sudo apt-get update)

Then see if the problem goes away.

Thanks, works great.

---

