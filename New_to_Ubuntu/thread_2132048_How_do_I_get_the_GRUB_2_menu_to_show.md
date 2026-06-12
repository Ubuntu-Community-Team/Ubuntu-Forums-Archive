---
title: "How do I get the GRUB 2 menu to show?"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by bwallum on 2013-04-03
32 bit 12.04 Desktop. Tried holding down shift key at end of POST with no luck. Just boots through to Desktop.

How can I get to the GRUB menu please?

---

### Post by JRV on 2013-04-03
Check out this thread, he wants to hide it but you just check instead of unchecking Show Menu:

[http://ubuntuforums.org/showthread.php?t=2130098&p=12577595#post12577595](http://ubuntuforums.org/showthread.php?t=2130098&p=12577595#post12577595)

---

### Post by bwallum on 2013-04-03
Thanks guys. I cannot get to edit a file. I've attached a usb bootable drive to the pc and can boot to Desktop ok. I have tried to copy over home files and intend to re-install the system on the pc's hard drive. However I'm told I don't have permission and running nautilus as sudo doesn't help. I need to get access to copy these files. How do I 'chown' a whole folder and it's subfolders and files?

---

### Post by d0006 on 2013-04-04
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by deadflowr on 2013-04-05
I had this problem on a machine with Ubuntu being the only install on it.

My solution was to open /etc/default/grub
And change the grub-timeout to -1.
This sets it to infinite timeout, so the screen stays on the grub menu until I press enter.

---

