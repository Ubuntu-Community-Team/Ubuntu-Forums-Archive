---
title: "Dual-booted with Windows 7, Dropbox folder (on Win7 partition) missing on startup"
date: 2014-10-09
forum: New to Ubuntu
---

### Post by Epistimi on 2014-10-09
I recently installed Ubuntu alongside Windows 7, and I keep most of my documents on the Windows 7 partition (ntfs), simply accessing them through Ubuntu. In Windows I use the Dropbox folder as my main "documents" folder for automatic backup (also taking regular backups to (an) external drive(s)), and after installing Ubuntu I also installed Dropbox, following [this guide]("http://www.dropboxwiki.com/tips-and-tricks/share-your-dropbox-folder-between-windows-and-linux-using-a-data-partition#Method_A"). However, on startup I get [this error message]("http://i.imgur.com/Lhnahh1.jpg"). I did some Googling and it seems like the problem is to do with Dropbox looking for the folder before the Windows partition has been mounted on startup, which I think happens automatically. I certainly don't mount it manually, but it happens. I found [this]("http://ubuntuforums.org/showthread.php?t=2111361") thread and followed [this]("https://help.ubuntu.com/community/MountingWindowsPartitions") guide for mounting the Windows partition on startup, but, assuming I did it correctly, hasn't resolved the issue.

I didn't create a directory for the partition as it was already located in /media/Windows7_OS.

I added the following to the /etc/fstab file:

```
UUID=9E5C5C425C5C16FD  /media/Windows7_OS  ntfs-3g  defaults,windows_names,locale=en_GB.utf8  0 0
```

According to the article, this is a "general-purpose read-write mount", which fits my needs.

By the way, looking up my locale with "locale" outputs the following:

```
LANG=en_GB.UTF-8
LANGUAGE=en_GB:en_US:en
LC_CTYPE="en_GB.UTF-8"
LC_NUMERIC=en_US.UTF-8
LC_TIME=en_US.UTF-8
LC_COLLATE="en_GB.UTF-8"
LC_MONETARY=en_US.UTF-8
LC_MESSAGES="en_GB.UTF-8"
LC_PAPER=en_US.UTF-8
LC_NAME=en_US.UTF-8
LC_ADDRESS=en_US.UTF-8
LC_TELEPHONE=en_US.UTF-8
LC_MEASUREMENT=en_US.UTF-8
LC_IDENTIFICATION=en_US.UTF-8
LC_ALL=
```

I live in Denmark but find it convenient for Ubuntu to be in (British) English. Initially it was in American, but I changed the order of preference in Language Support and rebooted before trying the above. I thought maybe this was an issue.

I don't really know what to do at this point, though if there isn't any solution, I suppose manually starting Dropbox is an option. Any help would be greatly appreciated, though. Also, I was a bit unsure where to post this, so if this is in an awkward place, I apologise.

---

### Post by oldfred on 2014-10-09
I do not use dropbox, but see that you use links.

Since you originally set link to a default mount type location, but then created a permanent mount with fstab did you update link to new mount location?

---

### Post by nerdtron on 2014-10-09
Seems about correct on your fstab entry but** /media/Windows7_OS** is not enough since dropbox is looking for the path** /media/dannynh/Windows7_OS** path.
See the difference? Update your fstab entry and reboot to try again.

---

### Post by Epistimi on 2014-10-09
> **nerdtron said:**
> Seems about correct on your fstab entry but** /media/Windows7_OS** is not enough since dropbox is looking for the path** /media/dannynh/Windows7_OS** path.
See the difference? Update your fstab entry and reboot to try again.
This seems to have worked. Thank you! Completely missed that.

---

