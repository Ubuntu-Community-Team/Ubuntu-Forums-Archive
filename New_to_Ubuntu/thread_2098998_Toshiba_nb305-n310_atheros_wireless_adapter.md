---
title: "Toshiba nb305-n310 atheros wireless adapter"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by dg91 on 2012-12-28
Hi I am still newbie to linux and I am now very tired of looking for solution on forums ...I tryed almost anything from any forum I could find and still cant get it to work...

The problem is next: I cant enable atheros wireless adapter on my toshiba nb305-n310 on ubuntu 12.10.

So if someone would be nice to write me a simple tutorial how to do this beacuse I am new to linux and I dont understand all things right now..

what I discovered so far looking on google is that I need to install ath9k or ath5k wireless backports but when I try to install them from terminal I allways get same message : backports packages could not be found.

---

### Post by audiomick on 2012-12-28
Could you please open a terminal and do
```
sudo lshw -C network
```

and post the results of that here. That will show people here exactly what network card you are dealing with.

Also, do you have a link to the site where you read that you need to install those backports? It might help to know what information you are working with.

---

### Post by dg91 on 2012-12-28
My wireless card is : Atheros AR9285 PCI Express network adapter.

What I understand from forums as linux newbie I need to install backport drivers for that wireless card..

sudo apt-get install linux-backports-modules-maverick-generic-wireless
sudo apt-get install linux-backports-modules-jaunty ....
etc..

but as I understand every ubuntu version has its own command for that drivers...and I found out that I need ath9k drivers for my wifi card...

---

### Post by audiomick on 2012-12-28
Firstly, which version of Ubuntu are you using, actually?

Have you already tried the "additional drivers" utility? Your machine needs to be connected to the internet, i.e. on a cable, to do this.

---

### Post by robertthebruce on 2012-12-28
hi Audiomick

im having a similar issue here [http://ubuntuforums.org/showthread.php?p=12425901#post12425901](http://ubuntuforums.org/showthread.php?p=12425901#post12425901) and also following this thread...

will using the additional drivers drivers mean using wep?

for the additional drivers utility for ubuntu 12.04 lts server is it sudo apt-get additional-driver?
I doubt it but i doubt my ability to find the package name for the distro i have
thanks for any help

---

### Post by robertthebruce on 2012-12-28
sorry crosspost

---

### Post by robertthebruce on 2012-12-28
sorry crosspost

---

### Post by robertthebruce on 2012-12-28
sorry crosspost

---

### Post by robertthebruce on 2012-12-28
sorry crosspost

---

### Post by dg91 on 2012-12-28
I am using Ubuntu 12.10 but I can change that if my wireless will work on some other version like 12.4, 11,10....its not a problem for me to download another ubuntu version... 

yes michael I tryed aditional drivers but there is nothing in there.... ;(

...and yes when I connect my cable to netbook internet works...so only that wifi card is problem...i need some kind of drivers that will turn on that atheros card.

and one more thing.... whenever I try to install some of this drivers in terminal this pop up: 
"unable to locate "xxxx" package"? :P

---

### Post by audiomick on 2012-12-28
> **robertthebruce said:**
> 

will using the additional drivers drivers mean using wep?

If you mean only wep as opposed to wpa, I don't believe so.

---

### Post by robertthebruce on 2012-12-28
many thanks AM

---

### Post by Pjotr123 on 2012-12-28
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by davidtrounce on 2012-12-29
I got an answer for enabling Toshiba NB305 wireless for 12.04 by simply going to the terminal and entering:
sudo modprobe ath9k

---

### Post by dg91 on 2013-01-06
It says "invalid argument" ....maybe I dont have ath9k drivers...how you installed them?

---

