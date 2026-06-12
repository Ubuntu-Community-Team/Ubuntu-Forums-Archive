---
title: "editing xorg.conf"
date: 2013-11-17
forum: New to Ubuntu
---

### Post by bob_guy123cheese on 2013-11-17
Hello, I recently found an old slot-loading iMac G3 at garage sale for only $12. I had always wanted to try ubuntu on a computer but I never really had one to just fool around with so I decided to try ubuntu 12.04 on it. Once I installed it, the graphics were really glitchy. i installed from a guide specificly for G3s and it said that there is a conflict with the graphics card and you have to edit /ect/X11/xorg.conf. On my laptop, I created a .conf file of what xorg should be and put it onto a flash drive. i tried to just drag it over to replace the old file but I didn't have permission to edit the folder.
     I spent a while looking up soultions and learning basic terminal skills. Whenever I try to gedit the file it shows up blank. using the cd command I found out the computer couldnt find the ect directory at all. 
     I am a complete noob with the os and was just wondering what I could do to get this working. Thanks! :D
                                     -jackson

---

### Post by steeldriver on 2013-11-17
Hello and welcome to the forum

The directory you are looking for is /**etc **not /**ect**

Note that since it's a system directory you will need to use sudo in your terminal command to copy files there (or *gksudo nautilus* if you are doing it via the GUI file manager)

---

### Post by bob_guy123cheese on 2013-11-17
That is seriously the most stupid thing i have ever done. Lol i spent 2 hours on this. Thanks!

---

### Post by mörgæs on 2013-11-18
Please mark the thread 'solved'.

---

