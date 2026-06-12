---
title: "Stuck on 'Loading second stage bootstrap...' after changing hardware"
date: 2012-01-21
forum: New to Ubuntu
---

### Post by jkitzmiller on 2012-01-21
I've been a Mac admin for a while, and just had a few Ubuntu servers dumped in my lap. I know OS X server backwards and forwards in my sleep, but Ubuntu not so much.

We had Ubuntu Server 8.04 installed on a PPC G5 PowerMac, and I pulled the drive out and put it in a G5 Xserve, but the Xserve won't boot. It sees the drive as having a bootable Linux OS, and it tries, but it gets stuck on 'Loading second stage bootstrap...' and then reboots. This loop goes on indefinitely.

Not really sure where to go from here. Any ideas?

---

### Post by Double.J on 2012-01-21
Hi there and welcome to the forums!

hmm it could be as simple as loading up a live cd/usb/reading the drive from anothe linux machine, and editing the yaboot.conf?

Of course it could be a case of reinstalling required - you can use the media involved above to copy any relevant data/settings off for post install.

I'm afraid I havn't tried moving a drive from one PPC mac to another - mine are G4 and G5, so I've allways assumed it wasn't going to happen lol.

All  the best, and best of luck!

---

### Post by jkitzmiller on 2012-01-21
> **gnu/mirow said:**
> Hi there and welcome to the forums!

hmm it could be as simple as loading up a live cd/usb/reading the drive from anothe linux machine, and editing the yaboot.conf?



Could you elaborate a little more? I'm somewhat (read: extremely) clueless when it comes to Linux. Where is yaboot.conf and what exactly am I editing?

---

### Post by Double.J on 2012-01-21
Hi there! 

I do apologise, I should have provided more information!

As I'm sure you're aware, PPC new world macs use Open Firmware instead of PC's BIOS. This means that the grub bootloader that most linux distro's use isn't usable. To boot on PPC macs, the bootloader used by linux is Yaboot. Yaboot.conf is the configuration file that controls booting, both of a single OS (linux) and also allows multibooting OS X.

To edit it if you can't get in, You first need a live environment to work from - this could be a USB, a CD or as I say another linux system that you can read the drive from.

The best way to edit the Yaboot.conf is to "chroot" into the OS you're trying to fix - litterally virtualise that OS, so coomands you enter will take effect on the drive you are trying to fix, not the device you booted from ;)

Once in, use gparted (availaible under system tools on most distros - for ubuntu 11.X open the dash and type gparted, then hit return to open.) to find the partition number of the Linux install root partition. For example /dev/sdb1, /dev/hda1, etc. also note which filesystem it is using - EXT3, EXT4

Use this information to mount the drive. As we'll be chrooting, best to make a new directory. the following commands will do this.
```

sudo mkdir /fix
sudo mount -t ext*[COLOR="Red"]X[/COLOR]* /dev/*[COLOR="Green"]Partition number[/COLOR]* /fix
sudo mount -o bind /dev /fix/dev
sudo mount -o bind /proc /fix/proc
chroot /fix bash

```That should get you in to the virtual system.
[COLOR="red"]X[/COLOR] is thefilestystem number from the partition table. 
[COLOR="Green"]partition number[/COLOR] - well you get the idea ;)

Navigate to /etc/yaboot.conf and make a backup
```

cd /etc/yaboot.conf
cp yaboot.conf yaboot.conf.bak
```

And get into the config with nano
```

sudo nano -w yaboot.conf
```

There are a lot of options, and I wont't pretend to be an expert - I am not when it comes to yaboot.. I shall point you to [this guide]("http://www.debian.org/ports/powerpc/inst/yaboot-howto/ch5.en.html")

N.B. You may also want to have a look at the bootstrap guide in the previous chapter.

For Yaboot specific queries, I suggest starting a new thread in the a[pple users section of the forums]("http://ubuntuforums.org/forumdisplay.php?f=328") as more PPC users will hopefully see it.

If all else fails you can use this CHROOT environment to make changes and run commands on the HDD you are trying to make boot, and the live CD/USB in general to copy data off of the linux formated partitions.

