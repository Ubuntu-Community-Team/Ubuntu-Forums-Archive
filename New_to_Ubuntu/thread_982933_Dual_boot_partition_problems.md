---
title: "Dual boot partition problems"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by knut100 on 2008-11-15
Hi, after Ubuntu suddenly hated me, I decided to format my disk and install Vista in addition to Ubuntu (couldn't install Vista before because of the primary boot-thingy).

But when I installed Ubuntu after Vista and expected to see the GRUB, Ubuntu was nowhere to be found. I've searched around after answers, but I loose track quite easily...

ANYWAY, here is some code I understand might be useful.


```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa3891dab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       153597465   163830869     5116702+  82  Linux swap / Solaris
/dev/sda2       163830870   205551674    20860402+  83  Linux
/dev/sda3       205553664   312578047    53512192    b  W95 FAT32
/dev/sda4              63   153597464    76798701    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa3891da9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312576704   156288321    7  HPFS/NTFS
```


```
ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 4498745
-rwxrwxrwx 1 root root         24 2006-09-18 21:43 autoexec.bat
-rwxrwxrwx 2 root root         10 2006-09-18 21:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 13:00 Documents and Settings
-rwxrwxrwx 1 root root 2146357248 2008-11-15 11:00 hiberfil.sys
-rwxrwxrwx 1 root root 2460286976 2008-11-15 11:00 pagefile.sys
drwxrwxrwx 1 root root       4096 2008-11-02 17:46 ProgramData
drwxrwxrwx 1 root root       8192 2008-11-02 18:06 Program Files
drwxrwxrwx 1 root root          0 2008-10-29 21:05 $Recycle.Bin
drwxrwxrwx 1 root root      28672 2008-11-15 11:33 System Volume Information
drwxrwxrwx 1 root root       4096 2008-10-29 21:05 Users
drwxrwxrwx 1 root root      24576 2008-11-06 16:29 Windows
```

[SIZE="4"]
**OTHER INFO:**[/SIZE]

**sda3** contains some files I'd rather not delete.
Runs **Ubuntu 8.04**
ACER **ASPIRE 7520G** with **AMD** Turion 64 x2



I'd be **extremely** happy if anyone had a quick solution to this.

---

### Post by bumanie on 2008-11-15
Post the output of > cat /boot/grub/menu.lst

---

### Post by knut100 on 2008-11-15
It doesn't work in Live CD boot

If I didn't make that clear;
I don't know if I can or how to boot Ubuntu at this time. only Live CD and Vista

Thanks for fast reply, hope you continue helping

---

### Post by knut100 on 2008-11-15
I found the menu.lst after mounting the ubuntu partition

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=40ee9f12-41aa-4704-8e3b-62a35185e025 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 8.04, kernel 2.6.24-16-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=40ee9f12-41aa-4704-8e3b-62a35185e025 ro quiet splash
initrd        /boot/initrd.img-2.6.24-16-generic
quiet

title        Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.24-16-generic root=UUID=40ee9f12-41aa-4704-8e3b-62a35185e025 ro single
initrd        /boot/initrd.img-2.6.24-16-generic

title        Ubuntu 8.04, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Windows Vista/Longhorn (loader)
root        (hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1
```

---

### Post by Bartender on 2008-11-15
You installed Vista on the *second* HDD and Ubuntu on the first?

Why would you do that?

What's in sda4?  Looks like you've got two Windows installs.  

I wonder what would happen if you removed sda and booted from sdb?

I'd suggest starting over.  Physically remove sda from the system since it has your personal data on sda3.  Burn a bootable CD from a GParted LiveCD (GPLCD) download, use that bootable CD to wipe sdb clean, format to ntfs, then install Windows to sdb.  

sdb will now be the new sda as far as Linux is concerned.

I suggest formatting to ntfs before popping in your Windows disc because if you leave it as ext3 Windows won't recognize the drive.

Regarding your personal data on sda3, the drive that you disconnected from the PC...

Use a LiveCD to copy your files from sda3 to external storage of some kind.  
Or plug sda back in, and you should be able to view/copy the sda3 files from the Windows environment.  
Or take sda to a friend's house, plug it in to their Windows PC, and back up sda3 files.
Or plug sda into a Linux PC and back up the sda3 files.
Or create a FAT partition on the Windows drive and copy the data there. 

Once you've backed up your personal data, plug that second HDD back into your system, boot from GPLCD, wipe the drive, and either format it to ext3 for an automatic install of Ubuntu or dice it up to your heart's content for a manual install.  That would be the time to create a vfat partition if you want the personal data on the second drive.  Pop in your ubuntu install CD.  Let it place Stage 1 of GRUB to the Windows MBR on sda1.  It'll do this automatically unless you tell it different.

You should end up with Windows on sda, Ubuntu on sdb, and GRUB Stage 1 installed to the Windows MBR.  It sounds like you can readily re-install Windows, so the most important aspect is safely backing up that personal data.

---

### Post by knut100 on 2008-11-15
The weird thing is that Vista is in sda4 and sdb is just files. Somehow it made boot along the way...


AND at this time, I don't have ANY external back-up possibilities. And it a laptop, so taking the HDD out isn't much of an idea, I think

[IMG]http://img372.imageshack.us/img372/441/screenshot2ly5.png[/IMG]

---

### Post by bumanie on 2008-11-15
Sorry about the command, I know it won't work off live cd - a lapse on my part - :oops:. However, as you got the /boot/grub/menu.lst anyway, that's good. What is the fat32 and ntfs on drive sda?

---

### Post by knut100 on 2008-11-15
sda1: SWAP
sda2: Ubuntu 8.04
sda3: Files which I want to keep
sda4: Vista

sdb: somehow boot and filled with my important ****.

Don't ask me how it got arranged this way :P

---

### Post by bumanie on 2008-11-15
Hmm... That makes a difference - I was thinking vista was on /dev/sdb, but as it's on sda, it is clear that the /boot/grub/menu.lst is wrong. From the ubuntu live cd try this in terminal;
> sudo grub> root (hd0,1)> setup (hd0,3)> quitThen restart without the live cd and see what happens - in theory, that should work.

---

### Post by Bartender on 2008-11-15
Oh, sorry, as soon as I saw talk of sda and sdb I just assumed a desktop.  It's relatively simple to remove HDD's from a laptop and jack into a desktop but you're probably wanting a solution that doesn't involve disemboweling your lappy.

Thanks for the picture.  
I'm a piker at the terminal, but I think bumanie gave you instructions that will tell GRUB to boot from sda4.  That should move the bootable flag to sda4.
Interesting that the Vista install is sda4 instead of sda1...

---

### Post by caljohnsmith on 2008-11-15
OK, from your Live CD try:
```
sudo grub
grub> root (hd0,1)
grub> setup (hd0)
grub> quit
```
Next, it would be a good idea to mark one of your partitions on sda as bootable, because some BIOSes will refuse to boot a drive that doesn't have one partition set as bootable:
```
sudo fdisk /dev/sda
```
Press "a", then "4" for the partition, then "w" to write the change, and finally "q" to quit. Then reboot, and hopefully you should get the Grub menu on start up, but selecting one of the OSes might result in a Grub error. See if you at least get the Grub menu though, and we can work from there if you want. :)

---

### Post by caljohnsmith on 2008-11-15
> **bumanie said:**
> ```
setup (hd0,3) 
```
Please don't do this knut100, because it will install Grub to the boot sector of your Windows partition which is not what you want; you won't be able to boot Windows after that. I'm sure it was a small typo on Bumanie's part. :)

---

### Post by knut100 on 2008-11-15
okay, no I'm confused

Give me two minutes :S

---

### Post by knut100 on 2008-11-15
> **caljohnsmith said:**
> Please don't do this knut100, because it will install Grub to the boot sector of your Windows partition which is not what you want; you won't be able to boot Windows after that. I'm sure it was a small typo on Bumanie's part. :)

You're right... I did what bumanie said... I didn't see you reply before it was too late

**NOW WHAT DO I DO?**

Ubuntu works
Vista says: "Windows failed to start. A recent hardware....."

---

### Post by caljohnsmith on 2008-11-15
OK, I see better what is happening now; from your first post, your Vista partition is missing its necessary boot files, which means most likely they are on the other drive in the sdb1 partition. If you are currently able to boot into Vista, that would mean you are booting the sdb drive on start up. If you follow the commands I gave in my previous post, you should be able to boot your sda drive, but most likely you will first need to go into your BIOS and set the sda drive to boot first on start up (instead of sdb). Give that a shot and let me know how it goes, or if you run into problems. :)

EDIT: Also, don't panic about installing Grub to your Vista partition; we can fix that too with a little effort. You'll need your Vista Install CD, or if you don't have that, you can download a Vista Repair CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). But for the moment, see if you can get your sda drive booting OK, and we can work from there.

---

### Post by bumanie on 2008-11-15
Do as caljonsmith suggests - I think I'm too tired - it's nearly 2 a.m here. Think I'll retire for the night.

---

### Post by knut100 on 2008-11-15
> **bumanie said:**
> Do as caljonsmith suggests - I think I'm too tired - it's nearly 2 a.m here. Think I'll retire for the night.

It's nearly 4 p.m. here in Norway. Thanks for your help anyway =)



Vista booted perfectly before I did Bumaine's edits.
Now it's the other way around.

I'll try what you said.

---

### Post by knut100 on 2008-11-15
> **caljohnsmith said:**
> OK, I see better what is happening now; from your first post, your Vista partition is missing its necessary boot files, which means most likely they are on the other drive in the sdb1 partition. If you are currently able to boot into Vista, that would mean you are booting the sdb drive on start up. If you follow the commands I gave in my previous post, you should be able to boot your sda drive, but most likely you will first need to go into your BIOS and set the sda drive to boot first on start up (instead of sdb). Give that a shot and let me know how it goes, or if you run into problems. :)

EDIT: Also, don't panic about installing Grub to your Vista partition; we can fix that too with a little effort. You'll need your Vista Install CD, or if you don't have that, you can download a Vista Repair CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"). But for the moment, see if you can get your sda drive booting OK, and we can work from there.


```
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> root (hd0,1)
root (hd0,1)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,1)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): a
Partition number (1-4): 4

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.

