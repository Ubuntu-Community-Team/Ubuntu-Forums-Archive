---
title: "i want make dual boot for ubentu"
date: 2012-08-11
forum: New to Ubuntu
---

### Post by speedman2202 on 2012-08-11
hiii

i am very interest to use Linux and learn command shell .... so i want make a dual boot for ubuntu and windows ....... cuz i am still beginner and my bro's not interest in Linux .... also i want install ubuntu in it's own partition also for windows cuz if anytime i want make a fresh copy of windows .......also  i want put a third OS like Puppy liinux to my pc .... can i add it to my boot list???


hope u help me understand and do this things with clear steps 


thx at advanced

---

### Post by drs305 on 2012-08-11
speedman2202,

Welcome to the Ubuntu forums! :-) 

The first thing to do is to make sure you have at least one available partition, preferably within an extended partition. Windows needs to be on a primary partition, but Ubuntu does not.

When making a partition for Ubuntu on a Windows system, we recommend you create the partition with Windows software - especially if you are going to have to shrink Windows. That provides the least risk of harming your Windows installation. Once you have an extra partition for Ubuntu, you can resize or move that partition with Linux software (gparted) with no problem.

Here is a link to a good explanation with illustrations on installing Ubuntu:

[_http://www.psychocats.net/ubuntu/installing_]("http://www.psychocats.net/ubuntu/installing")

---

### Post by speedman2202 on 2012-08-11
> **drs305 said:**
> speedman2202,

Welcome to the Ubuntu forums! :-) 

The first thing to do is to make sure you have at least one available partition, preferably within an extended partition. Windows needs to be on a primary partition, but Ubuntu does not.

When making a partition for Ubuntu on a Windows system, we recommend you create the partition with Windows software - especially if you are going to have to shrink Windows. That provides the least risk of harming your Windows installation. Once you have an extra partition for Ubuntu, you can resize or move that partition with Linux software (gparted) with no problem.

Here is a link to a good explanation with illustrations on installing Ubuntu:

[_http://www.psychocats.net/ubuntu/installing_]("http://www.psychocats.net/ubuntu/installing")


ty so much for quickly replay , i would like hit thx button to ur post if there a thanks button  ....... i have another question is what the recommend partition size for ubuntu partition? .... about 5 GB?? .... i am now download ubuntu cd (.ISO) .... is there way to setup it without burn it on cd???


thx anyway :)

---

### Post by gavv on 2012-08-11
Hi speedman2020 and welcome to the Ubuntu Forums, I am also new to Linux and just recently installed Ubuntu. Although I ran into a few difficulties, I was able to find an abundance of resources on-line to assist me. If you plan on installing Ubuntu from a CD, I recommend using [https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD). It is also advised that you have Windows installed first before installing Ubuntu.

---

### Post by mastablasta on 2012-08-12
> **speedman2202 said:**
> i have another question is what the recommend partition size for ubuntu partition? .... about 5 GB??
About 8GB seems to be quite good. but if you plan to add more programmes and also seriously work (i.e. have data and such then 20-25). also wih 8 GB you need to clean the old kernel after a while.
> 
 .... i am now download ubuntu cd (.ISO) .... is there way to setup it without burn it on cd???

you can use a (at least) 1 GB USB stick (use unetbootin or linuxliveusb to "burn" the image to it"

another option i think is virtual box but it's more complicated and not really that safe.
in fact if you have a strong enough maschine (enough CPU power and plenty  RAM)  you can simply use virtual box to give it a try (also live image).

---

