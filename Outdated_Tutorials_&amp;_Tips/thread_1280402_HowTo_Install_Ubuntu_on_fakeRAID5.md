---
title: "HowTo: Install Ubuntu on fakeRAID5"
date: 2009-10-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Keldek on 2009-10-02
I posted this guide over on the [LinuxMint forums]("http://forums.linuxmint.com/viewtopic.php?f=42&t=33694&p=194480#p194480") (yes, I'm cjhmdm) but figure I'd post it here too since LM is based off Ubuntu. Assume this guide is for 9.04 (Jaunty), but it should work for any of the newest releases.

Ok, so after a few hours of working this out, I've finally managed to install Linux Mint on a softRAID 5 setup. Here's how I got this ship sailing...
This is a step by step guide from start to finish, so everything you need to do should be here.
Much credit goes to my good friend Tonyric for helping with this whole mess. Thanks Tony!

Here's what my system looks like to give you an idea of how this will go:
MSI K9A2 Platinum mobo (4 working onboard sata controllers. 6 total but 2 use the promise t3 chip in which I haven't been able to get drivers compiled for without fragging my kernel, so I disabled those 2 via bios)
4GB RAM
3x 250GB hdds - /dev/sda, /dev/sdb, /dev/sdc
1x 256MB usb drive
Linux Mint 7 i386 (this should also work for X86_64)

NOTE: the usb drive is required for our grub and /boot partition as we can't install them to the raid devices. You can use an internal disk if you'd like. USB works better for me.

For my setup, here's the pertinent BIOS settings:
SATA mode set to AHCI
Boot Order: CDROM > 256M USB

Please note, I have my 3rd boot option disabled at the time of this writing as I will use that to boot from my windoze hdd if I install it again later.

Moving on smartly... boot up into the live cd and open a terminal.
Due to my dislike for constantly typing sudo, I set a root password and su to root. Assume ALL commands from this point on to be run as root.

Install the necessary tools for our install
```
# apt-get update
# apt-get install mdadm lvm2
```

Next, prep our hdds for raid
WARNING: This will erase ALL data from these 3 drives!

```

# dd if=/dev/zero of=/dev/sda bs=512 count=1
# dd if=/dev/zero of=/dev/sdb bs=512 count=1
# dd if=/dev/zero of=/dev/sdc bs=512 count=1

```

Now, this isn't actually necessary, I just find it easier than going through the whole fdisk process.

Next up, we create a physical volume for each hdd:
```

# pvcreate /dev/sda /dev/sdb /dev/sdc

```

We're using the entire disk here, not partitions per disk. If pvcreate fails, reboot into the live cd again, 'apt-get update' and 'apt-get install lvm2 mdadm' again, then run pvcreate again. No need to run the dd line again.

Ok, now we have our Physical Volumes created on /dev/sda /dev/sdb /dev/sdc... 

Time to create our raid array:
```

# mdadm --create /dev/md0 --chunk=128 --level=5 --raid-devices=3 /dev/sda /dev/sdb /dev/sdc

```

You'll get a message letting you know the array has been started... Next:
```

# watch cat /proc/mdstat

```
And go watch a movie or something while the array syncs. For my setup, sync time took approximately 70 minutes. Your mileage may vary.

Ok, back from our coffee break, snack, movie and whatever else we did...

Time to create our Volume Group:
```

# vgcreate -s 64M vg0 /dev/md0

```

And then our Logical Volumes:
```

# lvcreate -L 6G -n lvswap vg0
# lvcreate -L 20G -n lvroot vg0
# lvcreate --extent 100%FREE -n lvhome vg0

```

Ok, so far so good, let's format our newly created LVs:
```

# mkfs -t ext3 -m 1 -v /dev/vg0/lvroot
# mkfs -t ext3 -m 1 -v /dev/vg0/lvhome
# mkswap /dev/vg0/lvswap

```

And mount them to make sure everything is ok:
```

# mkdir /mnt/lvroot
# mkdir /mnt/lvhome
# mount -t ext3 /dev/vg0/lvroot /mnt/lvroot
# mount -t ext3 /dev/vg0/lvhome /mnt/lvhome
# df -h

```
df -h output will show you the size of lvroot and lvhome. Just making sure they're the expected size. Ok, let's dismount them now:
```

# umount /dev/vg0/lvroot
# umount/dev/vg0/lvhome

```

Alrighty, now our RAID 5 is set up and ready to roll. Let's set up our usb drive now...
First, let's get the necessary info for our usb drive:
```

# fdisk -l 

```
In my case, the usb is /dev/sdg
Let's partition it and format it. ALL data will be lost!:
```

# fdisk /dev/sdg

```
Then:
```

  p {enter} (print our current partition layout if any)
  d {enter} (delete any existing partitions)
  <partition number> {enter}
  {repeat as necessary}
  n {enter} (create new partition)
  p {enter} (for primary)
  1 {enter} (partition #1)
  {enter} {enter} {enter}
  p {enter} (print partition table again, all is well)
  w {enter} (write our changes to disk)

```

Now, let's format the empty partition on the usb:
```

mkfs -t ext3 -v /dev/sdg1

```

Ok, now that's all set...

Time to launch our installer...

Choose your language, time zone and keyboard layout. Then wait for the partitioner to come up...
Select 'Specify partitions manually (advanced)' and click Forward
On the next screen you should see something like the following:

```

/dev/mapper/vg0-lvhome
  /dev/mapper/vg0-lvhome  ext3
/dev/mapper/vg0-lvroot
  /dev/mapper/vg0-lvroot ext3
/dev/mapper/vg0-lvswap
  /dev/mapper/vg0-lvswap swap
/dev/md0
/dev/sda
/dev/sdb
/dev/sdc
/dev/sdg
  /dev/sdg1 ext3

```
NOTE: I left /dev/sdd /dev/sde and /dev/sdf out of the above to keep it simple. Your layout may look slightly different depending on how many hdds you have and whatnot.

Ok, so we have our layout in front of us, this should be pretty straight forward...

set /dev/vg0/lvroot to use as ext3 and mount on /
set /dev/vg0/lvhome to use as ext3 and mount on /home
/dev/vg0/lvswap shouldn't need to be touched (just make sure it's set to use as swap)
/dev/sdg1 to use as ext3 and mount on /boot

No need to format anything above as we've already done this. Once everything is done, click Forward. When prompted about not formatting, click continue...
Fill in your user info, click Forward

We should now be on the 'Ready to install' screen. You can leave the grub settings alone, we'll fix it later.

Click Install and wait for it to complete. DO NOT reboot after completion as we're not done yet...
The install will take around 20 minutes or so, so go have a smoke, grab a cup of coffee or whatever and wait for it to finish.
Once finished, click 'Continue Testing' to close the installer, and go back to your terminal (we're still root here)...

First, we'll mount our LVs so we can make some necessary changes:
```

# mkdir /target
# mount -t ext3 /dev/vg0/lvroot /target
# mount -t ext3 /dev/vg0/lvhome /target/home
# mount -t ext3 /dev/sdg1 /target/boot

```

Next, we mount some other necessary things:
```

# mount --bind /dev /target/dev
# mount -t proc proc /target/proc
# mount -t sysfs sysfs /target/sys
# mount -t devpts devpts /target/dev/pts

```

And then we copy over some needed files:
```

# cp /etc/apt/sources.list /target/etc/apt
# cp /etc/resolv.conf /target/etc

```

And now we chroot ourselves into our mounted install so we can go tweak some stuff:
```

# chroot /target

```

Now let's install the necessary tools:
```

# apt-get update
# apt-get install lvm2 mdadm

```
Then we check to make sure everything is working:
```

# cat /proc/mdstat
# vgscan
# lvscan

```
Each of the above should output the array, volume group and logical volumes we created above, respectively...

Next we create a startup script that will allow degraded arrays to start ([credit](https://help.ubuntu.com/community/Installation/SoftwareRAID?action=fullsearch&context=180&value=Convert+to+software+raid&titlesearch=Titles)):
```

# vi /etc/initramfs-tools/scripts/local-top/mdadm

```

And paste the following into the new file:
```

# The following code was added to allow degraded RAID arrays to start
if [ ! -e "${ROOT}" ] || ! /lib/udev/vol_id "${ROOT}" >/dev/null 2>&1; then
# Try mdadm and allow degraded arrays to start in case a drive has failed
log_begin_msg "Attempting to start RAID arrays and allow degraded arrays"
/sbin/mdadm --examine --scan | /sbin/mdadm --assemble --scan
log_end_msg
# If you use logical volume on raid partition, is better wait some seconds or the boot will fail!
sleep 10
fi

```
Save and close the script, then update initramfs:
```

update-initramfs -u

```


On to grub, you may have noticed that grub didn't complain during the actual install, but it won't work as it is, so let's fix grub and make our system actually bootable...
```

# grub {enter}
grub> device (hd0) /dev/sdg {enter}
grub> root hd(0,0) {enter}
grub> setup hd(0) {enter}
grub> quit {enter}
# update-grub

```
And then we update our menu.lst:
```

vi /boot/grub/menu.lst

```

find
```

## default grub root device

```

and make sure groot reads as follows:
```

# groot=(hd0,0)

```

Then we go to the end of the file where our boot list is shown and make sure all instances of 'root' are set to hd(0,0), for example:
```

## ## End Default Options ##

title           Linux Mint 7 Gloria, kernel 2.6.28-11-generic
root            (hd0,0)
kernel          /vmlinuz-2.6.28-11-generic root=/dev/mapper/vg0-lvroot ro quiet splash
initrd          /initrd.img-2.6.28-11-generic

```

Finally, save and close the file.

Now, we also need to do 2 more things (if you're NOT using a usb thumb drive for grub & boot then you can skip these next 2 steps):
```

# vi /etc/modules

```
And add 'usb-storage' under 'lp'... so it should look like this:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
usb-storage

```
Save and close the modules file... then we need to edit our mount setings for the usb drive in fstab:
```

vi /etc/fstab

```
Now, you'll notice everything is listed by uuid, this caused me some problems on first boot, so we'll not use the uuid. Your fstab file should look similar to this:
```

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/mapper/vg0-lvroot during installation
/dev/mapper/vg0-lvroot /               ext3    relatime,errors=remount-ro 0       1
#UUID=8bf54327-b4ed-4b09-99a4-e8157412da44 /               ext3    relatime,errors=remount-ro 0       1

# /boot was on /dev/sdg1 during installation
/dev/sdg1 /boot           ext3    relatime        0       0
#UUID=1ee97fa0-be87-4ecf-8acc-537e8c8fb3c7 /boot           ext3    relatime        0       2

# /home was on /dev/mapper/vg0-lvhome during installation
/dev/mapper/vg0-lvhome /home           ext3    relatime        0       2
#UUID=83d37225-93c4-440f-a601-9f1ba7f3e78d /home           ext3    relatime        0       2

# swap was on /dev/mapper/vg0-lvswap during installation
/dev/mapper/vg0-lvswap none            swap    sw              0       0
#UUID=592eb38d-3863-46fb-b586-0242a19fbf31 none            swap    sw              0       0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

And finally, we need to change our /dev/sdg line from:
```

/dev/sdg1 /boot           ext3    relatime        0       2

```
to
```

/dev/sdg1 /boot           ext3    relatime        0       0

```
Save and close the file...

And now, time to reboot. If all went well you should now be booting into your new Linux Mint install :)

---

