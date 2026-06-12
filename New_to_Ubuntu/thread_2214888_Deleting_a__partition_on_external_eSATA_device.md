---
title: "Deleting a / partition on external eSATA device"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2014-04-03
I have an external eSATA hard drive. In it is my old /dev/sda drive that booted Ubuntu (12.04 LTS Precise Pangolin). Using GParted, I see three partitions on the drive. Those are: / and /home and swap. Using GParted, I tried to delete the /home and swap and / (boot), and was able to delete /home and swap, but not the / (boot). The / is always reported as "In use" and cannot be modified from within or by GParted.

How do I delete or wipe or format the entire external hard disk drive to recover as much drive space (gigabytes) as possible?

Do I need to be in LiveUSB session to perform the partition deletion?

---

### Post by sudodus on 2014-04-03
The short answer is 'Yes'.

The long answer:

It complained "In use". And / is the current root partition, which is really used. Deleting it is like sawing the branch you are sitting on.

Boot from another drive (for example your Ubuntu install drive) and from there you can run gparted and do 'whatever you like' with this eSATA device, which behaves pretty much like a regular internal SATA device.

---

### Post by Mark_in_Hollywood on 2014-04-03
[ATTACH=CONFIG]251698[/ATTACH]

I'm not booting from it. A new drive is installed at /dev/sda (and sda1 is flagged as / or boot).

I'm trying to control (delete) a / partition on an external device and I'm not booting from that external device. Where you say: "which is really used" is confusing. It is not in use. At the moment, the device is powered down and I'm using the desktop's /dev/sda1 as the "boot" device, or operating system. Have you a reason why GParted sees this as /dev/sdb and will not control that partition?

If I power up the eSATA drive, will GParted understand it's not the / or boot partition or operating system? I already have to authenticate (input my password) to use GParted, so it's not a sudo issue.

When I try to manually umount the /dev/sdb1 this is what I see in the terminal:

mark@Lexington:~$ sudo umount /dev/sdb1
[sudo] password for mark: 
umount: /dev/sdb1: not mounted

or

mark@Lexington:~$ sudo umount /dev/sdb
umount: /dev/sdb: not mounted

Is there any other Linux software to control this? I would guess that 'parted', the CLI version of GParted is no better.

---

### Post by sudodus on 2014-04-03
I think we have been misunderstanding each other. I'm sorry for jumping to conclusions.

When you write / partition I'm thinking of the output of the command ***df***

which shows the current active root partition as /

-o-

I recommend ***gparted***, which makes it easy to 'see' what is happening thanks to the good graphic representation of the drives.

When you boot from another drive, you have to unmount the partitions you want to edit or delete. And you cannot have any process running, which uses that mount point, for example a terminal window.

After unmounting, it is possible to delete the partition.

-o-

If it still does not work to delete the 'inactive root partition', there is some error in the partition table, and it might help to wipe the first megabyte (overwrite with zeroes).

---

### Post by sudodus on 2014-04-03
You can use ***dd*** to wipe the first megabyte, but if there are other drives connected, and there are important data, it is risky to use dd. It will be safer to use the shellscript ***mkusb*** to wipe the first megabyte. See this link

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by Mark_in_Hollywood on 2014-04-04
While the following will not be for everyone, this is my solution.

The hard disk drive had been partitioned (GParted), as / and /home and /swap. When the drive was installed in an external eSATA box, GParted continued to reply that the / partition was in use.

Frustrated by GParted and DiskUtility not permitting me to modify the drive, I installed it in a Windows 7 machine. There, using the Format/Partition program (Win default, I believe), I deleted the partitions.

After that, I re-placed the box into my Ubuntu OS and then GParted formatted for ext4 and one large partition.

As always, GParted needs an extra feature to permit changing device ownership. GParted set the eSATA drive as:

root:root

and with enough searching, I eventually made it: 

user:user.

As well as modifying my fstab, and adding a directory named: backup in /media, I now have a working external storage device, and the badly name Ubuntu default program (application, package, app, or applet) Backup, is now running and I'm feeling a little more secure about 7 years of saved work.

Thanks for your help.

---

### Post by sudodus on 2014-04-05
Well, I was not able to help you much. I'm glad that you found a solution anyway, and thank you for sharing it with our community :KS

---

