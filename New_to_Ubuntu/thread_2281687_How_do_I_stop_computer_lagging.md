---
title: "How do I stop computer lagging"
date: 2015-06-08
forum: New to Ubuntu
---

### Post by gsegovia15 on 2015-06-08
Hi everyone new to the whole linux ios. I started with installing amahi on a old pc. Really easy setup, using plex and still learning on that end. But a few weeks ago I came across ubuntu read a bit about it. After multiple try I finally got it working. I installed ubuntu 14.04 desktop. But after playing with it. It is very lagging.  So I wanted to Ask what would yall recommend. I'm trhing to run my security cameras on it using xeoma. 

Pc info. Dell dimension 4600 (old)
Intel 4  2.8 processor
4gb  pc3200 low density Ram (upgraded)
500gb sata hard drive. (Upgraded)

---

### Post by wildmanne39 on 2015-06-08
Hi, welcome to the forum! I changed the title to make it more descriptive of your issue.

---

### Post by grahammechanical on 2015-06-08
At first glance the specification seems fine for Ubuntu but can the graphic adapter run Ubuntu's Unity user interface? That machine has integrated graphics and it seems that the graphic adapter shares the RAM. So, run this command

```
/usr/lib/nux/unity_support_test -p
```

If the answer is No, then consider installing Xubuntu or Lubuntu instead.

Regards.

---

### Post by mastablasta on 2015-06-09
if you need it only for sec cameras then use as light desktop as possible. Lubuntu would be a place to start as well as Xubuntu.

an even lighter one would be only a windows manager such as the one found in ToriOS or AntiX.

---

### Post by sudodus on 2015-06-09
I bought such a computer in 2004 (but only 1.5 GB RAM). It is still working, but slowly with standard Ubuntu. Like mastablasta I also suggest Lubuntu and Xubuntu, perhaps Ubuntu Mate, depending on your preferences. If it is important to get rid of lagging, I suggest that you get Lubuntu or even an ultra-light non-Ubuntu linux distro, for example ToriOS, Puppy Linux or Tiny Core.

---

### Post by LastDino on 2015-06-09
I've used Ubuntu on P4 3.0 4gig RAM with on board graphics. I suspect that [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") is right and your RAM is being shared. Both your processor and the shared RAM issue will make Ubuntu lag, as it use to lag (only slightly) on even my slightly higher config. I suggest to follow suggestion given by **Mastblasta** and **Sudodus** and go with lighter version: Xubuntu. Xubuntu should work fine on such a config, it packs all the punches that Ubuntu does but with less eye candy. 

Note: If you tweaked it too much to have more eye candy, you will experience the lag again, so it might be in your best interest to keep the load minimum.

---

### Post by gsegovia15 on 2015-06-09
I will download xubuntu this afternoon when I get off of work. Should this just be a matte of burning image to dvd and rebooting from it to install xubuntu. Reason I'm asking is because I tried booting from live DVD with ubuntu 12.04 and o could never get it to work. Thanks to all.

---

### Post by LastDino on 2015-06-09
> **gsegovia15 said:**
> I will download xubuntu this afternoon when I get off of work. Should this just be a matte of burning image to dvd and rebooting from it to install xubuntu. Reason I'm asking is because I tried booting from live DVD with ubuntu 12.04 and o could never get it to work. Thanks to all.

It should be, just don't forget to check MD5 checksum to be sure. You can also make USB bootable from the ISO of Xubuntu. That's what I usually do. 

As you've managed to install Ubuntu 14.04, you shouldn't have any problems as it is basically same process. However,  you should read up few things on partitioning for Linux before you jump into it, it is important to know that beforehand than later finding out that default one is not something you want.

---

### Post by HermanAB on 2015-06-09
Yup, Lubuntu of Xubuntu will work.

---

