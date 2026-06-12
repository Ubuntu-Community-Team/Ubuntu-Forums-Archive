---
title: "Directing install to specific partition"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by dluzius on 2012-03-03
How do I direct an install off a live cd to to a specific partition, to avoid overwriting OS on two other partitions?
Tks in advance, dave ;)

---

### Post by audiomick on 2012-03-03
When the installer gets to the point where it asks "use whole drive" or "install beside", there should be another option called "something else" or something similar to that. Choose that option to get to the manual partitioning tool. There, you can choose partitions on your drive and tell the installer what to do with them.

You might want to boot into the live environement and have a look at your drive with gparted before you start the installation. This will give you a chance to have a really good look at what is on the drive, write down partition names and what is on them, and things like that.

---

