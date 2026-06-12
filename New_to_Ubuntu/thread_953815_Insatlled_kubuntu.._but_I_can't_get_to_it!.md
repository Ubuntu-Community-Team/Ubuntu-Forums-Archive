---
title: "Insatlled kubuntu.. but I can't get to it!"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by highslime on 2008-10-20
Ok, here we go.  I guess I'll explain my set up first, then go into what's going on.

Windows XP Pro x64 - 200gig SATA drive
80gig IDE (master) - just for movies
20gig IDE (slave) - Target Ubuntu installation

The install seems to go fine.  I tell it to put the GRUB on hd0 (default option), and upon reboot I get no boot loader, it just loads straight to Windows.  I try to boot from the 20gig, and I get "error loading operating system".  I'm probably putting GRUB on the wrong drive, as the MBR is on the SATA drive.  I was told by a friend that I need to put it on sda0.  I was also told I'd have to unplug my SATA drive to get the install to stick.  I'm confused, and don't want to unplug stuff if I don't have to.  Any help would be GREATLY appreciated.

---

### Post by dougfractal on 2008-10-20
can you post these outputs

 sudo fdisk -l   # list the partition table


and 

cat /boot/grub/menu.lst


I guess you'll need to use the live CD to do this.  So for the grub menu 
enter the correct partition with nautilus then upload the file.

---

### Post by Ms_Angel_D on 2008-10-20
I'm not positive(but it couldn't hurt to look), but you may need to go into your bios and check your boot order if your not getting any options at all.

---

### Post by highslime on 2008-10-20
edit -- found answer to that question, see below for outputs

---

### Post by highslime on 2008-10-20
> **dougfractal said:**
> can you post these outputs

 sudo fdisk -l   # list the partition table


and 

cat /boot/grub/menu.lst

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0580057f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/hda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xdecbdecb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda2   *           1       10337    78147688+   7  HPFS/NTFS

Disk /dev/hdb: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        2382    19133383+  83  Linux
/dev/hdb2            2383        2491      875542+   5  Extended
/dev/hdb5            2383        2491      875511   82  Linux swap/Solaris

==============================================================

ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory


Those are the outputs of both commands, as instructed.  I did this with the Live CD.

---

### Post by Elfy on 2008-10-20
If the drive is mounte dit's likely on the desktop now as 20Gb drive - open that and then navigate to /boot/grub find menu .lst - open it and post here.

If it's not on the desktop try thes in aterminal - accessories menu

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/hdb1 /mnt/tmp
cat /mnt/tmp/boot/grub/menu.lst
```

---

### Post by highslime on 2008-10-20
> **forestpixie said:**
> If the drive is mounte dit's likely on the desktop now as 20Gb drive - open that and then navigate to /boot/grub find menu .lst - open it and post here.

If it's not on the desktop try thes in aterminal - accessories menu

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/hdb1 /mnt/tmp
cat /mnt/tmp/boot/grub/menu.lst
```
Ok, well keep in mind, I can only do this with a Live CD.  I'll try your instructions and post what comes back.  It's nice that I have net access on a Live CD though, helps tons!

---

### Post by Elfy on 2008-10-20
Indeed it does - get a partedmagic for your partitioning tool and that will get you on firefox as well - and it boots quicker lol

Those commands are for the livecd - it's mounting the ubuntu drive in a folder so you can get at it

---

### Post by highslime on 2008-10-20
Ok here goes:

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/tmp
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb1 /mnt/tmp
ubuntu@ubuntu:~$ cat /mnt/tmp/boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=8f267779-5946-4963-bec8-42a8aeb59298 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

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

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8f267779-5946-4963-bec
8-42a8aeb59298 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8f267779-5946-4963-bec
8-42a8aeb59298 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows XP Professional x64 Edition
root            (hd2,0)
savedefault
makeactive
map             (hd0) (hd2)
map             (hd2) (hd0)
chainloader     +1

```

---

### Post by Elfy on 2008-10-21
Try this from the livecd - it should reinstall grub, if you get errors then I imagine it's to do with sata and ide hdds - if that doesn't work please rerun the commands to get the disk mounted and get the result of the last please

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/hdb1 /mnt/tmp
cat /mnt/tmp/boot/grub/device.map
```

---

### Post by dougfractal on 2008-10-21
> The install seems to go fine. I tell it to put the GRUB on hd0 (default option), 

> /dev/sda1 * 1 24320 195350368+ 7 HPFS/NTFS

> # on /dev/sda1
title           Windows XP Professional x64 Edition
root            (hd2,0)


It look as if you want to do the grub setup to hd2 as this is the windows start drive.

or Use the Bios boot order and change the Hard Drive order, if it lets you.

I noticed that the menu says 7.10,  you might want to use 8.10 as intriped only has 9 day to go before release and is pretty hot right now. And has a very attractive installer.

---

### Post by highslime on 2008-10-21
I'm using 7.10 because at the moment, it's the only Ubuntu cd I have.  My burner died a horrible death after a cd exploded in it while ripping music, and I haven't had the time to go get another one.

And forestpixie, I'll try that in just a moment and get back to you, as well as dougfractal's suggestion.

```

(hd0)   /dev/hda
(hd1)   /dev/hdb
(hd2)   /dev/sda

```

Ok, it looks like hd2 is where I want it to be, as dougfractal said.  I'd found a thread that explained how to install grub manually, maybe I can find that and do it through the console and be good to go... I hope.  I know I can reinstall it and tell it hd2 when I need to, but that'll be a last result.

