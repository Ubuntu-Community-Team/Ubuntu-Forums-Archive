---
title: "Is it possible to use Filezilla client with Samba"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by graphicsmanx1 on 2013-11-05
Im wanting to learn more on how to deploy Ubuntu in my work environment but I am unsure what is the best route for a FTP.  I have taken a PC I used to run Windows 7 Home with shared folders and installed Ubuntu 12.10 on it with Samba.  I can setup Samba but I was wondering if there is a way I can allow my users on my LAN to send files to what I am treating as an FTP with Samba or would I need to look into OpenSSH?

---

### Post by newb85 on 2013-11-05
A ssh connection should not be necessary.  Your objectives are exactly what samba is for.   Of course, you'll have to grant the users write permission on the shares in question for them to add files to the server machine.

---

