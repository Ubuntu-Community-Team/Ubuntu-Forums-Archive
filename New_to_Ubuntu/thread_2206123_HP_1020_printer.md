---
title: "HP 1020 printer"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by Pieter_Meester on 2014-02-17
Have installed Lubuntu 12.04, 32 bits on my Compaq Presario V4000. Very fast now, but the printer HP1020 refuses. The system detects the printer nicely, but uses software for HP 1022.
Have been trying for days now and my enthousiasm has demished dramatically. What can I do?
Thanks for any help
Pieter

[ATTACH]250418

---

### Post by Vladlenin5000 on 2014-02-17
HP Laserjet 1020 is supported by the HPLIP package: [http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_1020.html)
Just installing HPLIP from the Lubuntu Software Center and following the instruction should be enough.

---

### Post by mörgæs on 2014-02-17
Hi, welcome to the fora.
12.04 is out of support, so a good beginning is installing 13.10. After that HP's are usually easy to set up.

---

### Post by howefield on 2014-02-17
> **mörgæs said:**
> 12.04 is out of support, so a good beginning is installing 13.10. 

Support for ?

---

### Post by oldfred on 2014-02-17
I missed it to. Lubuntu
All these different dates for different versions confuse me. :(

I almost always suggest repository, but the hplip was old in my 12.04 Ubuntu, so I installed the version directly from HP. 

This was for my HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup

# new version
hp-upgrade

---

### Post by deadflowr on 2014-02-17
> **howefield said:**
> Support for ?

Lubuntu 12.04 is eol.

Edit: Op, read oldfred's advice.

---

### Post by howefield on 2014-02-17
> **deadflowr said:**
> Lubuntu 12.04 is eol.

Thanks, missed it was Lubuntu :)

---

### Post by kestrel1 on 2014-02-17
> **oldfred said:**
> I missed it to. Lubuntu
All these different dates for different versions confuse me. :(

I almost always suggest repository, but the hplip was old in my 12.04 Ubuntu, so I installed the version directly from HP. 

This was for my HP Deskjet 3520
[http://ubuntuforums.org/showthread.php?t=2109050](http://ubuntuforums.org/showthread.php?t=2109050)
HP's newest On this website you can download the HPLIP software which supports 2,211 HP printers on nearly any Linux distribution available today.
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)
Ubuntu's older version
sudo apt-get install hplip-gui
gksudo hp-setup

# new version
hp-upgrade

Why do the dates/versions confuse you?
12.04 is April 2012
13.10 is October 2013
Basically it is the year & then the month as a number.
What confuses me is the names for the different versions :lolflag:

---

### Post by deadflowr on 2014-02-17
> **kestrel1 said:**
> Why do the dates/versions confuse you?
12.04 is April 2012
13.10 is October 2013
Basically it is the year & then the month as a number.
What confuses me is the names for the different versions :lolflag:

It's not the dates of release that are confusing, but the support length for the difference flavors.
I think lubuntu 12.04 was only 18 months, or two years or something where as Ubuntu 12.04(I'll call it normal/unity) is 5 years and xubuntu 12.04 is something like 3 years.
That differential can be quite confusing.

---

### Post by kestrel1 on 2014-02-17
I get what you mean now mate. That does seem a bit strange, but these distros are not supported by the same people. That is the only thing I can think of.
Anyway, sorry to disturb the original posters question.
In my experience HP printers just work under Linux.  Used to use a networked 1022 and it installed and worked fine.

---

### Post by Pieter_Meester on 2014-02-18
Thank you so much Vladlenin. It went differently from what you adviced. The procedure got stuck by not finding some DNS data, but then I got in the Lubuntu software centre a hplip app from HP directly and that worked out perectly after of course some trial and error. But you got me on the road again! Thanks

And now, Morgaes 13.10: how to? Din't find it in the Lub softw. centre
Pieter

---

### Post by mörgæs on 2014-02-18
You can download it from the drop-down menu above.

---

### Post by Pieter_Meester on 2014-02-18
Thanks for fast response Morgaes, but stupid enough I don't find a ' drop-down menu above' Not under either.
Sorry to bother you
Pieter

---

### Post by deadflowr on 2014-02-18
> **Pieter_Meester said:**
> Thanks for fast response Morgaes, but stupid enough I don't find a ' drop-down menu above' Not under either.
Sorry to bother you
Pieter

I think morgaes means the drop down on this forums page.
(or any forums page on this website)
If you look at the top of the page you will see a line with several options 
Quick Links Forum Community Ubuntu Community etc,etc.
click on the one for Ubuntu Community and a drop down will appear.
Select the one for  "Get Lubuntu"
and you will be re directed directly to lubuntu's web site, where you can get the latest release.

Hope that helps.

---

