---
title: "I can not access my &quot;Extra Drive 1&quot;"
date: 2014-08-23
forum: New to Ubuntu
---

### Post by david-wofford7237 on 2014-08-23
I can not access my "Extra Drive 1". I am new to Ubuntu and Decided I wanted to learn more about computers and thought this would be a great place to start. I bought a System76 Galago UltraPro with Ubuntu 14.04 already installed. When I am in the File Manager and I click on the link to access the Extra Drive 1 I receive the error message:
 

 Error mounting system-managed device /dev/sda1: Command-line `mount "/mnt/
 d3462389-2c99-44eb-8b8e-e8e0012a40ad"' exited with non-zero exit status 32: mount:
 wrong fs type, bad option, bad superblock on /dev/sda1,
        missing codepage or helper program, or other error
        In some cases useful info is found in syslog - try
        dmesg | tail  or so
 

 Any help is appreciated.

---

### Post by oldos2er on 2014-08-23
Is this a USB drive? What file system is on it? What was the command you used to generate the above output?

---

### Post by david-wofford7237 on 2014-08-23
The drive is an internal storage drive. That response is the result of an error message when I try to access the "Extra Drive 1" using the "Files" application. As far as the File System:

```
david@david-Galago-UltraPro:~$ sudo file -s /dev/sda1
/dev/sda1: Linux rev 1.0 ext4 filesystem data, UUID=d3462389-2c99-44eb-8b8e-e8e0012a40ad, volume name "Extra Drive 1" (extents) (large files) (huge files)


```

---

### Post by Mark Phelps on 2014-08-23
Normally, the first drive in your PC would be "sda" and the first partition on that would be "sda1" -- and this would be the main partition you're already using -- which would not let you mount it again.

Open a terminal, enter the command and post the output: "sudo fdisk -lu" (lowercase L, not a one).

---

### Post by david-wofford7237 on 2014-08-24
I see. Well the system works fine other than the Extra Drive. Here is what I got back

```
david@david-Galago-UltraPro:~$ sudo fdisk -lu
[sudo] password for david: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1953525167   976762583+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00040f91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   226050047   113024000   83  Linux
/dev/sdb2       226050048   234438655     4194304   82  Linux swap / Solaris


```

---

### Post by david-wofford7237 on 2014-08-24
I figured it out. I opened the search application, typed "Disks". On the "Volumes" diagram there are three buttons you can press; the first one is a square which will unmount the system. The second one is a minus "-" symbol which will delete the partition and the last option which looks like two gears turning with the option for "More Actions". I clicked on the gears for More Actions, then on the Edit Mount Partitions, and turned on the Automatic Mount Options. I remember turning the Automatic Mount Options off so that the drive would mount on start up and I would not have to go into the "Files" application to mount the drive since I have other applications that depend on it being mounted already, such as "Clemintine". I am sorry for my lack of understanding. One more thing though, Can anyone recommend some classes to take online so I may better understand the system and hopefully be able to resolve these kind of issues from happening in the future. Thank you.

---

### Post by obake2 on 2014-08-24
> **david-wofford7237 said:**
> I figured it out. 
[ ... ]

Can anyone recommend some classes to take online so I may better understand the system and hopefully be able to resolve these kind of issues from happening in the future. Thank you.

There is a [Introduction to Linux]("https://www.edx.org/course/linuxfoundationx/linuxfoundationx-lfs101x-introduction-1621#.U9u3MIBdVd8") class that is worth $2,400 but that it is offered for free this summer at edX. More info [here]("http://arstechnica.com/information-technology/2014/03/2400-introduction-to-linux-course-will-be-free-and-online-this-summer/"). The class is solely graded on the Final Test.


And no worries, the class is self-paced and there is still no end date for the class so anyone can still join.

And there is [LinuxCommand.org]("http://linuxcommand.org/") where you can learn Terminal commands used in Linux.

---

