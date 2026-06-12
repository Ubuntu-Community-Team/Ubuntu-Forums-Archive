---
title: "How can I enable vx-6000 webcam in hardy?"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Araiguma on 2008-06-26
Hello all! This is my first post so bear with me, ok? I recently (permanently) switched from xp 6 months ago, so I'm still very green. I have been searching for drivers for my m$ vx-6000 webcam. I don't know how to compile (or even what compiling is) and all the posts I've read relate to older versions (breezy through feisty). Can anyone help a noob get his webcam working with skype? I'm running hardy and skype 2.0.0.68. I'm living in Japan so local tech support is not really an option for me. ;-) Thanks in advance!

scott@beijingkaoya:~$ sudo lsusb
[sudo] password for scott: 
Bus 004 Device 002: ID 045e:00f4 Microsoft Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by finer recliner on 2008-06-27
the recommended webcam software for webcams in linux is called 'cheese'. you can install it by opening a terminal and typing:
```
 sudo apt-get install cheese
```


enjoy

---

### Post by Dutch70 on 2008-06-27
> **finer recliner said:**
> the recommended webcam software for webcams in linux is called 'cheese'. you can install it by opening a terminal and typing:
```
 sudo apt-get install cheese
```


enjoy

+1, cheese works for me, although I do have some brightness issues that I haven't had time to check out. this thread...
[http://ubuntuforums.org/showthread.php?t=651075](http://ubuntuforums.org/showthread.php?t=651075)
 been having fun in too many other places...lol,
cheese...I mean cheers!

Dutch

---

