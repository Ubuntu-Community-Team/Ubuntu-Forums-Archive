---
title: "HOW TO: No need for a &quot;Data&quot; partition"
date: 2009-08-19
forum: Outdated Tutorials &amp; Tips
---

### Post by theozzlives on 2009-08-19
If you're just setting up a separate partition to share documents between Windows and Ubuntu on your dual-boot system, there's no need. You can share Windows Documents and Settings folder and have it in your /home folder (partition).

First, you need to create your folders:
```
sudo mkdir /mnt/windrv
sudo mkdir /home/Documents\ and\ Settings
```

Then you'll have to edit fstab:
```
gksudo gedit /etc/fstab
```

You want to put the following lines in it:
```
/dev/sdaX /mnt/windrv ntfs relatime 0 1
/mnt/windrv/Documents\040and\040Settings /home/Documents\040and\040Settings none bind 0 0

```

Where "X" is would be your Windows partition (normally sda1). Now your ready to try it:
```
sudo mount -a
```

You should have /home/Documents and Settings now.

EDIT: An afterthought:

If security is an issue, you can create say /home/steve/data, have the mount point to Documents and Settings/Steve, then make the mount point /home/steve/data (assuming the username is Steve). Just have a set of lines in the fstab for each user that wants to share Windows documents. The possibilities are endless.

This can easily be changed to "Users" instead of "Documents and Settings" for Windows Vista and 7.

---

