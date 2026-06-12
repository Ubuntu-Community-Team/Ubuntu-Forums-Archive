---
title: "Mount HD using liveCD?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by cartisdm on 2008-10-27
I'm playing tech support for a friend of mine over the phone.  He's not very computer inclined so I'm trying to be as simplistic as possible with him.  His windows is corrupted and he can't boot in any longer.  It's on his laptop so he can't access his harddrive to back it up externally (I can't do it for him, he's in Arkansas).

If I gave him step-by-step instructions on downloading and creating a liveCD of Ubuntu, can he do a live session and mount/access his internal harddrive, plug in an external USB harddrive, and back up all his stuff?

---

### Post by cariboo on 2008-10-27
Yes you can mount any drive just like you would running an installed distro. to mount an internal hard drive you would do something like this:

```
sudo mount /dev/hda1 /mnt
```

It depends on what type if hard drive he has, it could be listed as /dev/sda1 also. Get him to run in a terminal:

```
sudo fdisk -l
```

to get a list of the hard drives.

To mount the external drive if the main drive is listed as /dev/sdax then:

```
sudo mount /dev/sdb1 /media
```

Jim

---

### Post by cartisdm on 2008-10-27
Eh.....I'm hoping to avoid any Terminal actions.  Will ubuntu not mount the USB harddrive when it's plugged in?  I mean, if I plug in a drive right now to my computer it just pops up on the desktop.

As for my windows partition, I can go to **Computer** and find **84GB Media**, enter my password, and I'm home free

---

