---
title: "Recover data after Ubuntu installation"
date: 2013-02-15
forum: New to Ubuntu
---

### Post by dangalpin on 2013-02-15
Hello,

I just built my first PC, and installed Ubuntu 12.10 last night (my first experience of pc building and linux!). I used a 1TB hard drive that I had previously been using in my Synology NAS drive, and it had over 300GB of data stored on it. I wanted to be able to install ubuntu without deleting all the data on the disk, so I chose the manual partition install option. I created a 10GB ext4 partition and an 8GB SWAP partition and all installed correctly. HOwever I now can't see any of the data on the disk.. Have I unwittingly deleted everything???

sudo fdisk -l returned the following:
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000957b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19529727     9763840   83  Linux
/dev/sda2        19531774    35153919     7811073    5  Extended
/dev/sda5        19531776    35153919     7811072   82  Linux swap / Solaris


I've got no idea what 'extended' means and whether it's recoverable. can anyone help? I do have backups of the irreplaceable stuff, but I'd really rather not re-rip all my CDs if I can possibly avoid it!

I should warn you I'm a rank amateur (I guess you've worked that out already). 

Thanks in advance,
Dan

---

### Post by fantab on 2013-02-15
First of all don't use your installed Ubuntu, if you wish to recover your data. Shut down and boot with Ubuntu CD or USB and opt to 'try ubuntu'.

**[Test Disk]("http://www.cgsecurity.org/wiki/TestDisk")** can recover your files, however there are no guarantees. Search these forum for recovering lost partitions and data, especially look for oldfred's posts... they are very informative and offer good advise.
More info: [http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html) ; [http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Some info on [Extended Partiton]("http://linux.about.com/cs/linux101/g/Extended_partit.htm").

Please wait for some more advice to come your way before you get started.

Good Luck...

---

### Post by offgridguy on 2013-02-15
Hello and welcome to the forums,  extended is one of the three partition types
which include primary,logical and extended. The defining feature about extended
partitions, is that you can have other{logical} partitions within them.

I would suggest downloading , gparted if it is not already installed, should be
available in the software center, run gparted and take a screenshot of the
partition table it shows and post it here.
     Use the paper clip icon and it will attach as a thumbnail.

---

### Post by Mark Phelps on 2013-02-15
What were the partitions on the drive prior to the installation? Were they all Linux filesystems? Or, were some of them Windows filesystems (e.g., NTFS)?

---

### Post by dangalpin on 2013-02-15
Thank you all for replying! 

I'll answer as best I can.. First up, attached is a print screen of gparted's view of things.

In terms of what the previous partitions were, I'm not overly sure. It was only ever used in my Synology NAS - I checked on their website and they use a linux-based OS and an ext4 parition..

Does that help at all??

Thanks again

---

### Post by dangalpin on 2013-02-15
Would it help at all if I put the hard disk back in to the NAS>?? I'm guessing not...

---

### Post by offgridguy on 2013-02-15
It looks like your 300 gb. of data is nowhere to be seen, may not
be totally gone though as the install would have only had to format 
the 10 gb and the 8 gb, partitions.  I'm not real optimistic about
it though. Like the 2nd post said, there are tools for data recovery, i have never had to do it so
not real familiar with it.

As to putting the HD back into the NAS, may not help, but sure
couldn't hurt either.

A suggestion regarding your partition table{if your data is irrecoverable}  you can enlarge the
dev/sda2 extended partition to whatever size you like, say 308 gb. then create another 300gb logical
partition within it, use mount point / Home and you would have a separate home partition for your data.

My preferred method of editing partitions is to use a live CD of parted magic {which contains gparted}  Boot from the live CD and edit the partitions when they are not in use.

---

