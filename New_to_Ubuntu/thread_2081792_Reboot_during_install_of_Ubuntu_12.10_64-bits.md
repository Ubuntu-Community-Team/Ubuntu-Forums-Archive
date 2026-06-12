---
title: "Reboot during install of Ubuntu 12.10 64-bits"
date: 2012-11-07
forum: New to Ubuntu
---

### Post by Leherenn on 2012-11-07
Hello.

I'm relatively new to Linux, and I'm trying to install Ubuntu 12.10 64-bits on a HP G72 laptop in dualboot alongside Windows 7 64-bits.

To do it, I'm using a USB key, which I used to install Ubuntu on two other computers (an Asus and a Sony).

I first had a black screen after booting off the key, which I solved by using the nomodeset option.
However, when I click on the "Next" button during the step where one can choose to install Ubuntu along Windows, the installation immediately stops, and this screen is displayed before the computer reboots.

[spoiler][IMG]http://image.noelshack.com/fichiers/2012/45/1352330051-img-20121107-200444.jpg[/spoiler]
I'm sorry for the image quality.

I've tried it a few times, and as far as I can tell, it's doing the same thing each time, with the same message.


Thanks in advance. :)

---

### Post by Leherenn on 2012-11-10
Anyone who could help me with this please?

PS : I'm sorry, I haven't found how to use things like spoilers on this forum.

---

### Post by grahammechanical on 2012-11-10
Your image does not appear in the browser. I would have been helpful to type the error message, which is:

> no more MTRRs available

What is an MTRR? No idea really. But I did find this for you by simply googling 'MTTR.'

[http://en.gentoo-wiki.com/wiki/MTRR]("http://en.gentoo-wiki.com/wiki/MTRR")

You might want to consider this advice at the bottom of the page.

> Memory remapping will push all that addressing above 4 GB, by making the system see the full 4 GB memory and share address pointers redirecting addresses that were previously overlapped. This does happen at a performance cost as well. On 64bit systems the same is apparent but of course with much more memory (about 8 Peta Bytes).

MTRR can manage this well and there is nothing from the how-to above extra you need do. One thing to point out is that some proprietary drivers such as ATI fglrx drivers do not always work with this feature. I have had them working before but at reduced performance because of the remapping feature, other versions just fail to find the graphics memory address so if your having X driver problems Blank screen, Lockouts, hard lock crashes etc then Disable the remapping in the bios.

You might need to re-instate memory mapping in the BIOS after installation as Windows might now work so well.

[http://superuser.com/questions/265319/out-of-mtrrs-at-boot]("http://superuser.com/questions/265319/out-of-mtrrs-at-boot")

Regards.

---

### Post by 2F4U on 2012-11-10
I haven't seen this error message before and the only thing useful Google comes up with is this:

[http://my-fuzzy-logic.de/blog/index.php?/archives/41-Solving-linux-MTRR-problems.html](http://my-fuzzy-logic.de/blog/index.php?/archives/41-Solving-linux-MTRR-problems.html)

---

