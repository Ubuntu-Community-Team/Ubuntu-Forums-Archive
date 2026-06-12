---
title: "Best recomended light distro for my desktop"
date: 2013-01-16
forum: New to Ubuntu
---

### Post by Krashx22 on 2013-01-16
I have an acer aspire m1100 desktop with ubuntu 12.04 that i recently installed. The coputer has as follows
Amd sempron 3400 2ghz single core
512mb of ram
Ati radeon onboard graphics card
250gb sata hard drive

I find ubuntu to have a massive struggle running. Sometimes firefox takes 5 minutes to open. Other programs fall flat on their face. So on and so forth. Im wondering if anyone can recomend the best user friendly and lightweight linux based os that is easy to install. And will run somewhat fast. Sadly i really like ubuntu so im looking for something similar. Ease of access is a big thing. Faster the better. I dont care if it looks like windows 3.1 as long as it can perform decently. Something i can customize and tweak. Backtrack seems like something exciting but may not run easily. So i thank everyone for their input before hand. I would like to speed this poor girl up a bit tonight

---

### Post by sffvba[e0rt on 2013-01-16
[Lubuntu]("http://lubuntu.net/")


404

---

### Post by |{urse on 2013-01-16
Puppy (fast, a pre-schooler could install and configure it, but it also looks like it was made for pre-schoolers)

-or-

Lubuntu (fast, easy to use) <-- My first recommendation

-or-

Slitaz (installed to HDD) (faster, fairly usable)

-or- 

Slackware 14.0 (ridiculously fast, needs love and sleepless nights to make it work)

---

### Post by Krashx22 on 2013-01-16
So. Now swapping ubuntu for lubuntu. Can i do it live or best to make an install disc?

---

### Post by Version Dependency on 2013-01-16
I have a couple of ten year old machines that I have installed Lubuntu on before.  One of them though did not like the graphical installer.  It's an easy workaround though...install Ubuntu Server (without all the server related software...so a very quick install) and then:  sudo apt-get install lubuntu-desktop .   Reboot and Lubuntu.

---

### Post by Krashx22 on 2013-01-16
And also. Any recomendation on a program that can list off my hardware specs.

---

### Post by sffvba[e0rt on 2013-01-16
> **Krashx22 said:**
> So. Now swapping ubuntu for lubuntu. Can i do it live or best to make an install disc?

You can install the Lubuntu DE unto your existing install... but it comes with many lighter alternatives to applications so if you want all the benefit I would suggest getting the ISO and installing it from scratch, but I am just lazy :p


404

---

### Post by Version Dependency on 2013-01-16
> **Krashx22 said:**
> And also. Any recomendation on a program that can list off my hardware specs.

For a nicely presented list of your specs displayed in Firefox, try: 

```
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
```

Or you could try this in terminal: lspci 
(not as pretty).

---

### Post by Krashx22 on 2013-01-16
im going to try to do a full install for sure. id rather not have a frankenacer here. i did find that hardware detection then any windows program. so Lubuntu. are the games and apps and everything the same?

---

### Post by Krashx22 on 2013-01-16
also, what version best suits the amd with 32 bit. the regular intel one im guessing?

---

### Post by sffvba[e0rt on 2013-01-16
> **Krashx22 said:**
> im going to try to do a full install for sure. id rather not have a frankenacer here. i did find that hardware detection then any windows program. so Lubuntu. are the games and apps and everything the same?

All the apps you can get in Ubuntu is available in Lubuntu...

> **Krashx22 said:**
> also, what version best suits the amd with 32 bit. the regular intel one im guessing?

As long as the image either states x86 or states 32-bit.


404

---

### Post by Krashx22 on 2013-01-16
last question... for now. :) i burt ubuntu 12.04 onto a verbatim cd-rom. and im doing the same with lubuntu. now even though they say you cant do it with new copies of ubuntu it worked and i had no problems with the ubuntu install. so what are my chances lubuntu should be so co operative?

---

### Post by sffvba[e0rt on 2013-01-16
If the ISO fits it will work.


404

---

### Post by Krashx22 on 2013-01-16
Iso was 693mb or something close to. When burning it said it was 739mb. It burnt. Wouldnt eject. I evected it. Restarded my comp. Tried the cd live to see if it works. Now im installing lubuntu. .... Hey whatever works

---

### Post by Paddy Landau on 2013-01-16
Lubuntu is a good system, which has rescued a few old computers.

An even lighter distro is [Bodhi]("http://www.bodhilinux.com/"), but it is an unofficial Ubuntu distro.

---

### Post by IWantFroyo on 2013-01-16
> **Krashx22 said:**
> Iso was 693mb or something close to. When burning it said it was 739mb. It burnt. Wouldnt eject. I evected it. Restarded my comp. Tried the cd live to see if it works. Now im installing lubuntu. .... Hey whatever works

Good luck!

I always had sound problems with Lubuntu... If you can't adjust sound then remember that ```
alsamixer
``` is your friend.

---

### Post by Krashx22 on 2013-01-16
ok so im up and running on lubuntu, holy its ten times as fast, and lots of nice features, and installed in no time, since i used a cd instead of a dvd though it didnt install some programs as it told me and that id just have to manually install them, however that works. but right from startup im impressed. Thank you for the help.

NOW, who do i talk to to put ubuntu on my SAMSUNG GALAXY S2 LTE? :)

---

### Post by SparkyPrawn on 2013-01-16
> **not found said:**
> [Lubuntu]("http://lubuntu.net/")


404
This.

---

### Post by IWantFroyo on 2013-01-16
That's probably not a good idea...

You'd have to root it and hit a hold of a .zip rom, which doesn't currently exist afaik.

---

### Post by Krashx22 on 2013-01-16
well that kinda sucks. ill have to wait like us all. now, chromium, when i go to download the flash plugin, what one do i choose and best way to go about installing it,

---

### Post by IWantFroyo on 2013-01-16
I would recommend downloading Google Chrome and installing it with:
```
cd Downloads

sudo dpkg -i chrome*
```

It comes with Flash.

---

### Post by sffvba[e0rt on 2013-01-16
*Thread moved to **Absolute Beginners Section**.* as this is not about another distro but mostly about Lubuntu.

I would also suggest searching the forum for some of the answers and if possible start creating separate threads in the correct sub-forum with other questions and queries.


404

---

### Post by Krashx22 on 2013-01-16
thank you not found, for the absolute realization. will do though, appreciate the help.

---

### Post by Krashx22 on 2013-01-16
> **IWantFroyo said:**
> I would recommend downloading Google Chrome and installing it with:
```
cd Downloads

sudo dpkg -i chrome*
```

It comes with Flash.


Will chrome slow down compared to chromium? im rather enjoying the speed.

---

### Post by IWantFroyo on 2013-01-16
No. 
Should be the same.

---

### Post by Krashx22 on 2013-01-16
#mcknight@mcknight-Aspire-M1100:~/Downloads$ sudo dpkg -i chrome*
[sudo] password for mcknight: 
dpkg: error processing chrome* (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 chrome*
mcknight@mcknight-Aspire-M1100:~/Downloads$#


trying to get it going but not having any luck

---

### Post by IWantFroyo on 2013-01-16
Ah right. Sorry.

Run:
```
sudo apt-get install -f
```

It should fix the issue.

---

