---
title: "wow, large hard drive!"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by jimclarke on 2008-04-30
I just installed the final release of Hardy on my computer and when I went to Applications>Accessories>Disk Usuage Analyzer, it tells me that Total filesystem capacity 456.4 GB (used: 4.8 GB available: 451.6 GB)

As the hard drive is only a 250 GB (seagate ST3250620A), where does the extra disk space from? or has Hardy heron been feeding on corn mash and has become confused?

---

### Post by ibutho on 2008-04-30
Could be a bug in the app. Run the command "df -h" and see if that shows reasonable output.

---

### Post by jimv on 2008-04-30
Well that's damn odd.

Try this:

sudo apt-get install smartmontools

sudo smartctl -a /dev/hda (or /dev/sda if you have a sata drive)

What does it say under === START OF INFORMATION SECTION === for your drive size?  This should be the correct size, because SMART pulls that directly from the drive.

---

### Post by Moop on 2008-04-30
Do you have more than one hdd?

---

### Post by master5o1 on 2008-04-30
[COLOR="Magenta"]It's a feature in Ubuntu, PhantomGB. It allows you to use 200% of you hard disk. Quite useful really.[/COLOR]

---

### Post by Dark Aspect on 2008-04-30
Go to edit and then preferences and you should be able to see why the disk analyzer does that.It combines ALL other file systems including your cd-rom,I don't why it does that by default.Just select you hard drive mount point and it will work.

---

### Post by jimclarke on 2008-05-01
wow, so much good help. really appreciate it people. 

Only a single hard drive system. 1 cdrw, 1 1.44 floppy and 1 ls120 drive.

go it working good now:)
unchecked gvfs-fuse-daemon and it shows only the harddrive it's self.

---

