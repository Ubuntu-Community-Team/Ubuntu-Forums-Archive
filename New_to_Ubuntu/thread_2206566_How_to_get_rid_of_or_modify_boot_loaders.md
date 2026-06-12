---
title: "How to get rid of or modify boot loaders?"
date: 2014-02-19
forum: New to Ubuntu
---

### Post by jteichma on 2014-02-19
Hi, I'm pretty new to using Ubuntu so apologies in advance for the nievity, however I did read other posts and haven't found a solution yet.

My problem and sequence of steps that created with questions below (and may angels in heaven bless you for reading this long post and responding with your help!):

[LIST]
[*]2 hard drives A, B
[*]Installed Win8.1 on one. Great!
[*]Attempted to run Ubuntu from a USB  stick which failed (because it was an ISO apparently), but not before it installed a boot loader which didn't really point to a valid instance of Ubuntu anyway (lets call it C, don't know if it was installed by windows or Ubuntu, looks like Windows)
[*]I finally burned a proper DVD with Ubuntu 13.10 and went to install it.
[*]Since the install option warned that it would erase all of my target drive (and didn't let me pick which drive), I opted for the "safer" approach and selected Something Else
[*]I read about the partitions required and partitioned my other empty SSD w/3 partitions as I read on the Ubuntu site to work with UEFI (small partition) and Ubuntu (basically swap and linux format)
[*]It said "important" pick where the boot loader should go - and I picked the same drive.
[*]Install went swimmingly or so it seemed and the best part was my Win 8.1 installation was unscathed.
[*]When I rebooted I was in a new boot loader (let's call this D) which gave as an option the pointer to the other Boot loader C and to run Ubuntu, etc.
[*]I clicked Ubuntu but the system failed initialize and fell back to shell as it couldn't find all the files it needed, so I apparently muffed the custom install.
[*]Now I am in a state where I get to a boot loader that points to a failed install of ubuntu or to another boot loader that points to a non-existing Ubuntu instance or Win8 (which thankfully is in-tact)
[/LIST]


Questions:
- How do I remove or modify or remove these boot loaders from each environment without wrecking my current Win8 install (remember I'm beginner)?
- How do I reinstall Ubuntu 13.10 on my SSD in the simplest fashion (e.g., would I have got an option in the install screen to pick a drive after warning me it was going to completely overwrite my drive)?

Sincere thanks for sharing your expertise and helping me get back to a successful and elegant dual boot platform.  :P

---

### Post by fdrake on 2014-02-21
first of all when you boot into ubuntu what is the error msg that you get.
second: at thhe boot menu select "recover" > root > and then type this command at the termina/console:
```
fdisk -l
```

if the menu doesn't have this option tell us what are the options.

---

### Post by jteichma on 2014-02-22
Thanks fdrake.  I'll take a look.  I'm not sure how the forum works and didn't know you replied.  I'll post that information shortly.  Thanks for the help.

---

### Post by jteichma on 2014-02-22
My grub menu doesn't have a "recover" option, only Ubuntu, Advanced Options for Ubuntu (different start options which I tried but don't work either), memtest, and Win8 Loader.

The message I get when Ubuntu fails to load is:

Gave up waiting for root device.  Common problems:
  - Boot args (cat /proc/cmdline)
	- check rootdelay (did the system wait long enough)  <<I think it did>>
	- Check root=(did the system wait for the right device <<I have no idea>>
  Missing modules (cat /proc/modules; ls /dev
ALERT! /dev/disk/by-uuid/d00baeae-ca20-4e56-95cd-f4352daf6a08 does not exist.
Dropping to shell!

BusyBox v1.20.2...

Thanks in advance for the help.

---

### Post by jteichma on 2014-02-23
I re-intalled the AMD64 bit version of ubuntu (recommended by Vladlennin5000) and the boot loader failed after the reinstall and reboot.  It went to the grub command line saying:

/boot/grub/i-386-pc/normal.mod not found.

So I guess re-installing Grub didn't clear its previous settings (as the i-386 version isn't on my system any more.

So then I ran boot-repair as instructed in [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and ran the standard options but that didn't help.  Grub still wouldn't run.

Then I restarted ubuntu in "Try it" mode and ran Boot Repair again and set the loader to Windows using advanced settings. Now I can at least directly boot to Windows (which is good because I was completely locked out before).

 Here is my result log from b: [https://paste.ubuntu.com/6980509](https://paste.ubuntu.com/6980509) if anyone can troubleshoot with that additional info.

All that remains are 2 problems:

- how to edit Grub so I can remove that bum entry.  
- try running ubuntu again once I can and see if it is still complaining it "can't find root"

Thanks.

---

### Post by fdrake on 2014-02-23
try the following:
boot with a live cd and open the terminal, run these commands
```
sudo mount /dev/sdg6 /mnt
sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
grub-install /dev/sdg
grub-install --recheck /dev/sdg
update-grub
exit && sudo umount /mnt/dev && sudo umount /mnt/dev/pts && sudo umount /mnt/proc && sudo umount /mnt/sys && sudo umount /mnt

```
reboot!
good luck!

---

### Post by jteichma on 2014-02-23
Thanks Fdrake.  I'll give that a try!

---

### Post by oldfred on 2014-02-23
You may have had the older verison of grub in MBR of sdg. fdrake's chroot & reinstall should work then.

Is sdg an external drive?
Some older BIOS will not boot from beyond 137GB and similar issues occur with USB external drives. Solution then is to make sure all of Ubuntu's boot files, grub & kernels are inside the first 100GB. Either /boot partition or a smaller / (root) partition with the rest of the drive as /home or data. 
You may need to shrink Windows using Windows tools and reboot Windows so it can run chkdsk and make whatever fixes it needs. 

If a newer system be sure not to boot in UEFI mode. Both Windows & Ubuntu are installed in BIOS boot mode.

---

### Post by jteichma on 2014-02-23
Hi oldfred,

SDG is a 160 GB intel SSD (internal drive).  The board and bios are new (bought them a couple week ago) Gigabyte Ultra Durable has the Intel 8 series chipset and EFI or Bios options.

I ran Fdrakes commands and they ran with no issues but I'm not sure if they work for two reasons:

1) I ran boot-repair before and changed the advance setting to point to the Windows boot loader so I could at least access one operating system.  That worked, but now the PC goes right to Windows on boot so I don't get to the grub bootloader.
2) Even when I start Ubuntu from the CD I get this message shortly after the bios shows on the screen - error: variable "root" isn't set.  Seems that this has been the heart of the problem that my many installs have failed as I've seen it a lot.

So, I can run boot-repair again and switch the loader back to Grub and hope that it works now but because of (2) above, I'm skeptical.  

Thanks. for your help.  I really appreciate it.

---

### Post by jteichma on 2014-02-23
Hi oldfred,

SDG is a 160 GB intel SSD (internal drive).  The board and bios are new (bought them a couple week ago) Gigabyte Ultra Durable has the Intel 8 series chipset and EFI or Bios options.

I ran Fdrakes commands and they ran with no issues but I'm not sure if they work for two reasons:

1) I ran boot-repair before and changed the advance setting to point to the Windows boot loader so I could at least access one operating system.  That worked, but now the PC goes right to Windows on boot so I don't get to the grub bootloader.
2) Even when I start Ubuntu from the CD I get this message shortly after the bios shows on the screen - error: variable "root" isn't set.  Seems that this has been the heart of the problem that my many installs have failed as I've seen it a lot.

So, I can run boot-repair again and switch the loader back to Grub and hope that it works now but because of (2) above, I'm skeptical.  

Thanks. for your help.  I really appreciate it.

---

### Post by fdrake on 2014-02-23
[COLOR="#FF0000"]-----------------------------------------------------------------------edit: not correct info see post below ----------------------------------------------------------------------------------------------------------
your windows partition has a boot flag. 
boot again from the live cd and run gparted. follow this instructions to get rid of the boot flag (in your case is/dev/sdg1 ; uncheck the boot flag )
make sure that the ubuntu partition hase the boot flag on (/dev/sdg6) 
[http://askubuntu.com/questions/58034/how-do-i-fix-grub-so-that-it-shows-up-during-boot](http://askubuntu.com/questions/58034/how-do-i-fix-grub-so-that-it-shows-up-during-boot)
-----------------------------------------------------------------------------------------------------------------------------------------------------[/COLOR]

---

### Post by oldfred on 2014-02-23
@fdrake
Grub does not use boot flag. Windows (and Lilo) use boot flag as they add more boot code into the PBR or partition boot sector and a Windows type boot loader (lilo, or syslinux also) jump to the PBR with the boot flag. The Windows boot loader will only jump to a primary partition, although the Windows like boot loaders do not check if primary.
       Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

    
Generally you want to leave boot flag on Windows NTFS primary partition. That is also the partition Windows will try to repair or install into. If boot flag is not on that partition then repair or install may not work.

---

### Post by fdrake on 2014-02-23
thanks oldfred. did not know that...

---

