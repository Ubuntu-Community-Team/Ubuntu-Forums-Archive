---
title: "Why does sudo command not work in chroot?"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by katch on 2012-04-10
I just installed a 32-bit chroot to run on my 64-bit system. In the  chroot environment the sudo command doesn't work, it sais 'sudo: command  not found'.   

Also, when I try the 'su root' command my password doesn't work ('su: authentication failure'). Why is that?
  

I'm quite new with ubuntu so actually I don't really know what I'm doing, just trying to follow instructions.

---

### Post by matt_symes on 2012-04-13
Hi

You have your paths set up correctly in the chroot environment ?

Are all the libraries in your path ?

That would be the first thing i would check.

Did you chroot into the correct part of the filing system ?

What command are you using to chroot into the system ?

Kind regards

---

