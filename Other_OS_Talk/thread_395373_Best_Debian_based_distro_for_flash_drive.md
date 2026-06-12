---
title: "Best Debian based distro for flash drive?"
date: 2007-03-28
forum: Other OS Talk
---

### Post by miggols99 on 2007-03-28
I have a windows computer at home, but I hate using windows as it's so slow for things like web browsing. I can't install Ubuntu (or any other distro) because no-one else likes them :( . Does anyone know any good Debian based distros based for a flash drive? I would prefer KDE.

---

### Post by igknighted on 2007-03-28
Why not dual boot?  Or spend $10/$15 USD on an old HD from a local computer store.  I got a 10gb drive for $8 the other day for just this purpose.  Then, you install Ubuntu and grub to the new drive.  Now you can leave the boot setup to go straight to the windows drive and bypass grub, or when you want linux hit F8 or whatever key gives you the boot options and pick the other HD, boot grub and then into Ubuntu.  No one else would be any the wiser, and you would be able to use linux when you wanted.

Any distro on a flash drive would (a) rely on the bios being capable of boot from USB, not a given, and (b) would have to be rather minimal unless you had a REALLY large flash drive.  I know it is possible with Ubuntu to run the live CD in conjunction with a flash drive, so you can update programs and settings and have them saved.  But even doing this you still get "live CD speed".

---

### Post by miggols99 on 2007-03-28
How do I dual boot and keep windows as default (so no-one finds out I've install Ubuntu ;)) 

EDIT: I heard things about VMware which lets you run windows in Linux. Can you run Ubuntu in Windows with it?

---

### Post by mips on 2007-03-28
> **miggols99 said:**
> How do I dual boot and keep windows as default (so no-one finds out I've install Ubuntu ;)) 

You can create a grub boot floppy or a boot flash disk that tells it to boot the linux partition on the HD. If the floppy/usb stick is not inserted it wont boot ubuntu and go straight to windows and no one would see it.

> **miggols99 said:**
> 
EDIT: I heard things about VMware which lets you run windows in Linux. Can you run Ubuntu in Windows with it?

Yes you can run ubuntu in a virtual machine like vmware etc. but it wont be as fast as normal and you will have no 3d support.

Another option if you have the money is to get a external firewire/usb hard drive and install ubuntu on there.

---

### Post by igknighted on 2007-03-28
> **miggols99 said:**
> How do I dual boot and keep windows as default (so no-one finds out I've install Ubuntu ;)) 

EDIT: I heard things about VMware which lets you run windows in Linux. Can you run Ubuntu in Windows with it?

You have two options.  I would recommend unplugging your winXP drive during the Ubuntu install.  Then grub will install to the Ubuntu drive.  If you don't want to mess with that, set up the install and on the last step click the link that says grub is being installed to (hd0).  Then change it to (hd1).  Voila.  Grub will install to the secondary (ubuntu) drive.  Then there should be a bios key that you press at boot to select what drive to boot from (if you don't want default).  Or, you could add winXP to the grub menu as default, set the grub menu to hidden and the timeout to like 2 or three seconds.  That way, when you boot you will have to catch it and go to Ubuntu, otherwise the windows users who probably don't watch the boot sequence very closely wont notice the 3 second difference.

VMWare is an option.  On windows I might recommend MS Virtual PC 2004.  Kind of like sticking it to Bill, using his own software to run linux.  It wont be the same tho, so I would stear you towards a dual boot on a separate HD.

---

### Post by miggols99 on 2007-03-29
> You have two options. I would recommend unplugging your winXP drive during the Ubuntu install. Then grub will install to the Ubuntu drive. If you don't want to mess with that, set up the install and on the last step click the link that says grub is being installed to (hd0). Then change it to (hd1). Voila. Grub will install to the secondary (ubuntu) drive. Then there should be a bios key that you press at boot to select what drive to boot from (if you don't want default). Or, you could add winXP to the grub menu as default, set the grub menu to hidden and the timeout to like 2 or three seconds. That way, when you boot you will have to catch it and go to Ubuntu, otherwise the windows users who probably don't watch the boot sequence very closely wont notice the 3 second difference.
Can I do this with one hard drive? I don't think I have room for another one. Also, how do you configure grub?

---

### Post by mips on 2007-03-29
Yes, you can do it with one drive. you have to edit the /boot/grubmenu.lst file

There you can setup what the menu looks like, the default boot os, the time it takes to autoboot the default etc.

You can even edit the ubuntu entry so no sees it, you could use like a ¨.¨ for it

---

### Post by miggols99 on 2007-03-29
Could you go through this step by step? I'm kinda new to grub and linux.

---

### Post by igknighted on 2007-03-29
It is certainly possible to do this on one HD, however be aware that if you wanted to remove it you would need a winXP disk to fix the MBR (master boot record) so XP could boot.  There are hundreds of step-by-step how to's for dual booting all over the forum, I would check them out.  By default Ubuntu should have options to boot either XP or Ubuntu, with Ubuntu the default choice.  To change that, you need to edit (as root/with sudo) the file /boot/grub/menu.lst.  There will be a line somewhere that says "default 0".  0 stands for the first line that says "title".  So scroll down, count the number of lines that say "title" without a # sign in front, including the divider, and subtract one from that number.  Now GRUB should default to windows.  There is also a line that says "timeout 10".  The ten is in seconds, to minimize the grub time change it to 3 or something shorter.  There is also an option for a hidden grub menu.  If you enable this you wont see the menu unless you hit escape during a brief phase it tell you to, otherwise it will boot the default.

---

