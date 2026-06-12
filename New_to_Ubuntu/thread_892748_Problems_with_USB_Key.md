---
title: "Problems with USB Key"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by nvilloria on 2008-08-17
I have a USB key (Corsair-Flash Voyager) with FAT32 file system that I want to use with both Ubuntu and Windows. The problem so far is that my Ubuntu (Hardy-Heron 64 bit) does not seem to recognize it, any suggestion about how to proceed with this?

Thanks,

Nelson

---

### Post by Naatan on 2008-08-17
Did you manually format it with FAT32 or are you using the default formatting that came with the USB stick?

If you are using the default I would recommend re-formatting it with FAT

---

### Post by nicedude on 2008-08-17
Try installing pysdm to mount the drive for you in a GUI window or you will have to learn the mount command ( much more difficult )

to install pysdm paste the following in a terminal

sudo apt-get install pysdm

then run this to start it up

sudo pysdm

Once you have it open look at the last disk in the list as this should be your portable ( plug it in of course before trying this ) and try to mount the partition in question on your voyager stick. It should do this for you or at least if not give you an error message that would help in trying the mount command.

---

### Post by nvilloria on 2008-08-17
Guys, thanks for the responses. 1) I gave to it a fresh format (FAT32), and I could have it mounted without any trouble --- I copied some files, etc. When I rebooted my machine, zas! it was gone: Ubuntu did not mount it. Two more things: I have tried the USB key in two different machines (both Ubuntu HH64), and in the different USB slots of those machines. Exactly the same happens: after a fresh format, Ubuntu loads the USB, and after a reboot, I lose it again. One more thing, pysdm does not see the key either. Hopefully there are more suggestions around.

Thanks!

Nelson

---

### Post by nicedude on 2008-08-17
I found a link to another person with similar problems, but most people answering them say this device works for them with no hassles so I don't know what to tell you.

[http://ubuntuforums.org/showthread.php?t=564568](http://ubuntuforums.org/showthread.php?t=564568)

---

