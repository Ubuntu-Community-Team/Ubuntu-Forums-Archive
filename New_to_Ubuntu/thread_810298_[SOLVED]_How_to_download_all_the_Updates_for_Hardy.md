---
title: "[SOLVED] How to download all the Updates for Hardy?"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by YldGuy on 2008-05-28
I am gonna wipe XP and put Ubuntu Hardy exclusively on my laptop once i get the internet connection at home by next week. One of my friends wanted to try out Ubuntu. I will be setting up her laptop also once mine gets working. And since when i install Ubuntu, it will ask for updates, I don't want to download the updates once again for the second laptop. I can very well download the updates on my laptop and use the same on the second laptop but I was wondering if there is some way to download all the updates released till date now and use THAT directly on both the laptops without waiting to connect to the internet? Is there any way?

---

### Post by sayakb on 2008-05-28
Try [AptOnCD]("http://aptoncd.sourceforge.net/"). This would burn your packages on a disk and you can restore them again using the same application.

---

### Post by lostlinuxkiwi on 2008-05-28
If your gonna be wiping xp I assume you will be doing a fresh install so why not just download the hardy iso instead. When I upgraded my laptop it was almost a 600MB anyway. That way you can use it on your friends computer 2.

---

### Post by kpkeerthi on 2008-05-28
If you have 2 or more machines on your LAN, you can set up a LAN repository in one of your machines ('X') and have the others in the LAN install the packages from 'X' in the LAN. 

[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)

---

### Post by YldGuy on 2008-05-28
Thanks... that would solve one of the problem. Is there any way to download all the updates right now while i am on a windows machine?

---

### Post by YldGuy on 2008-05-28
> **lostlinuxkiwi said:**
> If your gonna be wiping xp I assume you will be doing a fresh install so why not just download the hardy iso instead. When I upgraded my laptop it was almost a 600MB anyway. That way you can use it on your friends computer 2.

I already have the CD i ordered. Download will eat up my bandwidth at office.

---

### Post by YldGuy on 2008-05-28
> **kpkeerthi said:**
> If you have 2 or more machines on your LAN, you can set up a LAN repository in one of your machines ('X') and have the others in the LAN install the packages from 'X' in the LAN. 

[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher](http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher)

Its not networked. Both are standalone lappies.

---

### Post by kpkeerthi on 2008-05-28
> **YldGuy said:**
> Its not networked. Both are standalone lappies.

Just connect your friends lappy to your router and both are networked. Instantaneously.

---

### Post by forestpixie on 2008-05-28
When I'm mucking about with pre release versions I copy all the debs which update downloads onto a stick and then copy them back then do an update with 

sudo apt-get update

Maybe there are reasons for not doing it, I don't know, but it doesn't cause me a problem - personally I've never managed to get aptoncd to work for me.

---

### Post by sayakb on 2008-05-28
> **forestpixie said:**
> personally I've never managed to get aptoncd to work for me.

Unless you haven't ever issued the apt-get clean command or deleted something from the /var/cache/apt/archives, it should work I guess..

PS: forestpixie: Your bean count has gone above 3500. You can have a custom tagline now I guess ;)

---

### Post by YldGuy on 2008-05-28
> **kpkeerthi said:**
> Just connect your friends lappy to your router and both are networked. Instantaneously.

i am very impatient.. :) .. i have to wait till next week for my modem and router to arrive at home.. :).. so will hv to wait till next week to install or if i can somehow download the updates to this windows machine and xfer to my gutsy machine and burn it to a disk using APTonCD, that will be great. Thats what i am looking for. if it is possible i can go ahead and do both installations tonight itself. any ideas?

---

### Post by kpkeerthi on 2008-05-28
> **YldGuy said:**
> i am very impatient.. :) .. i have to wait till next week for my modem and router to arrive at home.. :).. so will hv to wait till next week to install or if i can somehow download the updates to this windows machine and xfer to my gutsy machine and burn it to a disk using APTonCD, that will be great. Thats what i am looking for. if it is possible i can go ahead and do both installations tonight itself. any ideas?

Install VMware on your windows machine. Install ubuntu as a guest. Update your guest ubuntu and create aptoncd off your guest ubuntu. Use the CD on your real ubuntu set ups later. Have fun.

---

### Post by forestpixie on 2008-05-28
> **LinuxIsInnovation said:**
> Unless you haven't ever issued the apt-get clean command or deleted something from the /var/cache/apt/archives, it should work I guess..

Clean install - download updates, install aptoncd - keep till it breaks through mucking about, reinstall buntu, reinstall aptoncd - throw disc away in disgust and download updates again :)

Probably something I'm doing wrong but it should be pretty self explanatory.

So long story short - I use a stick :)

---

### Post by YldGuy on 2008-05-28
> **kpkeerthi said:**
> Install VMware on your windows machine. Install ubuntu as a guest. Update your guest ubuntu and create aptoncd off your guest ubuntu. Use the CD on your real ubuntu set ups later. Have fun.

will try this out.

---

