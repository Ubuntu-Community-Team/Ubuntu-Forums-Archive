---
title: "expanding the ext3 partition"
date: 2008-09-09
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-09-09
while installing ubuntu8.04,i had allocated 4GB for the installation and a 4 GB ext3 drive with ubuntu installation was thus created.now i want to expand it to 8 GB?how can i do that?

---

### Post by wolfen69 on 2008-09-09
download the [Gparted]("http://downloads.sourceforge.net/gparted/gparted-live-0.3.7-7.iso?modtime=1215010676&big_mirror=0") live cd and use that.

---

### Post by P13808 on 2008-09-09
Get the installer cd.  When going through installation, resize the partition with the partitioner and then quit the installation.  (BTW, you can't resize ext3 while it's in use).

---

### Post by monolux on 2008-09-09
> **stonecoldjha said:**
> while installing ubuntu8.04,i had allocated 4GB for the installation and a 4 GB ext3 drive with ubuntu installation was thus created.now i want to expand it to 8 GB?how can i do that?

This will also depend on how you used your HD. If you need space I recommend you creat a ***fat32*** partition(because you probably have windows in your pc), and this extension is relly compatible with linux and windows.

---

