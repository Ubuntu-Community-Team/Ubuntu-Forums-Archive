---
title: "[SOLVED] Half drives invisible"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by SACHINVD on 2008-08-20
I have total 4 drives with FAT32 format.
in Ubuntu i am able to see only 2 drives 

What i should do to see all drives ?

---

### Post by Bucky Ball on 2008-08-20
They are possibly not mounted. Please open a terminal and type the following command:

sudo fdisk -l

Post the result (copy and paste into next post). Do you see all your hard drives there?

They should look like (for SATA drives);

sda
sdb
sdc
sdd

All with their appropriate partitions, if you have made any on the drives.

---

### Post by SACHINVD on 2008-08-31
I got the result

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdcfddcfd

   Device Boot         Start           End        Blocks     Id     System
/dev/sda1   *              1          2433      19543041      c     W95 FAT32 (LBA)
/dev/sda2               2434          7969      44467920      f     W95 Ext'd (LBA)
/dev/sda3               7970          9729      14137200      c     W95 FAT32 (LBA)
/dev/sda5               2434          4866      19543041      b     W95 FAT32
/dev/sda6               4867          7299      19543041      b     W95 FAT32
/dev/sda7               7300          7907      4883728+      83    Linux
/dev/sda8               7908          7969      497983+       82     Linux swap / Solaris
 

All drives are in the result

---

### Post by Bucky Ball on 2008-08-31
Okay. Fat32 present and correct as you say, but if the entries are not in your /etc/fstab then they are not mounting.

FAT32 (or vfat) need to be mounted with permissions at boot (they can be mounted later, but the permissions will not be set).

Type in terminal:

**nano /etc/fstab**

... and post the output here. You will probably (probably) notice that the entries for the two vfat drives that are mounting are different in there than the two that aren't. In fact, the two missing drives are probably missing from fstab also. If they are, should be reasonably straightforward to put their entries in there (or change the ones that are).

Just one thing ... all these drives/partitions are showing as being on sda1, which is weird. Each drive should be as I mentioned in the last post:

sda, sdb, sdc, etc.

sda1, sda5, sda6 etc indicates ***partitions*** on one drive (sda). Do you mean 4 *partitions* rather than drives?

Anyways, also try:

**sudo blkid**

and post that result as well and we'll see how we go from there. That will be about all the info we need to get those suckers visible. I'm guessing sda5 and sda6 are the missing ones. ;)

---

### Post by SACHINVD on 2008-09-02
Output of Command sudo blkid is

sachin@sachin-desktop:~$ sudo blkid
[sudo] password for sachin: 
/dev/sda1: UUID="8C34-E287" TYPE="vfat" 
/dev/sda5: UUID="40FB-5D61" TYPE="vfat" 
/dev/sda6: UUID="71BA-188B" TYPE="vfat" 
/dev/sda7: UUID="b429c48a-13c7-4c89-8009-3cff0d1dd977" TYPE="ext3" 
/dev/sda8: TYPE="swap" UUID="199dc4e7-7eaf-4b20-9fbc-13a9f3a9b2c4" 
/dev/sda3: LABEL="LOCAL DISK" UUID="9828-10D6" TYPE="vfat" 
sachin@sachin-desktop:~$

---

### Post by SACHINVD on 2008-09-02
Output of nano/etc/fstab 


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=b429c48a-13c7-4c89-8009-3cff0d1dd977 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda8
UUID=199dc4e7-7eaf-4b20-9fbc-13a9f3a9b2c4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by Bucky Ball on 2008-09-03
Sorry, been busy with uni stuff.

Okay. As suspected, your patitions are not mounted, simple as that. :)  Open a terminal and type (copy and paste is easier):

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup**

This backs up your menu.lst in case anything screws up. (In case, but if you just copy and paste from the forum to your terminal should be no problems). Next, type:

**cd /media**

This will take you to your /media directory. Next you will create a mount point for your vfat drive. First off, we'll tackle the partition at /sda1. Decide what you want to call it and type this, making sure you are in the media directory (it should look something like 'sachin@sachin-desktop media:~$' and then the cursor ready to type):

