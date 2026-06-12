---
title: "how to delete a workgroup"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by corkscrew on 2008-11-23
I have a mixed xp ubuntu network. I have samba installed and can share folders with xp boxes.
However the widows network workgroup is called homebase. By default when i installed samba it made a workgroup called "WORKGROUP". I have edited my smb.conf file to homebase.
But under network in from the places menu it still shows the WORKGROUP as well, and it will not allow me to delete it?
How can i delete it?

---

### Post by Dedoimedo on 2008-11-23
Did you restart the samba process after the change?
You can do it by running: sudo service samba restart. Also, try logging out of the session.
Dedoimedo

---

### Post by corkscrew on 2008-11-23
i tried restarting the computer and its stll there

---

### Post by Dedoimedo on 2008-11-23
What's inside this workgroup?

If you check the following files, does it mention workgroup anywhere?

```
cat /etc/hosts
```
```
cat /etc/resolv.conf
```

Dedoimedo

---

### Post by corkscrew on 2008-11-23
solved it, the "WORKGROUP" was still listed on one of my windows boxes, I deleted it there, restarted all boxes and its gone.

One other problem though i wonder if you could help me with, I have 2 notebooks i is dual boot vista and ubuntu (never use the vista) the other xp only, and 1 desktop triple boot vista xp and ubuntu (dont use vista).

I have samba installed on the desktop and can access from system - admin menu.
On the ubuntu notebook i have samba installed now as well but its not on the menu how do I add it to the admin menu?

---

### Post by Dedoimedo on 2008-11-23
Sorry, I don't follow what you need. You need a shortcut?
Dedoimedo

---

### Post by corkscrew on 2008-11-23
I suppose they are called shortcuts 
on the desktop if i click the top menu system and then administration there is an entry for samba there is'nt one on the notebook?

I had a look at the launcher properties of the one that works on the desktop it is 
" gksu system-config-samba" i have tried entering that into a terminal in the notebook.
It asks for password same as desktop but then nothing happens?

---

