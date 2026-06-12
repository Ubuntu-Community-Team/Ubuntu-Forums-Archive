---
title: "Problem with reboot"
date: 2016-03-09
forum: New to Ubuntu
---

### Post by JkR4Yne on 2016-03-09
I rebooted because somehow my mouse quit working.  This was right after an update.  I get a purple screen with 4 options now:
Ubuntu - which just cycles back to the same screen.
Advanced options- which has restore options for the last several updates, but doesn't seem to work.
Memtest 68+
Memtest 68+ plus Serial Console 115200  - these last two tests don't reveal any problems.

Any help is appreciated. Thanks!

---

### Post by oldfred on 2016-03-09
Can you boot the second entry or the recovery mode?

But may be best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by JkR4Yne on 2016-03-09
I can't boot the second entry or the recovery mode- Every time, it runs through some processes and then ends with {initramfs}  - I have no idea what to do after that.
My Ubuntu disk has no repair option, the only relevant options in one to run it without installing it, or just plain installing it. If I do the first, I can't get internet connection, so I can't use the commands suggested by the Boot-Info. I appreciate the help, though - it's helping learn me more.

---

### Post by oldfred on 2016-03-09
Are you using a hard wired Ethernet connection. They almost always work where Wi-fi may not work depending on chip & driver required.

---

### Post by JkR4Yne on 2016-03-09
I wasn't before, thanks for the tip.  The Boot-Info seemed to install fine, but while it was scanning it said it could take several minutes, and it's still going after 2 hours.  Is that normal.  Thanks.

---

### Post by oldfred on 2016-03-10
It may take a couple of minutes, normally depending on numbers of drives & partitions as well as speed of system
It like grub and some tools wants to scan all partitions to see if you have a bootable system.
If issues with any partition or drive then it may fail.

I might start with fsck on all ext4 partitions. But if you have NTFS then you have to use Windows to run chkdsk.
 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 

It also could be drive. In Disks, upper right corner icon are other features including Smart Data & tests. All I know is passed is good, anything else is not so good.

---

### Post by JkR4Yne on 2016-03-10
Thank you, it eventually stopped and gave me this report:  [http://paste.ubuntu.com/15340000/](http://paste.ubuntu.com/15340000/)

I then ran Boot repair and got this :  [http://paste.ubuntu.com/15340137/](http://paste.ubuntu.com/15340137/)

After I rebooted  ( and removed Ubuntu disk) however, I got the message  "Missing operating system.  Operating system not found."
I made sure the boot order was changed back to hard disk first.  I have no idea what I did wrong. but it just have been something big.

---

### Post by oldfred on 2016-03-10
It still is not mounting sda1, did you run the fsck as posted above? And what errors did it show?

---

### Post by JkR4Yne on 2016-03-11
Thanks ~ This is what I got:

sudo e2fsck -C0 -p -f -v /dev/sda1
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1 
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1 
Could this be a zero-length partition? 
ubuntu@ubuntu:~$ 
 


sudo e2fsck -f -y -v /dev/sda1


e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1 
Could this be a zero-length partition? 
ubuntu@ubuntu:~$  

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda 
e2fsck: Bad magic number in super-block while trying to open /dev/sda 
/dev/sda:  
The superblock could not be read or does not describe a correct ext2 
filesystem.  If the device is valid and it really contains an ext2 
filesystem (and not swap or ufs or something else), then the superblock 
is corrupt, and you might try running e2fsck with an alternate superblock: 
    e2fsck -b 8193 <device> 



sudo e2fsck -C0 -p -f -v /dev/sda2
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda2 
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda2 
Could this be a zero-length partition? 


ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda5 
e2fsck: Bad magic number in super-block while trying to open /dev/sda5 
/dev/sda5:  
The superblock could not be read or does not describe a correct ext2 
filesystem.  If the device is valid and it really contains an ext2 
filesystem (and not swap or ufs or something else), then the superblock 
is corrupt, and you might try running e2fsck with an alternate superblock: 
    e2fsck -b 8193 <device>

---

### Post by oldfred on 2016-03-11
It should give errors on sda2, and extended partition and sda5 swap as those are not partitions with files.

But error on sda1 is an issue.
You can try backup super block(s).

       [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3 (same for ext4)
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks:
sudo dumpe2fs /dev/sda1 | grep -i backup
then use backup superblock, 32768 just an example, try several
sudo fsck -b 32768 /dev/sda5
One user could not get partition unmounted (may have needed swapoff), but used another live distro

---

### Post by JkR4Yne on 2016-03-11
Thanks again - I'm in the process of finding a good block, will post when done.

---

### Post by JkR4Yne on 2016-03-11
Well, I could not find a superblock that worked. It asked me to fix them, which I did- I got errors like "free inodes count wrong for group # 2079". 
After the 5 the 5 th pass, every count would be off so I'd have to hold down the y button for thousands of times- this of course was the most time consuming part.  Then I would get the message that the files system changed, but upon reboot each time it says the OS is still missing.  I really appreciate the help, but I'm to the point where I just want to reformat and do a fresh install.

---

### Post by oldfred on 2016-03-12
I might first check what Smart Data says about drive.
It is in Disks and icon in upper right are other functions. Smart Data is one of them.
All I know is passed it good, but it also can run tests on drive.

---

