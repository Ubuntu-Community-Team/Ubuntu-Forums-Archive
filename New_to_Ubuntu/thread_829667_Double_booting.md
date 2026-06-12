---
title: "Double booting"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by liamkincaid25 on 2008-06-15
Greetings once more!
  I am trying to do a dual boot between Ubuntu and fedora. I have been receiving some help but being a newbie takes time to do things and sometimes people trying to help you take long to answer. Yesteday I posted a question here and in a matter of minutes A LOT  of people came to help me  with the right answer. I was amazed by the quickness. So I hope you help me once more.
 I was using Ubuntu and wanted to try Fedora. I thought it was going to be insert the disk let it install and that was it (several years ago I was using Mandrake with Windows that is how it went). I inserted the disk fro Fedora loaded everything and on reboot only Ubuntu shows up. I was told I needed to modify menu.lst. The process has been long and tortuous  I will give you all the info I have asked by other people to provide ( I guess is the same you will need.
 herbert@herbert-desktop:~$ su
Password:
su: Authentication failure
herbert@herbert-desktop:~$


When I go to terminal and type cd/boot/grun and the menu.lst I get the following
herbert@herbert-desktop:/boot/grub$ cat menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
# grub-install(8), grub-floppy(8),
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fcc8c971-4dbd-4800-9b38-9e410eef4bb0 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,5)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-18-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=fcc8c971-4dbd-4800-9b38-9e410eef4bb0 ro quiet splash
initrd /boot/initrd.img-2.6.24-18-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-18-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-18-generic root=UUID=fcc8c971-4dbd-4800-9b38-9e410eef4bb0 ro single
initrd /boot/initrd.img-2.6.24-18-generic

title Ubuntu 8.04, kernel 2.6.24-16-generic
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=fcc8c971-4dbd-4800-9b38-9e410eef4bb0 ro quiet splash
initrd /boot/initrd.img-2.6.24-16-generic
quiet

title Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root (hd0,5)
kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=fcc8c971-4dbd-4800-9b38-9e410eef4bb0 ro single
initrd /boot/initrd.img-2.6.24-16-generic

title Ubuntu 8.04, memtest86+
root (hd0,5)
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title Ubuntu 8.04 (8.04) (on /dev/sda1)
root (hd0,0)
kernel /boot/vmlinuz-2.6.24-16-generic root=/dev/sda1
initrd /boot/initrd.img-2.6.24-16-generic
savedefault
boot

herbert@herbert-desktop:/boot/grub$

 Also was asked for this

herbert@herbert-desktop:~$ sudo su
[sudo] password for herbert:
root@herbert-desktop:/home/herbert# fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cf95b

Device Boot Start End Blocks Id System
/dev/sda1 * 1 350 2811343+ 83 Linux
/dev/sda2 351 4863 36250672+ 5 Extended
/dev/sda5 4659 4863 1646631 82 Linux swap / Solaris
/dev/sda6 351 4475 33133999+ 83 Linux
/dev/sda7 4476 4658 1469916 82 Linux swap / Solaris

Partition table entries are not in disk order

And finally this

