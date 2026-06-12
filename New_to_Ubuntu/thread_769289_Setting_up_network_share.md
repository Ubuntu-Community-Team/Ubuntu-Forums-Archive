---
title: "Setting up network share"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Kymeia on 2008-04-26
OK installing 8.05 from scratch seems to have worked - I now have internet access and can browse the Windows network but it seems to be one way only. I tried setting up a Shared folder by right clicking on it (same as in Windows) and selecting sharing and it downloaded some stuff but it won't let me change sharing properties as it says it needs administrator permission but I'm logged in as an administrator already. All I want is to allow other users (i.e. me on my PC's) to read the files in the folder and add/share new ones.

---

### Post by fmartinez on 2008-04-26
To share from Linux system to windows look to using Samba. 
To share from Linux system to Linux system look to use NFS.
The links has some great tutorials on both subjects. 
[http://doc.ubuntu.com/ubuntu/serverguide/C/index.html](http://doc.ubuntu.com/ubuntu/serverguide/C/index.html)

---

### Post by Kymeia on 2008-04-26
I think it downloaded samba or something but I can't find it. All I want is for it to recognise me as admin.

---

### Post by Monicker on 2008-04-26
You might have run into the same bug as me.   I tried to share my Public folder, and it installed Samba.  When I change to give access to other people, it basically said I did  not have permission to create usershares.  The solution was to log out and log back in for the change to take effect.  After that I was able to give access to the folder.

Evidently a bug report has already been filed on this.

---

### Post by Kymeia on 2008-04-26
> **Monicker said:**
> You might have run into the same bug as me.   I tried to share my Public folder, and it installed Samba.  When I change to give access to other people, it basically said I did  not have permission to create usershares.  The solution was to log out and log back in for the change to take effect.  After that I was able to give access to the folder.

Evidently a bug report has already been filed on this.

Yes - that did it - thanks

---

