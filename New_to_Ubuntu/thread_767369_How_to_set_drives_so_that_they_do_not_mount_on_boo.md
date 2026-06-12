---
title: "How to set drives so that they do not mount on boot"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by avkhatri on 2008-04-25
Basically updating to 8.04 failed and it didn't work so I did a clean install of Ubuntu 7.10. Now whenever I boot up into Ubuntu, once it gets to the desktop it shows my Windows Partition and my Windows Recovery Partition on the left hand side of the screen as if they are a removable media that have just plugged in. It's just that I really do not like anything on my desktop and I like to keep it clean so that's why I'm trying to get them off the desktop. Before I had upgraded to 8.04, Ubuntu 7.10 did not do this, in 7.10 a drive would only mount and show on the desktop when I accessed it from "Places-->Computer". Also, when I try to unmount the drives it says that I do not have sufficient privileges to unmount them and only "root" can unmount them. I tried to go into the console and get root but no luck. Is there a way to stop these drives from mounting at boot? I remember when I was reinstalling 7.10 I saw this window pop-up before I was about to format my Ubuntu partition "Files system doesn't have expected sizes for Windows to like it. Cluster size is 2K (1K expected)" Would this have anything to do with it?

Thanks in advance guys :)

---

### Post by aparigraha on 2008-04-25
try editing fstab, but make a backup copy of the file first:

sudo cp /etc/fstab /etc/fstab_backup

then head [here]("http://ubuntuforums.org/showthread.php?t=283131") to see what fstab is all about.

---

### Post by avkhatri on 2008-04-25
> **aparigraha said:**
> try editing fstab, but make a backup copy of the file first:

sudo cp /etc/fstab /etc/fstab_backup

then head [here]("http://http://ubuntuforums.org/showthread.php?t=283131") to see what fstab is all about.

I would go to the site but it asks me to log into something :(

---

