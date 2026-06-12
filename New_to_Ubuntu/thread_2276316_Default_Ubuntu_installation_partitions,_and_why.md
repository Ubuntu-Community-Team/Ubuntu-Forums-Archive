---
title: "Default Ubuntu installation partitions, and why"
date: 2015-05-01
forum: New to Ubuntu
---

### Post by jjmgray on 2015-05-01
I'm curious.
A lot of Ubuntu/Linux installation guides I see have you  create multiple partitions manually when installing the OS (root, boot,  swap, and home).
How is this different from telling the OS to handle  it itself (such as with Erase and install Ubuntu) and why would you use  one or the other?

---

### Post by kc1di on 2015-05-01
Hello jjmgray and welcome to ubuntu. 

The default install will erase the disk and format with one big "/" partition and maybe a swap partion.

If your using a desktop with enough ram (Say 2Gbs or more) you most likely do not need the Swap space.  However if you using a Laptop and want to be able to suspend or hibernate you'll need a swap space that is about double the amount of ram installed. 
I personally like to have a separate "/home" partition so that if I need to reinstall the system at some point I don't loose all my settings.  most personal setting and of course documents saved are found in the "/home" directory. 

Some Distros use a separate /boot partition but unless your doing a UEFI install you really don't need it.   

here are a couple of pages that discuss various partitioning schemes: 
[https://help.ubuntu.com/community/PartitioningSchemes]("https://help.ubuntu.com/community/PartitioningSchemes")

[http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/]("http://www.howtogeek.com/howto/35676/how-to-choose-a-partition-scheme-for-your-linux-pc/")
Good Luck and Enjoy Ubuntu :)

---

### Post by Bashing-om on 2015-05-01
jjmgray; Hey !

I have been around a bit, and with computers in general more than just a bit.

My take on partitioning ubuntu for personal use. The install wizard in " erase disk and install ubuntu" is just fine for 80 + percent of the use cases.
It is when your use case requires doing "something else"  one deviates from that stock install.
For reference - I have been around  - my setup:
```

sysop@1404mini:~$ sudo fdisk -lu
[sudo] password for sysop: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00065f5e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    10242047     5120000   83  Linux
/dev/sda2        10244096    30724095    10240000   83  Linux
/dev/sda3        34207742   976771071   471281665    5  Extended
/dev/sda5       443795688   443811689        8001   82  Linux swap / Solaris
/dev/sda6       443811753   597409154    76798701   83  Linux
/dev/sda7       597409792   976771071   189680640   83  Linux
/dev/sda8        34207744    44447743     5120000   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x502a9772

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002ea65

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048   102402438    51200195+  83  Linux
/dev/sdc2   *   102404096   204804095    51200000   83  Linux
/dev/sdc3       204806144   266246143    30720000   83  Linux
sysop@1404mini:~$

```

Note that there is no separate /boot partition . That practice is long depreciated except in special cases;

I have my operating system at large installed to a separate /root partition; easier for me to visualize my file system hierarchy, directly manage disk space usage, and ---when I break it - enhances my ability to isolate the fault, see the fix without worrying that I affect any personal files and settings;

I do have my /home on a separate partition, as advised by kc1di,  it is an aide in keeping what is set up on the current install when (RE-)installing; and makes backing up so much easier. And it does enhance the ability to manage space usage on the system;

I have my logs on a separate partition .. Hey I break my system, logs go wild, and can kill the operating system by running out of disk space. I can better manage disk usage with a separate partition to log too;

You see only one /swap partition. That /swap partition is shared among the 5 'buntu installs .


This too might help you to see:
```

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdc3: LABEL="ubie1504" UUID="ec786c62-9548-4f56-ac2f-8dacf4e3bb96" TYPE="ext4" 
sysop@1404mini:~$

```
On my system I have a lot going on, and sometimes it is a real chore to keep track of what I do have going on. Separate partitions does help !

This is rather extreme usage, like advised... 80 + % of the time .. That install wizard is a wonderful thing. If you have a need then one makes adjustments.

[INDENT][INDENT]if it ain't broke
[INDENT][INDENT][INDENT]do not fix it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ajgreeny on 2015-05-01
I also used to have a disk setup a bit like Bashing-om's on my older desktop machine, and had 5 separate OSs on two physical hard disks so it was a lot easier to keep track of everything with manual partitioning at installation time.  I now, on a new powerful desktop machine, have just one OS but use VBox installations of things I want to explore a bit, currently 6 different VMs of some of the *ubuntu family, Bodhi, Mint and finally Windows XP , needed to update a satnav device which will not work in Linux.

On the old machine I had a separate /home partition, as I still do.  Now I just automount my main OS home partition in the VMs and then create  soft links to all the data folders from that into the homes of the VMs, which is more or less what I used to do previously, ie, automount /home from my main OS into the /home folders of all the other OSs and soft-link the data folders.

This means in effect that all my data is available to all my OS just as if it was sitting in folders in each OS rather than being linked from its one instance in the main OS.

The choice of options is almost infinite in number and may get as many different ideas as you get answers; there is no right or wrong, it is just a case of doing what fits your circumstances best.

---

