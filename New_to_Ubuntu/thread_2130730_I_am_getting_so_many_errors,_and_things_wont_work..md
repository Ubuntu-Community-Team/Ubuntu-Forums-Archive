---
title: "I am getting so many errors, and things wont work. What could be wrong?"
date: 2013-03-30
forum: New to Ubuntu
---

### Post by AndEilert on 2013-03-30
So... title says it all i guess..

I have had problems with things hanging, and go insanely warm from day one, but the last few days things have been extra difficult. And 10 minutes ago i got these messages, and at the same time my fans went ultraspeed and i checked sensors,  everything inside this puppy went to 95(!!!) degrees.   So can anyone please tell me what is going on?

Thank you:D

---

### Post by dabl on 2013-03-30
It is a thermal problem, but way too little information to know more.  Search the forum with the make and model of the PC and the word "thermal" and you will probably find some useful threads.

---

### Post by AndEilert on 2013-03-30
Well i couldnt find anything about my problem... so tell me what you need and you will get it.

Its a HP laptop. HP G6 Pavillion, i know its not the best computer when it comes to heats.. but it still shouldnt give me such error messages?

---

### Post by Bashing-om on 2013-03-30
AndEilert; Hi !

As advised, you have a heat problem. The solution might or might not be above your abilities. Opening up a lap top can be very difficult and exacting. Do your homework by searching for your system documentation.
One must blow out the dust from within the machine and components ( carefully!  not to damage the cooling fan's blades or dislodge wiring connectors) and replace the thermal paste seating the CPU onto the mother board ..this might require special tools to dislodge the cpu.
[INDENT=3]
caution and care is advised.

[/INDENT]

---

### Post by AndEilert on 2013-03-30
So the above error messages are only because of thermal problems?

---

### Post by Bashing-om on 2013-03-30
AndEilert;

Not necessarily, I have seen several threads in this respect of apport reporting errors with intel graphics chips. See:
[http://ubuntuforums.org/showthread.php?t=2053494](http://ubuntuforums.org/showthread.php?t=2053494)

But, I do not know that this issue correlates to a heating issue. If your box is in fact overheating that needs to be addressed soonest.[INDENT=3]
in my opinion

[/INDENT]

---

### Post by dabl on 2013-03-30
Hmmm -- is _my_ google better than _your_ google?

[http://ubuntuforums.org/showthread.php?t=2039443](http://ubuntuforums.org/showthread.php?t=2039443)

[http://askubuntu.com/questions/207733/ubuntu-12-04-gets-overheated-whereas-i-have-no-heating-problems-on-windows-7-wh](http://askubuntu.com/questions/207733/ubuntu-12-04-gets-overheated-whereas-i-have-no-heating-problems-on-windows-7-wh)

[http://askubuntu.com/questions/95922/why-am-i-having-overheating-problems-on-hp-pavilion-g6-1058er](http://askubuntu.com/questions/95922/why-am-i-having-overheating-problems-on-hp-pavilion-g6-1058er)

[http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/Thermal-Shutdown-Problem/td-p/627399/page/2](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/Thermal-Shutdown-Problem/td-p/627399/page/2)

---

### Post by carl4926 on 2013-03-30
> **AndEilert said:**
> So... title says it all i guess..

I have had problems with things hanging, and go insanely warm from day one, but the last few days things have been extra difficult. And 10 minutes ago i got these messages, and at the same time my fans went ultraspeed and i checked sensors,  everything inside this puppy went to 95(!!!) degrees.   So can anyone please tell me what is going on?

Thank you:D
I had this and just disabled the reporting
[http://ubuntuforums.org/showthread.php?t=2053494](http://ubuntuforums.org/showthread.php?t=2053494)

It's working fine

---

### Post by vanadium on 2013-03-31
Dissabling Apport messages is one thing. Do not worry doing that: apport was by default disabled on previous Ubuntu versions, so you never saw the messages. That it is enabled since 12.04 would wrongly give the impression that Ubuntu has become instable.

There is another issue. I started to have random freezes since a few kernel updates. I locked my kernel to 3.5.0-24, and never have these freezes: this is clearly reproducible. Today I stumbled upon this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1140716)

If you also have an Intel graphics card, then likely you will also benefit from reverting to a previous kernel for the time being.

---

### Post by coldraven on 2013-03-31
My HP 6715b laptop fan was half blocked with fluff. I found some very good pictures showing how to get to it, but I have lost the link.
You have to remove the three screws with the little keyboard icon, one is under the hatch for the memory.
Then click back the little spacers between the function keys.
Then carefully remove the keyboard, don't damage the ribbon cable, it is probably best to unplug it by flipping down the lock on the connector.
Then prise of the bezel and you can unscrew the fan for cleaning.
Now it runs sooo quiet :)

---

### Post by AndEilert on 2013-03-31
Thank you so much guys, i will try all of your solutions:D

---