**mkdir THE_NAME_OF_YOUR_vFAT_DRIVE**

'THE_NAME_OF_YOUR_vFAT_DRIVE' meaning the name you have decided on for this drive. Then type:

**dir**

... and check that the directory you have just created is in your /media directory. If it is, all is well. Now, open up your /etc/fstab file by typing:

**sudo nano /etc/fstab**

... and add this entry as the last, underneath the rest (copy from here and paste into terminal):

[B]# /dev/sda1
UUID=8C34-E287     /media/YOURDRIVENAME       vfat    defaults,umask=0002,gid=46 0  0
[/B]
... making sure '/dev/sda1' has a return after it (is on a separate line from the rest of the info like your other entries in there). '**YOURDRIVENAME' **refers, of course, to the mount point and its name you have just created.Now, type (one at a time, not both at once):

[B]sudo umount -a
sudo mount -a[/B]

This unmounts then mounts your partitions and drives. Cool. Go to the drop down menu 'Places' on the desktop. Does your fat partition appear there under the name you have given it? If so, great! Either way, **restart your machine** and try drag and dropping a file into that partition to make sure permissions are set correctly. If so, we can proceed with the others. If not, we can fix that first, then go on. You can probably see what we have done here and can mount the rest, but let me know how you go. 

:)

---

### Post by SACHINVD on 2008-09-03
Thanks a lot

Now all drives sorry partitions are visible 

Can u give me ur e-mail id,
if i get problems in ubuntu i will directly contact u

Thanks again

---

### Post by velociraptor101 on 2008-09-03
giving me an error when i try to create a directory "permission denied"

---

### Post by Bucky Ball on 2008-09-03
A pleasure. U can private message me here, no problem. Just click on my name. Are they mounting with permissions? You can drop files onto the partition and you don't get an error?

If you need help setting up the other partitions with mount points let me know, but basically, repeat what you just did for each one. Just wanted to get one happening to make sure the permissions were right for your machine before going for the rest. As long as you can access the partitions and get data on and off, go ahead with the rest.

Best idea is to 'mkdir NEWPARTITIONNAME' for each partition while you are in media directory, then type 'dir' to make sure they are all there, then they have somewhere to mount to. Then follow the steps for /etc/fstab.

:)

*** velociraptor - right back and should be able to fix that, need to switch on lappy.

---

### Post by Bucky Ball on 2008-09-03
Okay, for the permissions problem in terminal:

**sudo nano /etc/fstab**

and try this:

```
# /dev/**sda8**
UUID=**4893-E3A6**        /media/**fatso**    vfat    defaults,umask=0002,gid=46 0 0
```

You need to change **/dev/sda?** to the correct sda number for your partition.
Change **UUID=** to the correct number for your partition (find with 'sudo blkid')
Instead of **/media/fatso**, change to **/media/thenameofyourmountpoint**

And that should get your permissions. As I say, vfat drive permissions cannot be changed except on boot, so you have to reboot or **umount -a** then **mount -a** for changes to take effect.

SACHINVD - I know a lot about a couple of things, a little about a lot of things and nothing much about lots of other things, so if you have a specific problem, you are better off posting it in the right forum for that issue. I am around in most of them, the ones I do not frequent, folks with a better understanding of those issues are and 99% of people here are friendly and helpful. :) Having said that, feel free to PM.

Don't forget, when you fix a problem, go to 'Thread Tools' and mark the thread as 'Solved' so others can find it for a fix for their problems. If someone helps you with a fix and you want to thank them, you can click on the little blue star and ribbon in the bottom right of their post. Again, glad to help and good luck, welcome to the community and have fun with the best OS on the planet (at least for me).

---

### Post by Bucky Ball on 2008-09-03
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

A bit of info on fstab.

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Info on mounting from a forum post ... really excellent and informative.

Cheers. :)

ps: let me know how you go with the permissions, _veliociraptor101._[]("http://ubuntuforums.org/member.php?u=641790")

---

