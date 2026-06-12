---
title: "System cannot find or mount &quot;/&quot; partition"
date: 2012-11-27
forum: New to Ubuntu
---

### Post by jonSnow on 2012-11-27
Hello,
I am very new to linux, I have win7 and ubuntu on same machine.
Today during ubuntu update computer stopped working so I rebooted from button.
When I try to login to ubuntu I got this message: System cannot find or mount "/" partition... and the options: 
s- skip and m- manual solve this problem...

how can I solve this problem? 
thx

---

### Post by oldfred on 2012-11-27
Welcome to the forums.

Now you may have two issues. If in a middle of an update, that needs to be resolved. But writing and forcing shutdown may corrupt file systems.

From liveCD lets do filechecks to see if that resolves it. Change from sdb1 to your Linux install. If not known run this to see Linux ext3 or ext4 partitions.
sudo fdisk -lu

If more than one ext4 partition run commands below on each.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition [COLOR=Red]sdb1[/COLOR] to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/[COLOR=Red]sdb1[/COLOR]
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/[COLOR=Red]sdb1[/COLOR]
    
Best when forcing a shutdown to remember the elephants.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by jonSnow on 2012-11-27
Sry, I don`t think I understood exactly what you were saying. I did this:
Booted from the linux cd
then in the terminal:
sudo fdisk -lu
i got listed 
/dev/sda1
Partition 1 does not end on cylinder boundary.
/dev/sda2
...
/dev/sda6



then I typed in:
sudo e2fsck co -p -f -v /dev/sdb1

then... I didn`t know what to do anymore, I tryed typing p, or  "-p" but nothing....


can`t I just reinstall ubuntu, without afecting my windows partitions?

---

### Post by oldfred on 2012-11-27
When you run sudo fdisk you get a listing of partitions. If dual booting with Windows some will be LInux and some Windows.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   115330634    57665286    7  HPFS/NTFS/exFAT
/dev/sda2       156296385   312576704    78140160   83  Linux
/dev/sda4       115330635   156296384    20482875    b  W95 FAT32

```
So from my example above the only LInux partition is sda2, so I only need to run e2fsck on sda2. First example was with sdb1 which would be a second drive's first partition.
sudo e2fsck -C0 -p -f -v /dev/[COLOR=Red]sda2[/COLOR]
But you still have to use your partitions not my examples.

If you reinstall Ubuntu you have to use manual install to overwrite your existing install or else the auto installs will try to shrink existing space and install another copy of Ubuntu. You reinstall if you have nothing that you want to save from Ubuntu.

---

### Post by jonSnow on 2012-11-28
Ok, so i have two partitions that have "Linux" at the end  sda5 and sda6.
i typed:
sudp e2fsck -p -t -v /dev/sdb5
and
sudp e2fsck -p -t -v /dev/sdb6

i got same result:
the superblock could not be read or does not describe a correct ext2. If the device is valid and it really contains...then the superblock is corrupt and you might try running e2fsck with  an alternate superblock
e2fsck -b 8193 <device>

so I typed:
sudo e2fsck -b 8193
and nothing happened

---

### Post by audiomick on 2012-11-28
> **jonSnow said:**
> an alternate superblock
e2fsck -b 8193 <device>

so I typed:
sudo e2fsck -b 8193
and nothing happened


I think you have to point this
```
e2fsck -b 8193 <device>
```

at something, i.e. put a real device where <device> is.

That would be something like

```
e2fsck -b 8193 /dev/sdx1
```

You must, of course, work out which partition on your setup you want the command to work on.

---

### Post by oldfred on 2012-11-28
If one of the Linux partitions is Linux swap you cannot run e2fsck on that, just Linux partitions.

This will also show file system, not just type. Post what it outputs.

       sudo parted /dev/sdb unit s print
    
       [http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)
Remove first inode to use alternative superblock:
[http://ubuntuforums.org/showthread.php?t=1682038](http://ubuntuforums.org/showthread.php?t=1682038)
Using alternative superblock to check ext3
[http://planet.admon.org/using-alternative-superblock-to-check-ext3/](http://planet.admon.org/using-alternative-superblock-to-check-ext3/)
List backup superblocks, change to sdb6 if sdb5 is swap:
sudo dumpe2fs /dev/sdb5 | grep -i backup
then use backup superblock, [COLOR=Red]32768 just an example[/COLOR], try several
sudo fsck -b [COLOR=Red]32768 [/COLOR]/dev/sdb5

---

### Post by jonSnow on 2012-11-29
sorry, but I reinstalled and... problem solved.
thx for your help.

---

