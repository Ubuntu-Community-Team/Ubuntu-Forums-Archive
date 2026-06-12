---
title: "Ubuntu Live on USB doesn't start"
date: 2015-03-21
forum: New to Ubuntu
---

### Post by Erez_Manor on 2015-03-21
Hi,

I'm using Ubuntu Live on USB 8GB. I wanted to have more storage to save private/software data so I follow this tutorial:
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)


now Ubuntu doesn't start. it just start after the bios and that restart loop 

Any idea?

Thanks,
Erez

---

### Post by yancek on 2015-03-21
That method works, done it myself.  How did you unmount and try to make the changes?  Were you using another Linux system or the GParted on a CD/DVD?  Did you have any warnings/error messages in the process?

---

### Post by Erez_Manor on 2015-03-22
Thanks for your response.
Actually, I used the same ubuntu release to create the USB and to run GParted (14.10).
When I tried to fix the MBR I got warning: "ubuntu partition doesn't start on sector 1"
I tried to search the internet but could not solve this.

Here is my workaround in case it will help someone else:
1. copy the casper-rw file from USB root location to safe location (not on the USB)
2. erase/format the USB using USB creator
3. create the startup live USB from scratch
4. copy the casper-rw back to the usb (override the existing) just created

Have fun - it works with all the private data/software installed.

---

