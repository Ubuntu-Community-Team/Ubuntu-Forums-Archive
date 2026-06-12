---
title: "Installing Lubuntu"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by Sigord on 2014-06-16
If I try to install Lbuntu on and older PC will it give me the option to install it in an existing spare Partition alongside Windows XP? The partition is empty apart from another SYSTEM VOLUME INFORMATION and RECYCLER folder. Which perhaps explains why I cannot delete the partition.

Thanks

---

### Post by Impavidus on 2014-06-16
You can't install Lubuntu in a Windows partition (well, there is a hack but that's no longer supported), but you can use the Lubuntu live disk to delete that Windows partition to ceate unallocated disk space. Open a tool called gparted, click on the empty partition and click delete. Then the installer should give you the option to install Lubuntu alongside Windows. It will automatically create Linux partitions in the unallocated space.

---

### Post by sudodus on 2014-06-16
There is a bug (or lack of exact message) in the desktop installer, so that you might think that you install Lubuntu (or any other Ubuntu flavour) alongside Windows, but actually you will overwrite Windows.

See this link

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

So please do not use any of the automatic or semi-automatic options unless you want to use the whole drive. Instead, when you arrive at the partitioning window in the installer, select ***Something else***, and select or create partitions manually (one big root partition and one small swap partition).

I think it is easier to 'see what you have and what you make' with ***gparted***, so I suggest that you create the partitions with gparted, and then use them at ***Something else*** in the installer.

If you want to hibernate, you need at least as much swap as RAM in Gibibytes. Otherwise it is problably enough with less, for example 512 MB or 1 GB. Lubuntu's root partition '/' should be at least 4 GB, but I would recommend at least 8 GB. Otherwise it will soon be full.

---

### Post by mastablasta on 2014-06-16
> **Impavidus said:**
> ... but you can use the Lubuntu live disk to delete that Windows partition to ceate unallocated disk space... you can and it could break the XP install. especially if you gave some hidden system files on it.

---

### Post by LastDino on 2014-06-16
Use only windows partitioning tool to create free disk space.

---

### Post by Impavidus on 2014-06-16
> **mastablasta said:**
> you can and it could break the XP install. especially if you gave some hidden system files on it.
Yes, you may be right. There could be a valid reason why WinXP refuses to delete that partition. Thanks for reminding me.

Another option would be to try and use Windows tool not to delete that partition, but shrink it to something very small (if it allows that) and then use gparted to create new partitions for Lubuntu.

---

