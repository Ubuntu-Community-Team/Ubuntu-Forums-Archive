---
title: "migrating a small drive to a large one?"
date: 2008-12-08
forum: Other OS Talk
---

### Post by hardyn on 2008-12-08
Curious on what anybody can recommend for moving the a windows server 2003 (ntfs) from a small drive to a large one?

now i understand that there are ghost and other GPL tools for creating disk images that can be transferred, but what to do about the partition?  I do not have the option to add a second data partition.

there is no raid or anything like that, just a single disk to a single disk.  i would like to connect the drives in an IDE channel one master/slave setup transfer the data, then remove the small disk from the system.

Thanks for any help.

---

### Post by MeURi on 2008-12-08
Well, you can clone the partition, and then resize it using [Gparted Live](http://gparted.sourceforge.net/livecd.php).

I have never cloned partitions, so I cannot advise you for that step. But enlarging the partition once it has been cloned to the new hard disk should be possible without issues.

My just two cents.

---

### Post by smoker on 2008-12-08
most hard drive manufacturers have free applications that you can download from their respective support sites for this purpose, i would check this out first.

---

### Post by hardyn on 2008-12-08
smoker,

didn't know that, thanks; that is BY FAR the easiest solution.

---

### Post by withgamescom on 2008-12-10
good!~  lol````[[color=white]www.gold4rs.com[/color]](http://www.gold4rs.com/)[[color=white]www.withgames.com[/color]](http://www.withgames.com/)

---

