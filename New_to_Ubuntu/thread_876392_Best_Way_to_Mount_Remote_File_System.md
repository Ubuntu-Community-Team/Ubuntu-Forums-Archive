---
title: "Best Way to Mount Remote File System?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by tmcmulli on 2008-07-31
I'm separating my FTP and SAMBA servers internally, but I'm going to want my external driver that are mounted to my Ubuntu Samba server available to my FTP site...  I know I can use smbmount to mount the volumes, but is that the best way, seeing as I'm going Ubuntu to Ubuntu... I figured I should be able to use something better than SMB.

---

### Post by bgerlich on 2008-07-31
What about NFS ? For secure transfers you could try sshfs but your performance may suffer (depending on configuration).

---

### Post by tmcmulli on 2008-07-31
Thus why I posted in the noob section... How do I mount a drive remotely via NFS?  I don't need the transfer to be secure.

---

