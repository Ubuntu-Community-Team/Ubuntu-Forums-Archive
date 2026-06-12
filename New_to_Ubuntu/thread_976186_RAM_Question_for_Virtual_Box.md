---
title: "RAM Question for Virtual Box"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by benjoman on 2008-11-09
Hi, I'm new around here, so this will be my first post, i'd like to say thank you for everyone's info on here it help made my decision to slowly transfer into linux.

Currently I am about to run Ubuntu 8.10 on Virtual Box, on my laptop, my laptop has 2x 2gb ram sticks, and by using windows vista ulti 32bit, I understand that I can only use 3.5gb from the 4gb total..

My question is if i allocate my Virtual Box that unused 512mb ram, would that mean that my 3.5gb ram on vista will go unaffected?

Thanks in advance.

---

### Post by benjoman on 2008-11-09
Bump~

---

### Post by Greyed on 2008-11-09
Please don't bump unless at least 24 hours have passed.  Even then it's iffy.

No.  Vista has to be able to address it to assign it to VBox so that it, in turn, can give it to the guest OS.  So if you give VBox 512Mb you have 3 left for Vista.  4 - 512Mb lost to addressing - 512Mb assigned to VBox.

---

### Post by Peter09 on 2008-11-09
Vista should work around the RAM allocation from Ubuntu. I do not see that you should have a problem with RAM.Evenn if it ran out of RAM you would just start to use your swapfile.

---

