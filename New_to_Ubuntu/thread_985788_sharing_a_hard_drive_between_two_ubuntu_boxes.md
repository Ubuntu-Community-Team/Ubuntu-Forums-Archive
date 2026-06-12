---
title: "sharing a hard drive between two ubuntu boxes"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by DataSpy on 2008-11-18
Hello,

I was wondering how I would go about sharing a hard drive from one ubuntu box to another?

Any help greatly appretiated,
thanks in advance!!!

---

### Post by Crafty Kisses on 2008-11-18
Have you considered Samba?

---

### Post by DataSpy on 2008-11-18
> **Codename said:**
> Have you considered Samba?

I thought samba was for interconnectivity between two operating systems, like sharing a windows drive on an linux system?  but if samba works for connecting a hard drive between two linux boxes that work rock!

---

### Post by Crafty Kisses on 2008-11-18
> **DataSpy said:**
> I thought samba was for interconnectivity between two operating systems, like sharing a windows drive on an linux system?  but if samba works for connecting a hard drive between two linux boxes that work rock!

I'm pretty sure what you're thinking of is something to the extent of VNC.

---

### Post by bodhi.zazen on 2008-11-18
You can use any number on network protocols :

samba, NFS, ssh (sshfs).

If you are behind a LAN NFS or samba. If you are connecting over the Internet, sshfs.

---

### Post by hyper_ch on 2008-11-18
you can also use sshfs over lan ;)

---

### Post by mapes12 on 2008-11-18
I use OpenSSH and used the guide posted by SpaceTeddy in this thread to set it up: [http://ubuntuforums.org/showthread.php?t=793308](http://ubuntuforums.org/showthread.php?t=793308)

It's very easy to get up and running and use.

It works over wifi as well.

Hope that helps.

---

