---
title: "Getting Webcam in HP 2133 to work"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by sleepersnow on 2008-09-28
Hey, i will be the first to admit, I am the least experienced person concerning using Ubuntu (or linux for that matter), as i just installed it this morning on my HP 2133.** Does anyone know how to make the webcam work?** Again, i am a complete nOOb, so if its possible to do it with the GUI, then i would prefer that. Thanks!

---

### Post by starcannon on 2008-09-28
Very cool little notebook; okay so, lets start by looking at the output of lsusb. To get this output please open a terminal:
[INDENT]{Applications>Accessories>Terminal}
[/INDENT]Then run this command and copy paste the output back here.
[INDENT]```
lsusb > lsusb.txt && gedit lsusb.txt
```
[/INDENT]I'll check back in a few minutes.

GL

---

### Post by starcannon on 2008-09-28
is this the mini-note or is it the bigger dv series? HP made a 2133 model in both, and they are nothing alike; if its the dv2133 is it a dv2133ea or a dv2133tx? You should be able to find out by looking at the stickers on the bottom of the laptop.

---

### Post by nickfox on 2008-12-02
Hi this looks like  good thread to start in. 
Just to clarify, i have:
HP 2133 1.2G/120GB version ubuntu 8.04 kernel: 2.6.24-22

I have installed [cheese]("http://projects.gnome.org/cheese/") and the webcam works fine.

I know from reading the [HP 2133 thread]("https://wiki.ubuntu.com/LaptopTestingTeam/HP2133") that there are problems with some applications. I have had a look at gstreamer-properties and the plugin Video for Linux "v4l2" seems to be the same one Cheese is using. This renders the video fine when you click the test button but I get "could not get settings from resource" error on "v4l" setting.

So.. to get to my point here, VLC seems to be using "v4l" by default acording to the capture device options string:
v4l:// :v4l-vdev="/dev/video" :v4l-adev="/dev/dsp" :v4l-norm=3 :v4l-frequency=-1

I have messed around with this string to try to force v4l2 but no luck am i being a bit nieve here or am i on the right track?

And is there any documentation on the options in the above string so i can understand how these options work?

thanks for your help guys

---

### Post by Nonsense on 2008-12-10
I couldn't resist hijacking this thread...

Here's my output:

```
Bus 004 Device 002: ID 04f2:b107 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0f62:1001 Acrox Technologies Co., Ltd Targus Mini Trackball Optical Mouse
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

(I have a Trust optical mouse attached to one of the usb-ports)

---

### Post by windowsseven on 2008-12-11
I've set up a site for us with Hp 2133, 
[http://www.ubuntu2133.blogspot.com/]("http://www.ubuntu2133.blogspot.com/")

Check it out!

---

### Post by mazedlx on 2008-12-14
system is 8.10, Hp 2133, 1.6GHz. i installed cheese but it won't show anything. the webcam did work under xp btw.

i seem to have the same problems getting the webcam to work.
```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:0307 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f2:b107 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

i'd appreciate some help ;-) thanks in advance

---

### Post by mazedlx on 2008-12-16
update!

it seems the problems are cheese related, a bug has already been filed. nevertheless, cheese works when you change the cams resolution to 160x120 pixels. hope this helps anyone. seems like we have to wait for a new version of cheese.
by the way: i tried to run my webcam in skype, vlc and ekiga and it worked like a charm with any of these apps.

---

### Post by Nonsense on 2008-12-21
I get the same impression too.
I tried with LUVCview (install it from Synaptic) and everything works, but Cheese still crashes.

---

