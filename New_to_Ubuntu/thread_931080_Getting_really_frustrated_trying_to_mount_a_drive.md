---
title: "Getting really frustrated trying to mount a drive"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by dragon2 on 2008-09-26
i have searched and read posts all day and nothing is helping

now i don't even know if i am doing this correct so if someone can post a list of things to do to create a hard drive please help.

This is what I need:
I created a drive /dev/sdb2 in gparted
I want to call the drive Games & Programs 
Then mount it and have it mounted when I log on automatically

I know i have to create a line in fstab and I would like to mount it in the folder /media/name here

Can someone please help me and walk me through what to do 

THANK YOU IN ADVANCE

---

### Post by perlluver on 2008-09-26
> **dragon2 said:**
> i have searched and read posts all day and nothing is helping

now i don't even know if i am doing this correct so if someone can post a list of things to do to create a hard drive please help.

This is what I need:
I created a drive /dev/sdb2 in gparted
I want to call the drive Games & Programs 
Then mount it and have it mounted when I log on automatically

I know i have to create a line in fstab and I would like to mount it in the folder /media/name here

Can someone please help me and walk me through what to do 

THANK YOU IN ADVANCE

First create /media/name ```
sudo mkdir -p /media/name
```
then you might want to own this so: ```
sudo chown username /media/name
```
then edit fstab
```
gksudo gedit /etc/fstab
```
then you will want to add your lines, so it will look something like this
```
/dev/sda1 /media/name ext3 defaults 0 0
```
Hope this helps you.

---

### Post by wolfen69 on 2008-09-26
also make sure to create an empty line at the bottom of fstab. just go to the end of the last line and hit enter. then save.

---

### Post by dragon2 on 2008-09-26
Thanks all it seamed to work but now just some more question and this is prob a stupid one 

right now it comes up as 191.5GB Media how do i change the volume label 

and also what is the lost+found folder that is on the drive
and how come it says total capacity is 177gb(i am assuming from the format)
and with nothing on it it says 9.5GB is used so the free space is 169.5 gigs 

just wondering if i did everyhting right thats all

---

### Post by -Zeus- on 2008-09-26
> **wolfen69 said:**
> also make sure to create an empty line at the bottom of fstab. just go to the end of the last line and hit enter. then save.

No, I'm pretty sure you don't need that.

---

### Post by perlluver on 2008-09-26
> **dragon2 said:**
> Thanks all it seamed to work but now just some more question and this is prob a stupid one 

right now it comes up as 191.5GB Media how do i change the volume label 

and also what is the lost+found folder that is on the drive
and how come it says total capacity is 177gb(i am assuming from the format)
and with nothing on it it says 9.5GB is used so the free space is 169.5 gigs 

just wondering if i did everyhting right thats all

Ext 3 uses some room for the format, and adds the lost and found folder, as for changing the name, not to sure on that one.

---

### Post by dragon2 on 2008-09-26
i understand that some space is used for the format making it 177 instead of 191. but how come it is saying that on top the space used for the format there is 9.5 gigs used so the available space is 169.5 when there should be no space used and the available should be 177gigs

---

### Post by perlluver on 2008-09-26
> **dragon2 said:**
> i understand that some space is used for the format making it 177 instead of 191. but how come it is saying that on top the space used for the format there is 9.5 gigs used so the available space is 169.5 when there should be no space used and the available should be 177gigs

