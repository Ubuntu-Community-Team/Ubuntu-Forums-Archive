---
title: "[SOLVED] major brain fart"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by paul101 on 2008-11-13
ok, i've installed ubuntu 8.10 on my laptop with **wubi**



now, how would i get ubuntu to be the default OS??

---

### Post by Duck2006 on 2008-11-13
Edit the menu.lst file in your grub folder.

[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

---

### Post by CLomax on 2008-11-13
Hi there.

To make Ubuntu the default, I used EasyBCD for Windows: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

I can't remember how it works exactly but it's very easy to move Ubuntu to the top of the Windows MBR list. I'm sure you'll figure it out ;).

EDIT: If anyone knows the exact steps... well, you know what to do.

---

### Post by jimmy the saint on 2008-11-13
[http://www.psychocats.net/ubuntu/wubi#bootorder](http://www.psychocats.net/ubuntu/wubi#bootorder)

Look at this for detailed Wubi info, as well as the answer to your question

---

### Post by CLomax on 2008-11-13
> **Duck2006 said:**
> Edit the menu.lst file in your grub folder.

[http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc](http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc)

If it's installed with Wubi he'd (I assume he) be using the Windows MBR, I'm sure.

---

### Post by paul101 on 2008-11-13
cheers, fixed it now :D

---

### Post by CLomax on 2008-11-13
> **paul101 said:**
> cheers, fixed it now :D

Awesome :)

Just two more things:

Could you please let us know what fixed the problem so that others with the same problem in the future can find this thread and use it?

Also, mark the thread as 'SOLVED' with the thread tools option near the top ^ and thank the person who supplied the working answer with the little yellow ribbon at the bottom right corner of his/her post.

Cheers

---

