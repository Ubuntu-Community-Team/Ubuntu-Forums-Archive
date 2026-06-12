---
title: "Help! Ubuntu 12.04 issues!"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by Niemand000 on 2012-05-08
Alright, so I just got a brand new Toshiba laptop and installed ubuntu 12.04.  It ran great at first but then it would freeze at log in.
So I installed 10.04 on it and it's working fine except I can't connect to the internet at all (wired or wireless)! Maybe it's a driver issue? 
Network controller: Realtek Semiconducter Co., Ltd. Device 8176 (rev 01)
 
Now, when I try to install any later edition of Ubuntu I get the same thing: it will start loading but freezes as I hear the disc drive just stop reading the disc.  As in it's working, it's working, then it just powers down and I'm left with a purple screen, white ubuntu, four orange dots at the bottom of the page.  
Then I thought I'd try a USB install, it does the SAME THING!
 
So my question is: 1. Is there a way to fix this or should I send the computer in since I have a 1 year warranty?
2. What could the problem with the 10.04 internet be and how can I fix that?
 
Thanks so much for your help everyone!!

---

### Post by 2F4U on 2012-05-08
You should provide more information about your hardware. If you have an ATI or nVidia graphics card, it may be worth trying to add nomodeset to the grub kernel parameters and see if you get any further.

---

