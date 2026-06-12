---
title: "Backup /home into separate partition before doing upgrade"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by marcelo danico on 2008-05-18
I have some files in /home, same partition as root, and I want to copy them to a different partition before installing 8.04 from a cd.

I have plenty of space on the separate partition (currently mounted by default).
Do I use the live cd, mount the partitions and use mv?

or can I do it some other way without the live cd? 

Are my evolution emails also in /home?

---

### Post by brian_p on 2008-05-18
> **marcelo danico said:**
> I have some files in /home, same partition as root, and I want to copy them to a different partition before installing 8.04 from a cd.

I have plenty of space on the separate partition (currently mounted by default).
Do I use the live cd, mount the partitions and use mv?

or can I do it some other way without the live cd? 

I'd use cp but why not just copy or move them to the already mounted partition? I assume you know where it is mounted.

> Are my evolution emails also in /home?

Yes.

---

### Post by philinux on 2008-05-18
You could do this.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by marcelo danico on 2008-05-18
Thanks.

I thought I had to physically move the files or else they would just be listed to different directory, but stay on the original partition.

---

### Post by philinux on 2008-05-18
When I did this i made a backup of home on a Usb stick.

---

