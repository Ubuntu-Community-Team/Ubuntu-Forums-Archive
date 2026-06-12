---
title: "Installation Help! :S  :)"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by victorsdmp on 2008-07-01
Hi All,

Is it normal that the burnt iso image of xubuntu 8.04 alternate CD looks like this? (Please see the image) How is it going to be directly bootable if there are neither executables nor any bat files in the extracted image structure? :(

I created it from the file: "xubuntu-8.04-alternate-i386.iso"
Any suggestion? What happened?

Thanks,
Best Regards,

V

---

### Post by wrtpeeps on 2008-07-01
> **victorsdmp said:**
> Hi All,

Is it normal that the burnt iso image of xubuntu 8.04 alternate CD looks like this? (Please see the image) How is it going to be directly bootable if there are neither executables nor any bat files in the extracted image structure? :(

I created it from the file: "xubuntu-8.04-alternate-i386.iso"
Any suggestion? What happened?

Thanks,
Best Regards,

V

That looks correct. .bat files are windows files by the way, be no use on a linux cd. :)

---

### Post by aquavitae on 2008-07-01
exe and bat files are only used on windows systems. Linux executables (in fact all linux files) are identified by their content, not their extension. Most linux executable do not have an extension at all, or if they do then its something arbitary. As for being bootable, even windows does not boot directly from an executable file. The computer looks in the first sector of the first boot device for machine code which tells it how to boot. That code then points it to some sort of bootloader which can be anywhere on the system. On a typical installed linux system it would be under /boot. On windows its a file on the C drive.

The cd looks fine, but you can always check the md5sum of the iso if you're worried. Also, when you boot off the cd it has an option to check the disk for defects and that will pick up any problems.

---

### Post by victorsdmp on 2008-07-01
Thanks to all! I cannot wait to try the thing tonight at home. At last free! Best Regards, V

---

### Post by hyper_ch on 2008-07-01
on top of the first post you have a link "thread tools". Use that to mark this thread as solved and good luck with the installation.

---

