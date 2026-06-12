---
title: "Slow Copy Speed from PC to Usb pen drive"
date: 2019-10-05
forum: New to Ubuntu
---

### Post by skanth on 2019-10-05
Hello World,
I am a new Ubuntu user. So far i have been enjoying my experience with Ubuntu. And i am seriously considering switching from Windows 10 to Ubuntu 18.04 permanently.
However being new to Linux, i have run into a few problems. One of the issues i am facing is, slow copy speeds from my Ubuntu system to an usb pen drive. The file is copied, but shows zero seconds remaining, and it stays like that for a long time. When i try to safely eject my usb it shows an operation in progress. Kindly advice regarding the same. All help is appreciated.
Thank You

---

### Post by sudodus on 2019-10-05
What you see is that the copy process has copied the content to a buffer in RAM (which is fast), and then **the computer will be busy copying from the buffer to the USB memory cells** (which is slow).

Unmounting or 'ejecting' will wait until the buffer is completely flushed, and the data are safely stored in the USB memory cells. When the unmounting or 'ejecting' finshes successfully, you can safely unplug the drive.

You can also run the command

```

sync

```

to flush the buffers (there may be other data buffered) without unmounting/ejecting.

---

### Post by skanth on 2019-10-05
Wow, thanks for the quick reply. The copy process you mentioned, is it the default behavior in Ubuntu?. Also, can it be configured so that it copies directly on to the pen drive,without an intermediary buffer?.

---

### Post by sudodus on 2019-10-05
Yes, it is the default behaviour in Ubuntu.

I don't know the Ubuntu system well enough to tell if or how it can be configured to copy directly (without a buffer). But I think all modern operating systems use this kind of buffering (also Windows). Long ago with MSDOS (and maybe early versions of Windows) there were systems that did not buffer data on write. I remember when buffering was introduced, and you must wait for the system to flush the buffers before turning off the power.

---

### Post by Autodave on 2019-10-05
Are you using USB 1,2, or 3?  Are you sure that you are plugging it into the correct port?  I actually find copying files to a USB to be a bit quicker in Linux than Win10.

---

### Post by skanth on 2019-10-05
I am using a USB 2 pen drive. I just tried copying files to my external hard drive and the process was fast. Could it be an issue with my pen drive?.

---

### Post by oldfred on 2019-10-05
Also what format is flash drive?
Writing to NTFS is always slower as Microsoft has not directly supported driver. It has to be reversed engineered. 
And huge difference if USB3 port to USB3 flash drive.

---

### Post by skanth on 2019-10-05
Using fat32 on my pen drive.
And yes my external hard drive is a USB3 device.

---

### Post by sudodus on 2019-10-05
See [this link](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed) about the speed of USB pendrives.

---

### Post by TheFu on 2019-10-05
Writing to flash memory inside a USB2 device will always be slow.  It gets slower as the cells are used more and more times/cycles.  Eventually, the cells will fail.  I've had some flash drives last years which were mostly used for reading.  I've also had name brand, USB3 flash drives fail in about 13 months when used for daily video recording.

---