```


Is this right? Should I restart?

---

### Post by caljohnsmith on 2008-11-15
Please post the output of:
```
sudo fdisk -lu
```
And let me check it really quick before you reboot.

---

### Post by knut100 on 2008-11-15
I rebooted, hehe...

Eeh. I'm in Ubuntu now. Let me check fdisk -lu



[B]Only one difference from the first post

sda4 is also boot[/B]

Vista won't boot, I have the CD

---

### Post by Mardoct909 on 2008-11-15
Your problem is with the MBR (Master Boot Record). When you installed Ubuntu, it set up GRUB. When you install Vista, it removed GRUB in favour of its own booting mechanism. Vista doesn't support multiple OSes, so you're left only able to boot Vista.

Unfortunately, it seems that you ran the command to reinstall GRUB incorrectly (Did you run that command with the typo?) which installed GRUB right over Vista's booting mechanism.

My advice? Backup your files, install Vista THEN - Ubuntu always second so GRUB is set up properly - Ubuntu. This will keep everyone's bootloader intact and listed in GRUB's menu.

---

### Post by caljohnsmith on 2008-11-15
So you successfully booted into your Ubuntu install on sda2, is that true? To fix your Vista partition, you'll need to boot your Vista Install/Recovery CD, go to the command line, and do:
```
bootrec /fixboot
```
If for some reason the Vista CD won't let you run that command, then do:
```
diskpart
```
And at the diskpart prompt:
```
list volume
```
And let me know what it says. We can work from there. :)

---

### Post by knut100 on 2008-11-15
I could boot into my Ubuntu BEFORE i did what you asked (after the bumaine-accident). 

Now I'm booting the Vista DVD, will keep you updated

[B]bootrec /fixboot
     the operation completed successfully[/B]

I'm rebooting


...

[B]AND BOOTING INTO VISTA!

NOW IT'S JUST TO CHECK UBUNTU...

which works too![/B]

Thanks a ton for your help. 
I hope it continues to work!

---

### Post by knut100 on 2008-11-15
> **Mardoct909 said:**
> Your problem is with the MBR (Master Boot Record). When you installed Ubuntu, it set up GRUB. When you install Vista, it removed GRUB in favour of its own booting mechanism. Vista doesn't support multiple OSes, so you're left only able to boot Vista.

Unfortunately, it seems that you ran the command to reinstall GRUB incorrectly (Did you run that command with the typo?) which installed GRUB right over Vista's booting mechanism.

My advice? Backup your files, install Vista THEN - Ubuntu always second so GRUB is set up properly - Ubuntu. This will keep everyone's bootloader intact and listed in GRUB's menu.


Before I got in this mess (which is now sorted out, without back-up or format) I DID install Vista THEN Ubuntu.
Somewhere I f-ed it up myself =)

Thanks anyway

---

### Post by caljohnsmith on 2008-11-15
That's great news both Ubuntu and Vista are booting now. I should mention though that your Vista is a bit vulnerable the way it is set up right now, because the Vista boot files are on your data partition sdb1, while the main Vista install is on sda4. You could leave everything the way it is right now if you don't want to mess with it, but it would be a lot more ideal to put the Vista boot files back in the Vista partition and just boot Vista directly from sda4, not sdb1. If you want help doing that, let me know.

---

### Post by knut100 on 2008-11-16
I would like that.
Where do I start? =)

---

### Post by caljohnsmith on 2008-11-16
OK, I think the easiest way is to "hide" your sdb1 partition so that Vista can't see it, and then simply do a "Vista Repair" from your Vista DVD; that should put Vista's boot files back in sda4. But in case the "Vista Repair" option complains or gives errors, let me know. So begin by first hiding your sdb1 partition:
```
sudo grub
grub> hide (hd1,0)
grub> quit
```
Then do the "Vista Repair" from your Vista DVD, and if it goes smoothly without errors, you will need to modify your Grub's menu.lst to boot Windows from sda4 and not sdb1, so do:
```
gksudo gedit /boot/grub/menu.lst
```
And change your current Vista entry to:
```
title Windows Vista 
root (hd0,3)
chainloader +1
```
After that reboot, and see if you can boot Vista from Grub. Once you are sure that works, you can go ahead and unhide your sdb1 partition so you can access it again:
```
sudo grub
grub> unhide (hd1,0)
grub> quit
```
Let me know how it goes or if you run into problems.

---

### Post by knut100 on 2008-11-16
After changing Vista entry and reboot into Vista

[B]BOOTMGR is missing
Press Ctrl+Alt+Del to restart[/B]

---

### Post by caljohnsmith on 2008-11-16
So what happened during the Vista Repair? Did it say it was successful? Please provide as much information as possible if you want help troubleshooting. Also, how about posting:
```
sudo fdisk -lu
```
So I can check that your sdb1 partition is truly hidden.

---

### Post by knut100 on 2008-11-16
I'm sorry.

When I entered Vista Repair, it asked if I wanted to fix an error that it had found. I said "Repair and restart", and it did. So I restarted into Ubuntu, did the Vista entry edit. 

The fdisk -lu said

Device sdb1 is Boot (*) and System Hidden HPFS/NTFS


EDIT:
I think I might know what caused the error (I THINK). I left at USB-stick in the laptop as the repair took place. It's now set as Boot (*)...

Can this have something to do with it?

---

### Post by caljohnsmith on 2008-11-16
OK, since the Vista Repair didn't work, how about doing the following, and please post the entire output:
```
sudo grub
grub> unhide (hd1,0)
grub> quit
sudo mkdir /mnt/sda4 /mnt/sdb1
sudo mount /dev/sda4 /mnt/sda4
sudo mount /dev/sdb1 /mnt/sdb1
sudo cp /mnt/sdb1/bootmgr* /mnt/sda4
sudo cp -r /mnt/sdb1/boot /mnt/sda4
ls -l /mnt/sdb1
ls -l /mnt/sda4
```

---

### Post by knut100 on 2008-11-16
Did you see my edit?

ERROR

```
sudo cp -r /mnt/sdb1/boot /mnt/sda4
cp: cannot start '/mnt/sdb1/boot': No such file or directory
```

---

### Post by caljohnsmith on 2008-11-16
Sounds like your USB stick might now have your Vista boot files. :) For the moment don't worry that your USB is connected, go ahead and proceed with the above commands.

---

### Post by knut100 on 2008-11-16
uuuhm, I disconnected the USB device
And now I got the error above.

Sooo...Should I just try Vista Repair again? 

(I've hidden hd1,0 already... I'm a rebel...:S)

EDIT:
**Vista boots :S**

[B]And Vista Startup Repair couldn't find anything


I've unhidden hd1,0/sdb1 again it stills says that mnt/sdb1/boot doesn't exist. What to do, master?[/B]

```
 sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa3891dab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       153597465   163830869     5116702+  82  Linux swap / Solaris
