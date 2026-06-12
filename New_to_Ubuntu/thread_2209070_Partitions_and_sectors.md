---
title: "Partitions and sectors"
date: 2014-03-03
forum: New to Ubuntu
---

### Post by bjngchn on 2014-03-03
Are partitions and sectors hardware or software things? I heard things like bad partition, bad sector. Are these fixable? If yes, in my mind, these are soft things. If there is a bad partition or sector, is this fixed after the whole disk is formatted with a new installation, or will they continue to give errors and create problems?  ... Can LVM be used to fix such problems? Can part of a computer's harddisk remain untouched because the installation CD misses that part of HD and ignores it, and it may contain lots of data invisible to computer admin?

---

### Post by phidia on 2014-03-03
Bad sectors can be caused by a physical problem and/or formatting. Although the explanation [here]("http://www.auslogics.com/en/articles/bad-sector/") is windows based it's relevant none-the-less.

---

### Post by hebrewofyhwh on 2014-03-03
In my limited expereince with computers and also a very new user of Ubunto 12.04, I will make this statement about bad sectors  and bad partitions. When a hard disk begins to fail it is time to get a new hard disk. I have found that hard disks generally last about  five (5) years. Very rarely have  I got a hard disk to last longer than five (5) years.  When I hav e pushed the envelpoe of  five (5) years I have lost the gamble  in almost every case.  (Losing the gamble means complete failure.)

I forgot to answer: it is a hardware problem.  If I am mistaken somebody with more beans than I can correct me.

---

### Post by oldfred on 2014-03-03
Physical failure can be checked with Smart Status of drive. Generally passed it good, anything else is a new drive.
You can use Disks or Disk Utility to check status of drive. 

Abnormal shutdown due to power failure or just turning off computer incorrectly can corrupt file system. Then chkdsk from a Windows system on NTFS or FAT32 formatted partition may repair it. Or fsck on Linux ext family of partition formats. Other formats may have different tools.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1


 Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

