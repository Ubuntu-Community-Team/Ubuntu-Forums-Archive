---
title: "How to install Eset Nod 32 on Ubuntu version 15.04"
date: 2015-10-06
forum: New to Ubuntu
---

### Post by Mayan_Viljoen on 2015-10-06
Hi there, 
I am sooooo new to Ubuntu that I, pretty much, only know how to connect to the Internet. I have Ubuntu version 15.04 loaded on a 64 bit system. I want to load Eset Nod 32 on the system, but have no idea how. I can download the Nod 32 Linux installation file from the Net, but from there I know NOTHING. What I need is someone with extreme patience to help me and to tell me exactly what to do. I thank you in advance. Mayan Viljoen

---

### Post by Bucky Ball on 2015-10-06
*Thread moved to **New to Ubuntu**.*

Welcome. Please only post in the Resolution Centre for questions and support regarding the forum. It is not for Ubuntu support. :)

Please provide a link to the page you downloaded from.

---

### Post by NathanRodriguez on 2015-10-06
Eset support have a tutorial explaining how to install:

[http://support.eset.com/kb2653/](http://support.eset.com/kb2653/)

---

### Post by Mayan_Viljoen on 2015-10-06
Thanks for that, Nathan, but all I get when I right click on the ESET installer is a small rectangular window in which the following is written, i.e. Invalid url:'/home/mayan170/Downloads/eset_nod32av_64bit_en.linux'given,exiting  . . . . and then the following below that: No ':' in the uri
I have no clue what to do with this information.

---

### Post by sandyd on 2015-10-06
Run this
```

cd ~/Downloads
wget http://download.eset.com/download/unix/eav/eset_nod32av_64bit_en.linux
chmod u+x eset_nod32av_64bit_en.linux
./eset_nod32av_64bit_en.linux
```

---

### Post by Muhammad_Ahmad_Mujtaba on 2015-10-08
You can also skip this command rest do as **sandyd** told. If you follow him, you may be asked to overwrite previous downloaded file.
```
wget http://download.eset.com/download/unix/eav/eset_nod32av_64bit_en.linux
```

---

