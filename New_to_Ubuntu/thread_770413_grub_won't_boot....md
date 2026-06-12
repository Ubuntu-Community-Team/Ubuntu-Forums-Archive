---
title: "grub won't boot..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by ELD on 2008-04-27
I installed the latest heron via livecd and all went went, reboot and windows loads up, not even a choice to load ubuntu?! Where the hecks my boot loader, it told me it was installed :(

---

### Post by Captain panda on 2008-04-27
To get my CD to work, I had to install some assistance program that the CD suggested if ubuntu wasn't coming up during the reboot. Maybe that will do it?

---

### Post by ELD on 2008-04-27
You misread my post, the cd worked fine, GRUB is not loading up at all to boot my ubuntu partition. It is GRUB not loading that is causing this.

---

### Post by mister_pink on 2008-04-27
Have you got more than one physical hard disk? It probably installed it to a different disk to the one your bios tells the computer to load off. 

Look here: [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm) and scroll down to where it says "Reinstall Grub to the MBR", about a third of the way down. You don't need to do all of it, probably down to but not including the bit about editing menu.lst

---

### Post by ELD on 2008-04-27
No i installed it to the same hard disk windows is on just a different partition.

---

### Post by ELD on 2008-04-27
I fixed it, by defualt the ubuntu live cd did not install grub to the master boot part and it made grub look for ubuntu at hda(1,1) when it is it hda(0,1) how annoying. But hey it works now!

---

