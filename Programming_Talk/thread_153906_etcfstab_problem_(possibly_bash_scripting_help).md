---
title: "/etc/fstab problem? (possibly bash scripting help)"
date: 2006-04-02
forum: Programming Talk
---

### Post by stairwayoflight on 2006-04-02
Hi,

I'm pretty new to linux and enjoy messing around with it.. which screws up my box from time to time :-)

Minor problems can be fixed but sometimes i just end up doing a clean install.. this is one of the reasons i switched to ubuntu from gentoo ](*,) 

ok Heres the deal:
I have xp and ubuntu in a dual boot setup on hda, hdb is a 200g with just music, movies and docs on it.

my understanding of permissions is that info is resident in the file system right? (ext3) so if i can't read/write, i have to do a 'chmod' on every file & directory.

i would like a script i can run on the drive in case i install from scratch (ie. ubuntu, new distro, other user names, etc). that way i can just use it. if you have a routine that searches a filesystem and executs foo() on every file, i could just replace that with chmod.

or is there a much simpler way to do this?

thnx

---

### Post by tkiesel on 2006-04-02
Hi stairwayoflight,

You can set permissions for an enitre drive in fstab, and never need to go in and manually set them with chmod.  Even if you did it with chmod, the -R flag lets you chmod massive swaths of the filesystem without needing to go in directory by directory.  :)

Also, if we're talking FAT32 for a partition that Windows and Ubuntu share, there aren't Unix permissions at all to speak of!

When I had a shared Win/Linux media partition, I had it mounted in fstab roughly like this.

/dev/hda1  /mnt/windows  vfat  defaults,umask=0777 0 0

/dev/hda1 you would replace with the location of the partition in question. :)
My memory could be wrong here, but I believe FAT32 was in fstab as vfat.
Also, I didn't mount it at 777 permissions.  You'd change to suit your situation.

Do a bit of research. Don't rely just on me though. ;)

But yeah. Once you tweak it, it's set it and forget it!! :)

---

