---
title: "how to install gcc-3.4.6 on ubuntu 11.4?"
date: 2011-06-21
forum: Packaging and Compiling Programs
---

### Post by forgotnote on 2011-06-21
Hi there 
I want to install gcc 3.4.6 on natty (ubuntu 11.4)  I found a way to install it under 10.4 but it dosnt work in 11.4 
i dont remember the link but it was sth like this
1-downlaod gcc-3.4.6-base and gcc3.4.6 and  ... 
2-create Package file for adding to local reposity "apt-scanpackage"
3-add to apt reposity and apt-get install gcc-3.4
4 finish
 but in 11.4 it will install but in compile time it gave error that "can not find ld -lgcc " and "ld return 1 exit"
 so Im looking for any tested installation of gcc 3.4.6 in natty 11.4

Thanks :cry:

---

### Post by paolocastro on 2011-10-08
I know it's been a long time since you asked this, but I was facing the same problem a few days ago, and this was the first option from a google search unfortunately with no answer :( anyway, I solved this with the help of this link: 

[http://askubuntu.com/questions/39628/old-version-of-gcc-for-new-ubuntu]("http://askubuntu.com/questions/39628/old-version-of-gcc-for-new-ubuntu")

Hope this helps.

---

