---
title: "Changing file permissions"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by loren41 on 2011-11-18
I installed Samba 3.5.11 in Ubuntu 11.10.  The configuration file is located in /etc/samba/ and the man pages tell me that I can edit the config file using gedit.  When I try, I receive the message that I am not the owner and the file is read only.  What is my solution?

---

### Post by Lars Noodén on 2011-11-18
The file /etc/samba/smb.conf is owned by root, not your user.  You'll need root privileges to edit the file.  Try this instead:

```

gksudo gedit

```

---

### Post by loren41 on 2011-11-18
Thanks Lars - big help.

---

