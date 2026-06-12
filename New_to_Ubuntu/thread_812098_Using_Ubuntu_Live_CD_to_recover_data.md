---
title: "Using Ubuntu Live CD to recover data"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by shaff85 on 2008-05-29
I use windows xp 64 bit but had some HD issues and it wouldn't boot.  I am running Ubuntu 7.04 from my cd rom right now.  I can see my hard drives and access them but cannot change the permissions because I am not the owner.  Is there a way to become the owner so that I can change the permissions and drag those data files onto an external drive so that I can format and re-install windows?

---

### Post by Oldsoldier2003 on 2008-05-29
> **shaff85 said:**
> I use windows xp 64 bit but had some HD issues and it wouldn't boot.  I am running Ubuntu 7.04 from my cd rom right now.  I can see my hard drives and access them but cannot change the permissions because I am not the owner.  Is there a way to become the owner so that I can change the permissions and drag those data files onto an external drive so that I can format and re-install windows?

I can't remember what the default user name is for the live cd so do this in a terminal

```
whoami
```

then ```
sudo chown -hR <username>:<username> /path/to/the/files
```
from there go ahead and drag the files or use the command line to copy them to your external drive.

---

### Post by viljun on 2008-05-29
to do it graphically open terminal and type: sudo nautilus

now you are not restricted but be very careful with what you do

---

### Post by CirruZZ on 2008-10-05
> **viljun said:**
> to do it graphically open terminal and type: sudo nautilus

now you are not restricted but be very careful with what you do


Tanx! Awesome trick, that helped me allot!

---

