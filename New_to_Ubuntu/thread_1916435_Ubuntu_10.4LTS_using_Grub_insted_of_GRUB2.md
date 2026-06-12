---
title: "Ubuntu 10.4LTS using Grub insted of GRUB2?"
date: 2012-01-28
forum: New to Ubuntu
---

### Post by maureenc on 2012-01-28
Hi,
I've been running 10.4LTS for about 3 years and all was fine until January 2011.

After an automatic software update which contained a Kernel upgrade I was asked to reboot. When I did that I had the following message:
 **      Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)  **

Switching off and rebooting Ubuntu loaded OK.

The same occurred at the next Kernel upgrades and recently I have had to boot three times to get it working.

I have checked my hardware and all is OK.

After loads of reading on forums etc I have now learnt that I should be booting from Grub2..... This is not installed on my machine.... I upgraded from an older version, so maybe that is why?

I have years of setup changes and data etc which I don't want to have to reload.... 

If I install GRUB2, will I find myself even deeper in the brown stuff?

Any advice would be much appreciated.... Thank you

---

### Post by Rubi1200 on 2012-01-28
The best thing to do in this situation is to post the results of the boot info script so we can get a better overview of what is happening.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by maureenc on 2012-01-28
Thank you for your response Rubi1200.... I will do that over the next few days when I have printed the instructions off and fully understand them.

But that won't explain why there is no trace of GRUB2 will it?

There is definitely no GRUB.CFG  or anything related to GRUB2 anywhere on my system.

GRUB1 is definitely booting with the FAT_ STAGE1_5 and MENU.1ST

UBUNTU 10.4LTS should be using GRUB2 shouldn't it?

Thanks, Mo

---

### Post by Rubi1200 on 2012-01-29
You are right; versions of Ubuntu after 9.10 used GRUB2.

Interesting situation then ;-)

Posting the boot info script results might help us narrow down the problem.

---

### Post by Cheesemill on 2012-01-29
If you upgraded from a version prior to 9.10 then Grub won't have been upgraded, this is the expected behaviour.

You would only have Grub2 if you have done a fresh install of 9.10 or later.

More info here:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by drs305 on 2012-01-29
If you want to replace Grub with Grub2, here is a link on purging and reinstalling. It is very safe as long as you don't lose your Internet connection part-way through.

[HOWTO: Purge and Reinstall Grub 2 from the Live CD]("http://ubuntuforums.org/showthread.php?t=1581099")

If you accomplish it from a running Ubuntu, you don't need a LiveCD or to chroot. Just run steps 2 through 5, adding 'sudo' to the start of the commands since you won't be in a 'chroot' environment.

---

### Post by maureenc on 2012-01-30
Hi all, and thank you all for the helpful comments.

As far as I remember I did an install rather than an upgrade but had 8.04 loaded originally.... At that time this was the "recommended" procedure so I did it as instructed on the Ubuntu site.

I wonder if something changed with one of the Kernels in the way that it "sees" the Hard Drive? Although it is the only HDD installed at the moment, it is in the 2nd slot because there was another 40G drive which was running WIndows which crashed after a Trojan.

I removed that HDD as I was unsure of the insides of my Desktop at that time and didn't want it causing any problems with my original Ubuntu 8.04 install.

I still have that drive and plan to try to resurrect it this week using a USB to IDE device.

