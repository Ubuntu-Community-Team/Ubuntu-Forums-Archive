---
title: "Ubuntu not booting after successful installation"
date: 2013-06-10
forum: New to Ubuntu
---

### Post by Draymothisk on 2013-06-10
I've been going through many forms and different pages, but I can't find a suitable answer to my specific problem. I've wiped Windows 7 clear of my laptop, successfully installed Ubuntu 13.04, and run it in it's trial mode a few times, but I can't get it to boot automatically without the disk OR figure out how to use Ubuntu without the trial mode; I'm guessing that occurs after it boots successfully. I've changed my boot order to boot from the hard-drive first, but it just flashes an underscore at the top left corner, waiting to find an OS I assume. Any help? The specs on the laptop are fine and can run it, so I don't know why it won't boot.

---

### Post by ohnonot on 2013-06-10
afaiu, you wiped your hard drive but did not actually install ubuntu.

so booting from your hard drive will not work.

boot again from usb/cd and this time chose to install ubuntu!

if your hardware is very new, there might be some UEFI trouble; but there's no harm in trying.

also i recommend to use the ubuntu 12.04 LTS (meaning long term support). it's more stable and beginner friendly.

---

### Post by oldfred on 2013-06-10
It also could be video issue if you did install. With only one system, you do not get grub menu by default. If you hold shift key from BIOS do you get a grub menu?
Then you can try recovery mode or add nomodeset to linux line in grub boot stanza.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Graphics Resolution- Upgrade /Blank Screen after reboot  mega thread -  MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

What video card/chip do you have?

---

### Post by ohnonot on 2013-06-12
draymothisk, i'm still wondering what this trial mode is?
if you mean the big "try ubuntu" button - i'm not sure if it says "...without installing", but that's what it means.

---

### Post by VMC on 2013-06-12
You can use the "Try mode", then when ubuntu boots up, there should be a Install icon on the desktop. Double-clicking that will install Ubuntu to your hard drive.

---

