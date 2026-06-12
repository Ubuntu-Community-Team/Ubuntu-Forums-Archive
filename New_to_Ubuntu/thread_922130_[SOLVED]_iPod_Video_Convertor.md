---
title: "[SOLVED] iPod Video Convertor"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by adobrakic on 2008-09-17
Is there an iPod video convertor, such as videora, for ubuntu?

---

### Post by crazypenguin2008 on 2008-09-17
plytube should do the trick 

edit /etc/apt/sources.list file

sudo gedit /etc/apt/sources.list

Add the following line  deb [http://www.bashterritory.com/pytube/releases/](http://www.bashterritory.com/pytube/releases/) /

save and exit the file 

you need to update the source list using this command

sudo aptitude update

now to install 

sudo aptitude install pytube

or you can get it from here [http://www.getdeb.net/release/3057](http://www.getdeb.net/release/3057) 

download then run this command  

sudo dpkg -i pytube_0.0.11.4~getdeb1_all.deb

---

### Post by adobrakic on 2008-09-17
thanks a lot! :D

---

### Post by crazypenguin2008 on 2008-09-17
no problme. just doing my part to help out this great community!!

---

### Post by adobrakic on 2008-09-17
Alright, the program is working fine. But when I try to convert from avi to mp4 (for ipods), it doesn't do anything. It just says "converted" and leaves a file with nothing on it. However, when I tried .avi to .mpg, it was working fine. 
Any ideas?

---

### Post by adobrakic on 2008-09-18
bump

---