/dev/sda2       163830870   205551674    20860402+  83  Linux
/dev/sda3       205553664   312578047    53512192    b  W95 FAT32
/dev/sda4   *          63   153597464    76798701    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa3891da9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   312576704   156288321    7  HPFS/NTFS

Disk /dev/sdc: 2044 MB, 2044723200 bytes
2 heads, 63 sectors/track, 31695 cylinders, total 3993600 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00a64e86

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          32     3993599     1996784    6  FAT16
```



```
knut@Knut-PC:~$ ls -l /mnt/sdb1
total 0
knut@Knut-PC:~$ ls -l /mnt/sda4
total 0
```

```
$ sudo cp -r /mnt/sdb1/boot /mnt/sda4
cp: cannot stat `/mnt/sdb1/boot': No such file or directory
```

---

### Post by caljohnsmith on 2008-11-16
Ummm, I don't understand--you say Vista boots now? While you have sdb1 unhidden, how about posting:
```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sdb1
```
Where "-l" is a lowercase L, not a one.

---

### Post by knut100 on 2008-11-16
> **caljohnsmith said:**
> Ummm, I don't understand--you say Vista boots now? While you have sdb1 unhidden, how about posting:
```
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sdb1
```
Where "-l" is a lowercase L, not a one.

While sdb1 is hidden or not?

