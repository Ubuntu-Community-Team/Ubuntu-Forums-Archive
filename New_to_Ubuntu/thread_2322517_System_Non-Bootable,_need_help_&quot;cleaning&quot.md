---
title: "System Non-Bootable, need help &quot;cleaning&quot; off bad data"
date: 2016-04-28
forum: New to Ubuntu
---

### Post by whereismymindat2 on 2016-04-28
Hello,
Thanks for reading. 

Question. HEre is a copy of "Boot-Repair" info. 
[http://paste.ubuntu.com/16109098/](http://paste.ubuntu.com/16109098/)

1st-When I try to run boot repair (the repair function) it errors out saying it see's a 64-bit machine (I have a 32-bit machine)--thus my guess is I've accidently installed "something" 64-bit (also causing my boot issues?). 
-----FYI---the "Boot Issue" is that It "Locks up" at the Boot Logo Screen. (Paradoxically---the num lock and caps lock keys work--aka not a "total lock out" with Keyboard, etc.). HOWEVER---I try to do a CTRL-ALT-DELETE (REBOOT) --- OR A CTRL-ALT-BACKSPACE (have set up, 
"soft reboot"---will not work, need to "tun off" machine). ????


```


(my setup). 

/dev/sda (is a former "old drive" (that I guess I need to remove the grub/mbr??? It's never caused me "Boot" problems before). 

/dev/sdb (is my Boot Partition (and is /dev partitoned accordingly

/dev sdd (is my USB ("multisystem") BOOT USB


```



(courtesy fyi---when I first saw it I paniced, but the dev part SDD1 (double DD) is the USB Driver I'm booting from (not *******SDB1********* (sdb1--my boot drive). 

```
sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.05 20140113
    Boot sector info:  Syslinux looks at sector 2074990 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the 
                       /boot/syslinux directory. No errors found in the Boot 
                       Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/menu.lst /boot/grub/grub.cfg 
                       /boot/syslinux/syslinux.cfg /EFI/BOOT/grubx64.efi 
                       /sparkylinux1/EFI/BOOT/bootia32.efi 
                       /sparkylinux1/EFI/BOOT/bootx64.efi 
                       /boot/grub/i386-pc/core.img /boot/syslinux/ldlinux.sys

```


#################################


Prior attempts to fix 
(I've booted into recovery mode---for each kernel---and run all the "stuff"---fixes to run...to no avial (dpkg fix, grub fix, clean, fsck, etc.). 

Desired Outcome
"Boot back to my desktop/able to work"  ;-)

###################################


(from Pastebin Link Above---pulled out what I think is valuable (???)

###################################

```

=============================== StdErr Messages: ===============================

cat: write error: Broken pipe
cat: write error: Broken pipe
File descriptor 9 (/proc/23548/mounts) leaked on lvs invocation. Parent PID 8295: bash
File descriptor 63 (pipe:[98818]) leaked on lvs invocation. Parent PID 8295: bash
  No volume groups found

ADDITIONAL INFORMATION :
=================== log of boot-repair 2016-04-28__17h38 ===================
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14
File descriptor 9 (/proc/23548/mounts) leaked on lvs invocation. Parent PID 25132: /bin/sh
No volume groups found
boot-repair is executed in live-session (Boot-Repair-Disk 32bit 29nov2014, trusty, Ubuntu, i686)
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=(loop)/casper/vmlinuz root=UUID=1DFC-792C maybe-ubiquity debian-installer/language=en keyboard-configuration/layoutcode=us iso-scan/filename=/boot-repair-disk-32bit.iso boot=casper file=/cdrom/preseed/ubuntu.seed noprompt quiet splash --
ls: cannot access /dev/sda1: No such file or directory
sda10 (sda) has unknown type. Please report this message to boot.repair@gmail.com

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


```



THE RECCOMENDED FIX FROM BOOT REPAIR (BUT HOW DO I DO THIS????)


```



/boot detected. Please check the options.
/usr detected. Please check the options.
(debug) reinstall grub2 place-in-all-MBRs no-BIOS_boot (sdb1)


=================== Suggested repair
The default repair of the Boot-Repair utility would reinstall the grub2 of sdb1 into the MBRs of all disks (except USB without OS), using the following options:        sdb2/boot, sdb3/usr,
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s


=================== Blockers in case of suggested repair
64bits detected. Please use this software in a 64bits session. (Please use Boot-Repair-Disk-64bit (www.sourceforge.net/p/boot-repair-cd) which contains a 64bits-compatible version of this software.) 

This will enable this feature. GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). 

This can be performed via tools such as Gparted. Then try again.

Alternatively, you can retry after activating the [Separate /boot/efi partition:] option.


=================== Final advice in case of suggested repair
Please do not forget to make your BIOS boot on sdb (1000GB) disk!


=================== User settings
The settings chosen by the user will not act on the boot.

```


[Download as text]("http://paste.ubuntu.com/16109098/plain/")

Again, as a reminder, "Boot Repair" (either "Advanced" Or "Normal User"---won't run the above functions for me, thus need to do by hand, thus the advice. 

thank you!!!

---

### Post by grahammechanical on 2016-04-28
It is possible to run a 32 bit operating system on a 64 bit CPU but not the other way around. It seems that you are using a 32 bit version of the Boot Repair ISO image. It might be better to take the advice of Boot Repair and use a 64 bit version of the Boot Repair ISO image.

Using a 32 bit operating system is not proof that the CPU is not 64 bit. MIcrosoft was installing 32 bit version of Windows on 64 bit CPU machines for a long time. 

Perhaps you could look up the make & model of that machine on the internet and confirm for sure that the CPU is 32 bit.

There is a lot about your set up that I do not understand. Such as why sdb is GPT partitioning but you do not have a bios boot partition. It is possible to use GPT partitioning with a BIOS boot system motherboard. I am using this on one of my 2 drives. But I did think that we needed a bios boot partition.

GPT partitioning is usually found with UEFI boot systems motherboards. In that case there would be an efi boot partition. Your GPT patitioned drive (sdb) has neither type of boot partition. Could that be the problem?

Regards.

---

