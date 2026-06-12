---
title: "Old Laptop HP compac presario m2000 cannot find linux distro that will load"
date: 2016-11-02
forum: New to Ubuntu
---

### Post by solo2 on 2016-11-02
Hi UF Group,
I have an old laptop HP Compac Presario m2000 m2001EA
It works perfectly well, long battery life, installed a new keyboard in it a couple of months ago and just got around to looking for a Linux Distro to put on it, 
I has Windows XP on it at present but I would like to run Linux on it and let my Grand Daughter have it as a first real computer.
A couple of error messages have come up when trying Ubuntu 14.04 ( am on Ubuntu myself , just getting to grips with it), emmabuntus (which was recommended for older machines)and Trisquel 7, but no joy.

1, PAE is disabled on this Pentium M

2, Use parameter "forcepae" to enable at your own risk!

3, Unable to boot - Please use a kernel appropriate for your cpu

As a Linux newbie, could / would any of you knowledgeable fellows point me in the direction of a suitable linux Os for this laptop 
It has a Celeron (R) M 1.3Ghz processor and 768mb Ram.

Thanking you in anticipation...

Regards

Solo

---

### Post by ajgreeny on 2016-11-02
Have a look at Bodhi Linux which is based on Ubuntu but has lower (much lower) requirements than even Lubuntu.
[http://www.bodhilinux.com/w/system-requirements/](http://www.bodhilinux.com/w/system-requirements/)

---

### Post by solo2 on 2016-11-02
Thank you, ajgreeny, I'll give it a go.... not this evening though am on 6-2.....
Regards
Solo

---

### Post by mastablasta on 2016-11-03
the answers are Lubuntu (maybe even older 14.04 LTS) with forcepae switch:

[URL="https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M"][SIZE=2]https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Pentium_M_and_Celeron_M
[/SIZE][/URL][SIZE=2][/SIZE]more info on PAE with screenshots: [URL="https://help.ubuntu.com/community/PAE"][SIZE=2]https://help.ubuntu.com/community/PAE
[/SIZE][/URL][SIZE=2][/SIZE]
using One Button Installer:
[URL="https://help.ubuntu.com/community/OBI"][SIZE=2]https://help.ubuntu.com/community/OBI
[/SIZE][/URL]

another option is LXLE: [SIZE=2]http://www.lxle.net/

as long as you get arround the PAE limitation....

other easy to use distros with a light interface that use fewer resources:
ToriOS
AntiX
Bunsenlabs (formerly knwon as Chrunchbang )

really low resoruce usage:
Puppy Linux

[/SIZE]Slitaz
TinyCore

you can also go and use ubuntu mini.iso (netinstall) and add just a windows manager.

---

### Post by mörgæs on 2016-11-03
Forcepae works also for Lubuntu 16.04.1 and 16.10.

The only limitation I see here is the granddaughter's expectations. The computer will be fine for Libreoffice but for streaming videos and browsing heavy web pages she might get disappointed.

---

### Post by solo2 on 2016-11-05
Thank you mastablasta, for your information, I'll look into the "force PAE" as I think it means installing through command line and I've not done that before.....it seems this may be the key to me being able to chose a lite distro.

Regards
Solo2

---

### Post by solo2 on 2016-11-05
Thank you for taking the time to post an answer for me.....
Would you perhaps know how I would forcepae in an install ?
Regards

Solo2

---

### Post by gordintoronto on 2016-11-05
How much memory in this slow 11-year-old computer? 

Depending on where you live, and your financial situation, it might be a lot more productive to find a 6-year-old off-lease laptop costing around $150. Easy in a big city, more difficult in a small town. I easily found a quad-core laptop with 4 GB of memory and 200 GB hard drive, which would run Xubuntu or Ubuntu Mate really well.

---

### Post by mörgæs on 2016-11-06
> **solo2 said:**
> 
Would you perhaps know how I would forcepae in an install ?


Yes, and Mastablasta knows, too. He gave you a selection of links.

---

### Post by solo2 on 2016-11-15
[**[COLOR=#DD4814][B]**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=939075")Thanks to [URL="https://ubuntuforums.org/member.php?u=939075"]**[COLOR=#DD4814][B]mörgæs **[/COLOR]and [COLOR=#000000]mastablasta

[/COLOR][/B][U][COLOR=#000000]Problem solved thank you gents all is well with the old machine I used the "force pae -- force pae" after pressing f6 in the options screen
I had to press f6 at the startup/prior to the first bootup screen the OS I have used is ubuntu mate 12.04
sorry I took so long to reply and thank you, been the unfortuate receiver of a ...shall I state "challenging rota"
regards
solo2[/COLOR][/U][B][COLOR=#000000]
[/COLOR][/B][/URL]

---

### Post by mörgæs on 2016-11-15
Good that you managed to install but 12.04 is out of support. Better to install a recent release.

---

### Post by kurt18947 on 2016-11-15
> **mörgæs said:**
> Forcepae works also for Lubuntu 16.04.1 and 16.10.

The only limitation I see here is the granddaughter's expectations. The computer will be fine for Libreoffice but for streaming videos and browsing heavy web pages she might get disappointed.

This is a good point. Playing Flash content can pose quite a challenge to older machines for example. I've bought 4 Thinkpads (sold one) off Ebay as ex-Corporate off lease machines. So far so good, just read the posting carefully to be clear what's included and what's not. Hard drives are frequently not included for example. I would have second thoughts about buying a 4+ year old consumer grade machine. Business class machines are generally built with higher quality components that may have quite a bit of useful life left in them when they are retired as part of a hardware refresh.

---

