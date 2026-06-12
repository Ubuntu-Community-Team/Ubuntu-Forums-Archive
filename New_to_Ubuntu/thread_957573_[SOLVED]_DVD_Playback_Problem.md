---
title: "[SOLVED] DVD Playback Problem"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by revoman3 on 2008-10-24
I have already read through several guides on this topic however when trying to download the lib files for DVD playback (libdvdcss2 libdvdread3 libdvdnav4) apparently they don't exist on the repository, please help.

---

### Post by marko_4454 on 2008-10-24
You should add the Medibuntu Repositories or just download the deb file using wget.
heres a good link:
[https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs](https://help.ubuntu.com/community/Medibuntu#Playing%20Encrypted%20DVDs)

and here:
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories](https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories)

---

### Post by Crandom on 2008-10-24
Use this guide: [https://help.ubuntu.com/8.04/musicvideophotos/C/video.html](https://help.ubuntu.com/8.04/musicvideophotos/C/video.html)

---

### Post by jpoRS on 2008-10-24
Have you added the non-free repositories?

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_DVD_Support)

---

### Post by revoman3 on 2008-10-24
Thanks for the fast replies, I'm gonna try it now :)

---

### Post by revoman3 on 2008-10-24
The Video works perfectly now, however I can't seem to hear anything from gxine. Sound works with music on Rhythmebox but not with DVD's on gxine :confused:

---

### Post by marko_4454 on 2008-10-24
Try to run this command:
> sudo apt-get install w32codecs gstreamer0.8-plugins ubuntu-restricted-extras libdvdcss2


---

### Post by revoman3 on 2008-10-24
When I do this I get the following

> root@michael-desktop:/home/michael# sudo apt-get install w32codecs gstreamer0.8-plugins ubuntu-restricted-extras libdvdcss2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
w32codecs is already the newest version.
E: Couldn't find package gstreamer0.8-plugins


---

### Post by LowSky on 2008-10-24
```
sudo apt-get install w32codecs ubuntu-restricted-extras libdvdcss2
```
ubuntu-restricted-extras will install gstreamer plugins

if you have installed all the pacages then just reboot, sometime that is need for everything to start working

---

### Post by marko_4454 on 2008-10-24
So I am not currently in my linux box, so I dont know the version that is current. This is the reason why it gave you this error. 
What you can do is the following: 
1) Run: 
> sudo apt-get install w32codecs ubuntu-restricted-extras libdvdcss2

Hopefully this works :) I am going to get away from the computer, for a couple of hours, but it should be fine.

---

### Post by revoman3 on 2008-10-24
It's downloading the latest GStreamer Plug-ins right now (0.10)
Thanks Everyone! :)

---

