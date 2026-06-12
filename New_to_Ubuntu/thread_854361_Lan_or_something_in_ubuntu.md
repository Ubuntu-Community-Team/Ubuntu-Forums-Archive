---
title: "Lan or something in ubuntu ?"
date: 2008-07-09
forum: New to Ubuntu
---

### Post by bjarnii on 2008-07-09
I got two computers, and I want to put some stuff into this one from the main one .. over the internet or like LAN ? how do I do it on linux :) ? any code or something.

I tried one code but it did not work.
Thanks :)

---

### Post by mikewhatever on 2008-07-09
Make sure samba is installed on both, then look under Places>Network. You may also need to configure your router to allow file sharing.

---

### Post by bjarnii on 2008-07-09
what is samba and .. what setting  do I need to fix ? I have tried to let the file on my main computer on shared but i cant find it in "system - administrator - network" nothing there :(

---

### Post by mikewhatever on 2008-07-09
> **bjarnii said:**
> what is samba and .. what setting  do I need to fix ? I have tried to let the file on my main computer on shared but i cant find it in "system - administrator - network" nothing there :(

[What is samba.]("http://www.samba.org/") System>Admin>Network does not have a shared folder, you are looking in the wrong place.

---

### Post by melrokz on 2008-07-09
To share folders from an Ubuntu system 2 a windows one and back, Please check whether samba is installed by right clicking on a folder you would liketo share and click 'share folder'. Ensure that u r connected to the Internet, and install samba (and NFS if ur sharing between Ubuntu systems).

---

### Post by billgoldberg on 2008-07-09
> **bjarnii said:**
> I got two computers, and I want to put some stuff into this one from the main one .. over the internet or like LAN ? how do I do it on linux :) ? any code or something.

I tried one code but it did not work.
Thanks :)

If the two machines are ubuntu boxes, it's very easy.

Read this (should take 2 minutes).

[http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/](http://linuxowns.wordpress.com/2008/06/08/share-files-between-2-ubuntu-computers/)

If one of the boxes is a windows or osx one, this method is possible also, but a bit more tricky.

Use google for that.

---

### Post by bjarnii on 2008-07-09
the main one is windows the other one is linux .. that is the proplem ..

---

### Post by mikewhatever on 2008-07-09
> **bjarnii said:**
> the main one is windows the other one is linux .. that is the proplem ..

And why is that the problem?
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)
[https://wiki.ubuntu.com/EasyFileSharing](https://wiki.ubuntu.com/EasyFileSharing)

---

