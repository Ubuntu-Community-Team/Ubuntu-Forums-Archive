---
title: "Dual booting Ubuntu and XP"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by vpjayant on 2008-08-07
I've been using Ubuntu for a little over a month, and I discovered that I would need XP for a few programs for school, so I created a new partition using GParted and installed XP in it, everything went fine. But now when I turn on my laptop, it boots straight to XP. I clearly should have read up on dual booting beforehand but now I can't find how to choose which OS to boot to. Help?

---

### Post by billgoldberg on 2008-08-07
> **vpjayant said:**
> I've been using Ubuntu for a little over a month, and I discovered that I would need XP for a few programs for school, so I created a new partition using GParted and installed XP in it, everything went fine. But now when I turn on my laptop, it boots straight to XP. I clearly should have read up on dual booting beforehand but now I can't find how to choose which OS to boot to. Help?

If you have another spare cd laying around, go and download this program

[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5)

and burn it to a cd like you did Ubuntu.

--

The program is pretty easy to use.

It will put back the grub and you'll be able to choose wether to boot xp or ubuntu after you're done.

--

If you don't have a spare cd laying around, you can use the Ubuntu live cd to fix this problem. But it's so much easier to use the super grub disk live cd.

---

### Post by vpjayant on 2008-08-07
It just so happens that yesterday I bought 200 blank CD-Rs. You never know when you'll need one. I'm just downloading that now, thanks.

---

### Post by billgoldberg on 2008-08-07
> **vpjayant said:**
> It just so happens that yesterday I bought 200 blank CD-Rs. You never know when you'll need one. I'm just downloading that now, thanks.

Haha, true.

---

### Post by vpjayant on 2008-08-07
Hmm, should I just use the "Auto Super Grub Disk" or just use the normal one? It suggest the auto for Windows.

---

### Post by vpjayant on 2008-08-07
Ah, I have grub back, but now I can only boot Ubuntu. It's a slight improvement...

EDIT: Added a bit to menu.lst, all is good now.

---

