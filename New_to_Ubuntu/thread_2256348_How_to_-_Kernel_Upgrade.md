---
title: "How to - Kernel Upgrade"
date: 2014-12-11
forum: New to Ubuntu
---

### Post by Quarkrad on 2014-12-11
I have two 14.04 machines, one scans and the other does not (to the same wireless scanner).   One difference between the two machines (sudo hp-check -r) is that one (does not scan) has  Kernel: 3.13.0-24-generic #47-Ubuntu  whereas the one that does scan has Kernel: 3.13.0-43-generic #72-Ubuntu.  How do I upgrade from -24-generic #47-Ubuntu to -43-generic #72-Ubuntu?

---

### Post by oldrocker99 on 2014-12-11
Try this:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by nerdtron on 2014-12-11
Run the software updater. Kernel updates are there.

---

### Post by Quarkrad on 2014-12-11
Too late I'm afraid - I did it through Synaptic and now messed up my machine (sorry).  It boots to the Desktop and the graphics are wrong (minor) but worringly I do not have any newtwork capability.  There is a ! mark over the icon and I can enable or disable networking but I cannot get a conection (ethernet to router).  I cannot ping my router via the terminal - it says 'Network is unreachable'.   When I installed 14.04 I had a separate \ and \home - would it be quicker to reinstall \?   I think you format \ but not \home for reinstall of just the os.

---

### Post by nerdtron on 2014-12-11
> **Quarkrad said:**
>    When I installed 14.04 I had a separate \ and \home - would it be quicker to reinstall \?   I think you format \ but not /home for reinstall of just the os.

This is the reason why I don't like a separate /home partition. It contain some system settings which can cause conflicts if you install a new version and not format the /home partition.
I also save my data on a separate partition, it's not /home, I create the separate and make it /data. Save all data there and don't make a separate partition for /home.

---

### Post by Quarkrad on 2014-12-11
I have a complete back up of /home and (like you) personal data on a separate partition on a backup hd so I'm OK protection wise.  I guess it will be quicker to re-install \ and make the minor changes to \home re any conflicts.

---

### Post by nerdtron on 2014-12-11
If you already have backup of your data, format the main Linux partitions both the / and /home partitions.

---

### Post by ajgreeny on 2014-12-11
To reinstall you **MUST** use the "Something Else" option at partitioning stage or you may wipe out everything on the disk.

---

### Post by Quarkrad on 2014-12-12
I have reinstalled (using something else) and only changing my \ partition.  Configured as ext4, mount point \ and to format - I did not touch the other partitions including \home.  The install went ok but I now have empty desktop, downloads, documents, etc.   My original \home is there - I can see in nautilus under Devices, it is listed as \home; I guessing this issue is a 'pointing thing'.   How do I point my new install to my orginal \home?

---

### Post by Quarkrad on 2014-12-12
I'm copying from 'old' \home to 'new' \home and then will delete 'old' \home

---

### Post by ajgreeny on 2014-12-12
> **Quarkrad said:**
> I'm copying from 'old' \home to 'new' \home and then will delete 'old' \home

Have you already done this or not?

You may find, depending on the sizes of your old / and /home partitions that you don't have enough space to copy everything across to the new /home folder, now enclosed within root.  It is possible if we know the UUID of the old /home partition to scrap the new /home by mounting the old /home partition with an edit of /etc/fstab.  You can find the UUID of the old partition with ```
sudo blkid -c /dev/null
```then come back here if we're not too late, and well give you the line to add to fstab.
If you know how to edit fstasb already just add the following line with the correct UUID at the bottom of the file, save it, then run ```
sudo mount -a
```to check all is well; if there are no errors from that command it should be fine.
It will, however, perhaps easier to re-install again, but this time after doing exactly what you did last time for the root partition, click on the old /home partition, set it to be used as an ext4 partition (assuming it was ext4 last time) and set the mountpoint as /home, but be absolutely sure to **deselect the Format tick box!**

---

