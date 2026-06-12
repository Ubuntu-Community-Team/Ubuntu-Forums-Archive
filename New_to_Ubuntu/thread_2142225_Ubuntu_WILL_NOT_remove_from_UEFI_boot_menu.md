---
title: "Ubuntu WILL NOT remove from UEFI boot menu"
date: 2013-05-05
forum: New to Ubuntu
---

### Post by DRatJr on 2013-05-05
I have installed Ubuntu 12.04. It was installed on a created partition, alongside windows 8. I uninstalled Ubuntu, deleted its partition, and merged it back with my C:/ drive. Now, Ubuntu will not remove from the Windows 8 boot menu in UEFI. I have tried booting into a Ubuntu USB and using efibootmgr. I have also tried /FixMbr and /Fixboot. Nothing has helped. I have JUST completely reinstalled windows 8 and it is STILL there. I was informed by Samsung that only they can reinstall UEFI if I send in my laptop. I do not wish to send it in, this is my last resort. So what can I do to remove it from the boot options in UEFI?

---

### Post by squakie on 2013-05-05
I'm not very versed in this at all, but I can tell you what seemed to work for me, but you will lose what you have!  I made the reset to factory defaults DVD's when I first got my laptop, and when I had UEFI messed up on my laptop, I had to restore the entire disk (not just the OS partition) to put everything back.  I don't know if yours works the same or not, but *if* I remember correctly from when I did that, it gave me the option of keeping the things on my OS partition.  This essentially erased my entire disk and then restored back to factory defaults - so the EFI/UEFI partitions, etc., were also reloaded.  

I *think* boot-repair also "fixes" the EFI/UEFI things as well, but I don't know if to that degree.  You may want to research it, as you can run it from a "live" Ubuntu session.

I don't know if that will work for your PC or not, as I have a Dell.  However, perhaps it can give you another idea on where to look.

Best of luck!

---

### Post by MrSteve on 2013-05-05
is this of help ...

[http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/](http://www.redmondpie.com/how-to-fix-windows-8-mbr-master-boot-record/)

---

### Post by DRatJr on 2013-05-05
/fixmbr has not worked. Also, I don't know if the restoring will work. I have already restored OS but Idk if restoring UEFI is possible. Samsung tech support told me I can't install UUEFI on my own, it has to be sent in.

---

### Post by squakie on 2013-05-05
Samsung may be different - unfortunately it seems every vendor has their own way of dealing with UEFI.  As I said, though, for my Dell at least doing a full disk recovery to factory defaults, not just the OS, worked for me.  Ask Samsung what you are supposed to do if your entire hard disk has to be replaced - that should give you an idea.

---

### Post by oldfred on 2013-05-05
I already suggested several things in your other threads. I gather they have not worked.

But we need info. 

From an Ubuntu liveCD post these.

 find /boot/efi -name "*efi"
sudo efibootmgr -v

      
 [http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
# from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it).
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by MrSteve on 2013-05-06
this maybe of better help ...

[http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html](http://www.tomshardware.com/news/win7-windows-7-mbr,10036.html)

you not only need to fix the MBR but the boot INI file 

the above should also work in win 8 ...

---

### Post by oldfred on 2013-05-06
@MrSteve
Windows 8 pre-installed uses UEFI which is a lot different than BIOS mode systems. BIOS uses MBR(msdos) partitioning and BIOS boots from MBR or first sector on a hard drive.

UEFI uses gpt partitioning, and only has a protective MBR with one partition entry to tell old partition tools that drive is used and not to damage it. Otherwise the MBR in UEFI/gpt is not used. UEFI boots from efi partition by looking for efi files to boot. It also remembers those settings in its own UEFI memory on motherboard.

Boot.ini is only from XP, Vista/7 and 8 use a BCD to store Windows boot info. Normally only if EasyBCD is used, then there may be an Ubuntu entry in Windows 8's BCD. If that is the case you can use EasyBCD or Windows bcdEdit program to edit the BCD.

---

### Post by MrSteve on 2013-05-06
i stand corrected 
thanks for the info 

maybe that&#8217;s why i was having trouble getting Ubuntu to work on my mac mini so had to build a new system instead ...

---

