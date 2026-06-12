---
title: "Using Nas files with Non-Gnome applications"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by Gerry_Graves on 2013-09-13
I cannot find my NAS files in Audacious, VLC etc.

I have read thet I need to explicitly mount the NAS drives for non-gnome applications to allow this.

As a complete novice, could someone give me step by step instructions on how to do this in Ubuntu 13.04, please?

Thanks

---

### Post by TheFu on 2013-09-13
If you told us which sort of NAS services were offered, we could.  CIFS, NFS, iSCSI ... AoE ... each as pros and cons. For video editing, AoE is probably best, then iSCSI, then NFS and last CIFS.

Which does yours provide?

It is likely your NAS supports only NFS or CIFS.
NFSv4 - [https://help.ubuntu.com/community/NFSv4Howto#NFSv4_Client](https://help.ubuntu.com/community/NFSv4Howto#NFSv4_Client)
CIFS - [https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)

Good luck!

---

### Post by Gerry_Graves on 2013-09-13
It is a WDLiveTV which uses NFS

---

### Post by TheFu on 2013-09-14
Did those links help?

---

### Post by Gerry_Graves on 2013-09-16
Yes, thank you the links were very informative. I found that I needed to enable Linux shares in the WD box. This did not however allow me to us Audacious or Rhuythmbox, but Banshee works great.
Importing approximately 5000 albums now!

Thanks again for the help.

---

### Post by TheFu on 2013-09-16
I've been using **Clementine** recently. It feels very light for a fill-featured player. It even has a ID3 tag editor that let me easily merge all the different spellings of my AC-DC albums.
* ACDC
* AC DC
* AC/DC
* AC-DC
The zero-silence merging between songs is nice too.  Plus, I'm on LXDE and it never feels slow or heavy at all.

---