In terms of getting a live CD, it has to be a PPC version. I recommend the 10.04 LTS - desktop and server versions are available [here]("http://cdimage.ubuntu.com/ports/releases/lucid/release/") (server versions aren't live)

To make the image a bootable USB stick, best to use the DD command of either linux or Mac OS X If possible.

To boot a linux live USB in PPC macs - get into openfirmware, find where the USB is, and the command should be something along the lines of
```

boot usb0/disk@1:2,\\yaboot

```

You may have to change the numbers to find the usb ;)

Really hope it helps!

---

### Post by jkitzmiller on 2012-01-21
Ok, so I *think* I found the issue...

```
ubuntu@ubuntu:~$ df -T
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
tmpfs        tmpfs     3012416     19312   2993104   1%
/lib/modules/2.6.24-19-powerpc/volatile
varrun       tmpfs     3012416       108   3012308   1% /var/run
varlock      tmpfs     3012416         0   3012416   0% /var/lock
udev         tmpfs     3012416        40   3012376   1% /dev
devshm       tmpfs     3012416        12   3012404   1% /dev/shm
tmpfs        tmpfs     3012416        16   3012400   1% /tmp
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     3012416     19312   2993104   1% /home/ubuntu/.gvfs
**/dev/sda3 **    ext3   149232632  30380340 111331396  22% /media/disk
```


```
## yaboot.conf generated by the Ubuntu installer
##
## run: "man yaboot.conf" for details. Do not make changes until you have!!
## see also: /usr/share/doc/yaboot/examples for example configurations.
##
## For a dual-boot menu, add one or more of:
## bsd=/dev/hdaX, macos=/dev/hdaY, macosx=/dev/hdaZ

**boot=/dev/sda2**
device=/ht@0,f2000000/pci@9/k2-sata-root@c/k2-sata@0/disk@0:
partition=3
root=/dev/sda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
       label=Linux
       read-only
       initrd=/boot/initrd.img
       append="quiet splash"

image=/boot/vmlinux.old
       label=old
       read-only
       initrd=/boot/initrd.img.old
       append="quiet splash"
```

So I changed the boot=/dev/sda2 to boot=/dev/sda3, but I still have the same issue.

I think I have to run ybin to get the change to work, but that doesn't seem to be working either.

```
# sudo ybin -v
ybin: Finding OpenFirmware device path to `/dev/sda3'...
cat: /proc/device-tree/sep/fans/PS: No such file or directory
cat: Fan: No such file or directory
cat: Control@0/compatible: No such file or directory
Cannot create temp file, aborting.
ybin: An error occured while building first stage loader.  aborting...
```

Any ideas?

---

### Post by lazellama on 2012-01-23
I too have an Xserve G5 and I get the same error. I bought this Xserve without a hard drive with the intention on running ESXi5 on it and that doesn't even boot or get recognized. Although there is talk of ESXi 5 working with it. So I figured I'd try to get a linux going. I think once I get yaboot to work I can force it to read the EFI on the ESXi disk I burned. 

but...I am at the same spot as you... I get the following error when trying to run ybin. If we can get ESXi to run man we'd be set although we might have to put in a raid drive from another distro but that shouldn't a problem then we can run pretty much any OS from ESXi. 

#ybin -v
ybin: Finding OpenFirmware device path to `/dev/sda2'...
cat: /proc/device-tree/sep/fans/PS: No such file or directory
cat: Fan: No such file or directory
cat: Control@0/compatible: No such file or directory

I used mac-fdisk to make my bootstrap partition.

When I run mkofboot -b /dev/sda2

I get:



mkofboot: Create hfs filesystem on /dev/sda2? [y/N] y
Failed to initialize HFS working directories: Read-only file system
mkofboot: HFS filesystem creation failed


If I run ofpath /dev/sda

I get:

cat: /proc/device-tree/sep/fans/PS: No such file or directory
cat: Fan: No such file or directory
cat: Control@0/compatible: No such file or directory
/ht@0,f2000000/pci@7/k2-sata-root@c/k2-sata@2/disk@0:

Here is an interesting note:

[https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=174762](https://bugzilla.redhat.com/show_bug.cgi?format=multiple&id=174762)

I'm gonna try fooling around with that. let me know if ya get anywhere.

[email]lazellama@gmail.com[/email]

-mike

---

