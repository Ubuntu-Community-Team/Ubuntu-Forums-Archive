---
title: "Directory"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by cristo-father on 2008-05-30
What is the directory of dvd readers?

---

### Post by sdennie on 2008-05-30
Usually it's /media/cdrom.

---

### Post by cristo-father on 2008-05-30
> **vor said:**
> Usually it's /media/cdrom.

Actually it makes sense.
Problem is it doesn't detect the files in the dvd nor in the cd...
Any ideas? Drivers?

---

### Post by sdennie on 2008-05-30
So, there is no output when you type:

```

ls /media/cdrom

```

If not, the output of:

```

cat /proc/mounts

```

Might be useful in helping.  If the DVD isn't getting mounted you'd not see anything in that directory.

---

### Post by cristo-father on 2008-05-30
> **vor said:**
> So, there is no output when you type:

```

ls /media/cdrom

```

If not, the output of:

```

cat /proc/mounts

```

Might be useful in helping.  If the DVD isn't getting mounted you'd not see anything in that directory.

Here is the output.

---

### Post by Tom--d on 2008-05-30
Right.
This DVD a film? Data?
As if its Data. When I burned my data DVD in Vists (was going over to Ubuntu) Ubuntu would not mount it. (and I still don't know why).

And.. When you put the disk in. 
Open up Computer. double click on the cd/dvd rom? what does it say then?

---

### Post by cristo-father on 2008-05-30
> **Tom--d said:**
> Right.
This DVD a film? Data?
As if its Data. When I burned my data DVD in Vists (was going over to Ubuntu) Ubuntu would not mount it. (and I still don't know why).

And.. When you put the disk in. 
Open up Computer. double click on the cd/dvd rom? what does it say then?

It is a Data DVD.
I am not using gnome, i installed ubuntu from the mini iso(i am using icewm).

---

### Post by sdennie on 2008-05-30
If it's burned from Vista it may not be readable on Ubuntu.  Microsoft has decided to default to a not widely embraced disk burning format in Vista.  There are threads somewhere on these forums on how to access those disks or train Vista to not be so evil when burning disks.

---

### Post by sdennie on 2008-05-30
cristo-father: If you aren't using gnome or KDE, I don't know for certain that disks automatically mount (it seems like dbus or hal functionality but, I'm not certain).  If that's not the case, have you previously used powertop and disabled the hal disk polling for your CD drive?

---

### Post by Tom--d on 2008-05-30
> **vor said:**
> If it's burned from Vista it may not be readable on Ubuntu.  Microsoft has decided to default to a not widely embraced disk burning format in Vista.  There are threads somewhere on these forums on how to access those disks or train Vista to not be so evil when burning disks.


Another good reason why Vista is **** :D
Happened to me :(

---

### Post by cristo-father on 2008-05-30
> **vor said:**
> If it's burned from Vista it may not be readable on Ubuntu.  Microsoft has decided to default to a not widely embraced disk burning format in Vista.  There are threads somewhere on these forums on how to access those disks or train Vista to not be so evil when burning disks.

I think i burned it in xp, but with a cd burned in ubuntu the same thing occurred no files detected...
Please help me...

---

### Post by cristo-father on 2008-05-30
> **vor said:**
> cristo-father: If you aren't using gnome or KDE, I don't know for certain that disks automatically mount (it seems like dbus or hal functionality but, I'm not certain).  If that's not the case, have you previously used powertop and disabled the hal disk polling for your CD drive?
It is the first time i read any dvd or cd (in this version of ubuntu).

---

### Post by sdennie on 2008-05-30
If you aren't using gnome or a standard ubuntu configuration, you might try:

```

sudo mkdir -p /mnt/cdrom
sudo mount -t iso9660 /dev/cdrom /mnt/cdrom
cd /mnt/cdrom
ls

```

That's the basic idea.  If udev/hal isn't automounting your CDs that's about all you can do.

---

### Post by cristo-father on 2008-05-30
> **vor said:**
> If you aren't using gnome or a standard ubuntu configuration, you might try:

```

sudo mkdir -p /mnt/cdrom
sudo mount -t iso9660 /dev/cdrom /mnt/cdrom
cd /mnt/cdrom
ls

```

That's the basic idea.  If udev/hal isn't automounting your CDs that's about all you can do.
Thank you so much at last i got to read my precious data...

---

### Post by sdennie on 2008-05-30
I'm glad that helped.  It sounds like you aren't running a fullblown version of Ubuntu.  If you aren't familiar with Unix in general, it may be much easier for you to install the full Ubuntu desktop.  It will do things like this for you automatically.  If you have a network connection and the disk space (Probably about 3G), doing the following should get you a much more user friendly environment:

```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```

---

### Post by cristo-father on 2008-05-30
> **vor said:**
> I'm glad that helped.  It sounds like you aren't running a fullblown version of Ubuntu.  If you aren't familiar with Unix in general, it may be much easier for you to install the full Ubuntu desktop.  It will do things like this for you automatically.  If you have a network connection and the disk space (Probably about 3G), doing the following should get you a much more user friendly environment:

```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```

I do not use gnome because it is to heavy...
How can i auto-mount the dvds or cds?

---

### Post by sdennie on 2008-05-30
I don't know.  The mechanisms involved in automounting are udev and possibly hal.  It may be enough to install those two packages but, it's not something I've tried and so can't say for sure.

---

