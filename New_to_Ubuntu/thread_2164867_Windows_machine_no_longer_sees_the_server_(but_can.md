---
title: "Windows machine no longer sees the server (but can map drives?)"
date: 2013-08-02
forum: New to Ubuntu
---

### Post by fredfillis on 2013-08-02
I have a machine running ubuntu server (12.04.2 LTS), two ubuntu clients and several windows 7 clients. I am using NFS to share with the ubuntu clients and samba to share with windows 7 clients. On my windows 7 machines I usually can see an icon for the server machine in the network window. I can click on that as see any shared drives / folders. In the past I have done that and mapped a couple of these folders to drive letters.

Now that icon is no longer displayed but my mapped "drives" still work fine. At best, the server icon had been there intermittently over the last week or so but now it is just gone.

I'm confident that there is a logical explanation for this behavior but it is beyond this noob. Does anyone know what might be going on here?

---

### Post by stevesy on 2013-08-02
Not sure if it'll fix your problem but you could try method 2 here [http://support.microsoft.com/kb/978980](http://support.microsoft.com/kb/978980)

---

### Post by fredfillis on 2013-08-03
Thanks stevesy but I figured it out. It was a noob move as I expected. One of my linux clients is running openelec which includes samba. When I switched off samba on that machine, everything worked fine. 

Duh!

---

