---
title: "[SOLVED] not enough memory"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Zoonosis on 2008-06-01
I have Ubuntu installed 'inside' windows, is there any way that I can add more memory to the Ubuntu, or am I going to have to reinstall Ubuntu to add more memory? Thanks.

Brandon Bovy
Zoonosis

---

### Post by quelx on 2008-06-01
Are you using VirtualBox, VMWare, or something else?

VirtualBox and VMWare will let you adjust the memory but only when the virtual machine is powered off.

---

### Post by PinkFloyd102489 on 2008-06-01
If you installed it via Wubi, Ubuntu is utilizing all of your RAM. If you want more, you'll have to physically install more.

---

### Post by Zoonosis on 2008-06-01
I'm not sure what VirtualBox and VMWare are. I just ordered the Ubuntu disc and installed it.

---

### Post by Joeb454 on 2008-06-01
Then no - Ubuntu will be using all the RAM that your PC has - just the same amount that Windows can use.

This is assuming you have to restart if you want to switch from Windows to Ubuntu - which you do I believe?

---

### Post by Zoonosis on 2008-06-01
yeah, but when I installed it, I could chose how much space I wanted to allow for Ubuntu. So I guess I'll have to reinstall to increase that. Thanks.

---

### Post by schiznik on 2008-06-01
you mean hard drive space, then you will either need to reinstall or use a partition editor to resize the partitions (something like gParted from within ubuntu).

I think most of the previous replies assumed you were talking about the amount of RAM allocated/in your machine, rather than the paritioning of the hard drives.

---

### Post by Joeb454 on 2008-06-01
Sorry yes - I did assume you meant RAM :p

And I think with Wubi you would have to delete C:\Ubuntu (or wherever it is located) first, and then try and install Ubuntu again :)

---

### Post by Zoonosis on 2008-06-01
Alright guys, that's it! Thanks for your help :D

Brandon Bovy
Zoonosis

---

### Post by Joeb454 on 2008-06-01
Excellent :D You can mark your thread as solved by clicking "Thread Tools" at the top of this page, and then choose "Mark Thread as Solved" :)

---

