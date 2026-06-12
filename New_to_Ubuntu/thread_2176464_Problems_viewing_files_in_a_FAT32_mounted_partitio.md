---
title: "Problems viewing files in a FAT32 mounted partition"
date: 2013-09-24
forum: New to Ubuntu
---

### Post by john113 on 2013-09-24
Hello,

I am new to Linux and just installed Lubuntu 13.04. I recently bought a 32GB SanDisk Cruzer Fit. Since Windows does not recognize more than 1 partition on removable devices, I updated the driver so that it is viewed as a local disk. I wanted one partition to be NFTS so that is could be a Live Lubuntu partition and the other one FAT32 to use as normal storage. The device works on every Windows system I've used it with. However on Lubuntu, both drives are mounted but the only file that appears in the FAT32 partition is a file called $RECYCLE.BIN. I realize that some of the MS Office files may not appear/work, but my pdfs and folders should at least show up. What can I do to view the files?

Thank you in advance for your help!
John

---

### Post by whitesmith on 2013-09-24
Welcome to the forum! Ubuntu and derivatives require an ext3 or ext4 format in order to recognize permissions that are essential for *nix. I think that's your whole problem.

---

### Post by Impavidus on 2013-09-24
> **john113 said:**
> I wanted one partition to be NFTS so that is could be a Live Lubuntu partitionWhat do you mean by that?

Ubuntu can read and write both ntfs and fat partitions, although it's not very good at resizing or repairing ntfs partitions. It's native file system is ext3/4, which you can use too on usb drives, but which aren't recognised by windows, so this is often not very useful. Only the partitions with your Ubuntu installation and your Ubuntu user data must be ext3/4.

All files and directories on your usb drive should be listed in your file manager, even though Ubuntu may not be able to understand all of them. Maybe you didn't properly unmount (safely remove) the drive? In Windows this is usually not essential, as Windows (by default) automatically flushes all writes to usb drives at once, but Ubuntu doesn't, so this may be especially important if you put the files on the drive with Ubuntu.

Another possibility is that the files are hidden. Any filename or directory starting with . (dot) is interpreted as a hidden file/directory and not shown by default. In most file managers (not sure about the one in Lubuntu) you can unhide them with ctrl-h. If you prefer the terminal, use **ls -a**.

---

### Post by walterorlin on 2013-09-24
Ctrl-h does show hidden files in pcmanfm the file manager for lubuntu. You can also get to it from the view menu in pcmanfm.

---

