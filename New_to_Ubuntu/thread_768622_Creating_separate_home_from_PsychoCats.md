---
title: "Creating separate /home from PsychoCats"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-04-26
I've managed to add a new partition to my drive. GParted named it: **/dev/sda3**.

I'm trying to understand the rest of:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

He says:

sudo mkdir /old
sudo mount -t ext3 /dev/hda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/hda7 /new

what I want to know is is the /old directory in /home? That is: do I need to be in /home before issuing the above commands? Also, while PCats doesn't say so, are the above to be run in a LiveCd session? Can they be run from the hard drive session?

So where he uses /dev/hda1 I would type **/dev/sda1**?

mark@Lexington-19:~$ sudo fdisk -l
[sudo] password for mark:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7687    61745796   83  Linux
/dev/sda2           38537       38913     3028252+   f  W95 Ext'd (LBA)
**/dev/sda3            7688       38536   247794592+  83  Linux**
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

---

### Post by philinux on 2008-04-26
Yes substitute sda for hda

---

### Post by SOULRiDER on 2008-04-26
The PS tutorial seems a but outdayed...

Ive found this [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/) IMO its better explained, if you have any questions just ask.


By the way,
sudo mkdir /old will make a new directory called old in the filesystem root, not in your home. So, it will NOT be /home/mark/old  it will be just /old

---

### Post by Mark_in_Hollywood on 2008-04-26
Using the suggestion to see:


[http://ubuntu.wordpress.com/2006/01/...own-partition/](http://ubuntu.wordpress.com/2006/01/...own-partition/) 

I got this far:

mark@Lexington-19:~$ sudo mkdir /mnt/newhome
[sudo] password for mark:
mark@Lexington-19:~$ sudo mount -t ext3 /dev/sda3 /mnt/newhome
mark@Lexington-19:~$ cd /home/
mark@Lexington-19:/home$ find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/
cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information.

R2D2 are you there?

---

### Post by philinux on 2008-04-26
According to psychocats it's --null --sparse -pvd

---

### Post by Mark_in_Hollywood on 2008-04-26
Both methods are using

--null --sparse -pvd

as arguments.

by the by: is it proper to do this type of work in a NON-LiveCD session?

Both methods are found at:

[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/](http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/)
or
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by philinux on 2008-04-26
Requirements
You must use a **live CD** for this process, for two reasons:

   1. In order to resize your existing / partition, it needs to be unmounted. The only way to unmount it is for it not to be in use, which means you can't boot to your regular Ubuntu installation while resizing it... which means you need a live CD
   2. If you screw up your installation by accident, you can use the live CD to restore your old settings and, in the worst situation, at least recover your important files

---

### Post by Mark_in_Hollywood on 2008-04-26
I got as far as:

ubuntu@ubuntu:/$ sudo mount -t ext3 /dev/sda3 /new
ubuntu@ubuntu:/$ cd /old/home
ubuntu@ubuntu:/old/home$ find . -depth -print0 | sudo cpio --null --sparse -pvd /new/
0 blocks

ubuntu@ubuntu:/old/home$ sudo find . -depth -print0 | cpio –null –sparse -pvd /mnt/newhome/
cpio: You must specify one of -oipt options.
Try `cpio --help' or `cpio --usage' for more information.

and

ubuntu@ubuntu:/old/home$ cd /home
ubuntu@ubuntu:/home$ sudo mkdir /recovery
ubuntu@ubuntu:/home$ sudo mount -t ext3 /dev/sda1 /recovery
ubuntu@ubuntu:/home$ sudo cp -R /recovery/home_backup /recovery/home
cp: cannot stat `/recovery/home_backup': No such file or directory

Any ideas?

---

### Post by vanadium on 2008-04-26
The options need to have two dashes instead of a long dash. –null –sparse must be --null --sparse instead. On the blog, the two dashes were replaced by a long dash, probably by the blog software.

[edit]I am sorry: I missed that you already picked this up. If you list your /old/home, do your directories and files show up? (ls /old/home)? Is your /new properly mounted?

---