**Anyway it doesn't work**
```
mkdir: cannot create directory 'mnt/sdb1': File exsists
```

---

### Post by caljohnsmith on 2008-11-16
OK, let's start fresh:
```
sudo umount /dev/sdb1
```
Don't worry if that gives a "not mounted" error, proceed with:
```
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sdb1
```

P.S. sdb1 should be unhidden, and the command is "umount".

---

### Post by knut100 on 2008-11-16
with sdb1 hidden or unhidden? 
and should it say umount or unmount?


```
umount: /dev/sdb1: not mounted
knut@Knut-PC:~$ sudo mount /dev/sdb1 /mnt/sdb1
knut@Knut-PC:~$ ls -l  /mnt/sdb1
total 621
drwxrwxrwx 1 root root   4096 2008-11-02 16:59 ACER
drwxrwxrwx 1 root root   4096 2008-05-09 21:20 ANALOGT FOTOGRAFI
drwxrwxrwx 1 root root   4096 2008-10-14 18:04 BILDER
drwxrwxrwx 1 root root   4096 2008-11-02 14:50 Boot
-rwxrwxrwx 1 root root 443912 2008-11-02 13:59 bootmgr
-rwxrwxrwx 1 root root   8192 2008-10-30 07:54 BOOTSECT.BAK
drwxrwxrwx 1 root root   4096 2008-04-26 19:20 DIGITALT FOTOGRAFI
drwxrwxrwx 1 root root   8192 2008-05-09 21:22 DOKUMENTER
drwxrwxrwx 1 root root      0 2008-09-29 17:18 EDIT
-rwxrwxrwx 1 root root     65 2008-10-01 18:32 lenke.txt
drwxrwxrwx 1 root root 139264 2008-10-14 18:05 LYD
-rwxrwxrwx 1 root root   4265 2008-09-25 18:17 menu.lst
drwxrwxrwx 1 root root      0 2008-10-29 22:05 $RECYCLE.BIN
drwxrwxrwx 1 root root      0 2008-10-29 22:57 System Volume Information
drwxrwxrwx 1 root root   4096 2008-09-29 17:18 web


```

