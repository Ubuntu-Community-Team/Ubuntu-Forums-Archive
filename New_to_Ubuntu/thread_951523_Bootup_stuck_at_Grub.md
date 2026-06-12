---
title: "Bootup stuck at Grub"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by uchihaitachi on 2008-10-18
I had a power trip causing an unexpected shutdown of ubuntu.
On my next bootup I'm left at the Grub screen.

Was there any quick remedy to the problem?
Does the fragility my ubuntu has anything to do with it being installed on ntfs?

I've no error message to share as I've since reformatted and in the process of reinstalling.

---

### Post by philinux on 2008-10-18
From the grub menu can you select the recovery mode?

---

### Post by yubrew on 2008-10-18
I am having the same problem.  There is no recovery mode to select.

Also, the following file is not found: "ubuntu/disk/boot/grub/menu.lst"

---

### Post by Duck2006 on 2008-10-18
You can try reinstalling grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by philinux on 2008-10-18
If you've got the livecd try this.
[How to install Grub from a live Ubuntu cd. - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=224351") 

or 

Supergrub which I always keep handy. The download options are on the right of the page.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by yubrew on 2008-10-18
> **Duck2006 said:**
> You can try reinstalling grub.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

I tried installing via this guide. When I enter "find /sbin/init" it returns "File not Found".

Supergrub could not fix/repair the problem.  It returns the following:
Requires: 
normal super grub disk
rescatux
linux live cd
the force, luke

It seems the initializing files are not present, so maybe I need to use live CD to reinstall grub?

---

### Post by kansasnoob on 2008-10-18
> Does the fragility my ubuntu has anything to do with it being installed on ntfs?

Is this a Wubi install? Kind of sounds like it when you say it's installed in NTFS, and if so the answer is yes!

I have read in the past that Wubi installs are susceptible to problems related to power outages.

---

### Post by kansasnoob on 2008-10-18
> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

---

### Post by MunkyJunky on 2008-10-18
> **yubrew said:**
> 
Also, the following file is not found: "ubuntu/disk/boot/grub/menu.lst"

I had that problem a while back. Reinstalling GRUB did nothing. My method to fix it was:

[LIST=1]
[*]Boot up using a Ubuntu Live CD
[*]Open Nautilus as root (Alt+F2, then type 'gksudo nautilus')
[*]Navigate to /boot/grub/
[*]Have a look for menu.lst backup file, called something like menu.lst.backup
[*]Duplicate the backup file, and rename it from menu.lst.backup(2) to menu.lst
[*]Reboot
[/LIST]

---

