---
title: "Combing Free Space w/ Filesystem Partition"
date: 2013-09-07
forum: New to Ubuntu
---

### Post by Kanefa on 2013-09-07
I used Clonezilla to backup my 20 GB HD and restore it to my new 80 GB HD.  The problem I am running into is the new HD is is not using 60GiB of space.

This is what it looks like in Disks (Preferences -> Disks).

Filesystem Partition 1 19 GB EXT4
Extended... Partition 2 533 MB
Swap Partition 5 533 MB Sw...
Free Space 60 GB

How can I safely combine the 60 GB of Free Space with the 19 GB from the Filesystem Partition?

---

### Post by r_avital on 2013-09-07
If the 60 GB portion is labeled "free space" then it is usable and available, but only after you create a partition on it.

Use the administrative utility gparted (in a terminal, enter sudo gparted) and you will need the su password.  Once gparted is running, you can either create a partition on the remaining 60 GB free space, or extend/move partitions to suit your needs.

[COLOR=#000000]**Please be very careful with this.  I definitely suggest a tutorial on gparted, and read it carefully,**[/COLOR] [at this location]("http://www.dedoimedo.com/computers/gparted.html").

---

### Post by nerdtron on 2013-09-07
I think this won't be possible. You can only extend/combine partitions that are next to each other.
Unless somebody gives a solution.

---

### Post by Kanefa on 2013-09-07
> **nerdtron said:**
> I think this won't be possible. You can only extend/combine partitions that are next to each other.
Unless somebody gives a solution.

This appears to be the case to me.  The swap partition is in between my free space and the partition I want to grow.

---

### Post by Quackers on 2013-09-07
You could delete the swap partition then extend the partition you wish to extend, then create another swap partition.
But beware that your /etc/fstab file may need to be edited to reflect your new swap partition's UUID change (new number). Otherwise your system may not boot.

---

### Post by Kanefa on 2013-09-08
Thanks Quackers that worked perfectly.  My system did boot without updating the fstab file (there was a blurb about the UUID under the Lubuntu splash screen).  I updated and the blurb went away.

---

