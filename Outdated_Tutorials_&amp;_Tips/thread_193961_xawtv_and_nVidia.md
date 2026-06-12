---
title: "xawtv and nVidia"
date: 2006-06-10
forum: Outdated Tutorials &amp; Tips
---

### Post by marcw on 2006-06-10
This HOW-TO is for someone who's not afraid of the command line and who has a non-working xawtv.  This solution might be for you. 

I had installed xawtv from Synaptic as a way to watch TV on my computer since I had a TV card already installed.  My card is a Pinnacle but lspci lists it as a Brooktree Corporation Bt878.

xawtv installed fine but I couldn't get it to work with my new Dapper install.  scantv would find all my channels ok but all that would display on xawtv was blue static.  I suspected that my problems might have been a compatibility issue with my nvidia driver but I wasn't (and still am not) 100% sure.

Since xawtv -hwscan would display the following:
```
~$ xawtv -hwscan
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-k7)
looking for available devices
port 244-244                            [ -xvport 244 ]
    type : Xvideo, video overlay
    name : video4linux

port 245-245
    type : Xvideo, image scaler
    name : NV17 Video Overlay

port 246-246
    type : Xvideo, image scaler
    name : NV17 Video Texture

port 247-278
    type : Xvideo, image scaler
    name : NV05 Video Blitter

port 279-279                            [ -xvport 279 ]
    type : Xvideo, video overlay
    name : NVIDIA Video Interface Port

/dev/video0: OK                         [ -device /dev/video0 ]
    type : v4l2
    name : BT878 video (Pinnacle PCTV Stud
    flags: overlay capture tuner
```
I was pretty sure that xawtv was grabbing the wrong device as the the docs said that it would grab the first available device in the hardware list.  But including "-device /dev/video0" in the xawtv command line didn't work either and would display the following error:
```
~$ xawtv -device /dev/video0
This is xawtv-3.94, running on Linux/i686 (2.6.15-23-k7)
X Error of failed request:  XF86DGANoDirectVideoMode
  Major opcode of failed request:  137 (XFree86-DGA)
  Minor opcode of failed request:  1 (XF86DGAGetVideoLL)
  Serial number of failed request:  63
  Current serial number in output stream:  63
```

A little bit of Googling showed that I was on the right track but needed one more switch to get it to work since nVidia has apparently stopped including DGA support in their driver.  Anyway, the command line that eventually got xawtv to work for me is this:

```
~$ xawtv -c /dev/video0 -remote
```
I then used the Alacarte Menu Editor to change the command line that my xawtv menu entry uses.

A couple of pointers:
1) As always, make sure your .xawtv config file is correct first.  I think that "~$ scantv -o ~/.xawtv" is a good way to write one that should work.
2) Make sure that v4l is loaded in the "Module" section of your your xorg.conf file.  "~$ sudo dpkg-reconfigure xserver-xorg" can help with that.
3) Read the man pages for help.  man xawtv, man scantv, and man xawtvrc are good ones to start with and helped me.

---

### Post by bluntz on 2007-09-19
Works on 2.6.15.26 too.
Any Idea how to get the sound to work  ?????

---

