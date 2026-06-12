---
title: "Windows ntfs Spanned volume in Ubuntu server"
date: 2017-05-07
forum: New to Ubuntu
---

### Post by xorium on 2017-05-07
Hello all ,


I've been trying to figure out how to add my Windows spanned volume to Ubuntu server 16.04.
I cant figure it out, but I explain what the situation is like:


I have a computer installed with Windows home server 2011 here I have one 2TB disk and two 1TB discs.
I have merged with the Windows Disk manager so that these drives are 1 partition.
Now I got acquainted with Ubuntu server 2 weeks ago and know that I have a lot more options here.
And would like to switch to Ubuntu server.


This partition I would like to access in my ubuntu server.
On the internet I have already found ldmtool and a tutorial to make a volume. But It is not really want to get it done, but if I want to mount it, something does not work with the ntfs system.
I also found dmraid and tried this but also get the message that if I want to mount this it does not have a valid NTFS.


I'm new to ubuntu but have learned so much and quickly.
Hopefully someone can help me on this forum.


These are the disks that lsblk indicates what it's all about:




NAME        MAJ:MIN  RM     SIZE        RO    TYPE       MOUNTPOINT
sda           8:0         0        931,5G    0       disk
&#9492;&#9472;sda1      8:1         0        931,5G    0       part
sdb           8:16       0         931,5G    0      disk
&#9492;&#9472;sdb1      8:17       0         931,5G    0      part
sdc           8:32       0         1,8T        0      disk
&#9492;&#9472;sdc1      8:33       0         1,8T        0      part






is i let ldmtool to scan it wont find anyting if i let it scan in sda1 sdb1 and sdc1 it find the id
If i use ldmtool diskgroup and the id i get this:


"name" : "SERVER-Dg1",
  "guid" : "d9582c53-fe4e-11e4-aaf6-bc5ff45e6ca3",
  "volumes" : [
    "Volume1"
  ],
  "disks" : [
    "Disk1",
    "Disk3",
    "Disk2"
  ]

---

### Post by mastablasta on 2017-05-08
in other words you created a software raid 0 using windows tools. this is the worst kind of RAID. one disk fails and you will lose everything.

but back to using windows tools. windows OS things are best done in windows. so best thing to do would be to boot into windows, backup the drives and then reformat and move the backed up data back. NTFS while it works in linux is not a linux file system, so i suggest changing that as well if you plan to run linux OS. as you porbably know NTFS can get corrupted, can get fragmented... none of these issues can be solved using linux. you need ot boot into windows and use windows tools on NTFS. which is why it is best to use linux file system if you intend to use linux OS. default one is ext4, but you can explore more advanced file systems such as BTRFS or ZFS4linux. depending on what the server is doing and how much ram it has.

if you insist in seing windows software raid in linux then have a look here: [https://askubuntu.com/questions/567432/how-do-i-properly-access-windows-software-raid-0](https://askubuntu.com/questions/567432/how-do-i-properly-access-windows-software-raid-0)


another option is also to continue using windows server.

---

