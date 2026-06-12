---
title: "have I got a virus"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by philipluna66 on 2008-06-19
After booting up my  1 weeks hols I noticed it seemed slower than normal. When I click on a icon on the screen they dont work I have to right click and click open.My desktop picture has changed to just a blank grey.And everything takes ages to click in. I have375 mb ram and it is using 163mb to stand still and my swap is using 428k but it increases till my swap is full then I have to reboot. It is an old computer with a pentum 111 processor My cpu is using 6 - 18% standing still with nothing runing

---

### Post by Xerp on 2008-06-19
No, you do not have a virus. Take a look at the output from "top" (run it from the terminal) and see whats going on. It should show the top processes and your memory usage.

If you have to right-click and open on icons, try a different mouse.

You may also be starting to have hardware problems. Check the status of your hard disk drives by using smartmontools - [http://smartmontools.sourceforge.net/](http://smartmontools.sourceforge.net/)

Your logs files are also a great place to see if anything strange is happening. Check */var/log/syslog *and */var/log/messages*.

---

### Post by Paqman on 2008-06-19
You don't have a virus.

Let's try a bit of preliminary fault-finding: try popping the LiveCD in and running off that session. If you get the same behaviour then you have a hardware problem, if not then it's a software problem.

---

### Post by Pjotr123 on 2008-06-19
I award a bottle of excellent red wine (Cabernet Sauvignon) to anyone who finds a Linux virus on his computer!  :-)

Only condition: you should not have put it there on purpose, it must be an accidental infection.

Greeting, Pjotr.

---