As already mentioned in my original post, there was no problem running this way for about 2 years until one specific Kernel update (I didn't note which one) started this sequence of events. 

I have just run the Info Script and the results are below:

I note that is says that Grub is looking at Stage 2? Would this be normal?
```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub Legacy (v0.97) is installed in the MBR of /dev/sda and looks on the 
    same drive in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/menu.lst /etc/fstab

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders, total 78125000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63    74,830,769    74,830,707  83 Linux
/dev/sda2          74,830,770    78,124,094     3,293,325   5 Extended
/dev/sda5          74,830,833    78,124,094     3,293,262  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        233265fc-be7a-4791-9e4c-4d2c59c5fe4f   ext3       
/dev/sda5        42a0accf-bebd-4c9a-8366-c0c174f81927   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext3       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

--------------------------------------------------------------------------------
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
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

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

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-34-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-34-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-34-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-34-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-34-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro  single
initrd        /boot/initrd.img-2.6.32-34-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-33-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-33-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-33-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-33-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro  single
initrd        /boot/initrd.img-2.6.32-33-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-30-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-30-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-30-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-30-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro  single
initrd        /boot/initrd.img-2.6.32-30-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-29-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-29-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-29-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-29-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-29-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro  single
initrd        /boot/initrd.img-2.6.32-29-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-28-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-28-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-28-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-28-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro  single
initrd        /boot/initrd.img-2.6.32-28-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-27-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-27-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-27-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-27-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro  single
initrd        /boot/initrd.img-2.6.32-27-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro quiet splash 
initrd        /boot/initrd.img-2.6.32-26-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.32-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.32-26-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro  single
initrd        /boot/initrd.img-2.6.32-26-generic

title        Ubuntu 10.04.3 LTS, kernel 2.6.24-26-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro quiet splash 
initrd        /boot/initrd.img-2.6.24-26-generic
quiet

title        Ubuntu 10.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.24-26-generic root=UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f ro  single
initrd        /boot/initrd.img-2.6.24-26-generic

title        Ubuntu 10.04.3 LTS, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=233265fc-be7a-4791-9e4c-4d2c59c5fe4f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=42a0accf-bebd-4c9a-8366-c0c174f81927 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  23.554728985 = 25.291697664   boot/grub/menu.lst                             1
  23.586074352 = 25.325354496   boot/grub/stage2                               2
  23.624099255 = 25.366183424   boot/initrd.img-2.6.24-26-generic              3
  23.510768414 = 25.244495360   boot/initrd.img-2.6.32-26-generic              5
  23.599494457 = 25.339764224   boot/initrd.img-2.6.32-27-generic              4
  23.605189800 = 25.345879552   boot/initrd.img-2.6.32-28-generic              5
  23.546470165 = 25.282829824   boot/initrd.img-2.6.32-29-generic              3
  23.630660534 = 25.373228544   boot/initrd.img-2.6.32-30-generic              5
  23.636764050 = 25.379782144   boot/initrd.img-2.6.32-33-generic              6
  23.546782970 = 25.283165696   boot/initrd.img-2.6.32-34-generic              5
  23.612643719 = 25.353883136   boot/vmlinuz-2.6.24-26-generic                 2
  23.589683056 = 25.329229312   boot/vmlinuz-2.6.32-26-generic                 3
  23.520884991 = 25.255357952   boot/vmlinuz-2.6.32-27-generic                 2
  23.574134350 = 25.312534016   boot/vmlinuz-2.6.32-28-generic                 2
  23.523131847 = 25.257770496   boot/vmlinuz-2.6.32-29-generic                 4
  23.613105297 = 25.354378752   boot/vmlinuz-2.6.32-30-generic                 5
  23.581927776 = 25.320902144   boot/vmlinuz-2.6.32-33-generic                 2
  23.558497906 = 25.295744512   boot/vmlinuz-2.6.32-34-generic                 2
  23.546782970 = 25.283165696   initrd.img                                     5
  23.636764050 = 25.379782144   initrd.img.old                                 6
  23.558497906 = 25.295744512   vmlinuz                                        2
  23.581927776 = 25.320902144   vmlinuz.old                                    2
```
Once again, thank you.
Mo

---

### Post by drs305 on 2012-01-30
> **maureenc said:**
> 

I have just run the Info Script and the results are below:

I note that is says that Grub is looking at Stage 2? Would this be normal?

Yes, that is quite normal.

You are using Grub legacy with no traces of Grub 2. While I'd recommend upgrading to Grub 2, your Grub files look like they should be working.

Although upgrading to G2 won't hurt, I'm not sure it will help with this specific issue either. Although removing drives is an area to look at, it appears your Grub files correctly identify the drive by device name and UUID.

One thing you might try is updating the initrd images. If you can boot to the recovery mode prompt it would be fairly simple. Otherwise, you would need to boot a 10.04 LiveCD and 'chroot' into your sda1 partition.

The command to run from the root prompt would be:
```
update-initramfs -uk all
```
This would update the initrd images of all kernels. If you are more conservative, you might want to try running the command only on one kernel - I'd use the second kernel. Just make sure to boot the second kernel after attempting the repair.
```
update-initramfs -uk 2.6.32-33-generic
```

If you had to chroot from the LiveCD, you would boot to the Desktop, open a terminal, mount /dev/sda1, copy files, chroot into sda1 and then run the same command. I wrote chroot instructions in another thread which you can access via the 'chroot' link in my signature line. Just accomplish the procedures through Step 2 to chroot. The remaining steps would install Grub 2 but you can run only through Step 2 and then run the command above if you wish.

---

### Post by maureenc on 2012-02-01
Thank you very much for your help DRS305, RUBI1200 and CHEESEMILL.... Much appreciated and, hopefully solved!

I installed GRUB2 and have now rebooted the machine 4 times without an error.... Hope I haven't spoken too soon.

Boot is much faster now.... Although I currently have a black screen with flashing cursor at bootup.... A quick glimpse of the Ubuntu screen and then straight into the Desktop.... I will have a look at the Splash Screen config when I have some more time and energy!

I learnt a lot, how to use the terminal.... Change to Root.... How to get into my machine BIOS with a USB Keyboard (luckily there was an old Dell monster laying around) and generally a whole lot more about Ubuntu and Linux.... A very good learning session.

OH already thinks I'm a nerd.... 

Will be posting a few more threads over the coming weeks as I want to make some changes and boot up an old HDD with the latest 10.4 at some point.... But, meanwhile, could I please just ask how I can get into my User CP to edit my profile? Each time I try to do something there (apart from Password and E-mail changes) I get the following:


vBulletin Message                                                           **maureenc**, you do not have permission to access this page. This could be due to one of several reasons:
  
[LIST=1]
[*]Your user account has less than 50 posts.
[*]Your user account may not have sufficient privileges to  access this page. Are you trying to edit someone else's post, access  administrative features or some other privileged system?
[*]If you are trying to post, the administrator may have disabled your account, or it may be awaiting activation.
[/LIST]
Once again, many thanks for your kindness and help... Will mark this as SOLVED when I figure out how...

Cheers all,
Mo

---

### Post by arubislander on 2012-02-01
Hi Mo,

It seems that the first reason listed might be the one that is preventing you from performing the changes you want.

---

### Post by maureenc on 2012-02-01
Hi Arubislander.... But why? I've never been on a forum where I can't add/change an Avatar or anything else within my own profile..... I could be old and grey before I get a chance to, if that is the case!

Also.... It doesn't show me any of my threads or any I have subscribed to... It says none exist....But you are living proof that they do....

Maybe I really don't exist..... Scary

---

### Post by drs305 on 2012-02-01
The 50 post limitation is an attempt to get a handle on spammers. The staff recognizes it is not a perfect solution but users with less than 50 posts can still post and receive unrestricted support. In special cases the administrators can make changes requested via the Resolution Center.

You should be able to mark the thread SOLVED via the 'Thread Tools' link at the top right of the original post.

Happy Ubuntu-ing !

---

### Post by maureenc on 2012-02-02
Thank you DRS305...... Will just have to get on and post the rest of my queries ASAP then...

Cheers,
Mo

---

