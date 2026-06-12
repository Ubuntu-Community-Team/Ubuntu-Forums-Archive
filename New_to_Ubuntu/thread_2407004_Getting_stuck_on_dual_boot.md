---
title: "Getting stuck on dual boot"
date: 2018-11-28
forum: New to Ubuntu
---

### Post by dantheman187 on 2018-11-28
I've used ubuntu and various distros way back in 2014 and as of yesterday wanted to try dual booting ubuntu 18,04?  on my windows 10 pc to mess around with.  i'm using a live usb but have completely forgotten about the partitioning step ext4 file system and all that jazz.  I have vague memories of doing this a long time ago but have long since forgotten and was unable to find a infographic on the ubuntu webpage to hold my hand through the installation process.

I used a guide from the official ubuntu site to set up a live usb and all that but i got stuck on the partitioning side of things and didn't want to muck things up.  If you guys could point me to a resource for this that would be great.

---

### Post by Autodave on 2018-11-28
To start, you need to boot into Win10 and defrag the drive. Then use Win10 to resize the Win10 partition so as to leave the required/desired space for Ubuntu.  You will not need to format the unused portion: the installer will do that for you.

---

### Post by CatKiller on 2018-11-28
I've never set up a UEFI dual boot, but the general principle is that you use Windows to fiddle with Windows partitions and Linux to fiddle with Linux partitions.

So use Windows to shrink your existing partitions, leaving some unpartitioned space to install Linux to later. Then run the Ubuntu installer and tell it to use that free space.

---

### Post by oldfred on 2018-11-28
Perhaps too much info in link in my signature.

  
Often while reconfiguring better to have UEFI fast boot off, as that is assuming no system changes.
Be sure to always boot in UEFI mode (if Windows is UEFI).
Often better to turn off UEFI Secure boot, may be called "Windows" or "Other", but if installing Windows 7 it says to use "Other" as Windows 7 does not support UEFI Secure Boot.

With Windows 10, you need to have fast start up off.
Use Windows to shrink the NTFS partition, and reboot so it runs chkdsk.

New versions of Ubuntu now use swap file, so no swap partition needed. You really only need / (root) as ext4 and if UEFI it will use the existing ESP - efi system partition that Windows uses.
Many like to have /home as separate partition or data partitions and then smaller / partition.

---

