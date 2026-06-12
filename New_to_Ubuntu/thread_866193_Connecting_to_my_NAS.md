---
title: "Connecting to my NAS"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by P.E.C.K. on 2008-07-21
Hi, have just recently switched to ubuntu hardy, and am wondering what is the best way to connect to my Freecom network drive pro? its on a static ip at 198.162.1.106 through my router, it has SSH and FTP server switched on. Basically i just want to be able to browse the folders through Nautilus? and to then archive my music in something like Amarok?

I have tried the connect to server and putting in the relevant info, but doesnt seem to want to connect, when i browse through on the network it shows as a windows share, but nothing in it shows. The hard drive is in NTFS format.

Would quite like to get used to working through the terminal, as then i can understand whats going on?

Okey hope thats enough info, if not just ask for what you need.

---

### Post by chrisod on 2008-07-21
Read the documentation for your NAS drive closely. My NAS drive had a funky addressing scheme that needed to be followed to get it to work. See below, I don't have your brand of NAS drive, but maybe the principal is the same.

> With Samba, the entry in fstab was simple:
*//mediaserver/Photos /mnt/photos smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0*

So I figured the corresponding NFS code would be
*mediaserver:/Photos/ /mnt/photos nfs rsize=8192,wsize=8192,timeo=14,intr*

as per the how-to in the Ubuntu Forums. However, I kept getting “permission denied” errors when trying to mount the directories.

For some reason that I don’t understand, you have to specify the SimpleShare folders like this:
mediaserver:/shares/SimplePool/Photos/ /mnt/photos nfs rsize=8192,wsize=8192,timeo=14,intr

assuming you haven’t messed with the default pool set up on the SimpleShare.

---

