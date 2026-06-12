---
title: "grub error 5 without rescue option on disc"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by davidvanbibber on 2008-09-02
hello,

im new to ubuntu and i have encountered a problem. when ever i boot it gives me an error. grub error 5 to be exact. i was told to use the the ubuntu install cd and select rescue, but the disc i have doesnt have that feature and it told me to check online.
is there any way to fix it with out that feature? im currently using a diffrent computer because i cant boot into anything due to that error. please help so i dont have to use this dreaded operating system any further (windows xp).

---

### Post by Dedoimedo on 2008-09-02
Hello,

Error 5 means the partition table is corrupt. This means you have have accidentally resized, deleted partitions.

To solve the problem, let's try the following:

1. Boot from Ubuntu live CD.
2. In the CD environment, open a terminal window.
3. Type sudo su.
4. Type fdisk -l.
5. Show the output you have here.

We'll see what partitions you have or not and if it's possible to fix the problem. We'll also try to see if the Windows partition is intact.

Dedoimedo

---

### Post by bumanie on 2008-09-02
Grub error 5 indicates that the partition table on your hard drive has been corrupted. It is possible to re-write it with testdisk, available off the ubuntu live cd > sudo apt-get install testdisk followed by > sudo testdisk to run it. Alternatively you could go [here]("http://www.cgsecurity.org/wiki/TestDisk") and download the testdisk from the developer. There is also a tutorial available on that site. I restored a partition table (hard drive was getting grub error 5) via testdisk recently on a friend's computer, the hard drive and OSes have worked flawlessly since. Read the tutorial before doing anything else. Also have a look at Herman's [testdisk site]("http://www.users.bigpond.net.au/hermanzone/p21.html") for more pointers on how to use testdisk correctly. Good luck.

---

### Post by davidvanbibber on 2008-09-02
umm how do you copy words from terminal to shorten things up?

---

### Post by davidvanbibber on 2008-09-02
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

i meant the keyboard shortcut in terminal to copy things.

---

### Post by davidvanbibber on 2008-09-02
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda2ada2a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17165   137877831    7  HPFS/NTFS
/dev/sda2           17166       30401   106318170    5  Extended
/dev/sda5           17166       29857   101948458+  83  Linux
/dev/sda6           29858       30401     4369648+  82  Linux swap / Solaris

Disk /dev/sdb: 8074 MB, 8074035200 bytes
39 heads, 31 sectors/track, 13043 cylinders
Units = cylinders of 1209 * 512 = 619008 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       13044     7883772    b  W95 FAT32

sorry bout that. though it was a 1 instead on a l

---

### Post by bumanie on 2008-09-02
> **davidvanbibber said:**
> umm how do you copy words from terminal to shorten things up?

Not sure what you mean by shorten things up. A corrupted partition table will cause a hard drive give to a message such as there is no hard drive or there is no operating system. To return the computer to its former state, there are no shortcuts. I usually use testdisk's live cd or a 'multi' rescue disc with testdisk as part of its inventory, but ubuntu live cd is an option. 
If you choose the ubuntu live cd, boot the computer with it and then go to Applications --> Accessories --> Terminal and insert the code, first code downloads testdisk, second code runs testdisk. If you use the testdisk live cd, boot the computer with it and it opens directly into the testdisk program. Your only other alternative is to reinstall, but you will not be able to save anything that will not open up. You may be able to access some things from the live ubuntu cd, but only parts of the hard drive that isn't corrupted in the partition table, which is on the first 512mb of a hard drive.

---

### Post by bumanie on 2008-09-02
Check out this from Herman's grub page

Quoted from the GNU/GRUB manual

    5 : Partition table invalid or corrupt
        This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 

Check the partition table by running fdisk as root ('sudo fdisk -lu) in Linux, or use your favourite partition editing software to make sure one of your partitions has been marked 'active'.

GRUB's 'makeactive' command is used for setting a boot flag on a partition, so you can also do it with GRUB. Windows in particular requires a boot flag or it won't boot.

If more than one partition has already been marked as active, you might need to remove the 'active' flag from one of them, as only one is supposed to be set as active at a time. Use your favourite partition editing software for that.

If nothing else works, you might be able to use TestDisk to write you a brand new partition table.
TestDisk is an excellent Linux program that can scan you hard disk for partition starting blocks and identify those and offer you the chance to have the one you select written to a new partition table for you. TestDisk can do lots of other useful jobs as well. This website has its own page about TestDisk, TestDisk Page.

You should always back up your data before using any software to work on your partition table.
If you can't boot any operating system you might need to use a Live CD for doing that, and you can visit these links to learn how, File Systems and Mounting Page, SSH Network.

---

### Post by davidvanbibber on 2008-09-02
i tried "sudo apt-get install testdisk"

but received:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk

---

### Post by bumanie on 2008-09-02
Maybe you don't have the correct repository enabled. Hmm, I think one has to enable the universe repository. It's definitely the correct code. The universe repository is under your software sources System --> Administration --> Software sources. Not 100% sure whether you can enable it off a live cd. As said, I use trinity rescue kit that has testdisk as part of its programs, so have never tried downloading testdisk via live ubuntu cd - it downloads fine on a working ubuntu OS. Sorry, because I haven't done it this way, I'm a bit scratchy on detail.
If you are unable to do this you could download the live testdisk cd from the gcsecurity site I linked above - testdisk does work well when used correctly. Read the links I sent re its use.

---

### Post by Dedoimedo on 2008-09-02
Hello,

It looks like you have all the partitions, but something got messed up along the way. To make things simple, I'd now try the following tools, to begin with:

1. Super Grub Disk (download iso burn to cd).
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

2. TestDisk (download one of live cds that contains).
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

Try using the tools to repair the grub, partitions. If this does not work, we will try other methods. Follow the wizards instructions as you run each. Stop and ask if you don't understand something.

Dedoimedo

---

### Post by davidvanbibber on 2008-09-02
lol there is no need to apologize, even scratchy details are far more than enough than what i know :). but i enabled the repositories and no luck. is testdisk like a program that you can write to and boot off of a disk or a regular program? and also, how do you install things off the net after you download them, because i downloaded it and dont know what to do after that.

---

### Post by Dedoimedo on 2008-09-02
See my post above...
Dedoimedo

---

### Post by davidvanbibber on 2008-09-02
im afraid supergrub didnt work. it flashes a screen before it reboots, after i tried everthing and all i was able to see was a little part of the error and it said "not lucky". the grub error 5 still remains

---

### Post by Dedoimedo on 2008-09-02
Hello,
Now download a live cd with TestDisk - Knoppix, SystemRescueCD or others and try running it. I recommend SystemRescueCD.
Dedoimedo

---

