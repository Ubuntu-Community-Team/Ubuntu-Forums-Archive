---
title: "GRUB doesn't work anymore, laptop can't load."
date: 2015-01-13
forum: New to Ubuntu
---

### Post by domenico6 on 2015-01-13
Hi everybody,
I'm facing a very annoiyng problem with my laptop that has a  dual boot system with Windows 7 and Ubuntu 12.04.  Since I don't know why the GRUB bootloader stopped to work and the  laptop can't load. I'm very worried about this because I'm  working on my thesis with this laptop and I can't access my work in the  while. :cry:
I'm posting also the report URL made with Boot-Repair>[http://paste.ubuntu.com/9734513/](http://paste.ubuntu.com/9734513/)
  
I will appreciate so much suggestions for solving this problem...

  
Thank you in advance.

---

### Post by yancek on 2015-01-13
At the bottom of the boot repair script, it tells you: 

> 64bits detected. Please use this software in a 64bits session. (Please use Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)) which contains a 64bits-compatible version of this software.) This will enable this feature.

I'm not familar with boot repair but that would indicate to me you are using the wrong version of boot repair, 32bit rather than 64 bit so download and burn the correct one and use it.
I don't see anything really weird in the output although you have windows boot files on three different partitions which I would not expect.  Do you have multiple windows installs?

You have Grub in the master boot record pointing to the core.img file on sda6 and it is there so I'm not sure what the problem is.  Were any changes made just prior to this happening and how old is this laptop?

---

### Post by domenico6 on 2015-01-13
-For the 1st question: No, I have one Windows install on two partitions, as it was the laptop originally. Then I installed the dual boot with Ubuntu.
-For the 2nd question: The laptop is a Samsung RF511 with more than 3 years. During the last access to the GRUB I made a mistake selecting the recovery partition while I would have run Windows ( recovery partition is the last option of the GRUB menu, under Windows), but then I closed the recovery system and restarted the laptop without doing anything more.

Thank you for your prompt answer!

---

### Post by yancek on 2015-01-13
>  During the last access to the GRUB I made a mistake selecting the recovery partition while I would have run Windows

I would not expect that to create problems but maybe it started the Recovery process.  That would explain not being able to boot Grub.  Take a look at the site below which explains some methods for reinstalling Grub from your Ubuntu CD/flash drive.

[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by oldfred on 2015-01-14
Were you copying files with Linux. Linux is case sensitive so /BOOT is different than /boot. But in Windows they are the same and if you have that it becomes a a major conflict in Windows as it cannot deal with duplicate files.

But you have many duplicate files and folders in several places.
```
   Boot files:        /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD
```
You should only have one bootmgr and one BCD. Does not matter which other than if one of the BCD works and the others do not. Backup first then delete all but one. 
Same in main install.
```
    Boot files:        /Windows/System32/winload.exe 
                       /WINDOWS/system32/winload.exe 
                       /WINDOWS/SYSTEM32/winload.exe 
                       /windows/system32/winload.exe 
                       /Windows/System32/Winload.exe 
                       /WINDOWS/system32/Winload.exe 
                       /WINDOWS/SYSTEM32/Winload.exe 
                       /windows/system32/Winload.exe
```

Backup and delete all but one folder & file.

---

### Post by domenico6 on 2015-01-16
> I'm not familar with boot repair but that would indicate to me you are  using the wrong version of boot repair, 32bit rather than 64 bit so  download and burn the correct one and use it.
Finally I was able to restore the GRUB using Boot-Repair 64 bit and now both Windows and Ubuntu work fine. By the way, now in the GRUB list appears another entry on WIndows: they seem to be two different windows boot on /dev/sda 1 and /dev/sda2. I run Windows from sda1 and I don't know what could happen if I run it from sda2.

Anyway, thank you guys for helping me!

---

### Post by oldfred on 2015-01-16
Windows has a 100MB boot partition. But so many users do not know what it is and delete it. Then you do not have any Windows boot files.

So Boot-Repair backs up the boot files to the main install. You then can boot from either partition and grub2's os-prober finds both and adds them to grub menu.

---

