---
title: "How to run bleeding edge"
date: 2006-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2006-12-10
[size=2][b]How to run bleeding edge
[indent]... And maintain your sanity[/indent][/size][/b]

I like to run on the bleeding edge but as you know this sometimes leads to problems ranging from minor bugs to major problems to total system failure.

To file a bug [Bug reporting](http://ubuntuforums.org/showthread.php?t=284595)

To work around this I suggest running two partitions, might call them stable and testing.

You may partition however you like, but here is an example:

Partition table:> /dev/hda1 = 10 Gb = Stable root partition
/dev/hda2 = 10 Gb = Testing root partition

/dev/hda3 = 1 Gb = swap

/dev/hda4 = the rest = data

I suggest you use a data partition rather then /home

I will use /dev/hda1 as the "master" menu.lst (grub). Alternately you may use a /boot partition.


In addition I use the gparted live CD

You can Download it [here](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

=====================

First download and install Ubuntu 7.04 Feisty Fawn Herd 1:
[Download Feisty](http://cdimage.ubuntu.com/releases/feisty/herd-1/)

Install into /dev/hda1

Update```
sudo aptitude update && sudo aptitude upgrade
```

Go ahead an customize Firefox, install additional packages, or your desktop or what have you.

Do not do anything bleeding edge (like beryl or the latest nVidia beta drivers) yet .... 

=====================

Now go ahead and set up your testing partition.

[list=number][*]Boot to the gparted CD

[*]Format /dev/hda2 if you have not already done so (same format as /dev/hda1)

[*]Now copy partition /dev/hda1 to /dev/hda2

[*]_Note_: When you copy a partition, both partitions will have the SAME UUID
[Indent]To fix this:[list][*]Either revert to referring to partitions as /dev/hdxy (as below)
[*]Or set a new UUID and use the new UUID rather then /dev/hdxy (not shown)
[indent]To set a new UID (ext2/3) : ```
tune2fs -U random <partition_to_set_UUID>
```To list you devices by UUID : ```
blkid
```[/indent][/list][/indent][/list]

When the copy is done we need to do some minor edits:

Open a terminal. In gparted you are root so no need for sudo.
[list=number][*]Edit /boot/grub/menu.lst on **/dev/hda1**

```
cd /tmp
mkdir hda1 hda2
mount /dev/hda1 hda1
mount /dev/hda2 hda1
```

Now:```
nano hda1/boot/grub/menu.lst
```
Edit and add these lines:

In the top of menu.lst you need to edit a few configuration defaults :
 > 
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# **kopt=root=/dev/hda1 ro**

## default grub root device
## e.g. groot=(hd0,0)
# **groot=(hd0,0)**

Make sure the root device is properly identified ;)

> 

title		Feisty STABLE kernel 2.6.19-7-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.19-7-generic root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.19-7-generic
savedefault
boot


title		Feisty TESTING kernel 2.6.19-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.19-7-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.19-7-generic
savedefault
boot

_Note_: Initially you will have your root partition identified by UUID. Example: UUID=fe139e06-121d-4887-b74a-ac2ccc178e3a although you will obviously have a different (unique) number. Change this, as above, to /dev/hda1 (STABLE) and /dev/hda2 (TESTING).

Save and exit nano (Ctrl-X, answer Y).

Copy menu.lst to TESTING:```
cp hda1/boot/grub/menu.lst /hda2/boot/grub/menu.lst
```

_Note_: You will need to manually update the kernel line for your testing partition (/dev/hda2 in this example) after kernel updates. Alternately you can use a boot partition and chainload both the stable and testing partitions. Just be sure to watch those configuration lines in menu.lst :p


[*]Edit /etc/fstab on TESTING **/dev/hda2**
```
nano hda2/etc/fstab
```

Change the root partition to hda2
Change> # /dev/hda1
UUID=fe139e06-121d-4887-b74a-ac2ccc178e3a /  ext3  defaults,errors=remount-ro  0  1

To> # /dev/hda2
/dev/hda2 /  ext3  defaults,errors=remount-ro  0  1

_Note_: Again, your UUID=fe139e06-121d-4887-b74a-ac2ccc178e3a will be a different (unique) number. In this case we need to change to /dev/hda2

Save and exit nano (Ctrl-X, answer Y).[/list]

=====================

Done.

=====================

Now go ahead and boot to /dev/hda2 **Feisty TESTING kernel 2.6.19-7-generic**

Go ahead and install any bleeding edge stuff you like. If it works, use gparted to copy /dev/hda2 to /dev/hda1 as follows:

[list=number][*]Boot the gparted CD

[*]Copy /dev/hda2 to /dev/hda1

[*]Update fstab:

```
cd /tmp
mkdir hda1
mount /dev/hda1 hda1
nano hda1/etc/fstab
```

Change:> # /dev/hda2
/dev/hda2 /  ext3  defaults,errors=remount-ro  0  1

To:> # /dev/hda1
/dev/hda1 /  ext3  defaults,errors=remount-ro  0  1

Save and exit nano (Ctrl-X, answer Y).


[*]Do not forget to update menu.lst:
```
nano /hda1/boot/grub/menu.lst
```

Update your [color=red]kernel information[/color] and [color=blue]initrd.img[/color] for:> title Feisty STABLE kernel 2.6.19-7-generic
root (hd0,0)
kernel **[color=red]/boot/vmlinuz-2.6.19-7-generic[/color]** root=/dev/hda1 ro quiet splash
initrd [color=blue]**/boot/initrd.img-2.6.19-7-generic**[/color]
savedefault
boot

Save and exit nano (Ctrl-X, answer Y).

If you are unsure of your kernel and initrd,```
ls hda1/boot
```Use the set with the highest number....
[/list]

=====================

You should run updates and install new (bleeding edge) software in TESTING.

If, however, you experience total system failure, boot to the gparted CD and copy /dev/hda1 to /dev/hda2 and try again !


Enjoy,

[color=navy]bodhi.[/color][color=darkgray]zazen[/color]

---

