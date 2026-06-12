---
title: "I think I screwed up...."
date: 2008-06-04
forum: New to Ubuntu
---

### Post by PinkFloydFan on 2008-06-04
During the instalation of Ubuntu, I set my FAT32 partition as /swap

But now I need to change the permissions on this partition, cause I use it for my Thunderbird files. (I dualboot with WinXP and Ubuntu, on both OS's I have thunderbird installed with the same account, and they share these files, that way I have all my emails on both OS's).

I read about changing the /etc/fstab, but I'm not 100% sure.

This is how the partition currently shows up in /etc/fstab:

# /dev/hdc3
UUID=1c9fa9a4-617a-4e51-83ce-12c57017d24c none            swap    sw              0       0

Any idea how I should change this?

Help will be greatly appreciated!

---

### Post by Paqman on 2008-06-04
I don't quite understand what you mean when you say you use your swap part for storing Thunderbird files. The swap isn't ever used to store anything. It's only used by the system.

Also, your swap part won't be formatted as FAT32, it'll be formatted as swap.

---

### Post by Sef on 2008-06-04
Do you have any extra room on your hard disk?  If you do, you could set the spare partition up as a FAT32.

---

### Post by PinkFloydFan on 2008-06-04
> **Paqman said:**
> I don't quite understand what you mean when you say you use your swap part for storing Thunderbird files. The swap isn't ever used to store anything. It's only used by the system.

Also, your swap part won't be formatted as FAT32, it'll be formatted as swap.

So why does it show in Windows as FAT32?

Like I said...I think I screwed up LOL.

Is it necessary to have a swap drive for Ubuntu to function?

> **Sef said:**
> Do you have any extra room on your hard disk?  If you do, you could set the spare partition up as a FAT32.

Yes, it's a 5Gb partition. Should I split this in 2? A 1G swap and 4 G Fat32?

---

### Post by Sef on 2008-06-04
> Is it necessary to have a swap drive for Ubuntu to function?

How much ram do you have?

If you have 1 GB or more, then it may or may not be necessary depending on what you do.  Less than 1 GB, you do need it.

---

### Post by PinkFloydFan on 2008-06-04
> **Sef said:**
> How much ram do you have?

If you have 1 GB or more, then it may or may not be necessary depending on what you do.  Less than 1 GB, you do need it.

I have 1,5G Ram

edit: I just looked on the clock, saw it's already 1am, time for this Floydian to head to bed, tomorrow is a new day,

---

### Post by Paqman on 2008-06-04
You can monitor your memory usage easily by adding a system monitor applet to a panel. If you ever top out your RAM usage, then your system will go hunting for swap space to use. If you never use all your RAM, then you should technically be able to run without a swap partition. Most people have one as a backup though, and it's essential if you want to use hibernate.

With 1.5GB of RAM, I wouldn't expect to be using swap space, but it really depends on what aps you're using.

---

### Post by PinkFloydFan on 2008-06-04
> **Paqman said:**
> You can monitor your memory usage easily by adding a system monitor applet to a panel. If you ever top out your RAM usage, then your system will go hunting for swap space to use. If you never use all your RAM, then you should technically be able to run without a swap partition. Most people have one as a backup though, and it's essential if you want to use hibernate.

With 1.5GB of RAM, I wouldn't expect to be using swap space, but it really depends on what aps you're using.

I don't use any memory hogging programs, I checked, and with firefox and thuinderbird use, it doesn't go above 25% for the memory.

Edit: I opened Firefox, Thunderbird, Pidgin, Update manager, File browser, Openoffice and RhythmBox, and the memory is at 29.1%

---

