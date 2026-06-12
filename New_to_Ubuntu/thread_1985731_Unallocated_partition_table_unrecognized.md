---
title: "Unallocated partition table unrecognized"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by phil66 on 2012-05-23
Dell XPS pentiun 3 dual core 3.0ghz 2.0 gb ram
80gb hard drive --250 gb hard drive
Ubuntu-10.04 
Puppylinux lucid-5.28

When I open gparted I get the error unallocated partition table.
From either hard drives.

Opening CF from fdisk I get the error:"bad primary partition 1: partition ends in the final partial cylinder I also get this on both drives.

Test disk shows I have one bad sector "warning"

In gparted when I open information I get:Warning invalid partition table on /dev/sda--wrong signature 5954

Sda Is the drive Ubuntu is installed on:

Can this be fixed without creating a new table.

---

### Post by choppyfireballs on 2012-05-23
> **phil66 said:**
> Dell XPS pentiun 3 dual core 3.0ghz 2.0 gb ram
80gb hard drive --250 gb hard drive
Ubuntu-10.04 
Puppylinux lucid-5.28

When I open gparted I get the error unallocated partition table.
From either hard drives.

Opening CF from fdisk I get the error:"bad primary partition 1: partition ends in the final partial cylinder I also get this on both drives.

Test disk shows I have one bad sector "warning"

In gparted when I open information I get:Warning invalid partition table on /dev/sda--wrong signature 5954

Sda Is the drive Ubuntu is installed on:

Can this be fixed without creating a new table.

I'm not an expert but it sounds like your operating system installed to the last available cylinder on the hard drive. this could be if you have a bad sector it installed after it and ended at the end of the hdd or that something is wrong in your partition table. Again i'm no expert and i'm not sure how to go about fixing this, i have some ideas but I want to let someone else poke at it first for you.

---

### Post by phil66 on 2012-05-23
Choppyfireballs

Thanks for the reply.

Those were my exact thoughts after looking at all the errors.

I have never had this kind of an error although I have had Ubuntu since version 8.04

---

### Post by DELL JonathanS on 2012-05-24
[FONT=Calibri]Is your drive still booting, or did you run testdisk and gparted from a live CD? It's not likely to boot with a corrupt partition table so I am just trying to make sure I did not assume something. The partition 1 ending cylinder message may not be bad; sometimes you can create a partition with an older/newer version of the tool which infers different limits from the drive geometry. However it is also possible a false partition boundary is being read from faulty partition table. Can you please paste the output of:[/FONT]
```

[FONT=Calibri]# dd if=/dev/sda count=1 bs=512 | xxd[/FONT]

```
[FONT=Calibri]It would be wise to check the disk also. You can do:[/FONT]
```

[FONT=Calibri]# smartctl -t short /dev/sda[/FONT]

```[FONT=Calibri]And wait two minutes and then do:[/FONT]
```

[FONT=Calibri]# smartctl -a /dev/sda[/FONT]

```[FONT=Calibri]And paste the output of the second command.[/FONT]

[FONT=Calibri]Do you happen to know how your disk was partitioned also? If the disk is good it may not be terribly difficult to rewrite the partition table -- though that is not always true![/FONT]

---

