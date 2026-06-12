---
title: "[SOLVED] No CUPS No CUPS oh where is my CUPS"
date: 2008-11-30
forum: New to Ubuntu
---

### Post by comsparks on 2008-11-30
I did a fresh install of Ubuntu 8.10 and can't use printers (Stand alone USB) on it. The print setup is all grayed out Check services and there is no CUPS. What Up with the CUPS. Any ideas? Thanks

---

### Post by binbash on 2008-11-30
what is the output of sudo /etc/init.d/cups status ?

---

### Post by comsparks on 2008-11-30
Status of Common Unix Printing System: cupsd is not running.

---

### Post by binbash on 2008-11-30
sudo /etc/init.d/cups start

then try to print.(If you see an error at above command, post the output)

---

### Post by comsparks on 2008-11-30
* Starting Common Unix Printing System: cupsd                                  cupsd: Child exited with status 1!

---

### Post by binbash on 2008-11-30
sudo dpkg-reconfigure cups

post the output if possible (also after this command, give this  : sudo /etc/init.d/cups start)

---

### Post by pyromanic123boom on 2008-11-30
I had problems with cups after updating to 8.10
Run a quick 

$ sudo apt-get install cups

and then 

$ sudo /etc/init.d/cups restart

Cupsd is non-existent in 8.10, just restart cups.

---

### Post by binbash on 2008-11-30
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462069](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=462069)

It maybe this bug

---

### Post by comsparks on 2008-12-01
When I first installed Ubuntu 8.10 I configured it to the way I liked it and then remastered it. I used the remastered disk several times without any problems except the last time. It got hung up several time during the install and I think that was the problem. I loaded in the original live CD and everything works great. They say the third time is a charm and I guess they are correct as it is working now. I want to thank everyone for the assist.

---

