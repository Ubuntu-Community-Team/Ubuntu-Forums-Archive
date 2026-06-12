---
title: "banshee"
date: 2012-01-09
forum: New to Ubuntu
---

### Post by openation1 on 2012-01-09
hello, I am having difficulty in getting  my music album names. it suppose to do it automatically and it doesn't. would you please help me with this issue? thank you.

---

### Post by Basher101 on 2012-01-09
i for myself have no knowledge on banshee whatsoever, you can go ahead and try a different music player like Rhythmbox and see if that works out for you.

regards

---

### Post by Double.J on 2012-01-09
Hi there!

Which version of banshee are you using? it seems that versions before 2.2 (ubuntu 11.10) have a bug fetching the cd info.

---

### Post by Basher101 on 2012-01-09
> **gnu/mirow said:**
> Hi there!

Which version of banshee are you using? it seems that versions before 2.2 (ubuntu 11.10) have a bug fetching the cd info.

i dont use banshee at all and never did^^ on my laptop i use Amarok (slows down the system a bit since its a KDE app) and on my Desktop i use Rhythmbox. I must say Rhythmbox is one of the better music players, have had no problems with it whatsoever, just try it out yourself.

regards

---

### Post by Double.J on 2012-01-09
> **Basher101 said:**
> i dont use banshee at all and never did^^ on my laptop i use Amarok (slows down the system a bit since its a KDE app) and on my Desktop i use Rhythmbox. I must say Rhythmbox is one of the better music players, have had no problems with it whatsoever, just try it out yourself.

regards

Me either, I use VLC for it's cross platform support - I like having the same player across my distros n OS X - little bit of OCD there!

I just asked the OP in case they wanted to attempt to resolve the banshee issue :)

---

### Post by wildmanne39 on 2012-01-09
Hi +1 for Rhythmbox it seems to work better, I had nothing but trouble with banshee so I installed Rhythmbox and have had no more trouble, plus Rhythmbox is suppose to be the default player in the next release.

You may want to have a look at these links.
[http://askubuntu.com/questions/47571/can-banshee-fix-music-metadata-information](http://askubuntu.com/questions/47571/can-banshee-fix-music-metadata-information)
[http://askubuntu.com/questions/43905/banshee-is-unable-to-determine-audio-cd-metadata](http://askubuntu.com/questions/43905/banshee-is-unable-to-determine-audio-cd-metadata)
Thanks

---

### Post by openation1 on 2012-01-09
thank you for the info I will try some of them. like in windows media player you insert a musical cd and it will get the name of the album by itself that is awesome. that is what I want in ubuntu. I am using 11.04 should I upgrade to 11.10?

---

### Post by Basher101 on 2012-01-09
> **openation1 said:**
> thank you for the info I will try some of them. like in windows media player you insert a musical cd and it will get the name of the album by itself that is awesome. that is what I want in ubuntu. I am using 11.04 should I upgrade to 11.10?

if you have no issues when using the Live CD you can make an upgrade. Note that upgrades tend to be buggy, so some things may not work so backup your important data. 

I always recommend making a fresh install as it has much higher chances of not being buggy.

regards

---

### Post by Double.J on 2012-01-09
> **Basher101 said:**
> if you have no issues when using the Live CD you can make an upgrade. Note that upgrades tend to be buggy, so some things may not work so backup your important data. 

I always recommend making a fresh install as it has much higher chances of not being buggy.

regards

+1 

Yes it does look as though this may be the reason - you'll have version 2.0.1 that has trouble connecting to host. It's up to you whether you want to upgrade a distro for a media player - as you can see there are a great many. Take into account that 11.10 will be being replaced in 3 months as it is. Ubuntu never updated banshee for 11.04, but banshee do provide a repo which should work for 11.04

```

sudo apt-add-repository ppa:banshee-team/ppa
sudo apt-get update
sudo apt-get purge banshee
sudo apt-get install bansee

```
That should give you a working banshee without re-installing the system, be sure to try the other recommendations as well!

:)

---

### Post by wildmanne39 on 2012-01-09
Hi, please remember that this ```
sudo apt-add-repository ppa:banshee-team/ppa
sudo apt-get update
sudo apt-get purge banshee
sudo apt-get install banshee
```
is the developmental ppa's so they will be updated often but may cause breakage.
Thanks

---

### Post by openation1 on 2012-01-25
well thank you so much you are great companions.....

---

