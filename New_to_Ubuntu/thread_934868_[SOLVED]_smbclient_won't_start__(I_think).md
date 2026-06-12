---
title: "[SOLVED] smbclient won't start?  (I think)"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by il-luzhin on 2008-10-01
First time setting up samba without GUI.  Just installed 8.04 server on piece of junk.  

I type this

smbclient -L //kerenin/kerenin -U estragon

What I get is a brief OS, SERVER VERSION, etc, list but in the end not the 

smb: \>

prompt.  Just right back to my 

pissedoff@thegoddamnnotworkingproperlyserver:~$

suggestions please?

---

### Post by Nepherte on 2008-10-01
To connect:
```
smbclient //kerenin/kerenin -U estragon
```

---

### Post by il-luzhin on 2008-10-01
thnx

---

