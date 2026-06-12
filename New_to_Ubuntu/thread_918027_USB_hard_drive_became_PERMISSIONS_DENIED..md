---
title: "USB hard drive became PERMISSIONS DENIED."
date: 2008-09-12
forum: New to Ubuntu
---

### Post by egalvan on 2008-09-12
Ok, I was following a series of posts, trying to teach my self things Linux.
I messed up several items, and will be posting separately.

General Information:
Ubuntu 8.04.1
Kubuntu meta-package installed under Synaptic

Specific information:
Running Kubuntu:

I was "playing" with ownership settings, and seem to have muffed up my external USN hard drive.

Last session, all was well, everything worked, and I could read/write/delete/create on that drive.

Booted up today, and all I get now is 

[COLOR="red"]PERMISSIONS DENIED[/COLOR]

if I try to access the drive.

How do i "reset" this?

It has been working for over four months, 
under Ubuntu (gnomne) and Kubuntu.

Still works under XP

Dolphin shows no info under the  "Owner" tab.

What other info do you need?

---

### Post by cdtech on 2008-09-12
A USB device is auto mounted within the directory "/media". If you type (in a terminal) "ls -la /media/**devicelabel** (devicelabel being the drive) you will see the permissions. Post them here and lets have a looksee.

---

### Post by egalvan on 2008-09-12
OK, this is what i had to type to get this to work,
I tried several different ways, but this was the only success



```
ernest@m7690n:~$ ls -la /dev/sdg1

brw-rw---- 1 root disk 8, 97 2008-09-12 10:54 /dev/sdg1

ernest@m7690n:~$ 

```



further, in case it helps, here is my /etc/fstab
(don't know what else to send, I'm new at this stuff)

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/sda6
UUID=b89bf81f-e350-4400-9ca7-4a7451c5d238 / ext3 nouser,relatime,errors=remount-ro,atime,auto,rw,dev,exec,suid 0 1
# /dev/sda5
UUID=9753c87c-bace-4082-9ae7-0efd8f8d46bb /boot ext2 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda7
UUID=9c673b2e-aeeb-415d-95a8-1be135c4b400 /home ext3 nouser,relatime,atime,auto,rw,dev,exec,suid 0 2
# /dev/sda2
UUID=f091c8ab-aa29-4ca6-a540-b2d0aa1ca924 none swap sw 0 0
/dev/scd1 /media/cdrom0 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/scd0 /media/cdrom1 udf,iso9660 user,utf8,atime,noauto,rw,dev,exec,suid 0 0
/dev/sdg1 <mount\040point> auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
LABEL=100gb /media/100gb auto nouser,atime,auto,rw,nodev,noexec,nosuid 0 0
LABEL=movies /media/movies auto nouser,noauto,atime,auto,rw,nodev,noexec,nosuid 0 0

```

---

### Post by cdtech on 2008-09-12
No, the device is listed within the "/media" directory. I see it mounted under "/media/mount point"

I would create a new directory within /media called sdg1:
**sudo mkdir /media/sdg1**

Then edit this line:
**/dev/sdg1 <mount\040point> auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0**

To this:
/dev/sdg1 **/media/sdg1** auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0

Then run:
**sudo mount -a**

---

### Post by egalvan on 2008-09-12
> **cdtech said:**
> No, the device is listed within the "/media" directory. I see it mounted under "/media/mount point"



OK, here is the result.
I'm either doing something wrong, or I broke something...

```
ernest@m7690n:~$ ls -la /media/100gb
ls: cannot access /media/100gb: No such file or directory
ernest@m7690n:~$

```


Further, I'm new to this stuff, but this doesn't look right to me...
Is it OK? (fstab as it is now, before i do your recommended changes)

```
/dev/sdg1 [COLOR="Red"]<mount\040point>[/COLOR] auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0

```


that "mount\40point" looks wrong...

---

### Post by egalvan on 2008-09-12
What would happen if I disconnect the drive, 
and delete this line from fstab...

```

/dev/sdg1 /media/sdg1 auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
```

and then run 

sudo mount -a


which i take to mean "mount all" or something>?


In other words, try to remove all traces of that USB drive?

---

### Post by cdtech on 2008-09-12
Yes, USB drives are auto mounted once they are plugged in. The directory is automatically create via the label of the device.

Rather than remove, just comment that line:
```
**#** /dev/sdg1 <mount\040point> auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
```

You really should learn to make a backup of any file you edit:
sudo cp /etc/fstab /etc/fstab.bak (for instance)

---

### Post by egalvan on 2008-09-12
> **cdtech said:**
> Yes, USB drives are auto mounted once they are plugged in. The directory is automatically create via the label of the device.

Rather than remove, just comment that line:
```
**#** /dev/sdg1 <mount\040point> auto nouser,atime,noauto,rw,nodev,noexec,nosuid 0 0
```

You really should learn to make a backup of any file you edit:
sudo cp /etc/fstab /etc/fstab.bak (for instance)

My files ARE backed up. I was asking because I don't know what the results of that edit would be....for all I know it would totally crash my system.
I've done that a time or two hundred :)

I'm a newbie with Linux, but I've had 50 years in computers, so I know how easily they can make all your data disappear.
User-generated or computer-generated gremlins, all eat data :)
And not only do I back up my data, but I also back up my computer :lolflag:
I have a second computer on which I have as exact a copy of my main work machine. This is what I am experimenting on.

I love to experiment, therefore I have a much bigger probability of messing things up. I like to change settings just to "see what happens".

I really believe I created this problem by trying to teach myself about permissions., or mount points.

But part of my problems also come from the fact that the 'man' pages are not always clear about what "happens", and "search functions", while often turning up a tremendous amount of information, does not always make it easy to wade through it all.

And I am extremely appreciative of the tremendous help I have recieved here on this forum ( amongst several others that I frequent ).

Among other ways of showing that appreciation, I will seek out "donation" pages on the software that I use on a frequent basis. I may only give two or three dollars, or sometimes more. 
I must admit that this is the only point on which I think this forum is lacking.....voluntary donations to software authors should be suggested a bit more.... "If you like, or use, this piece of software, then consider a small donation to the author"
I haven't found a "donate" button anywhere on this forum, yet.

But I ramble...and I digress...

Back to the problem at hand, my disappearing USB hard drive...:
"Come Watson, the game is afoot!"

guitar:

And please don't think I am complaining, not in the least.

ErnestG

P.S.
I need to reboot my machine,
 and feed my stomach.
back in a few

---