### Post by phil66 on 2012-05-24
ray@ray:~$ sudo dd if=/dev/sda count=1 bs=512 | xxd
[sudo] password for ray: 
0000000: eb63 9010 8ed0 bc00 b0b8 0000 8ed8 8ec0  .c..............
0000010: fbbe 007c bf00 06b9 0002 f3a4 ea21 0600  ...|.........!..
0000020: 00be be07 3804 750b 83c6 1081 fefe 0775  ....8.u........u
0000030: f3eb 16b4 02b0 01bb 007c b280 8a74 018b  .........|...t..
0000040: 4c02 cd13 ea00 7c00 00eb fe00 0000 0000  L.....|.........
0000050: 0000 0000 0000 0000 0000 0080 0100 0000  ................
0000060: 0000 0000 fffa 9090 f6c2 8075 02b2 80ea  ...........u....
0000070: 747c 0000 31c0 8ed8 8ed0 bc00 20fb a064  t|..1....... ..d
0000080: 7c3c ff74 0288 c252 bb17 0480 2703 7406  |<.t...R....'.t.
0000090: be88 7de8 1c01 be05 7cf6 c280 7448 b441  ..}.....|...tH.A
00000a0: bbaa 55cd 135a 5272 3d81 fb55 aa75 3783  ..U..ZRr=..U.u7.
00000b0: e101 7432 31c0 8944 0440 8844 ff89 4402  ..t21..D.@.D..D.
00000c0: c704 1000 668b 1e5c 7c66 895c 0866 8b1e  ....f..\|f.\.f..
00000d0: 607c 6689 5c0c c744 0600 70b4 42cd 1372  `|f.\..D..p.B..r
00000e0: 05bb 0070 eb76 b408 cd13 730d f6c2 800f  ...p.v....s.....
00000f0: 84d0 00be 937d e982 0066 0fb6 c688 64ff  .....}...f....d.
0000100: 4066 8944 040f b6d1 c1e2 0288 e888 f440  @f.D...........@
0000110: 8944 080f b6c2 c0e8 0266 8904 66a1 607c  .D.......f..f.`|
0000120: 6609 c075 4e66 a15c 7c66 31d2 66f7 3488  f..uNf.\|f1.f.4.
0000130: d131 d266 f774 043b 4408 7d37 fec1 88c5  .1.f.t.;D.}7....
0000140: 30c0 c1e8 0208 c188 d05a 88c6 bb00 708e  0........Z....p.
0000150: c331 dbb8 0102 cd13 721e 8cc3 601e b900  .1......r...`...
0000160: 018e db31 f6bf 0080 8ec6 fcf3 a51f 61ff  ...1..........a.
0000170: 265a 7cbe 8e7d eb03 be9d 7de8 3400 bea2  &Z|..}....}.4...
0000180: 7de8 2e00 cd18 ebfe 4752 5542 2000 4765  }.......GRUB .Ge
0000190: 6f6d 0048 6172 6420 4469 736b 0052 6561  om.Hard Disk.Rea
00001a0: 6400 2045 7272 6f72 0d0a 00bb 0100 b40e  d. Error........
00001b0: cd10 ac3c 0075 f4c3 75ed 0600 0000 8020  ...<.u..u...... 
00001c0: 2100 83fe ffff 0008 0000 0068 ee08 00fe  !..........h....
00001d0: ffff 05fe ffff fe77 ee08 0280 6200 0000  .......w....b...
00001e0: 0000 0000 0000 0000 0000 0000 0000 0000  ................
00001f0: 0000 0000 0000 0000 0000 0000 0000 55aa  ..............U.
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.000484255 s, 1.1 MB/s
ray@ray:~$ 

The smartctl command requires I install smartmontools after install it changes to postfix configuration window and I can not respond to the inquiry.

I have run smart data self-test and the results are: 1 bad sector and reallocated sector count>

The drive still boots Ubuntu-10.04 on sda drive and Puppylinux-5.28 on sdb drive and test were run from hard drive.

I have lost sdb7 & 8 partition (Mageia 1) and swap partitions 

The sda drive was partitioned sda1 as root and sda5 as swap and a small unallocated partition.

Fdisk will not run from sda but I can run it from sdb drive.

Thanks for the reply any further suggestions

---

### Post by phil66 on 2012-05-24
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9328    74920960   83  Linux
/dev/sda2            9328        9730     3227649    5  Extended
/dev/sda5   ?       66975      125675   471505690+  4d  QNX4.x
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: ignoring extra data in partition table 5
Warning: invalid flag 0x5954 of partition table 5 will be corrected by w(rite)

Disk /dev/sdb: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2573    20667591   83  Linux
/dev/sdb2            2574       10617    64613430    5  Extended
/dev/sdb3   *       27845       30395    20478976   83  Linux
/dev/sdb5   ?       60221      118920   471505690+  4d  QNX4.x
sh-4.1# 

Data from fdisk -l from sdb hard drive

---

### Post by phil66 on 2012-05-24
[http://pastebin.com/qRhkPdxQ](http://pastebin.com/qRhkPdxQ)

[http://pastebin.com/ak6vjVi8](http://pastebin.com/ak6vjVi8)

These were run on both drives from Puppylinux

Sorry for all the info but I would like to solve this problem without reinstall all systems

---

### Post by phil66 on 2012-05-25
Would someone look at this info

And advise what to do next to correct this error

I would like to fix without having to reformat everything

Thanks for looking

---

### Post by oldfred on 2012-05-25
It looks like you sda5 partition table entry is totally corrupted. Since it was just swap, I might try to delete. But you mention other partitions also?

Not sure if fixparts or testdisk may be the better way to fix issue. I might look at drive with both.

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

