---
title: "Linux C++ Compiler"
date: 2005-10-16
forum: Programming Talk
---

### Post by dwessell on 2005-10-16
Hey all.. 

I'm moving completely to Ubuntu, I've been so impressed with it.. But I'm short a C++ compilier now.

I've been using Codewarrior for Windows.. Can anyone suggest a good compilier for Linux?

Thanks
David

---

### Post by hod139 on 2005-10-16
If you install the meta-package build-essential
```
 sudo apt-get install build-essential 
```
that will get you access to the gnu compiler g++.  It sounds like you are also asking about IDEs for linux, and there are many of those.  You can  start by looking at eclipse (with the cdt plugin for c++) and kdevelop.

---

### Post by dwessell on 2005-10-16
Hey hod139, thanks for the response.. I'm looking for something along the lines of Codewarrior, in that it's not over excessive in trying to be helpful, but does have some nice features.. I'll check out the ones that you mentioned.. 

Thanks a ton..

dw

---

### Post by hod139 on 2005-10-16
There is codewarrior for linux. though it isn't free.  For free solutions, the two I mentioned earlier are very good.  Make sure you don't confuse compilers (g++) with development kits (codewarrior) though.

---

### Post by David Marrs on 2005-10-17
check out the favourite ide thread as well. Of what's been suggested, I've found Anjuta to be looking rather good. I'd also recommend installing Glade for GUI building.

---

### Post by remin8 on 2005-10-17
In order to get a "full" working Anjuta system, I would install build-essiential and anjuta and all the recommended packages as well. If you are using Synaptic, you can go to the prefrences and set to treat recommended as deps, this will make the install easy for you. On a side note, I have been using Anjuta for a short while now, and although it is a little different than any other IDE I have used the interface is nice and simple and alows you to really focus on your code. Hope this helps.

---

