---
title: "HOWTO: Keep Ubuntu From Writing Thumbnails to Disk (Use RAM Instead)"
date: 2009-06-25
forum: Outdated Tutorials &amp; Tips
---

### Post by guywithcable on 2009-06-25
If you're like me, you have some pictures that would best not be stored unencrypted in your thumbnails dir. So here's a way to make Ubuntu keep thumbnails in RAM instead of on the disk.

Run:
```
rm -r ~/.thumbnails/*
```To clear out your thumbnail dir, then run
```
gksu gedit /etc/rc.local
```**Method 1 (Using a RAM Disk with Fixed/Limited Storage)**
Now paste this before the "exit 0"
```
/sbin/mke2fs -q -m 0 /dev/ram0

/bin/mount /dev/ram0 /home/username/.thumbnails

/bin/chmod 777 /home/username/.thumbnails

/bin/chmod +t /home/username/.thumbnails

/etc/init.d/gdm restart
```Save... exit.

Since this method has limited storage, if you don't restart for a long time, the dir may fill up and Nautilus will stop making new thumbnails. The simple way to fix this is to run
```
rm -r ~/.thumbnails/*
```**Method 2 (Using Shared Memory with No Limit)**
Now paste this before the "exit 0"
```
mkdir /dev/shm/thumbnails
```Save... exit.

Now run
```
mkdir /dev/shm/thumbnails && rm -r ~/.thumbnails && ln -s /dev/shm/thumbnails/ /home/username/.thumbnails
```Since this method has no limit on storage, it will keep making thumbnails until you run out of RAM. This shouldn't really be a problem unless you *never* restart.



Now obviously you have to replace "username" with your own name in all the commands.

Once you've completed the steps, restart.

There you go, you should now have no worries about anyone seeing what kind of pictures/videos you've been watching. ;)

---

### Post by Wanas on 2009-06-26
I dont understand why this Howto for :(?
is it for security only or for to make free space or for what ?

---

### Post by lstepnio on 2009-06-26
This is something I've been doing on my laptop (single user system) sporting 4gb of RAM and a SSD drive. 

# /etc/fstab:
tmpfs /tmp tmpfs defaults,noatime,nodiratime,mode=1777 0 0

# ls -al ~ |grep tmp

lrwxrwxrwx  1 lstepnio lstepnio      4 2009-04-10 18:42 .adobe -> /tmp
lrwxrwxrwx  1 lstepnio lstepnio      4 2009-04-10 18:43 .java -> /tmp
lrwxrwxrwx  1 lstepnio lstepnio      4 2009-04-10 18:42 .macromedia -> /tmp
lrwxrwxrwx  1 lstepnio lstepnio      4 2009-04-10 18:41 .thumbnails -> /tmp

also, additional items I have as tmpfs on my laptop:
tmpfs /tmp tmpfs defaults,noatime,nodiratime,mode=1777 0 0
tmpfs /var/tmp tmpfs defaults,noatime,nodiratime,mode=1777 0 0
tmpfs /var/log tmpfs defaults,noatime,nodiratime,mode=0755 0 0
tmpfs /var/cache/apt tmpfs defaults,noatime,nodiratime,mode=0755 0 0

---

### Post by guywithcable on 2009-06-26
> **Wanas said:**
> I dont understand why this Howto for :(?
is it for security only or for to make free space or for what ?

I use it for security. I have some pics that are *cough* personal, and I don't want the thumbnails to be kept in an unencrypted part of the drive. I could have mounted an encrypted volume to ~/.thumbnails but I decided to just go with shared memory, so they never even touch the hard drive. The only downside is that Nautilus has to redraw every thumbnail after a restart, but I have a fast enough drive that it doesn't matter to me.

If you're worried about the space occupied by thumbnails, there is a setting in Nautilus to limit the thumbnail storage.

---

### Post by anaconda on 2010-05-29
Thanks!

I noticed recently that thumbnails are accurate enough to actually read my changing  bank account password from an unencrypted thumbnail!! The actual picture I store in an encrypted volume.

Quite annoying. First I encrypt my sensitive data, and think that they are safe, but later find out that the pictures are actually copied to home/anaconda/.thumbnails AND they were stored there in READABLE form !!!###¤!"  unbeliavable.

One solution is to increase the size of the picture. Then the thumbnail wont be readable any longer.

---

### Post by stinger30au on 2010-05-29
i dont understand why you created a new ram drive for when ubuntu already has a ram drive built in to it already

is location is

/dev/shm

---

### Post by lavinog on 2010-06-01
Why not disable thumbnails.
I find thumbnail generation to be wasteful anyway.  jpeg thumbnails are stored as lossless png files, and sometimes the thumbnail takes up more space than the original.
generating a png thumbnail uses more resources than making a jpeg one also.

Edit:  It looks like you disable thumbnailing or set an age limit with gconf-editor
/desktop/gnome/thumbnail_cache
and
/desktop/gnome/thumbnailers

---

