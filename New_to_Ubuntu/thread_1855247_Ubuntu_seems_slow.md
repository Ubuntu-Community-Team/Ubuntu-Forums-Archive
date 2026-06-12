---
title: "Ubuntu seems slow"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by Phaddie on 2011-10-05
Hey guys!

  My last issue was solved so quickly here I thought I might post a second concern.  I am VERY new to linux (about 2 days).  I installed ubuntu 11.04 on my PC, which consists of:

Intel 2600k
ASUS p8-z68vpro
8 gigs RAM
GTX-580

 Ubuntu is installed on its own 500gig HDD.

 The system seems very sluggish compared to my windows 7 install on the same machine.  It takes quite a bit longer to boot, and applications take quite a while as well.  I apologize for not having exact times.

  Could this be a settings or drivers issue?  And if so where is a good place to start?  Or is ubuntu just not as responsive as windows 7?

  Thank you in advance

    Phad

---

### Post by wildmanne39 on 2011-10-05
Hi, here is a link try it since it is easy to do then see if performance has improved.
[http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow](http://www.jondev.net/articles/Ubuntu_11.04_choppy_or_slow)
Thank you

---

### Post by Phaddie on 2011-10-05
Awesome thank you.  I will report back.

---

### Post by Phaddie on 2011-10-05
I cannot install it I get an error that says:

Package dependencies cannot be resolved

 When I press details it just says that simple-ccsm has unmet dependencies (which I think is the program I am trying to install)

  Phad

---

### Post by wildmanne39 on 2011-10-05
Hi, you want to install CompizConfig Settings Manager not the simple ccsm.
Thank you

---

### Post by Phaddie on 2011-10-05
That is what I am installing.  I just assumed that the error msg was calling Simple CompizConfig Setting Manages - Simple-ccsm.

  In either case it will not install.

---

### Post by wildmanne39 on 2011-10-05
Hi, try this in a terminal please:
```
sudo apt-get install -f install
```
```
sudo apt-get update && sudo apt-get upgrade
```
You my need to restart you computer after the first 2 commands.
```
sudo apt-get install compizconfig-settings-manager
```
Thank you

---

### Post by Phaddie on 2011-10-05
That installed it and I followed the instructions.  Things do seem a bit more snappy for sure.  

  Thank you!!

  Phad

---

### Post by wildmanne39 on 2011-10-05
Hi, I am glad to help, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