herbert@herbert-desktop:~$ sudo su
[sudo] password for herbert:
root@herbert-desktop:/home/herbert# mkdir /mnt/fedora
mkdir: cannot create directory `/mnt/fedora': File exists
root@herbert-desktop:/home/herbert# mount -t ext3 /dev/sda6 /mnt/fedora
root@herbert-desktop:/home/herbert# cd /mnt/fedora/boot/grub/
root@herbert-desktop:/mnt/fedora/boot/grub# ls -l
total 204
-rw-r--r-- 1 root 999 197 2008-06-13 04:04 default
-rw-r--r-- 1 root 999 15 2008-06-13 04:04 device.map
-rw-r--r-- 1 root 999 8056 2008-06-13 04:04 e2fs_stage1_5
-rw-r--r-- 1 root 999 7904 2008-06-13 04:04 fat_stage1_5
-rw-r--r-- 1 root 999 16 2008-06-13 04:04 installed-version
-rw-r--r-- 1 root 999 8608 2008-06-13 04:04 jfs_stage1_5
-rw-r--r-- 1 root root 5099 2008-06-13 05:19 menu.lst
-rw-r--r-- 1 root root 4671 2008-06-13 05:19 menu.lst~
-rw-r--r-- 1 root 999 7324 2008-06-13 04:04 minix_stage1_5
-rw-r--r-- 1 root 999 9632 2008-06-13 04:04 reiserfs_stage1_5
-rw-r--r-- 1 root 999 512 2008-06-13 04:04 stage1
-rw-r--r-- 1 root 999 108356 2008-06-13 04:04 stage2
-rw-r--r-- 1 root 999 9276 2008-06-13 04:04 xfs_stage1_5
root@herbert-desktop:/mnt/fedora/boot/grub# 


 I must apologize for this being that long and if I am providing information not needed. I really do not know what I am doing  (but surely hope to learn...and so far I have)Never thought tha doing a dual boot was going to be this complicated(or maybe the learning curve is too steep for me....at my age that happens  :lolflag: ) . I do not like to be spoonfed  but remember I know almost nothing about linux ubuntu , have been doing just what I have been told Thank you for your help

---

### Post by Rocket2DMn on 2008-06-15
In Ubuntu we don't allow root login by default (for security reasons), so we use sudo from your own username (the original user has sudo privileges by default) - that is not the same as su.  So in Ubuntu, to edit GRUB's menu.lst, you run
```
gksudo gedit /boot/grub/menu.lst
```
for gedit (gksudo = graphical sudo) or
```
sudo nano /boot/grub/menu.lst
```
for a terminal text editor.

Make sure that Fedora did not install its own GRUB which is being used.  If so, you need to edit that one instead.

---

### Post by liamkincaid25 on 2008-06-15
> **Rocket2DMn said:**
> In Ubuntu we don't allow root login by default (for security reasons), so we use sudo from your own username (the original user has sudo privileges by default) - that is not the same as su.  So in Ubuntu, to edit GRUB's menu.lst, you run
```
gksudo gedit /boot/grub/menu.lst
```
for gedit (gksudo = graphical sudo) or
```
sudo nano /boot/grub/menu.lst
```
for a terminal text editor.

Make sure that Fedora did not install its own GRUB which is being used.  If so, you need to edit that one instead.

 Thank you again for your quickness. I am sorry to  tell you , but I do not know how to edit . What I mean is that I do not  know what to write and where.I look at the things I get when I input your commands but I am at a loss. How do I know if fedora installe its own GRUB?

---

### Post by meierfra. on 2008-06-15
> Yesteday I posted a question here and in a matter of minutes A LOT of people came to help me with the right answer. 

I looked at that thread, and the first bunch of people gave you the **wrong** answer. I can see that you enabled the root account.  I **strongly** recommend to disable it:


```
sudo passwd -l root
```

Please use

```
sudo -i   or sudo
```


Using a root password is an unnecessary security risk.

Now to your real question: 

You seem to think that Fedora is on /dev/sda6 . But from the "menu.lst"  and the list of files in /mnt/fedora/boot/grub it  seems to me that /dev/sda6 is actually the Ubuntu partition. 


So do this

```

sudo -i
mount -t ext3 /dev/sda1 /mnt/fedora
cd /mnt/fedora/boot/
ls
cd grub
ls
cat menu.lst

```

and post the output.


Do you know where Fedora installed Grub (the boot loader)?

---

### Post by Rocket2DMn on 2008-06-15
You can check inside Fedora from Ubuntu, so look inside the mount point you said you are using: /mnt/fedora, there is a /boot directory, and you can follow that to /mnt/fedora/boot/grub/menu.lst (you were there before!)
Have a look at that file and see if it shows Ubuntu AND Fedora as boot options - you can compare it to Ubuntu's GRUB menu.lst file.  
If you find that Fedora'a GRUB is being used, you may want to consult the Fedora helpers with their GRUB entries since they may vary a little bit - they are at [http://www.fedoraforum.org/](http://www.fedoraforum.org/)

Otherwise, this is going to get more difficult since we need to know more information about Fedora's install, like the kernel version and kernel image names.  I think you may be using your Fedora GRUB though, since you installed that second.

---

### Post by meierfra. on 2008-06-15
> mnt/fedora/boot/grub/menu.lst (you were there before!)

That was not the fedora grub folder. Fedora uses "grub.conf" and there  is no grub.conf" in that folder. Also according to "menu.lst",   ubuntu is on /dev/sda6.

---

### Post by Rocket2DMn on 2008-06-15
> **meierfra. said:**
> That was not the fedora grub folder. Fedora uses "grub.conf" and there is not "grub.conf" in that folder. Also according to "menu.lst",   ubuntu is on /dev/sda6.

It's been awhile since I worked in Fedora, you may be right.  However, this is getting very confusing.  The menu.lst file that was posted has most of the Ubuntu kernels on (hd0,5) which is of course /dev/sda6, but the Other Operating Systems has (hd0,0) which again, is /dev/sda1 of course.  But why are all of them titled with Ubuntu 8.04?

---

### Post by meierfra. on 2008-06-15
It seems to me that the OP had two Ubuntus installed and Fedora now overwrote  the one on /dev/sda1.


That's why I requested  the information from /dev/sda1, so that we can see what is really going on.

---

### Post by liamkincaid25 on 2008-06-15
> **meierfra. said:**
> I looked at that thread, and the first bunch of people gave you the **wrong** answer. I can see that you enabled the root account.  I **strongly** recommend to disable it:


```
sudo passwd -l root
```

Please use

```
sudo -i   or sudo
```


Using a root password is an unnecessary security risk.

Now to your real question: 

You seem to think that Fedora is on /dev/sda6 . But from the "menu.lst"  and the list of files in /mnt/fedora/boot/grub it  seems to me that /dev/sda6 is actually the Ubuntu partition. 


So do this

```

