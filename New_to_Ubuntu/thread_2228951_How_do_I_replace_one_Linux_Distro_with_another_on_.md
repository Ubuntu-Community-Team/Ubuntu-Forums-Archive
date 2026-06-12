---
title: "How do I replace one Linux Distro with another on a dual boot XP-Linux"
date: 2014-06-10
forum: New to Ubuntu
---

### Post by ross4 on 2014-06-10
I set up a dual boat system XP & Linux Mint on my Toshiba Satellite 100. Now I want to try Xubuntu instead of the Mint (and I'll probably try some others, too, at some time). At the moment, the Mint has four partitions (/boot, /, /home, & swap. I have no data worth keeping (on the Linux side) but it might be a good exercise to learn how to keep the present data but replace all else. Could someone explain or point me to an explanation on how to do this? I got to the "something else" screen in the install process and quit when I realized I didn't know what to do next.
Regards,
Ross

---

### Post by pfeiffep on 2014-06-10
You might consider trying out different flavors by using a live usb...
To answer you question directly ... once in 'something else' you'll want to use the partitions that already exist for Mint. If you don't have data stored in home then make sure you check the format this partition for 3 - I don't thing /swap needs to be formatted.

---

### Post by Bashing-om on 2014-06-10
ross4; Hi !

It is your system and only you know how you will use it, but I can give some "general" guidelines.
Always be aware of how the hard disk is partitioned, what is where,
The terminal commands:
```

sudo blkid
sudo fdisk -lu

```
will tell you this information.
As you no longer want Mint, and do want to set up for future additional operating systems; I do suggest:
In gparted delete all the current Mint partitions - keep in mind that with the MBR partitioning scheme one can have a MAX of 4 primary partitions - how many is Windows utilizing ?  You "might be able to keep the current swap partition, that remains to be seen.

Let's say that Windows XP takes up 2 of those 4 primary partitions, leaving 2 to work with.

How about this, after deleting the Mint partitions what is available for disk space is now marked "unallocated" Set up a primary partition of 50 gigs for (x)ubuntu to install onto, leaving 1 primary partition available to be made, make this last primary partition as "extended" . This "extended" partition will be the container to hold as many logical partitions as desired, say at this point in that "extended" partition you make up the swap partition and say 2 more logical partitions of 50 gigs to hold those future test installs.

As a reference; my set up ( quad booting presently ).
```

sysop@1310mini:~$ sudo blkid
/dev/sda1: LABEL="1310mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1310mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1310mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="1404std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdc2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
sysop@1310mini:~$ 

sysop@1310mini:~$ sudo fdisk -lu
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
sysop@1310mini:~$

```
Where the point of interest is my 1st hard drive 'sda'.
I have 3 primary partitions, one of which is the "extended" partition 'sda3'.
Now - contained in 'sda3' are the "logical" partitions 'sda5' (swap - for all my linux installs), 'sda6' ( a shared "data" partition), 'sda7' (Lubuntu 14.04), 'sda8' (/var). Leaving me 1 primary partition available for future uses. This partitioning scheme is rather exotic for the casual user ( left overs from this box as a file server once upon a time, and my mind set had not changed much).

This all boils down to what you have now, what you want in the future, and how to see it.

[INDENT][INDENT]make a plan
[INDENT][INDENT][INDENT][INDENT]and just do it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ross4 on 2014-06-10
Thanks for those replies. I've successfully replaced the Mint with Xubuntu. I made one newbie error: I didn't give enough info in my first post: 1) I have already tried a number of 'live' linux sessions. 2) I didn't fully describe the types of partitions I had on my drive. Still, just by reading the two responses to my post AND by carefully reading the 'something else' screens, I was able to figure out what to do. Just for interest sake, I did not format the /home partition, figuring it would leave my data intact, which it did. Even my Firefox bookmarks. Again, thanks for the help.  I'll mark this thread as solved if I can figure out how to do it. Ross

---

### Post by Bashing-om on 2014-06-10
ross4; Great !

[INDENT][INDENT]you do good work
[/INDENT][/INDENT]

---

