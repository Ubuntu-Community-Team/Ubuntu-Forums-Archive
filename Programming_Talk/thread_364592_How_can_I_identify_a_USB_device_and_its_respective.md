---
title: "How can I identify a USB device and its respective partitions using C or sh script?"
date: 2007-02-18
forum: Programming Talk
---

### Post by AsGF2MX on 2007-02-18
On my Linux box right now, I have a fair few USB disks attached (2 right now). The problem is I want to identify the device and its respective partitions. What way can I do this with either a C application (using libusb and any other required method)? I'd really appreciate any help on this.

What am I trying to accomplish really? I just want to run my little program and have it tell me which USB device has what partitions associated with it.

So far I have written small programs (snippets of code here and there) to identify what USB device has what vendor and product ID and the like but I want to be able to print out its associated partitions as well.

---

### Post by mogliii on 2007-02-18
Hi,

I am not sure why you want to identify it, but I guess from my own experience that you have a problem with mounting the partitions.

So the harddrive you plug in the first time is always /dev/sda*. If you have written in your automount list /dev/sda* you will have different partitions mounted depending on the order of plugging in the usb drives.

To avoid this problem (if you have two usb devices that look similar) you can use the UUID of the partitions.

I already had issues about that, so please this thread: [http://ubuntuforums.org/showthread.php?t=145467]("http://ubuntuforums.org/showthread.php?t=145467")

If this is not what you are looking for, I suggest you to wait for other replies

---

### Post by AsGF2MX on 2007-02-18
Actually, I don't have any mounting problems but am doing this for my own curiosity's sake. Just how I learn :) 

I can make sense of it; plug in a usb disk and I get sdb or sdc or etc and any partitions in it will be marked sdbN or sdcN where N is an integer.

The problem appears when I want to associate the partitions or device with its respective USB device. I would prefer to do it in C (to let me to extend my program).

I can get so far as to get a handle to the device and get info from it. However I don't have any leads on how to associate the device with its partition(s).

---

### Post by AsGF2MX on 2007-02-19
Well I found out not long after I posted the previous message but I fell asleep

```
udevinfo -q env -n /dev/sdb |grep SERIAL 
```

That will give you the serial number of the disk you specified. This is a pretty good start for me. Just thought I'd share.

---

