---
title: "Running Windows XP under QEmu"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by noland on 2008-06-09
Hello! i am trying to run WinXP using QEMU following the tutorial found at this page :

[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)

but when i get to step 7 i get the following message :

noland@noland-laptop:~$ sudo update-modules
[sudo] password for noland: ha ha

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************

QEMU and winxp actually run but not kqemu i figure because of that step. i get this message when i run QEMU

noland@noland-laptop:~$ qemu -hda /home/noland/windows/windows.img -boot c -m 384 -localtime -cdrom /dev/cdrom -smb /home/noland/windows/qemu_share/ -usb -usbdevice tablet
Could not open '/dev/kqemu' - QEMU acceleration layer not activated: No such file or directory

now at the end of the tutorial a person says to have tested it in hardy, so i guess there is a way to make it work... but how?

i have followed all the steps successfully previously in the tutorial... any hints?

thanks in advance,

Phil

---

### Post by noland on 2008-06-09
there is also this page in reference : 

[https://answers.launchpad.net/ubuntu/+question/32078](https://answers.launchpad.net/ubuntu/+question/32078)

i am still a newbie.. any help apreciated!

thx,

Phil

---

