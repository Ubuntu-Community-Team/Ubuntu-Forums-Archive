---
title: "Problem With Gparted"
date: 2015-06-19
forum: New to Ubuntu
---

### Post by akash14 on 2015-06-19
Hello Guys,
I am in love with ubuntu, i use now only linux and thats ubuntu, i removed windows,
but i like to partition of HDD on my linux, i know it is possible via Gparted.

i watched many tutorials but i still confused, help me please :)

sorry if my english hurts you :P

---

### Post by dino99 on 2015-06-19
hello & welcome  ):P

we will be glad to help you, but you did not said what is confusing you  ;) Remember that 'partitionning' is ALWAYS made on an unmounted system: so boot with the 'gparted live cd/usb' to set the partitions.
with an old bios system you cant set more than 4 'primary' partitions (recent uefi does not have that limitation), so better to create only the first one as 'primary' and the rest as 'extended'; that one is as a container where you can create multiple partitions inside it.
[http://howtoubuntu.org/how-to-resize-partitions-with-the-ubuntu-or-gparted-live-cd](http://howtoubuntu.org/how-to-resize-partitions-with-the-ubuntu-or-gparted-live-cd)

To create the required ubuntu partitions, set :
- / (root) with ext4 and about 15 gb size; that is the 'bootable' partition for the OS
- swap, about 4 gb (can be not needed with >= 8 gb ram)
- /home, ext4 with unlimited space for storing your data & settings

Then you will select 'something else' installer option to use the previously created partitions. When the installer will ask you about the bootloader (grub), select to install it on /dev/sda.

---

### Post by v3.xx on 2015-06-19
> i like to partition of HDD on my linux, i know it is possible via Gparted

Like dino99, we need to know what partitioning strategy you have in mind.

---

### Post by Bucky Ball on 2015-06-19
> **v3.xx said:**
> ... we need to know what partitioning strategy you have in mind.

More importantly, so do you. ;)

Scribble down a plan on paper of how you want the disk to be partitioned at the end of the process *before* you are sitting in front of Gparted about to partition. Make sure you know where you are going and how you're going to get there to avoid confusion or wrong turns.

---

### Post by yancek on 2015-06-19
Reading through or at least reviewing the sections of the GParted Manual at the link below would be very helpful to you:

[http://gparted.org/display-doc.php?name=help-manual](http://gparted.org/display-doc.php?name=help-manual)

---

### Post by Mike_Walsh on 2015-06-19
Hi, akash14.

> **Bucky Ball said:**
> More importantly, so do you. ;)

Scribble down a plan on paper of how you want the disk to be partitioned at the end of the process *before* you are sitting in front of Gparted about to partition. Make sure you know where you are going and how you're going to get there to avoid confusion or wrong turns.

Please do be aware that, unlike Windows, which use [COLOR=#0000ff]**Megabytes & Gigabytes**[/COLOR] (which are multiples of 1000=decimal), Ubuntu, and indeed just about all Linux distros, tend to work in [COLOR=#ff0000]**Mebibytes & Gibibytes**[/COLOR] (multiples of 1024...which is binary). 

It's only a small point; but if you work out your partition sizes in multiples of 1000, when gParted has finished its magic, you will find that your partitions aren't quite the size you intended them to be.

It seems complicated.....but it isn't, really. All part of the 'learning curve'!


Regards,

Mike. ;)

---

### Post by akash14 on 2015-06-20
Thank You I Solved :)

---

### Post by Bucky Ball on 2015-06-20
Please share with the community how you solved? Thanks. ;)

---

