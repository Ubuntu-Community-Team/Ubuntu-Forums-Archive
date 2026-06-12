---
title: "must run dpkg manually..."
date: 2008-04-27
forum: New to Ubuntu
---

### Post by seymone on 2008-04-27
Hi, 
I'm getting this error message while trying to install gdesklets does anyone know how to correct this error?
thanks!
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by frup on 2008-04-27
do what it tells you, dpkg --configure -a

open terminal and type sudo dpkg --configure -a

---

### Post by pbpersson on 2008-04-27
It is telling you to go to a console prompt and type the following:

sudo dpkg --configure -a

That is supposed to fix the problem

---

### Post by bowhawk85 on 2009-07-09
> **pbpersson said:**
> It is telling you to go to a console prompt and type the following:

sudo dpkg --configure -a

That is supposed to fix the problem
You are a wizard at making the not so apparent, apparent. That simple, straight forward and direct answer was the equivent of reverse aging on this side.... Many Thanks for my refound youth.

---

### Post by aysiu on 2009-07-09
You can just paste in ```
sudo dpkg --configure -a
``` into [the terminal](http://www.psychocats.net/ubuntu/terminal). You do not have to type it.

---