How big is the hard drive?  Are there any other partitions on it?  For Example mine is 200GB, when I install Linux I only have about 170GB left, because of the partitioning and because of the room it uses.  And also hard drives are not what they are advertised as.  Like a 200GB hard drive is only really around 189GB or so, because of the ratio and how the disks space is laid out.  More info here: [http://en.wikipedia.org/wiki/Hard_drive](http://en.wikipedia.org/wiki/Hard_drive)

---

### Post by dragon2 on 2008-09-27
there is no data whatsoever on the drive the drive is actually 191.5 gigs
it says that there is 9+ gigs of data on it

[http://s377.photobucket.com/albums/oo214/dragon2777photo/?action=view&current=Screenshot-1915GBMediaProperties.jpg]("http://s377.photobucket.com/albums/oo214/dragon2777photo/?action=view&current=Screenshot-1915GBMediaProperties.jpg")

---

### Post by perlluver on 2008-09-27
> **dragon2 said:**
> there is no data whatsoever on the drive the drive is actually 191.5 gigs
it says that there is 9+ gigs of data on it

[IMG]http://s377.photobucket.com/albums/oo214/dragon2777photo/?action=view&current=Screenshot-1915GBMediaProperties.png[/IMG]

Ext 3 uses that space for the file system, for lost+found, and also for journalizing.  Not sure I can explain it better.

---

### Post by dragon2 on 2008-09-27
> **perlluver said:**
> Ext 3 uses that space for the file system, for lost+found, and also for journalizing.  Not sure I can explain it better.

30 gigs for a 190gig hard drive seemed like a lot just for the format and stuff

---

### Post by perlluver on 2008-09-27
> **dragon2 said:**
> 30 gigs for a 190gig hard drive seemed like a lot just for the format and stuff

Indeed, I agree, that is why I used JFS for a while, for example, my 200GB hard drive, formatted as Ext 3, went down to 182GB, and I have 159GB free.  So it does use space.  But with the compression on it I hardly notice.  How did you format the drive?  With gparted or did you format for a system at one time.  Like did you format to install Ubuntu on?  If you did that, then it will be using space for Swap and an extended partition.

---

### Post by perlluver on 2008-09-27
Ok try this, post the output of sudo fdisk -l.  Run that in the terminal, and post back the output.

---

### Post by shafin on 2008-09-27
> **dragon2 said:**
> Thanks all it seamed to work but now just some more question and this is prob a stupid one 

right now it comes up as 191.5GB Media how do i change the volume label 

and also what is the lost+found folder that is on the drive
and how come it says total capacity is 177gb(i am assuming from the format)
and with nothing on it it says 9.5GB is used so the free space is 169.5 gigs 

just wondering if i did everyhting right thats all
To change Volume label, try this:
```
**sudo e2label** /dev/sdb2 Games & Programs  
```

---

### Post by dragon2 on 2008-09-27
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25568   205374928+  83  Linux
/dev/sda2           26177       60801   278124840    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           25569       26176     4883760   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09aa1473

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37518   301363303+   7  HPFS/NTFS
/dev/sdb2           37519       60801   187020697+  83  Linux



it is sdb2 that i am talking about

and i formated with gparted

---

### Post by dragon2 on 2008-09-27
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25568   205374928+  83  Linux
/dev/sda2           26177       60801   278124840    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           25569       26176     4883760   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09aa1473

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37518   301363303+   7  HPFS/NTFS
/dev/sdb2           37519       60801   187020697+  83  Linux



it is sdb2 that i am talking about

and i formated with gparted

---

### Post by perlluver on 2008-09-27
> **dragon2 said:**
> Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25568   205374928+  83  Linux
/dev/sda2           26177       60801   278124840    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           25569       26176     4883760   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x09aa1473

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       37518   301363303+   7  HPFS/NTFS
/dev/sdb2           37519       60801   187020697+  83  Linux



it is sdb2 that i am talking about

and i formated with gparted

Well everything seems ok, except the part about the cylinder error on sda2 that seems weird.

---

### Post by niteshifter on 2008-09-27
Hi,

> **shafin said:**
> To change Volume label, try this:
```
**sudo e2label** /dev/sdb2 Games & Programs  
```

I promise all that the above will not work: The file system label on /dev/sdb2 will be .... Games. Followed by an error that the command Programs could not be found.

The & character, when used in a terminal (fed to the shell) instructs the shell to start the preceding string as a command and return to the shell.

Ponder that for a moment and then think about some arbitrary script run that encounters that file or folder name. **If** the script is well written (quotes it's arguments or variables) then all is well. If it's not: it breaks.

Upshot: don't use & in file or folder names unless you like living on the edge!

---

### Post by vamped on 2008-09-27
> **dragon2 said:**
> there is no data whatsoever on the drive the drive is actually 191.5 gigs
it says that there is 9+ gigs of data on it



By default, 5% of the space is used by the system. Reading the documentation

$ man tune2fs

-m reserved-blocks-percentage
Set  the percentage of the filesystem which may only be allocated by privileged processes. Reserv&#8208;ing some number of filesystem blocks for use by privileged processes is done to  avoid  filesystem fragmentation,  and  to  allow system daemons, such as syslogd(8), to continue to function correctly after non-privileged processes are prevented from writing to the filesystem.  Normally, the  default percentage of reserved blocks is 5%.

This accounts for the 9 Gb of space that it says is used.

You could change it to 1% by:

$ tune2fs -m 1 /dev/sdb2

---

