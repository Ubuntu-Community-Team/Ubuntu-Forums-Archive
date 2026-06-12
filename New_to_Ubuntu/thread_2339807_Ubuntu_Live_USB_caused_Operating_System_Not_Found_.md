---
title: "Ubuntu Live USB caused Operating System Not Found error"
date: 2016-10-13
forum: New to Ubuntu
---

### Post by bradykoehler on 2016-10-13
I installed Ubuntu 16.04 LTS on a USB and booted from it.  After doing so, when I shut down the computer and tried to boot back into Windows, I got a no operating system found error.  I tried the repair measures I found when I searched the problem (using lilo and boot-repair), but the same error still occurs.  Here is the output from boot-repair [http://paste2.org/pXd25LvH](http://paste2.org/pXd25LvH).  I can access the windows files from Ubuntu, so the hard drive is still fine.   Any help about how I can get configure it so that it will boot into windows fine again would be appreciated.

---

### Post by mastablasta on 2016-10-13
Live USB does not touch the hard disk. in fact you can uplog the hard disk and boot only form USB if you want.

full install on USB does touch it. specifically you need to install the boot loader on USB manually (direct it manually) in order to avoid this.

you can recover Windows boot loader (MBR) using Windows recovery or repair CD. [SIZE=2][https://support.microsoft.com/en-us/kb/927392](https://support.microsoft.com/en-us/kb/927392)

if you are using 8 or 10 you may go through additional menues to get to console where you can use the tool to repair it.
[/SIZE]

---

