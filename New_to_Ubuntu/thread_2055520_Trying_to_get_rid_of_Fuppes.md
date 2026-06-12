---
title: "Trying to get rid of Fuppes"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by garyhdez on 2012-09-09
Hi all.  Complete novice here.  Just got my Ubuntu Server up and running.  I tried to install Fuppes to stream to my xbox 360 but it is a complete nightmare.  I am now trying to get rid of it.  I have tried the following two commands:

> apt-get autoremove fuppes
apt-get remove --purge fuppes
Both of them give me the following:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package fuppes
I tried reloading my synaptic package manager and nothing changed.

Please help me out.

---

### Post by newb85 on 2012-09-09
Fuppes (whatever it is) isn't in the main repositories.  You need to give a little information about how you installed it.

---

### Post by garyhdez on 2012-09-09
Thanks for the reply.

I installed it following the steps in the following link:

[http://carsongee.com/blog/2011-01-17/install-fuppes-for-streaming-media-to-xbox-360-and](http://carsongee.com/blog/2011-01-17/install-fuppes-for-streaming-media-to-xbox-360-and)

---

### Post by oldos2er on 2012-09-09
Try these commands: ```
cd fuppes

sudo make uninstall

sudo apt-get autoremove

``` You can delete the fuppes folder if you're sure you no longer want it: ```
rm -rf fuppes
```

---

### Post by garyhdez on 2012-09-09
Thanks for the help.  That seemed to take care of it.

---

