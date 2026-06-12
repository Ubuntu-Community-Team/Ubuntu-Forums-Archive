---
title: "Running Ubuntu 14.0.4 From DVD?"
date: 2014-08-05
forum: New to Ubuntu
---

### Post by Daveski17 on 2014-08-05
I have successfully burned the Ubuntu ISO file to DVD on my Belnea O.book (Vista x86). When I run the DVD (I have turned off autorun) I can see the Wubi installer on the local drive. Do I just run that as admin to run Ubuntu off the DVD? I don't wish to dual boot off my hard drive yet.

Thanks, Dave.

[IMG]http://i386.photobucket.com/albums/oo307/Davebucket17/Ubuntu14041LWubiss_zpsdf07644d.jpg[/IMG]

---

### Post by MoebusNet on 2014-08-05
No. The wubi installer is to install Ubuntu as a windows application on your hard drive. If you enable 'autorun', you should be able to boot your PC from the DVD into Ubuntu without affecting your hard drive.

EDIT: This shpuld give you a more complete idea of how to burn & run a Live-CD/DVD/USB session of Ubuntu without changing your hard drive:

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by Mark Phelps on 2014-08-05
When, and if, you DO decide later to dual-boot, do NOT use Wubi to do that.  That has been discontinued and is no longer supported, and while it might work, it's not the best approach to use to install Ubuntu.

---

### Post by ajgreeny on 2014-08-05
As you may have gathered from the previous posts, you need to shutdown your windows completely, not into the semi hybrid-hibernation that some windows OSs use by default, and then restart the computer again with the DVD in the drive and the BIOS set to boot the DVD as first device.

---

### Post by Daveski17 on 2014-08-05
OK, thank you everyone for your replies. I shall have to research this a bit more.

---

