---
title: "can't connect to xserver"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by tiger63 on 2008-08-03
Hi,

I'm trying to edit fstab so my c drive is always mounted (dual booting with winxp) and when I try to open kate as root, it says it cannot connect to the xserver.

---

### Post by louieb on 2008-08-03
Are you doing this from the command line?
If so 
```
sudo nano -B /etc/fstab
```
note
>        -B (--backup)
              When  saving  a  file, back up the previous version of it to the
              current filename suffixed with a ~.


---

### Post by tiger63 on 2008-08-03
I don't know what was wrong, but yes, I tried it with sudo and it didn't work.  I logged out and relogged and it worked.

---

