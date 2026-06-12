---
title: "Eclipse on ubuntu 7.10?"
date: 2008-02-08
forum: Programming Talk
---

### Post by Firepony302 on 2008-02-08
I recently updated to ubuntu 7.10, and now eclipse doesn't work correctly, it opens, but it doesn't open the windows inside of eclipse, they all are throwing null pointer exceptions.
Has anyone run Eclipse on 7.10?

---

### Post by rufius on 2008-02-08
I've been running it regularly, but I didn't "upgrade." Try removing your eclipse preferences folder, maybe by renaming it something else or creating a fresh login and testing there. That'll tell you whether eclipse is broken altogether or if your settings are just screwed up.

Hope that helps :)

---

### Post by Firepony302 on 2008-02-08
sorry i should have been more detailed... 
what i ment to say was, i formated my hd and installed 7.10, then downloaded Eclipse IDE for Java EE Developers. 
and did a fresh install with that, and it does not work.
could it be that its not the base version of eclipse?

i know the base version worked great when i had 7.4 installed

---

### Post by buntu_Geek on 2008-02-09
Me too having the same problem....

I was using Eclipse for j2ee development... also used the IBM WebSphere Community edition with Eclipse.... In Fiesty it was working great....

But After i upgraded to Gutsy .. the WebSphere server isnt starting and its giving me java exceptions...

Problem isn't resolved yet.... :(

---

### Post by tenmillionmilesaway on 2008-02-09
After you did a fresh install of 7.10 did you install the sun java jdk and update-alternatives?

People have had trouble running eclipse with the gnu java that comes with ubuntu before.

---

### Post by Firepony302 on 2008-02-11
hmm didn't even think about that, I'll try the sun JDK, thanks!

---

### Post by buntu_Geek on 2008-02-16
But i guess upgrading to Gutsy  takes care of updating the available packages too....

Any ways i ll give it a try...

---

### Post by dempl_dempl on 2008-02-16
My friend had  that problem too.  He installed  Feisty back , and everything worked fine.

---

### Post by Geekkit on 2008-02-16
> **Firepony302 said:**
> Has anyone run Eclipse on 7.10?

I tried but Eclipse went and globbered my default Java compiler at the console. My solutions was easy: remove Eclipse all together and stick with Netbeans 5.5.1.

That and the UML diagram features and plugin architecture in Netbeans are both light years ahead of what Eclipse offers.

---