sudo -i
mount -t ext3 /dev/sda1 /mnt/fedora
cd /mnt/fedora/boot/
ls
cd grub
ls
cat menu.lst

```

and post the output.


Do you know where Fedora installed Grub (the boot loader)?

 This are the results

 herbert@herbert-desktop:~$ sudo -i
root@herbert-desktop:~# mount -t ext3 /dev/sda1 /mnt/fedora
mount: /dev/sda1 already mounted or /mnt/fedora busy
mount: according to mtab, /dev/sda6 is already mounted on /mnt/fedora
root@herbert-desktop:~# cd /mnt/fedora/boot/
root@herbert-desktop:/mnt/fedora/boot# ls
abi-2.6.24-16-generic             memtest86+.bin
config-2.6.24-16-generic          System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak
root@herbert-desktop:/mnt/fedora/boot# cd grub
-bash: cd: grub: No such file or directory
root@herbert-desktop:/mnt/fedora/boot# ls
abi-2.6.24-16-generic             memtest86+.bin
config-2.6.24-16-generic          System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak
root@herbert-desktop:/mnt/fedora/boot# cat menu.lst
cat: menu.lst: No such file or directory
root@herbert-desktop:/mnt/fedora/boot# 


Concerning on where FEDORA installed GRUB I remember telling it NOT to install it on the MBR , The story goes  : I installed Fedora first and told it not to install the GRUB to the MBR (it was working ok this way), then decided to install Ubuntu but in my stupidity told Ubuntu not to install GRUB  to the MBR  when I rebooted was received with the message "error loading OS" needing the pc I decided to install Ubuntu once more this time told to put GRUN in the MBR maybe that will help you (I decide to install Ubuntu instead of Fedora when faced with the no OS problem becaus e Ubuntu is quicker to install Fedora took like forever.)

---

### Post by meierfra. on 2008-06-15
Oops, my mistake. I should have told you to unmount first.

```
sudo -i
umount /mnt/fedora
```

and then try the same instruction again.

---

### Post by meierfra. on 2008-06-15
Actually it looks like you overwrote Fedora then you installed Ubuntu the last time. But I'll wait for your revised output.

---

### Post by liamkincaid25 on 2008-06-15
> **meierfra. said:**
> Oops, my mistake. I should have told you to unmount first.

```
sudo -i
umount /mnt/fedora
```

and then try the same instruction again.
Same result with new instructions

 herbert@herbert-desktop:~$ sudo -i
root@herbert-desktop:~# umount /mnt/fedora
root@herbert-desktop:~# mount -t ext3 /dev/sda1 /mnt/fedora
root@herbert-desktop:~# cd /mnt/fedora/boot/
root@herbert-desktop:/mnt/fedora/boot# ls
abi-2.6.24-16-generic             memtest86+.bin
config-2.6.24-16-generic          System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak
root@herbert-desktop:/mnt/fedora/boot# cd grub
-bash: cd: grub: No such file or directory
root@herbert-desktop:/mnt/fedora/boot# ls
abi-2.6.24-16-generic             memtest86+.bin
config-2.6.24-16-generic          System.map-2.6.24-16-generic
initrd.img-2.6.24-16-generic      vmlinuz-2.6.24-16-generic
initrd.img-2.6.24-16-generic.bak
root@herbert-desktop:/mnt/fedora/boot# cat menu.lst
cat: menu.lst: No such file or directory
root@herbert-desktop:/mnt/fedora/boot#

---

### Post by meierfra. on 2008-06-15
Yes, I actually was pretty sure it would be the same.

So this means you really overwrote Fedora.

I suggest to do this:

Reinstall Fedora. Make sure you install it on /dev/sda1.
As location for the boot loader choose "/dev/sda1".  This will leave the Ubuntu Grub intact.

Add this to the end of the Ubuntu "menu.lst":

title Fedora 
root (hd0,0)
chainloader +1

---

### Post by liamkincaid25 on 2008-06-15
> **meierfra. said:**
> Yes, I actually was pretty sure it would be the same.

So this means you really overwrote Fedora.

I suggest to do this:

Reinstall Fedora. Make sure you install it on /dev/sda1.
As location for the boot loader choose "/dev/sda1".  This will leave the Ubuntu Grub intact.

Add this to the end of the Ubuntu "menu.lst":

title Fedora 
root (hd0,0)
chainloader +1

 Thank you for all your help and patience. I have a few last questions (concerning this matter.....because if I keep using UBUNTU I will be around here a lot)
 1- I installed Ubuntu twice , is there a way to get rid of the first installation which I think is taking space or will it be better to erase the disk and start fresh? (I have nothing important on the hard disk only the OS)
 2- If I install Fedora on top of what I have now , do I add this
   
title Fedora 
root (hd0,0)
chainloader +1[/QUOTE]


 before or after I install Fedora (it may sound stupid and I am sorry for that)
 
Thank you so much , and if it was hard to understand some of the things I wrote, forgive me for that but english is not my main language.
Thank you to all of you

---

### Post by meierfra. on 2008-06-15
> 1- I installed Ubuntu twice , is there a way to get rid of the first installation which I think is taking space or will it be better to erase the disk and start fresh? (I have nothing important on the hard disk only the OS)

If you install Fedora to /dev/sda1, it will automatically erase the first Ubuntu.


> title Fedora
root (hd0,0)
chainloader +1


before or after I install Fedora

Before ( but doesn't matter all that much)

---

### Post by liamkincaid25 on 2008-06-15
Thank you for your help. I decided to start from scratch , erase the disk and install UBUNTU, now that is the only OS in the hard disc. I am going to install FEDORA  to have a dual boot system ( as was my original plan). But with linux nothing seems to be straight forward .I do not know if this questions belong to a FEDORA forum or if it is alright to ask it here (I assume it is because is to do a dual boot).
  When I inserted the FEDORA disc and reached the point where the partitions will be modified I am presente with the following alternatives
 1-Remove all partitions on selected drives and create default layout (I did not use this because I think it will erase Ubuntu)
 2-Remove linux partitions in selected drives and create default layout (I did not use this pne either because I think it will erase Ubuntu too)
 3-Resize existing partitions and create default layout in free space (when  I choose this one I get a message "COULD NOT ALLOCATE REQUESTED PARTITIONS .NOT ENOUGH SPACE TO CREATE /BOOT)
 4-Use free space on selected drives and create default layout(when  I choose this one I get a message "COULD NOT ALLOCATE REQUESTED PARTITIONS .NOT ENOUGH SPACE TO CREATE /BOOT)
5-Create custom layout this take me to a screen that is something like this

Drive/de/sda(38147mb)
 sda1 36538mb

NEW EDIT DELETE RESET RAID LVM

Device             type   format   size (mb)   start    end

hard drives
 /dev/sda
  /dev/sda1        ext3             36538      1       4658

  /dev/sda2        extended          1608     4659     4863
   /dev/sda5       swap              1608     4659     4863    
 

If I try to select let say /dev/sda1 then it start to ask for parameters I barely know about.. I was going to post this as a new thread  but thought it might be wiser to leave it here. Basically I am stuck in the part of disk partitioning. I have been told that it is not important which system is installed first it is possible to do the dual boot. I installed Ubuntu first and the GRUB is in the MBR .If installing FEDORA first and the  Ubuntu I will do it that way , whatever is easier and takes less time. Any further help will be deeply appreciated.

---

### Post by liamkincaid25 on 2008-06-16
Is there a way around this or must I install Fedora first?

---

### Post by meierfra. on 2008-06-17
> I try to select let say /dev/sda1 then it start to ask for parameters I barely know about.. I 


Choose mount point "/"

Click on the format box. Choose format to "ext3"

Leave everything else as it is.


Don't edit any of the other partitions.

---

### Post by liamkincaid25 on 2008-06-18
Double checking. I have just messed the installation so many time that I want to be sure before doing anything.
NEW EDIT DELETE RESET RAID LVM

Device type format size (mb) start end

hard drives
/dev/sda
[COLOR="Red"]/dev/sda1 ext3 36538 1 4658[/COLOR]

/dev/sda2 extended 1608 4659 4863
/dev/sda5 swap 1608 4659 4863 

 According to you I should select /dev/sda1 ext 3 , mark it as a mounting point and the in the format mark format to ext 3? ( I am confused on where  "/" ( when I inserted the fedora disc and reach the partition point  I just selected /dev/sda1 then a window appeared where I was able to select "/" and the the same wondow allowed to format to ext 3 ( which is confusing to me because it is already formatted as ext 3). I am very sorry for so many possibly "stupid" questions. But I just want to be sure that what I think I am doing is the correct thing. Will wait for your answer to continue. Thank you

---

### Post by meierfra. on 2008-06-18
> when I inserted the fedora disc and reach the partition point I just selected /dev/sda1 then a window appeared where I was able to select "/" and the the same wondow allowed to format to ext 3

That is exactly what you need to do.  


> ( which is confusing to me because it is already formatted as ext 3).

Reformating will erase all the old data. So this gets rid of the Ubuntu partition on /dev/sda1

---

### Post by liamkincaid25 on 2008-06-18
> **meierfra. said:**
> That is exactly what you need to do.  




Reformating will erase all the old data. So this gets rid of the Ubuntu partition on /dev/sda1

Did everything as told , some screens appeared which prompted me to make decisions. One was where to put the boot loader (Ubuntu boot loader was on MBR , at other sites I was told that on a dual boot the next boot loader you put it on the partition)
 1- I put the boot loader for fedora on first sector of boot partition /dev/sda1
 2-A small screen set boot loader on fedora /dev/sda1 as default (I tried to change it but the system did not allow it) ( I thought that on reboot fedora was going to be the first system to boot and that is what happened) From my efforst in the past days and what I have read I was expecting Ubuntu to load first and then modify it so that on booting the dual option appears.

 I do not know if the process went south or if now I need to modify Fedora to allow dual boot with Ubuntu ( which of course I do not know how to do )

---

### Post by meierfra. on 2008-06-18
> I do not know if the process went south or if now I need to modify Fedora to allow dual boot with Ubuntu 

Open a terminal in Fedora and post the output 

```
su

