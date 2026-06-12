---
title: "Hard Drive Mapping for a Noob"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by tigerr on 2013-05-07
Hey everyone,

I have used Ubuntu in VMs for a little while, and now I want to install it as my host OS instead of Windows.  I have only ever used one drive in those VMs and the Ubuntu installer seem to put everything where it needs to go in order to work.  However, on my host sytem, I have multiple drives.  I plan to install Ubuntu into one drive, and then use the additional drives for storage (mainly other VMs so they have their own drive to read from).  Kind of like under Windows, I use my C: as host + hypervisor, and have the VMs on Drives E: and F:.

Once I get Ubuntu installed, how do I go about mapping/using/connecting to those drives?  My understanding is it is mounted as a directory somewhere, but I am unsure of how I go about doing that.  (I just realized I should mess around with it in a VM with multiple drives first, but upon thinking I was dumb for not trying, I realized I wouldn't know how to do it anyway.  Edit: OK, I am going to go try anyway, but I'm sure I'll need an answer anyway, haha)

So, if you are so kind, how do I first identify additional drives attached ot the computer, and then how do I mount additional drives in Ubuntu/linux?

Cheers!

---

### Post by alhefner on 2013-05-07
Once you install Ubuntu as the sole operating system, the other drives will mount and you can use them however you like. They'll show up on the left side of the folders window as separate devices.n Linux can also use them easily if they are formatted NTFS instead of EXT4.

It will be how you set up the computer's BIOS that determines your boot order. As always, you can have boot records on all the drives and choose between them during initialization (F12 usually)...

---

### Post by tigerr on 2013-05-07
OK, I messed around with my Ubuntu in VM.  I shut it down, added a drive to the VM, and booted back up.  I did the following:

After finding that Ubuntu recognized this second drive as /dev/sdb, I ran:

sudo fdisk /dev/sdb

I created a partition option n (new partition), option p (primary), and accepted the defaults for first and last sector.  I then wrote the settings with w, and it exited.

Then I "ls" in my /dev and saw a /sdb1, so i saw that a new partition was created, cool!

Next I created a file system on that partition with:

sudo mkfs -t ext3 /dev/sdb1

After creating a mount point /media/seconddrive, I also found how to mount and unmount the drive with:

sudo mount /dev/sdb1 /media/seconddrive
sudo umount /media/seconddrive

Before I unmounted the drive, I tried to write a file to the directory /media/seconddrive, but I did not have permissions. How do I change permisions?

Also, is there a way to automatically mount the drive on bootup?  Thanks!!

---

### Post by mastablasta on 2013-05-08
drives or partition? in Windows partitions are shown as drives.

so if you are really installing ubuntu to a different drive then easiet way is simply unplug windows drive, install ubuntu on different drive using full disk (no rocket science here) then re-attach the disk and do sudo update grub. windows will then appear in boot menu. 

is that what you want to have?

if you want separate partition for data in ubutnu you can create separate /home partition

---

