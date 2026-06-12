---
title: "boot problem with Ubuntu 11.04 (Dualbooted with windows7)"
date: 2011-09-18
forum: New to Ubuntu
---

### Post by hahnbrad25 on 2011-09-18
Hello, I just currently installed Ubuntu 11.04 alongside windows 7 following a guide from LinuxBSDos.com. I am absolutely new to Linux so any help would be appreciated. I gave it 4 different partitions as /boot, root directory, swap, and /home. I placed Grub 2 into the /boot partition. I also used easyBCD but it says both Ubuntu and Windows 7 is on the boot menu, but every restart it goes directly to windows. I cannot access Ubuntu at all. I saw a forum on here and followed and instructions and got the boot info summary so if someone could please help that would be greatly appreciated.

Thanks, Brad





============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048     3,074,047     3,072,000  27 Hidden NTFS (Recovery Environment)
/dev/sda2           3,074,048   771,971,071   768,897,024   7 NTFS / exFAT / HPFS
/dev/sda3         771,973,118   976,771,071   204,797,954   5 Extended
/dev/sda5         771,973,120   772,474,879       501,760  83 Linux
/dev/sda6         772,476,928   776,380,415     3,903,488  82 Linux swap / Solaris
/dev/sda7         776,382,464   795,912,191    19,529,728  83 Linux
/dev/sda8         795,914,240   976,771,071   180,856,832  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        C0EE3569EE3558BC                       ntfs       System
/dev/sda2        C6245BA0245B9273                       ntfs       TI105835W0M
/dev/sda5        8a7cae9c-fb08-471d-ac25-9e7a6fd4c7fb   ext2       
/dev/sda6        51e99d9d-9420-4884-a691-16f8b3df91cb   swap       
/dev/sda7        0aceb7a6-875f-408d-ae9a-96e6dcbf4beb   ext4       
/dev/sda8        58eb0a0f-e42f-461d-ae11-59a69e1d1784   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda2        /tmp/BootInfo0/sda2      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

/home/ubuntu/Desktop/boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")

---

### Post by staticd on 2011-09-19
Looks like some thing on windows overwrote grub in the MBR with the default windows boot loader.
The Master boot record or MBR is the first code that executes when a  comp boots. Its supposed to either load an OS directly( Win boot loader)  or give you a menu (the menu in the boot partition in the case of  grub).

The culprit is probably an antivirus software or the DELL data safe  recovery software.(many viruses sneakily hide in the MBR, so grub was  mistaken)

To confirm that this is the problem could you:
1)boot from a live CD
2)mount your boot partiton (I think its /dev/sda5) from the nautilus side pane. confirm that it has the /grub directory in it. get the path of the mount point by pressing Ctrl+L . It will most probably be 
"/media/8a7cae9c-fb08-471d-ac25-9e7a6fd4c7fb"
3) run ```

sudo grub-install --boot-directory=/media/8a7cae9c-fb08-471d-ac25-9e7a6fd4c7fb /dev/sda

```
where the "/media/8a...." is the mount point of your boot partition.

when you restart, you should get the grub menu. If it is a problem with some windows software, as long as you dont boot into windows, the problem wont reappear( kind of poointless having a menu) and when you boot into windows, from the ne boot you will not get the menu again.

I'll look around and post a link to the forum thread that gives the list of windows softwre that may give trouble and what to do about them.

---

### Post by hahnbrad25 on 2011-09-19
Ok thanks alot. I did it and I got the grub loader page and it works. I went to both windows and ubuntu and they both work. But I was wondering is there anyway I could use the windows boot loader instead and grub. Or do I have to use grub to get the boot menu?

---

### Post by staticd on 2011-09-19
Does the menu vanish every time you Boot windows? If so you could try disabling boot sector scans in your anti virus/ dell /hp protect sofware before installing grub and then re-enabling them.( they usually detect changes in the mbr when they are acive)

I'll look up and see if there is a way to chain load grub from the windows boot loader.

---

### Post by hahnbrad25 on 2011-09-19
Well, I have a toshiba satellite A665 and avg anti virus. But I booted windows and restarted and I was still able to boot up unbuntu. So it's working but I was just wondering if I could use the windows boot loader instead of grub. It doesnt really matter the windows boot loader is just a little neater and not so cluttered.

---

### Post by staticd on 2011-09-19
OK got it:
Check out [http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)
Under the "windows 7 boot loader menu" section.
 You should use[B] "dd if=dev/sda" instead of /dev/sda3.
If you get an option to boot linux under the windows boot menu, you could restore the win MBR with
[/B]a windows rescue disc. and have it load linux.
check out: [http://ubuntuforums.org/showpost.php?p=10397479&postcount=6](http://ubuntuforums.org/showpost.php?p=10397479&postcount=6)

I dont have windows myself so Im not sure of the exact details. Good luck!

---

### Post by hahnbrad25 on 2011-09-19
I put in my repair cd and fixed the mbr and all. But now everytime I restart my computer stops at windows boot screen but all that is there is windows 7. I did not move the windows boot file because I dont know how to do so. Any thoughts?

---

### Post by hahnbrad25 on 2011-09-19
Ok, i got it. I used EasyBCD and got it to work. But when I click on ubuntu it takes me to grub then takes me to the right desktop. Is there anyway I can set it up to where I just click ubuntu on the windows bootloader and get it to boot straight for there or will it always have two steps

---

### Post by staticd on 2011-09-20
Check your /boot/grub.cfg file.
and set the search for "timeout" and set timeout=0.
Good luck!

---

### Post by sadaruwan12 on 2011-09-20
You can use a GUI tool like Grub Customizer the installation steps are listed below.

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

---

### Post by hahnbrad25 on 2011-09-23
It won't let me edit grub.cfg. How can I edit it and where do I change the setup. I saw the timeout but again it wouldn't let me edit.

---

