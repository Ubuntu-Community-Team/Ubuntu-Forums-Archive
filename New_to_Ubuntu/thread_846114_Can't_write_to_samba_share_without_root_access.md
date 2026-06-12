---
title: "Can't write to samba share without root access"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Jalexxi on 2008-07-01
I'm trying to write to a samba share I've mounted with smbmount, but it doesn't let me write to it unless I write as root. I can't change the user with chown, and I've already set the permissions to 777 with chmod. I'm not sure if it's a local problem, or a problem with the server setup, but several Windows boxes have no problem at all writing to that same share. Any ideas?

---

### Post by Jalexxi on 2008-07-01
Ah, I solved 10 minutes after I made this thread, now I feel stupid. Sorry for a useless thread.

For the people interested in the solution, the server was OpenBSD so I needed to set the user and group id #'s before it would let me write.

---

