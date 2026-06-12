---
title: "New to disk formatting"
date: 2016-08-24
forum: New to Ubuntu
---

### Post by hughoranga on 2016-08-24
Hi all

I have downloaded GParted, but I'm not confident about formatting disks. In particular, I would like to format an old external hard drive for backing up my ubuntu 14.04 machine (the disk was originally formatted for mac, so HFS+). I experimented with GParted and only managed to render my usb flash stick thingy inoperable, hence my hesitation. I guess a link to a current tutorial on GPArted that doesn't assume I know how sudo my way out of trouble would be really helpful, but I'm open to any suggestions. Do I need to provide any more information?

Thanks in advance for your help.

---

### Post by oldos2er on 2016-08-24
With the external not plugged in, can you run the *mount* command, post the info here; then rerun the mount command with the drive plugged in, and post the info? It should be easy to determine where the disk is mounted this way.

---

### Post by papibe on 2016-08-24
Hi hughoranga.

A tip:
[LIST]
[*]Open gparted without the external disk connected,
[*]Take note of the current drives so you can avoid them later,
[*]Quit gparted,
[*]Connect the external drive, and count to 10,
[*]Open gparted again. The new drive should be the external one, and it should be safe to re format it.
[/LIST]

Hope it helps. Let us know how it goes.
Regards.

---

### Post by yancek on 2016-08-24
The GParted Manual is available online at the link below to help you get a basic understanding.  You can read it all or just the sections of interest to you and if you have questions, post them here.

[http://gparted.org/display-doc.php%3Fname%3Dhelp-manual](http://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

