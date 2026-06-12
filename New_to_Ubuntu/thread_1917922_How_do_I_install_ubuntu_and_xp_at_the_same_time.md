---
title: "How do I install ubuntu and xp at the same time"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by SAIYANPRINCE on 2012-01-30
Hi, i currently have windows xp installed on my pc and i want to download and install ubuntu. But i want to know if its possible to install ubuntu without removing xp. If it is possible then how can i do this? Also will extra ram be used if both are installed, or will it not do anything if only one is open? (my pc only has 504 mb ram, yeah i know its rubbish lol but when i get some money i am going to buy a new pc but as for now I will have to put up with this.) Or will I have to uninstall xp to get the ful power of ubuntu?

Really keen to install ubuntu, if it was my own pc i would have installed it but its shared to i gotta install it WITH xp. sorry for all the questions but yeah any help would be appreciated ty

---

### Post by bluexrider on 2012-01-30
This should cover your questions [HERE]("https://help.ubuntu.com/community/WindowsDualBoot")

Pretty simple really

---

### Post by carl4926 on 2012-01-31
You can install Linux but 512mb RAM is not much and Ubuntu will not work properly. I suggest you use Lubuntu.

[http://lubuntu.net/](http://lubuntu.net/)

Or even lighter:
[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

If you burn one of those to a CD and boot from it. You can try it without installing. When in the Live desktop, open a terminal and post here for us the result of

```
sudo fdisk -l
```

---

### Post by Bucky Ball on 2012-01-31
Yes, you can. Just make sure you have enough free disk space next to the Windows partition and any other partitions you want to keep.   

RAM irrelevant as only one running at a time (they have nothing to do with one another apart from sharing the same disk). You will have the full power of either to the limit of your hardware's abilities. 

I would advise release 10.04 LTS for a starter as it is solid, stable, and has been around awhile.   All depending on how experienced you are, you can let Ubuntu do the partitioning or do it manually (which I normally do for safety). I would backup valuable data first.  

Download the 10.04 LTS desktop ISO, burn a CD, boot from that and you're away. You will get to the partitioning section of the install. If you choose to 'Do something else' you can partition yourself. You will see the NTFS Win partition in there, just don't touch it. Advisable and default selections in there are: 

/ - this is where Ubuntu goes and 20Gb is plenty;
 /home - where your personal data goes and can be as big as you like but you can use existing partitions, too;
 /swap - swap partition and 2Gb enough.

... and as mentioned above in post #3, Lubuntu or Xubuntu would be fine. I love Xubuntu personally. ;)

---

### Post by mastablasta on 2012-01-31
you need to defragment the dfisk first before creating partitions. installing it next to XP is easy. 
 
defragment partition (2x times-second time will be much faster), run check disk (chkdsk), then use windows disk manager to create an empty disk partition (do not format it). then when you boot ubuntu liveCD/live USB you can just use defaults and select to install next to XP. works just fine. you need to create partition of size 20-30 GB. though it works on much less you might need to reserve some space for user files and any new programmes instalations.
 
don't worry about creating linux partitions. they will be done automaticly if you do not specify them.
 
oh and for an older mashcine 10.04 LTS version (supported until 2013) is more friendly (as it uses less ram and works well on no hardware graphics acceleration) or you can also use the latest version but instead use Xubuntu or Lubuntu which are lighter on system resources as they both run on less than 256 MB RAM. 
 
depending on your CPU, graphics card and processor - and if you increase ram to at least 1 GB (or 1.5 :-)) you can try Kubuntu and Ubuntu.
 
Remember, winXP is from 2001, Ubuntu is modern OS from 2011. ;-)
 
good luck and let us know how it went.

---

