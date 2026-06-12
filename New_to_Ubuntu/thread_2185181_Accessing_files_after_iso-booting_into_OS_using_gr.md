---
title: "Accessing files after iso-booting into OS using grub2"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by gnometorule on 2013-11-01
Using grub2, I dual-boot into Ubuntu 12.04 and Windows 7. Except for a swap partition, Ubuntu is installed on one logical partition (6).

I added a menuentry in /etc/grub.d/40_custom to iso-boot into Ubuntu 9.10.; the iso file is located on partition 6 in /boot/iso. The entry is added fine, and I can boot into the iso OS.

Booted into it, I can browse through the Windows related files (using Places), but not those on partition 6 relating to Ubuntu 12.04.

(1) Given the current setup, is there any way to access the partition 6 files relating to my Ubuntu 12.04 (command line access description preferred)?; or

(2) Do I need to create a new partition, save the iso there, adust the menuentry to the new location; and then can access partition 6 files after mounting the partition from within Ubuntu 9.10.?

---

### Post by newb85 on 2013-11-01
I don't have an answer, but I suspect the problem is ext4 support.   By default, 12.04 installs to an ext4 partition.   I don't think 9.10 had native support for ext4.

---

### Post by gnometorule on 2013-11-01
That's a good point, but I checked ([https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview](https://wiki.ubuntu.com/KarmicKoala/TechnicalOverview)), and it's natively supported.

---

### Post by oldfred on 2013-11-01
Probably a permissions issue. I notice with all my ISO boots that I cannot directly mount my other partitions.

Does this work even though there is no password.
gksudo nautilus

I noticed with 13.10 dailies some issue with gksu not there, but have not tried after I just I just installed a couple of days ago.

---

### Post by gnometorule on 2013-11-01
> **oldfred said:**
> Probably a permissions issue. I notice with all my ISO boots that I cannot directly mount my other partitions.

Does this work even though there is no password.
gksudo nautilus

I noticed with 13.10 dailies some issue with gksu not there, but have not tried after I just I just installed a couple of days ago.

The command executes fine, both (a) before mounting 'Acer' (my netbook) in Places, and (b) after (it produces some error code, but executes). Not surprisingly, before mounting, I only find iso disk files; after, I see the same as in Places in my question: the Windows files, but not the Ubuntu ones. 

Just to confirm I understand you correctly though: in principle, if you do what I did, you should be able to access your files from the iso OS (after mount)?

---

