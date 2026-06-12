---
title: "graphics driver for my Intel HP G6laptop for ubuntu 13 10"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by dbranston4 on 2013-12-01
i have been researching graphic drivers for my ubuntu 1310 on my hp pavilion g6 with onboard intell hd family graphics card 

i have read a couple of instances where apprently you can use bumble bee but when i go to there site everything seems to be aimed at amd not intel so i am very confused as what to do any suggestions please 

ps i fould a couple of things that said you can go to intel to install theres but when i try to downlaod it through terminal its says there not found in the repositry 

HEEELLLPPP :)

---

### Post by fantab on 2013-12-01
Why?
Ubuntu comes with pre-loaded Intel Graphics drivers. You don' have to do anything extra, other than install Ubuntu.
Do you have [Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics")?
What issues do you have exactly with your Graphics?

---

### Post by deadflowr on 2013-12-01
> **dbranston4 said:**
> i have read a couple of instances where apprently you can use bumble bee but when i go to there site everything seems to be aimed at amd not intel so i am very confused as what to do any suggestions please 


Bumblebee is for nvidia optimus cards.
Has nothing to do with amd cards.

Like fantab stated, Ubuntu comes with graphics drivers for intel cards out of the box.
Perhaps newer versions could help, but that can be fraught with problems.
From intel
[https://01.org/linuxgraphics/](https://01.org/linuxgraphics/)

And from the xorg-edgers
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

But I would recommend staying with what is there already.
Unless the system is completely unusable.

It is up to you if you feel the risk of utter breakage will be better than the state it is in now.
And chances are the drivers  provided in either link won't give you much better results then what you have now.

Choice is your though.

---

### Post by dbranston4 on 2013-12-02
i sometimes go on secondlife i recently installed it on my comp downstairs and had to install drivers mind you it did have a gt 430 card in it nvidia i will download second life and see how it goeas with the drivers pre istalled

---

### Post by deadflowr on 2013-12-02
> **dbranston4 said:**
> i sometimes go on secondlife i recently installed it on my comp downstairs and had to install drivers mind you it did have a gt 430 card in it nvidia i will download second life and see how it goeas with the drivers pre istalled


If you have an nvidia card, then you can install alternative drivers for it.
Where as intel only provides open-source drivers, nvidia cards can run either open-source or nvidia closed-source drivers.

If in 13.10 open the program software and updates and go to the tab marked additional drivers.
It will run a quick scan of the setup and should open a window with a list of drivers.
Normally the best is one either marked recommended or tested.
Select the card you want and then click activate.
Normally after it installs you need restart the machine.

In case of any problems look over this
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by dbranston4 on 2013-12-02
[FONT=arial]Update on things so far now i believe that intel was supposed to install generic drivers assigned to intel family of inbuilt graphic cards this for some reason didnt happen 
after doing the command sudo lshw 
which clarified it so i did the 

[/FONT][FONT=arial] sudo apt-get install mesa-utils

this then installed what i currently hve on my system which is this :-
Graphics Card: Mesa DRI Intel(R) Sandybridge Mobile x86/MMX/SSE2
 
 OpenGL Version: 1.4 (3.0 Mesa 9.2.1)
so i believe that is the best i can get on my system as it is a intergrated card 
am i correct gents and ladies if there are any in here [/FONT]

---

### Post by deadflowr on 2013-12-02
The intel drivers are part of the xorg packages that come with the system.
Nvidia and Ati cards(as well as several lesser named gpu brands) also have packages within the xorg packages.
Nvidia has what is known as the nouveau driver, and ati has the radeon driver.

The lshw command would show the intel card's driver simply as intel.
The mesa-utils package simply reads and outputs more verbose info on the drivers in use.
It has nothing to do with the driver though.
The driver is in xserver-xorg-video-intel.

---

### Post by dbranston4 on 2013-12-02
> **deadflowr said:**
> The intel drivers are part of the xorg packages that come with the system.
Nvidia and Ati cards(as well as several lesser named gpu brands) also have packages within the xorg packages.
Nvidia has what is known as the nouveau driver, and ati has the radeon driver.

The lshw command would show the intel card's driver simply as intel.
The mesa-utils package simply reads and outputs more verbose info on the drivers in use.
It has nothing to do with the driver though.
The driver is in xserver-xorg-video-intel.
ok i found it guess it is already there tried running it through synaptic

---