fdisk -l
```

This well tell us what is going on. As long as Ubuntu did not get erased, it will be fairly easy to add Ubuntu to the Fedora Grub menu.

---

### Post by liamkincaid25 on 2008-06-18
The command "su" did not do the trick , reported only command not found but when used "sudo -i" the information appeared

 [root@localhost herbert]# sudo -i
[root@localhost ~]# fdisk -l

Disk /dev/sda: 40.0 GB, 40000000000 bytes
255 heads, 63 sectors/track, 4863 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001c61e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4658    37415353+  83  Linux
/dev/sda2            4659        4863     1646662+   5  Extended
/dev/sda5            4659        4863     1646631   82  Linux swap / Solaris
[root@localhost ~]#

 If by any chance the dual boot went south (once more) that means I have only fedora , then could you  guide me on how to install Ubuntu ? ( to tell you the truth I have not had time to familiarize myself with the output of this commands. I want to thank you for taking from your time to help me.

---

### Post by meierfra. on 2008-06-18
Sorry I should have noticed this earlier:
Quote  From Post 1

> dev/sda1 * 1 350 2811343+ 83 Linux
/dev/sda2 351 4863 36250672+ 5 Extended
/dev/sda5 4659 4863 1646631 82 Linux swap / Solaris
/dev/sda6 351 4475 33133999+ 83 Linux
/dev/sda7 4476 4658 1469916 82 Linux swap / Solaris


Quote From Post 16:

> /dev/sda
/dev/sda1 ext3 36538 1 4658

/dev/sda2 extended 1608 4659 4863
/dev/sda5 swap 1608 4659 4863 

So the Ubuntu on /dev/sda6 got erased sometimes before post 16. Did you do that on purpose or did that happen  accidentally while  trying to install Fedora?

Doesn't really matter. Ubuntu is gone.

Is where any particular reason why you want Ubuntu and Fedora?  I suggest to use Fedora for a while, until you get more familiar with Linux, and then add Ubuntu.

---

### Post by liamkincaid25 on 2008-06-18
> **meierfra. said:**
> Sorry I should have noticed this earlier:
Quote  From Post 1



Quote From Post 16:



So the Ubuntu on /dev/sda6 got erased sometimes before post 16. Did you do that on purpose or did that happen  accidentally while  trying to install Fedora?

Doesn't really matter. Ubuntu is gone.

Is where any particular reason why you want Ubuntu and Fedora?  I suggest to use Fedora for a while, until you get more familiar with Linux, and then add Ubuntu.

 No I did not do it . It was done  (I guess) while trying to install Fedora. No particular reason , just have the space in the hard drive and wanted to try  both for comparison without booting from a live cd ( which render the cd useless while you are using it) I guess in linux doing a dual boot system is not as easy ( I have been looking around for the last 2 weeks and all my efforts  has been fruitless) Thank you so much for your time, PATIENCE and kindness.

---

