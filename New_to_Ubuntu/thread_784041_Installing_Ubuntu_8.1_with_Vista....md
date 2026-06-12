---
title: "Installing Ubuntu 8.1 with Vista..."
date: 2008-05-06
forum: New to Ubuntu
---

### Post by Mulenmar on 2008-05-06
Well, I can't give up Vista, or at least XP SP2, without losing my ability to play Halo and Elder Scrolls 3. (No internet, hard to get all the packages for Wine :()

But I've been using Ubuntu and Xubuntu on several of my older computers, and I want to give it a try on my newest computer -- which even Vista runs quickly on. :) I know about roughly how to partition for Ubuntu.

Here's the question: How do I install Ubuntu 8.1 without destroying my ability to boot Windows Vista?

Windows Vista came pre-installed on my machine, and although I  made the HP backup DVDs when I got the computer, I DO NOT have the ordinary Windows Vista installation CD. If this ruins Vista, I'm SOL.

Thx!

EDIT: I can't check to see if this works until this afternoon, but does this look like it would work?

[http://www.pronetworks.org/forum/about78184.html](http://www.pronetworks.org/forum/about78184.html)

---

### Post by ilrudie on 2008-05-06
Generally Ubuntu plays nice with other operating systems as long as you know what all the existing partitions on your disk are.  Its still always a good idea to make a backup of anything you would mind losing.  Most Vista installs come with at least 2 partitions.  1 is where Vista lives and the other will usually be where the restore files are located because some one decided that a 10 cent CD was too expensive to include with a $600+ PC.  I have seen a few that have a 3rd partition for data or automatic backups.  

Resizing the Vista partition and taking a slice of that is the way to go.  You need a / (root) partition and will probably want a small swap partition for Ubuntu (no bigger than the amount of ram installed in the box).  I also recommend making a 3rd /home partition where your personal Ubuntu files will reside.  If you have to reinstall Ubuntu later you can do so without worrying about destroying your music/documents/videos/personal settings/etc...

---

### Post by phr0ze on 2008-05-06
Boot Vista, Put in Ubuntu 8.04 CD and choose the install option on the menu. This installs Ubuntu much like an application (Meaning it can be removed easily and doesn't screw up your partitions)

Thats it.

The biggest problem with this is Hibernate fails to work in Ubuntu. But that isn't a problem for desktops.

---

### Post by baymacdrizzle on 2008-10-18
if you go to the control panel and search "partition" it takes you to disk management where you can shrink the vista partition to make space available for it.

---

### Post by kansasnoob on 2008-10-18
A dual boot is simple and practical. I much prefer it to either a virtual machine or Wubi.

But you should resize Vista only with it's own tools! This simple guide shows how:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

Should you decide you want to go back to pure Vista fine:

> You'll need to restore Vista's mbr. If you have no disc you can get one here:

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Instructions here:

[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You want to "fix boot" and "fix mbr"!

---

### Post by kansasnoob on 2008-10-18
> **baymacdrizzle said:**
> if you go to the control panel and search "partition" it takes you to disk management where you can shrink the vista partition to make space available for it.

+1!

---

### Post by Bones80 on 2009-02-08
I have laptop running Ubuntu 8.04 and Vista. How can I change to 8.1? HDD is 200 Gig, 100 Vista, 100 Ubuntu.
Vic

---

