---
title: "Dual booting external drive"
date: 2011-10-11
forum: New to Ubuntu
---

### Post by SoulRetriever on 2011-10-11
I am trying to create a dual-bootable external HDD

My general idea is to have two or three partitions:

1. Primary to boot either DSL or Ubuntu
2. A NTFS partition that can be used as a removable device for any OS
3. somewhere to store my documents on if they aren't held on the 1st partition (ideally the documents would be shared between DSL & Ubuntu

This would essentially be so i can have a bootable OS to help me fix my friend's computers (unfortunately i've become *that* guy that they come to for help when thier computer stops working) AND have a large portable storage device.

if it helps any; the device is 160gb and i'd prefer to have 40gb allocated to the linux partitions.

Does anyone have any pointers for me on how to do this or is this a stupid idea?

---

### Post by wildmanne39 on 2011-10-11
Hi, most people use a usb flash drive to carry with them for fixing other peoples computers, they install ubuntu on it,it is much smaller and easy to carry and if it gets damaged or lost it does not cost as much to replace.
Thank you

---

### Post by Lisiano on 2011-10-11
Yes, a USB flash drive is cheaper and not as greedy on the wallet if you lose or damage it. But regardless the procedure for both is the same.
In your scenario, first you will need to partition the drive into 6 partitions if you count Extended as being one.
[LIST]
[*]"Removable disk" partition - 120GB
[*]Extended - 40GB
[/LIST][INDENT][LIST]
[*]Ubuntu - 10GB
[*]DSL - 2GB (Probably overkill)
[*]Home - 26GB
[*]Swap - 2GB
[/LIST][/INDENT]

There is no exact order of how you should do it but you MUST put the 1st partition as the "Removable disk" (Probably FAT32) partition as Windows does NOT see anything past the 1st partition on external disks, at least that is true for flash drives, not sure about hard drives but probably true.
Then comes the Extended partition and everything else goes into it.
Ubuntu is logically your Ubuntu install (EXT4)
DSL is logically your DSL install (EXT2, AFAIK DSL does not support EXT4, if it supports EXT3, use it instead.)
Home is your home folder that will be shared across both Ubuntu and DSL (EXT2, AFAIK DSL does not support EXT4, if it supports EXT3, use it instead.)
Swap is needed since we don't know if the machine you will be using the disk on will have a Swap partition, this way you always have some Swap. You should install Ubuntu first and DSL next and tell DSL to NOT touch the bootloader, after that is done, tell Ubuntu to update GRUB. You can create the partitions using Ubuntus built-in Disk Utility or use GParted.

---

### Post by SoulRetriever on 2011-10-13
Thanks, i will try this when i get home.

Just out of curiosity (and possible stupidity) would i be able to keep a portable virtual machine program on the windows partition and boot the other partitions into a virtual machine.

i'm not sure if it'd work as you said windows doesnt see past the first partition but it was just a thought that passed my mind.

Thanks for all the help

---

### Post by Lisiano on 2011-10-14
Well. It should let you boot it in a VM as long as you tell vmware to use the whole disk instead of a partition.

---

