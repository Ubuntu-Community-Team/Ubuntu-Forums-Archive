---
title: "Help! My grub isnt showing"
date: 2015-06-02
forum: New to Ubuntu
---

### Post by Giovanni_Leon_ on 2015-06-02
So i dual booted Windows 8.1 and Ubuntu 14.4 (My computer was preinstalled with windows) but whenever i shut down or restart my computer it goes directly to windows boot loader and skips grub2. I can access my ubuntu, but i have to press escape on start up go to boot options and manually pick ubuntu (also there is like 10 instances of Ubuntu there and i have just been picking the top one, is there anything wrong there?). also when i enter ubuntu in boot options it goes to the grub2 menu and from there i can pick either windows 8.1 or ubuntu. I have made a BootInfo Summary for you guys to help with [http://paste.ubuntu.com/11527087/](http://paste.ubuntu.com/11527087/) . It will help a lot if someone could figure this out. Thx

---

### Post by oldfred on 2015-06-02
What brand/model system?

Are you doing something to get Ubuntu reinstalled so many times?
I would start with housecleaning entries. Some UEFI do not like to have NVRAM over 50% full.

 # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Some systems will not directly boot ubuntu entry as they modify UEFI to only boot by description and only description is "Windows" that works. But hard drive entry also works which you also seem to have many duplicates that need housecleaning.

Hard drive boots /EFI/Boot/bootx64.efi, so we back that up or rename it, and copy grub or shim into that folder and rename it to bootx64.efi. Then hard drive entry should boot grub/Ubuntu.
 
If needed specific command line ways to copy grub are in link in my signature.

---

