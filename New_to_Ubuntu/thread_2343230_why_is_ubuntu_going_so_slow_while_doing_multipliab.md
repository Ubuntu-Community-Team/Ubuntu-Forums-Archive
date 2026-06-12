---
title: "why is ubuntu going so slow while doing multipliable things usb-harddrive-download"
date: 2016-11-14
forum: New to Ubuntu
---

### Post by a.dusty.trail on 2016-11-14
why is ubuntu going so slow while doing multipliable things ?

im downloading an iso at 1mb/s
im watching a 720p movie 
and im transfering 15 gigs of files to a usb drive..
while doing a little bit of surfing (firefox open mostly to read a few things like here)

and ubuntu is dog slow..
it is pausing and im having to wait for it to catch up on mouse clicks
the screen is pasueing with nothing channging for minutes at a time
( i have to kill the movie which was a trial all in it self waiting for it to accept the mouse click)
its a dual core processer with 4gbs of ram 4 tb hard drivees usb2.0 and the screen is only at 1360x768
ive seen intel atom systems with 1gb of ram do all that in windows.


and if i start copying a large file over 1gb to the usb consider the whole system frozen 
really any file operation on anything but the boot drive slowes down everything to a crawl
its like ubuntu has lost the ability to multitask.

system monitor is saying nothing is useing the cpu but the load indicator is almost maxed out
swap is at less than 5% and only 25% of memory is being used.

---

### Post by TheFu on 2016-11-14
On some systems, I've seen large USB workloads drastically slow the system - even lock it up for 20-45 seconds at a time. I think it is related to the USB controller, but don't know for certain.  I've never seen the issue when USB wasn't being used by more than a single task.  I think it is a design flaw in some systems that only proprietary drivers get around. Of course, few proprietary drivers for USB exist for Linux. Either the kernel supports it or it doesn't.

On other systems running the same release, no issues at all with USB. 

For the video playback, please check that the GPU is doing all the video codec workload, not the CPU. That is usually possible for mpeg2 and h.264 streams. Everything else has to be decoded in software and eats CPU. Some systems and programs don't automatically do what we want. Those need a little extra help.

Of course, it could be all sorts of other issues. Check the log files. See what they say. Could be failing HW too.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1208993](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1208993) might be related.  Tried to solution there (doesn't need a reboot) and it appears to help.  By any chance, did you add more RAM to the system since doing the install?

And just to be clear, none of my systems are running the OS on USB. USB is just for data storage and all formatted with Linux file systems.

---

### Post by MartyBuntu on 2016-11-14
This is an installation of Ubuntu on a USB drive?

You're asking a lot from USB read/write rates. Installation to USB drive is fine for testing or "proof-of-concept", but not very practically for everyday use.

---

