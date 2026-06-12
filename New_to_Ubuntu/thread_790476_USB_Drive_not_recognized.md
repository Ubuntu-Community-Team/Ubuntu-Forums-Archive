---
title: "USB Drive not recognized"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by tprzepiorka on 2008-05-11
Hello,
The other day I was copying files to my 2GB USB stick when I got an error that the files couldn't copy. The device had disappeared from the left panel on nautilus. So I took it out and put it back in the USB slot. Now, it isn't recognized on this or my laptop running Ubuntu. I booted up a gParted live cd with the USB pen drive in and it only recognized it as a 7MB drive and I wasn't able to format it. I have no idea what to do from here since it isn't working.
Thanks in advanced for any help that can be provided,
Tprzepiorka

---

### Post by bumanie on 2008-05-11
Unless anyone else knows more than I, it sounds like the device has been read or written to one too many times. Unfortunately these devices have a limited life. Try it in a windows machine or a mac - if it doesn't work in them either, it's likely the device has seen better days.

---

### Post by niteshifter on 2008-05-11
Hi,

It's possible the device has reached it's end of life, but I've got to say it's not probable - wear-leveling and all that in the device's firmware. More likely I think is the MBR on the device got trashed.

But since the device is not usable as is and recovery of any data on it not very likely if you feel up to some experimentation you could try:

{ in the below procedures I'm going to call the device /dev/sdX. You need to use the /dev string that your system identifies the device. **BE SURE YOU ID THE DEVICE - NOT YOUR HARD DRIVE!!!**  }

Let's see if we can be lucky and the simple fix works:
```
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1
```
Now see if gparted will work with it. If that doesn't work, we'll try clearing the entire device:
```
sudo dd if=/dev/zero of=/dev/sdX oflag=direct
```
Some versions of dd (this is rare) don't support oflags, dd will tell you if it doesn't. Use this instead:
```
sudo dd if=/dev/zero of=/dev/sdX
```
This can take some time to complete, be patient. If errors start to appear, the device is gone, sorry. If it completes OK, try gparted again.

---

### Post by tprzepiorka on 2008-05-11
I highly doubt that it has been used too many times since I only bought it about a month or so ago and I have rarely used it. I don't care about losing any data on it since I didn't have anything important on it.Niteshifter, I'll that a try tomorrow when I have time. Thanks for the replies.

---

### Post by tprzepiorka on 2008-05-13
So I tried out the first command and it didn't work under gParted again. The second command it said that it didn't exist. The third one froze my computer. I'm not sure what else to try.

---

### Post by niteshifter on 2008-05-15
Hi,

Froze on the third (a straight-up dd write zeros)? That's not a good sign, I think the device has failed on you. One of those three has always brought back a scrambled USB flash drive for me.

---

