---
title: "Howto: Cool video effects in amsn"
date: 2007-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by HumanAnarchist on 2007-06-24
This is a short guide for having cool video effects in amsn.

You need:
[list]
[*] webcam that uses v4l and not v4l2
[*] effectv
[*] vloopback module
[*] a setup that is ready for making kernel modules
[/list]

First install effectv:

```

apt-get install effectv

```

Check that effectv is working

```

effectv -device /dev/video0 nervoustv (name of effect at the end, see effectv -h)

```

Everything ok? then next step:

Make things ready for creating kernel modules in Ubuntu. I used this guide to get things set up:
**[http://dinomite.net/archives/setting-up-ubuntu-for-building-kernel-modules](http://dinomite.net/archives/setting-up-ubuntu-for-building-kernel-modules)**

Then make vloopback module:

Get the source:
```

wget http://www.lavrsen.dk/twiki/pub/Motion/VideoFourLinuxLoopbackDevice/vloopback-1.1-rc1.tar.gz

```

untar and follow the instructions on the page:
**[http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice](http://www.lavrsen.dk/twiki/bin/view/Motion/VideoFourLinuxLoopbackDevice)**

Short version of ^^
```

make 
insmod vloopback.ko
lsmod | grep vloopback 

```

Then start effecttv like this:
```

effectv -device /dev/video0 -vloopback /dev/video1 NervousTV

```

Now you can configure amsn to use the new virtual video device and get cool effects when you use webcam in amsn. Enjoy :popcorn:

-ha-

---

### Post by PsychedelicReaction on 2007-06-26
1. on feisty repository it seems effecttv is called affectv, with one t

2. that's what i get before compiling loopback module, so i think it's not ok ^^

```
mdm@astharot:~$ effectv -device /dev/video0 nervousTV
v4lopen:VIDIOCGCHAN: Invalid argument
Video initialization failed.
```

cam is recognized with v4l2 drivers

---

### Post by HumanAnarchist on 2007-06-26
changed effecttv to effectv.

It seams that effectv only supports v4l and not v4l2 :(

-ha-

---

