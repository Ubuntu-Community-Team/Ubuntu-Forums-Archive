---
title: "[SOLVED] Superuser Privledge .. How ?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by will_s54 on 2008-10-14
Installinging an update and it failed with the following message

'E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.'

So I used the terminal window and posted this

"will@will-xpubuntu:~$ dpkg --configure -a"

and recieved the follwing reply


"dpkg: requested operation requires superuser privilege"

So how do I get superuser privledge  ?

---

### Post by perlluver on 2008-10-14
Type this in ```
sudo dpkg --configure -a
``` sudo gives temporary super user privileges.

---

### Post by mullenrbock on 2008-10-14
you must type "sudo" before the dpkg command. It'll ask you for a password, you just put your normal user password there.

---

### Post by will_s54 on 2008-10-14
Thankyou

Updates now all installed

---

