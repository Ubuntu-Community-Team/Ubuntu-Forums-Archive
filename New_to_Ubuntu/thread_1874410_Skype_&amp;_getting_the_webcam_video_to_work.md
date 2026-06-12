---
title: "Skype &amp; getting the web/cam video to work"
date: 2011-11-03
forum: New to Ubuntu
---

### Post by Koyanggi on 2011-11-03
Hello, I just installed Ubuntu 11.10 and I'm trying to get Skype to work. 

 I finally got the mic to work by turning off the (Allow Skype to automatically adjust my mixer levels) in Skype and then using Pulse Audio Volume Control to unlock R/L channels together and then adjusting them so one was high and one was low. Problem solved when I opened Skype back up. I can now make a test call and hear my voice.

Now I'm trying to get the video working. My web/cam works great with Cheese WebCam Booth and also with Guvcview. But when I open Skype/options/video devices/test -  I just get a black screen and no video image. 

I am new to Ubuntu 11.10 (4 days now) any and all advice and information would be very helpful to me.  I have been looking around the forms here for info. but most of the stuff I found was a little old, above my level of understanding or related to another version of Ububtu. Maybe that last sentence does not make sense, maybe old is ok, I don't know.

Thank you for taking the time to read this.

Peace

---

### Post by Script Warlock on 2011-11-03
may we know the webcam model?

---

### Post by Koyanggi on 2011-11-03
Hello, Script Warlock

Yes, indeed the model is:  Gigaware model #25-157  Bought it from RadioShack.

Specifications:

PC Interface: USB 1.1 / 2.0

Video Format: AVI

Audio: Built-in mic

Image Sensor: 640x480 Pixels CMOS

Frame rate: 640x480 Pixels @ 30fps
                    320x240 Pixels @ 30fps

Video Capture Resolution: 640x480 / 320x240 pixels

I hope that helps

Peace

---

### Post by Script Warlock on 2011-11-03
open terminal and type

lsusb

lsmod | grep videodev

---

### Post by Koyanggi on 2011-11-03
Hello, Script Warlock

> type lsusb and lsmod | grep videodev on your terminal and post some info

Ok I found out how to open the terminal.


Is that one long thing or three separate things?

example: one long thing "lsusb and lsmod | grep videodev
OR
three separate things
  
lsusb 

lsmod

| grep videodev 


I just confused about what I should type,

---

### Post by Script Warlock on 2011-11-03
post some info after it displays some result

---

### Post by Koyanggi on 2011-11-03
Ok got it.:)

lsusb  - results:

e@Koyanggi:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 093a:2620 Pixart Imaging, Inc. 
Bus 004 Device 002: ID 12cf:0047  

lsmod | grep videodev 	- results:

e@Koyanggi:~$ lsmod | grep videodev 
videodev               85626  1 gspca_main

I hope I did that right. I have no idea what any of those results mean.

---

### Post by Script Warlock on 2011-11-03
try this

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by Koyanggi on 2011-11-03
> try this

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype 	

How do I try it? 

Do I type LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

into the terminal?

---

### Post by Script Warlock on 2011-11-03
> **Koyanggi said:**
> How do I try it? 

Do I type LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

into the terminal?
yes on your terminal

---

### Post by Koyanggi on 2011-11-03
Ok I did that, after I hit enter, Skype opened, I tested the video, and got the black screen,

The results in the terminal:

e@Koyanggi:~$ LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.

(skype:7907): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:7907): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:7907): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:7907): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by Script Warlock on 2011-11-03
try this and lets see the result on your terminal

sudo lsmod | grep gspca

---

### Post by Koyanggi on 2011-11-03
Ok,

Results:

e@Koyanggi:~$ sudo lsmod | grep gspca
[sudo] password for e: 
gspca_pac7302          18212  0 
gspca_main             27610  1 gspca_pac7302
videodev               85626  1 gspca_main

---

### Post by Script Warlock on 2011-11-03
> **Koyanggi said:**
> Ok,

Results:

e@Koyanggi:~$ sudo lsmod | grep gspca
[sudo] password for e: 
gspca_pac7302          18212  0 
gspca_main             27610  1 gspca_pac7302
videodev               85626  1 gspca_main

sudo rmmod gspca_pac7302
then
sudo modprobe gspca_pac7302
then
/usr/bin/skype

---

### Post by Koyanggi on 2011-11-03
e@Koyanggi:~$ sudo rmmod gspca_pac7302
[sudo] password for e: 
ERROR: Module gspca_pac7302 does not exist in /proc/modules


e@Koyanggi:~$ sudo modprobe gspca_pac7302
[sudo] password for e: 

(This one gave me no results)


e@Koyanggi:~$ /usr/bin/skype 

(skype:8387): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:8387): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:8387): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(skype:8387): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

---

### Post by Script Warlock on 2011-11-03
are you using 32 or 64bit ubuntu?

---

### Post by Koyanggi on 2011-11-03
I'm using 32 bit.

I have Cheese installed. It works fine. I'll launch it on now.

All of the effects show up just fine when I choose Effects. But when I select some of them they don't work.

No effect seems to be working fine.

---

### Post by Script Warlock on 2011-11-03
for the meantime check this [link]("http://ubuntuforums.org/showthread.php?t=993262") if it can give more infos for you

---

### Post by cmfrtblynmb on 2011-11-05
> **Script Warlock said:**
> try this

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

The problem is, that location does not exist anymore

In 64 bit, libv4l has been moved to : /usr/lib/x86_64-linux-gnu/libv4l

But here is the problem, in 64 bit we used to use 32 bit libv4l files. Now as far as I see, they did not pack this 32 bit version

Can anybody help please??

---

### Post by cmfrtblynmb on 2011-11-05
> **Script Warlock said:**
> try this

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

OK, for 32 bit one of  these should work

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l1compat.so skype
```

or 

```
LD_PRELOAD=/usr/lib/i386-linux-gnu/libv4l/v4l2convert.so skype
```

But my problem is this: I am using 64 bit and in the past we used to install lib32v4l-0. That was the 32 bit version of libv4l packages. They don't exist anymore

What are we supposed to do now?

---

### Post by rtega on 2012-01-08
Well, you do exactly that install lib32v4l-0 and you're set. If I run 
LD_PRELOAD="/usr/lib32/libv4l/v4l1compat.so" skype
everything works OK for me.

---