Rather than make another post, I'll just edit this one! Again, haha.  Anyhow, I used
```

sudo grub
find /boot/grub/stage1

```
It returned that grub was on (hd1,0), so I entered:
```

root (hd1,0)
setup (hd2)

```
I was thinking that'd get grub to my start drive, which is indeed hd2.  Well, apparently it did, but on booting now, I get just
```

GRUB_

```
Is it loading a blank GRUB menu or something?  I have a feeling I've screwed something up here, but I'm not sure.

---

### Post by highslime on 2008-10-21
Ok, I'm at my wit's end.  I ended up up tossing in my Windows cd and fixing the boot record so I can get back into Windows.  I'd reinstalled Ubuntu, and told it to put GRUB on hd2, which is my start drive, and once again I was greeted with GRUB_ upon reboot.  I'm not sure how to go about editing the GRUB menu (if I even need to) so that I get options.  It's like loading a blank one or something, I don't know.  I'm about ready to just give up on it, but then again I'm rather determined to get this to work.

---

### Post by Titan8990 on 2008-10-21
Sometimes by default GRUB does not give a splash screen and you have to hit Esc to see the menu. Although it sounds to me you have more than one instance of GRUB on your computer and it is loading the wrong one.

---

### Post by Elfy on 2008-10-21
Load the livecd again, 

```
sudo mkdir /mnt/tmp
sudo mount -t ext3 /dev/hdb1 /mnt/tmp
ls /mnt/tmp/boot/grub
cat /mnt/tmp/boot/grub/menu.lst
```

If menu list is same as previous don't post it again - otherwise post results of last 2.

Sata and ide can get confused by grub sometimes it seems. There are a few threads about on the same issue - I'll have a look shortly, if you don't.

---

### Post by highslime on 2008-10-21
It's the same as the first time you told me to do it.  

And by the way, I haven't thanked you yet for your help and patience, so Thank You Very Much for the assistance you've given me thus far.  I didn't have this much trouble installing Ubuntu like 2 years ago on a different machine.  This isn't easy, but if it were.. everyone would do it.

---

### Post by highslime on 2008-10-21
double post.. my bad!

---

### Post by highslime on 2008-10-21
> **Titan8990 said:**
> Sometimes by default GRUB does not give a splash screen and you have to hit Esc to see the menu. Although it sounds to me you have more than one instance of GRUB on your computer and it is loading the wrong one.

Just to let you know, ESC didn't work.

---

### Post by Elfy on 2008-10-21
I want this please

ls /mnt/tmp/boot/grub

you'll have to mount it

Edit - if menu.lst is the same then it is not picking up the 8.04 installation - the original said this 

> title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=8f267779-5946-4963-bec
8-42a8aeb59298 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

the install is actually on hd2,0 and should be looking for the newer kernel

---

### Post by highslime on 2008-10-21
```
ubuntu@ubuntu:~$ sudo mkdir /mnt/tmp
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hdb1 /mnt/tmp
ubuntu@ubuntu:~$ ls /mnt/tmp/boot/grub
default        fat_stage1_5       menu.lst           stage1
device.map     installed-version  minix_stage1_5     stage2
e2fs_stage1_5  jfs_stage1_5       reiserfs_stage1_5  xfs_stage1_5

```

---

### Post by highslime on 2008-10-21
> **forestpixie said:**
> I want this please

ls /mnt/tmp/boot/grub

you'll have to mount it

Edit - if menu.lst is the same then it is not picking up the 8.04 installation - the original said this 



the install is actually on hd2,0 and should be looking for the newer kernel

Well, the disc I've installed from is 7.10 64-bit, one that was mailed to me by Canonical.  I'd use a more recent version of Kubuntu (I prefer KDE over gnome, but anyhow), but my burner is dead, so at the moment, this is the only option I have, unless I do a net install, and I'm rather leery of doing that because I don't want to nerf my beloved Windows, lol.

---

### Post by Elfy on 2008-10-21
Which version do you have installed at the moment - if it's still Gutsy try this

```
gksudo gedit /mnt/tmp/boot/grub/menu.lst
```

On the first ubuntu line change 
root (hd1,0) to 
root (hd2,0)

See if it boots with that

---

### Post by highslime on 2008-10-21
Yes, I'm using Gutsy, I haven't been able to get into the install to update or do anything.  
Question though. ```
ubuntu@ubuntu:~$ gksudo gedit /mnt/tmp/boot/grub/menu.lst
The program 'gksudo' is currently not installed.  You can install it by typing:
sudo apt-get install gksu
```
Is what happens when I enter in what you instructed.  I'm on the Live CD, so can I even get packages and install them?

EDIT - Well, it seems I can.  After getting the packages I need, the command you instructed me to type seemed to do nothing, I get another command prompt.  In theory I can edit menu.lst in Kate, which I tried to do, but I don't have write access to it.  Am I doing something wrong?

---

### Post by Elfy on 2008-10-21
sorry dude - thought it was another thread, evn though ti says kubuntu in blue :)

```
kdesu kate /mnt/tmp/boot/grub/menu.lst
```

---

### Post by highslime on 2008-10-21
> **forestpixie said:**
> sorry dude - thought it was another thread, evn though ti says kubuntu in blue :)

```
kdesu kate /mnt/tmp/boot/grub/menu.lst
```

Haha, it's ok.  That command worked, so I'll reboot and update you with progress.

EDIT -  OK, well I still got the GRUB_ when I rebooted, so I went into my BIOS, and in the BIOS, the hard drive order was listed as SATA, 80gig IDE, 20gig IDE.  I swapped the order of the two IDE drives, lo and behold.. I got my precious GRUB menu!  It's not quite done yet though, because when I try and load it, I get an ERROR 22.  I try to load Windows and I get ERROR 22 once again.  I boot into the recovery mode, and when I typed exit at the command prompt I was greeted by Kubuntu!  So something else is screwy now.

---

