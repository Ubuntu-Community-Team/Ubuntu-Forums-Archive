---
title: "Where did my partition go?"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by pikeman47 on 2008-07-15
I recently reformatted my comp and put ubuntu on it. I have 250 gig hard drive that i partitioned roughly in half giving me two 120's. The first 120 was to be reserved for Ubuntu and Virtualbox and the second 120 was supposed to be reserved as a storage drive. So I install ubuntu and my storage is nowhere to be found. On a previous ubuntu installation, my spare drives were represented as "## Media" under the Places menu. Now i have nothing and my filesystem is only 120 gigs. So i seem to have lost 120 gigs of space somewhere.
However, when i run gparted, it shows both partitions: /dev/sda1 and /dev/sda2, both being roughly 120 gigs. it also says that sda2 has 63.12 gigs used up, which is curious because i don't think i've put anything on it (unless that 60 is the 60 i allotted for virtualbox). Anyway, is there a way that i can get set up with a storage drive that is represented as "120 gig Media" under the places menu?

PS: While in gparted, the filesystems for sda1 and sda2 are ext3 and the mountpoints for them are 
sda1: /
sda2: /home

Thanks!

---

### Post by annda on 2008-07-15
it looks like the partition intended for storage is actually used as /home. to make sure, check the output of
```
mount
```
and
```
df -h
```

if you are not sure what they mean, post the contents here.

---

### Post by natirips on 2008-07-15
You can find them under "/" and "/home". So everything you save in your /home/... folders will be on /dev/sda2 partition, everything else will be on /dev/sda1. BTW, it is not necessary to specifically make a /home partition, if you don't make in specially, your /home will be a simple directory/folder under / (root).

So for example I have:
/dev/sda1 mounted as /
/dev/sda2 mounted as /media/sda2
So my /home is on /dev/sda1.

---

### Post by bobnutfield on 2008-07-15
annda beat me to the answer.  Your description of the gparted report on your drive gives you the answer.  There is no media partition for storage because it has been used for /home.  Now, /home can still certainly be used for storage and that in fact may be what you indended.  Should you ever reinstall, you can keep your /home partition intact.

---

### Post by pikeman47 on 2008-07-15
Thanks for the help guys, i think i've got a better grasp on how ubuntu organizes things now. 
another question: if my /home drive is saving all my files, how can i access the / drive to use it as a storage, since that drive has over a 100 gigs free?

---

### Post by pikeman47 on 2008-07-15
The output of Mount:

> /dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda2 on /home type ext3 (rw,relatime)
none on /proc/bus/usb type usbfs (rw,devgid=124,devmode=666)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/WD Passport type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb2 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
gvfs-fuse-daemon on /home/josh/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=josh)

and  df -h:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             111G  5.2G  101G   5% /
varrun                760M  120K  760M   1% /var/run
varlock               760M     0  760M   0% /var/lock
udev                  760M   60K  760M   1% /dev
devshm                760M   36K  760M   1% /dev/shm
lrm                   760M   39M  721M   6% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             120G   67G   47G  59% /home
/dev/sdc1             112G  106G  6.8G  94% /media/WD Passport
/dev/sdb2              75G   69G  6.2G  92% /media/disk
gvfs-fuse-daemon      111G  5.2G  101G   5% /home/josh/.gvfs


sdc1 and sdb2 are an external hard drive and an internal hard drive, respectively

---

### Post by natirips on 2008-07-15
> **pikeman47 said:**
> Thanks for the help guys, i think i've got a better grasp on how ubuntu organizes things now. 
another question: if my /home drive is saving all my files, how can i access the / drive to use it as a storage, since that drive has over a 100 gigs free?

Try in console:```
gksudo nautilus
```if using Ubuntu, or```
kdesudo konqueror
```if using Kubuntu (shame on me, I don't know for the other versions).
Then go to your root directory ( / ), and make a new directory/foler, now right-click it and open properties, then search the tabs and find the owner, change it to your self. Now you can use this folder/directory for your stuff.
Many people might say this is not elegant, but what's the fuss anyway XD.

P.S.: Remember to close the root nautilus after you're done with it, as using it further might cause ownership troubles later.

---

### Post by annda on 2008-07-15
> **pikeman47 said:**
> if my /home drive is saving all my files, how can i access the / drive to use it as a storage, since that drive has over a 100 gigs free?

/home partition is where all your user files and settings are stored, and the root (/) partition is where the system and applications are installed. as you can see, this is only a little different than windows.

but it's not a good idea to use / as storage, just as you wouldn't want to put your photos or mp3s in c:\windows\system 

---UPDATE: what natirips suggests is possible and easy, but i believe the reason of having separate storage should be to protect it from any risks. linux IS very stable, but at some point something may go very wrong and you might prefer to reinstall it rather than spend a lot of time discovering and correcting errors.---

i recommend using gparted from the livecd to shrink / and create another partition for your data in the empty space. it's safe to carve out at least some 80 GB (you need to leave some space for new programs and system updates).

when you create the new partition, give it a label in gparted (e.g. storage). then you can mount in permanently under /media.

---

### Post by bodhi.zazen on 2008-07-15
> **bobnutfield said:**
> annda beat me to the answer.  Your description of the gparted report on your drive gives you the answer.  There is no media partition for storage because it has been used for /home.  Now, /home can still certainly be used for storage and that in fact may be what you indended.  Should you ever reinstall, you can keep your /home partition intact.

It's OK bobnutfield, they ignore me sometimes too :)

---

### Post by pikeman47 on 2008-07-16
Wow, thanks guys.
that live cd idea worked like a charm. i shaved off about 80 gigs and repartitioned to get that storage partition i was looking for. 
thanks a ton

---

