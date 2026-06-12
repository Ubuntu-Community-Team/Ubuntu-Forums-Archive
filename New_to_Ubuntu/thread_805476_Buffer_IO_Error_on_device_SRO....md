---
title: "Buffer I/O Error on device SRO..."
date: 2008-05-24
forum: New to Ubuntu
---

### Post by wcook101 on 2008-05-24
I get a whole list of these error codes when I tried installing both ubuntu and Xubuntu onto an ibm netvista x40. Then it just frezzes up and does nothing.
I searched the forums but didnt come up with any matches. Can you point me to whats the hang up? 

Thanks

---

### Post by FuturePilot on 2008-05-24
If I remember correctly, /dev/sr0 usually refers to the CD-ROM drive. That could possibly mean the CD is corrupted which would definitely explain the odd behavior you are seeing. Check the CD for errors. You can do this by booting the CD and then selecting the Integrity check from the main boot menu.

---

### Post by wcook101 on 2008-05-25
Well i tried a new machine and a new cd of xubuntu. Same results. A whole bunch of error cades all the same. Linux have something against IBM?? Does anyone have any clues to this. Someone had to have wrote these error codes. Should I look in a different forum?

---

### Post by golgi on 2009-02-01
I have the same situation---long lists of error messages that chug on and on until suddenly the machine freezes. Or worse, I get a screen saver of an orange wall. Nothing budges that orange wall. Several hours later, I crash the system, and try again to reboot. I ran the CD check and it was fine. I switched the boot order and it's booting from the disk. 
This is a 10-year-old Sony Vaio with an AMD 1 Ghz Athlon chip. I see that this thread stopped eight  months ago but I'm still hoping that someone knows how to escape the endless string of buffer i/o errors and then the orange wall.

---

### Post by cfc7763 on 2009-02-17
I dont know if this helps but after trying to boot from cd to a partitioned drive i kept getting the same problem of the blank orange screen in the i downloaded virtual clone drive (free from filehippo.com) this allows you to mount an iso file rather than burning it to CD i then downloaded a fresh ubuntu 8.10 ran a program called winMD5sum (info can be found at [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM) ) and ran a hash check when the check turned out fine i mounted the iso on clone drive and ran the install when a black screen comes up saying something like "press esc for menu" i pressed escape and after trying some of the other boot options i chose the one that says something like "install for possible display problems" that option was the one that worked for me in the end. I know this isnt the best description and probably not the easiest way but it worked for me. Problem is I dont have a clue how to use ubuntu i believe it relies a lot on an internt connection but it doesnt recognise my Orange internet dongle or when i attached to a modem via ethernet cable. lol

---

### Post by JAKEer on 2009-11-26
I'm having the same error. Buffer I/O error on device SRO. I'm trying to duel boot with the newest version of Ubuntu 9.10. I have burned multiple disks with the same results. It seems that there are no clear cut answers about this problem on the forums to date. If anyone has solved this problem It would be much appreciated, I am brand new to Ubuntu and am already getting frustrated.

---

