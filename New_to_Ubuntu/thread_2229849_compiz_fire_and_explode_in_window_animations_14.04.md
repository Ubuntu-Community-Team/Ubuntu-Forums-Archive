---
title: "compiz fire and explode in window animations 14.04"
date: 2014-06-15
forum: New to Ubuntu
---

### Post by misswham2 on 2014-06-15
Hi forum, I just installed Ubuntu 14.04 and in compiz under the animations I dont see fire and explode anymore.  I came from 12.04.  How can I get it?  Those 2 animations are my favorite, the others are just BLAH!  HAHAHA  Thanks for your help in advance.

---

### Post by philinux on 2014-06-15
Look in software center for compiz plugins extra iirc.

---

### Post by misswham2 on 2014-06-15
I copied and pasted what u typed and it says no results found.

---

### Post by Vladlenin5000 on 2014-06-15
*Subscribed*

---

### Post by grahammechanical on 2014-06-15
Just type compiz-plugins in the search panel of the software centre.

---

### Post by WogBoy on 2014-06-15
Would something like this help?


sudo apt-get install compizconfig-settings-manager compiz-plugins-extra

---

### Post by misswham2 on 2014-06-15
this is what came up after i put the code in

~$ sudo apt-get install compizconfig-settings-manager compiz-plugins-extra 
[sudo] password for aretha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz-plugins-extra is already the newest version.
compizconfig-settings-manager is already the newest version.
The following packages were automatically installed and are no longer required:
  kde-l10n-engb linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

---

### Post by philinux on 2014-06-17
Looks like the extra package has been deleted. The one in the repo is just a dummy.

You'll have to try and find a ppa etc.

---

### Post by philinux on 2014-06-17
Looks like the extra package has been deleted. The one in the repo is just a dummy.

You'll have to try and find a ppa etc.

---

### Post by egeezer on 2014-06-17
Another way: stock Ubuntu doesn't include Synaptic Package Manager, so in a terminal type:

sudo apt-get install synaptic

Open Synaptic, and in the search box type: compiz.  You will see a long list of all the available Compiz packages and notation of which are and are not installed.  You can install the ones you want from there.

---

### Post by monkeybrain20122 on 2014-06-17
paint fire is in compiz-plugins but not explode.

---

### Post by grumblebum2 on 2014-06-17
You won't find some of the old animations and plugins in the repos.
No-one is updating them to work with the the latest compiz.
The compiz-plugins package contains some of the old plugins but they aren't officially supported.
Does not contain fire or explode window animations.

---

### Post by misswham2 on 2014-06-22
I have introduced linux to 18 people by installing it on their computers and ALL of them were attracted to linux because of my desktop having fire and exploding windows including the same in cairo dock.  I had 12.04 for 2 yrs and I loved it but the only reason I updated to 14.04 is because it was a LTS and 14.04 recognized my android phone where 12.04 didn't.

---

### Post by moster on 2014-06-23
I was searching same some time before. I cannot believe only few ppl care about such cool animations. There is no way to make that work...

---

### Post by misswham2 on 2014-06-26
Well Im sure that more people like the fire and other animations because thats why I went back to 12.04 from 12.10 but I dont know why it wont be carried over.  Those animations are what really make the visual part of Linux stand out from others.

---

### Post by mgt2000 on 2014-10-13
That was also how I introduced Linux to several friends but it seems that it is gone now!!!

---

### Post by nerdtron on 2014-10-13
Lot's of animations are lost on newer version of Ubuntu. One that I miss is the "snow" animation on the KDE desktop. I really liked that eye candy. Still hoping to see it.

I don't think fire, explode and snow will comeback anytime soon. :(

---

