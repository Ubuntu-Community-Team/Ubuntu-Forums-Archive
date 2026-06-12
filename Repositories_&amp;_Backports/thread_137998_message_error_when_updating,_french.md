---
title: "message error when updating, french"
date: 2006-03-01
forum: Repositories &amp; Backports
---

### Post by koubicha on 2006-03-01
a frenchie needs your help  ;) 
i'm unable to reach the french forum... so excuse me for my english...

my problem is with the "mise à jour" system that telles you where's updates you should do .
I have this error message "impossible d'obtenir un verrou exclusif". it indicates that another application as ap-get has probably been launched, but of course it's not the case !
so I can't update my system...

is there anything I could do ??

---

### Post by cronholio on 2006-03-01
Usually the reason is that Synaptic is running. You can check the System Monitor to be sure.

---

### Post by koubicha on 2006-03-01
thank you for helping me.
synaptic wasn't runing I didn't launched it...

the french forum is active again, it was easier to find an answer in french, I wasn't the one with this problem...

I just did
 sudo dpkg --configure -a

and now it works !

---

