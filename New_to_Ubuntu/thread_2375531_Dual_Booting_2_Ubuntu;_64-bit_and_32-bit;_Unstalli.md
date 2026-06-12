---
title: "Dual Booting 2 Ubuntu; 64-bit and 32-bit; Unstalling Question"
date: 2017-10-25
forum: New to Ubuntu
---

### Post by ikhwan.arif on 2017-10-25
Hello guys, newbie here.

I plan on dual booting 64-bit and 32-bit Ubuntu. I am familiar with partition scheme and I don't expect much problems with this venture. But I want to know if there will be complications should I choose to uninstall one of them. 

For example, I know that with a Windows and Ubuntu dual boot, uninstalling Ubuntu requires a boot repair for windows. Do I need to do the same thing with Linux? Especially if it is the same distros? Or is it as simple as using Gparted to simply delete the second partition and resizing it? 

Thanks for reading. Regards.

---

### Post by Dennis N on 2017-10-25
You don't want to delete the Ubuntu OS that controls (creates) your grub menu. The last Ubuntu installed will control the grub menu, so if you ever want to delete that one, you need to take steps to switch default boot to the other Ubuntu first.

The specific course of action depends on whether you are using UEFI or BIOS on you computer.

Removing the Linux distro that does not control the booting can be done by removing or formating its partition and then updating grub from the remaining Linux.

---

### Post by Andrew_Lucas on 2017-10-26
Whilst what has already been said is true, and you might have to fix GRUB, ultimately it should just be a case of putting something else in that space. Either you could use Gparted (from a live session, not whilst your OS is running) to delete and extend your partitions which will still be in use to fill the extra space, or you could just make a new partition and then configure the system such that that new partition is automatically mounted at boot (you'll have to Google for exactly how to do that, but I've done it in the past and recall it not being complicated, just a case of issuing a few commands). You could then set up sym links (the command for which is 'ls') so that all folders show in the same place, even if they're not on the same disk.

---

