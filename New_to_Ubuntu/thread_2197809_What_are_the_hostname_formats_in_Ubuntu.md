---
title: "What are the hostname formats in Ubuntu?"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by raymondvillain on 2014-01-05
Installed 13.10 on a new laptop, setting up file sharing.

Instructions say to run this command in a terminal window:

```
sudo mount example.hostname.com:/ubuntu /local/ubuntu
```

But I have no clue what "example.hostname.com:" should be.  Is it the computer name of the server to which I wish to connect?  Can it be something like 192.168.0.102 ?

Embarassing!

---

### Post by tfrue on 2014-01-05
What did you do to get set up? Are you using Samba and defining shares? Are you trying to get a samba share to mount when you restart? I don't believe you have to use that command to connect to a samba share from a window's computer.

---

### Post by raymondvillain on 2014-01-05
Not using samba. Using nfs tutorial:

[https://www.digitalocean.com/community/articles/how-to-set-up-an-nfs-mount-on-ubuntu-12-04](https://www.digitalocean.com/community/articles/how-to-set-up-an-nfs-mount-on-ubuntu-12-04)

---

### Post by raymondvillain on 2014-01-05
Meant to say I was using this link:

[https://help.ubuntu.com/lts/serverguide/network-file-system.html](https://help.ubuntu.com/lts/serverguide/network-file-system.html)

---

