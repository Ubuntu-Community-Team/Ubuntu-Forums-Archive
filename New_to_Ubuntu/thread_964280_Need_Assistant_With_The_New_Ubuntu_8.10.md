---
title: "Need Assistant With The New Ubuntu 8.10"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by afbuntu on 2008-10-30
Hi there... Can somebody explain to me why is my new ubuntu 8.10 system tend to freeze or crash more frequently than ubuntu 8.04. Its really hinder my work. Actually, with ubuntu 8.04 i dont have this problem. The one i use is fresh install not an upgrade one.

---

### Post by nynoah on 2008-10-30
My advice is to always wait a month before you install/upgrade to the newest version.  That way a great deal of the bugs will be worked out and the updates to fix those bugs will be available.  If you only have one computer and can not afford down time, stick with 8.04 for a little while longer.

---

### Post by jbrown96 on 2008-10-30
If you upgraded, it is probably worthwhile to do a clean install. Could you give us some more information about the crashes? what apps are you running? Hardware (post the output of lspci)?

---

### Post by afbuntu on 2008-10-30
Its just freezes. The capslock and numlock indicator on my keyboard blink together. The whole system just froze. When this happen, nothings work. The keyboard, the mouse, its just froze stiff. The only thing I can do is hit the reset switch on my computer.

---

### Post by SunnyRabbiera on 2008-10-30
yeh sometimes the updates can do this, if it aint broke dont fix it as they say.

---

### Post by afbuntu on 2008-10-30
So... any suggestion on what should i do? should i turn back to ubuntu 8.04. Is it because my computer don't is not compatible with the new version? I would really appreciate any help>

---

### Post by afbuntu on 2008-10-30
So... any suggestion on what should i do? should i turn back to ubuntu 8.04. Is it because my computer don't is not compatible with the new version? I would really appreciate any help.

---

### Post by nynoah on 2008-10-30
Get the live disk, an external Hard drive, pull all your files onto that that you want to keep and then do a clean install.  Sounds like you have a serious problem.  I really wish that there was no way to upgrade.  Its more hassle than it is worth.  I always do a clean install, learned that the hard way a while ago.

Seriously, right now is the time when you go into data protection mode.  Get the files you NEED so you won't regret what you might lose.

---

### Post by hyper_ch on 2008-10-31
> **nynoah said:**
> My advice is to always wait a month before you install/upgrade to the newest version.  That way a great deal of the bugs will be worked out and the updates to fix those bugs will be available.
Only problem is that if everybody thinks like that, nobody is testing early releases and nobody is reporting bugs. In the end you will ahve the same bugs a month later ;)

---

### Post by narnian99 on 2008-10-31
> **hyper_ch said:**
> Only problem is that if everybody thinks like that, nobody is testing early releases and nobody is reporting bugs. In the end you will ahve the same bugs a month later ;)

nynoah's advice is sound, no matter how well it is tested by others, a, operating system upgrade is a major event. if you care about your data you should ensure you have a good backup before upgrading. if you need to ensure your computer is working following an upgrade, it is wise to test the upgrade first, preferably on an alternative system (with the same hardware). at worst you need to be able to restore your previous system from your backup.

yes, it is important to do testing, but not always wise to do it on production machines.

that being said, for most people an upgrade should be painless. if you can get your system to boot, have a look at /var/log/messages and /var/log/syslog for error messages just before the crash - this might give you a pointer. also run memtest86+ and make sure you don't memory issues that may not have surfaced until the upgrade. (the new system may be touching parts of memory that it hadn't before)

---

### Post by redbob on 2008-10-31
Upgrading is a two-face knife, as we call it in Brazil. By one hand, we eliminate so much incompatibilities... for example my laptop worked better with Intrepid alpha 6 than with Hardy LTS due to astonishing better wireless support. By other hand my desktop is running Hardy LTS so fine, that I'm lazy to upgrade it! :popcorn:

---

### Post by alwez_loner on 2008-10-31
> **hyper_ch said:**
> Only problem is that if everybody thinks like that, nobody is testing early releases and nobody is reporting bugs. In the end you will ahve the same bugs a month later ;)

+ 1
If no body tries it out then they won't know where to fix the bugs. But i would advice you to back up you systems and then give it a try...

---

### Post by hyper_ch on 2008-10-31
> **narnian99 said:**
> if you care about your data you should ensure you have a good backup before upgrading.

> **alwez_loner said:**
> + 1
But i would advice you to back up you systems and then give it a try...

I disagree... there should be no need for a backup because of an upgrade ... instead you should have regular backups all the time. Even if you don't plan on changing anything major, hardware can fail anytime... I hope you get what I mean to say ;)

---

### Post by Ron G on 2008-10-31
Im no expert, but no one knows what type maching you are running, the hardware you have, memory etc, etc. You need to supply as much info as you if you want help. Its like asking "whats wrong with my car", and not telling the make, model and year of the car. Understand? Try to give as much info as possible , and Ill bet someone out here will have something for you.

---

### Post by afbuntu on 2008-11-01
Thank you for the advice. Come to think of it i think its time for me to go data backup mode. But i will stick to linux especialy ubuntu. With windows i can do almost everything, its so easy. With ubuntu everything is new and exciting. Thanx a lot.

---

### Post by okey666 on 2008-11-01
> **nynoah said:**
> Get the live disk, an external Hard drive, pull all your files onto that that you want to keep and then do a clean install.  Sounds like you have a serious problem.  I really wish that there was no way to upgrade.  Its more hassle than it is worth.  I always do a clean install, learned that the hard way a while ago.

Seriously, right now is the time when you go into data protection mode.  Get the files you NEED so you won't regret what you might lose.

Am I right in saying that he DID NOT upgrade and did a clean install?

---

