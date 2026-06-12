---
title: "Difference between external fileystem and remote filesystem"
date: 2016-02-13
forum: New to Ubuntu
---

### Post by Salvatore_Palomino on 2016-02-13
Hello all!

In **Introduction to Linux: A Beginners Guide** 

   [http://tille.garrels.be/training/tldp/ch03.html](http://tille.garrels.be/training/tldp/ch03.html)

I am confused on the difference between an external filesystem and remote filesystem. The two are mentioned in table 3.2, where the author talks about /mnt and /net.



Any help is much appreciated!

---

### Post by papibe on 2016-02-13
Hi Salvatore_Palomino.

Most of that are general conventions. You can mount anything you want on either /mnt or /net.

The common practice is use /mnt for temporal mounts. Things that you mount manually, use it for awhile, and then unmount it.

Debian and Ubuntu don't have a /net directory by default, so there's no special use for it.

As far as I can tell, the tutorial uses the term 'external' as something that you connect to the machine, like a USB drive, an external CDROM, etc. Something that was not present, or mounted at boot time.

'remote' is usually a service offered over the network. Like a nfs or samba share.

Just some thoughts. Hope it helps.
Regards.

---

### Post by bab1 on 2016-02-13
> **Salvatore_Palomino said:**
> Hello all!

In **Introduction to Linux: A Beginners Guide** 

   [http://tille.garrels.be/training/tldp/ch03.html](http://tille.garrels.be/training/tldp/ch03.html)

I am confused on the difference between an external filesystem and remote filesystem. The two are mentioned in table 3.2, where the author talks about /mnt and /net.



Any help is much appreciated!
+1  @papibe

An external file system is on media that is physically connected to your local host (the computer).  Beside a Floppy Drive, CD-ROM, DVD or USB stick you also can have a formatted partition on a HDD or SSD that you could mount.  I have local but external  2 HDD's that I mount.  One at /srv/nas and the other at /srv/backup.

Remote file systems are not directly connected to your local host.  As @papibe said, you can remotely mount a SMB share (Samba) or a NFS export (NFS) via a local network connection from a separate host (computer) on that network

---

### Post by Salvatore_Palomino on 2016-02-13
Thank you to both of you!

---