---

### Post by caljohnsmith on 2008-11-16
OK, while sdb1 is still unhidden and mounted, try:
```
sudo mount /dev/sda4 /mnt/sda4
sudo cp /mnt/sdb1/bootmgr /mnt/sda4
sudo cp -r /mnt/sdb1/Boot /mnt/sda4
ls -l /mnt/sda4
```
It's OK if the first command says sda4 is all ready mounted, and please post the output of all the commands.

---

### Post by knut100 on 2008-11-16
```
sudo mount /dev/sda4 /mnt/sda4
sudo cp /mnt/sdb1/bootmgr* /mnt/sda4
sudo cp -r /mnt/sdb1/Boot /mnt/sda4
ls -l /mnt/sda4
total 4499181
-rwxrwxrwx 1 root root         24 2006-09-18 23:43 autoexec.bat
drwxrwxrwx 1 root root       4096 2008-11-16 17:02 Boot
-rwxrwxrwx 1 root root     443912 2008-11-16 17:02 bootmgr
-rwxrwxrwx 2 root root         10 2006-09-18 23:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 14:00 Documents and Settings
-rwxrwxrwx 1 root root 2146353152 2008-11-16 16:49 hiberfil.sys
-rwxrwxrwx 1 root root 2460286976 2008-11-16 16:49 pagefile.sys
drwxrwxrwx 1 root root       4096 2008-11-02 18:46 ProgramData
drwxrwxrwx 1 root root       8192 2008-11-02 19:06 Program Files
drwxrwxrwx 1 root root          0 2008-10-29 22:05 $Recycle.Bin
drwxrwxrwx 1 root root      28672 2008-11-15 12:33 System Volume Information
drwxrwxrwx 1 root root       4096 2008-10-29 22:05 Users
drwxrwxrwx 1 root root      24576 2008-11-06 17:29 Windows
```

---

### Post by caljohnsmith on 2008-11-16
OK that's great, next boot your Vista DVD, go to the command line, and run:
```
diskpart
```
And at the diskpart prompt:
```
list volume
exit
```
Find the drive letter for Vista from the above commands, probably it will be "C", which we will assume in the next commands, so change it if the drive letter is different:
```
bcdedit /store [COLOR="Blue"]C:[/COLOR]\boot\bcd /set {default} osdevice boot
bcdedit /store [COLOR="Blue"]C:[/COLOR]\boot\bcd /set {default} device boot
bcdedit /store [COLOR="Blue"]C:[/COLOR]\boot\bcd /set {bootmgr} device boot
bcdedit /store [COLOR="Blue"]C:[/COLOR]\boot\bcd /set {memdiag} device boot
```
Next reboot, and let me know how far you get when booting Vista from Grub.

P.S. Many thanks to forum member meierfra for providing the above Vista hack.

---

### Post by knut100 on 2008-11-16
I'm in. Vista up and running.
 
Should I post fdisk -l?

sdb1 is boot (*) still.

Should I delete the bootmgr in the sdb1 drive?

---

### Post by caljohnsmith on 2008-11-16
> **knut100 said:**
> I'm in. Vista up and running.
 
Should I post fdisk -l?
You don't need to post fdisk at this point since everything is working; just make sure sdb1 is unhidden and you should be good to go. Cheers and have fun with your OSes. :)

P.S. You can delete the "bootmgr" file and "Boot" directory in your sdb1 partition if you want to since you don't need them there any more.

---

### Post by knut100 on 2008-11-16
> **caljohnsmith said:**
> You don't need to post fdisk at this point since everything is working; just make sure sdb1 is unhidden and you should be good to go. Cheers and have fun with your OSes. :)

Thanks for all your help!

I guess everything is where it should be now.

But I still find bootmgr in all my partitions now...

---

