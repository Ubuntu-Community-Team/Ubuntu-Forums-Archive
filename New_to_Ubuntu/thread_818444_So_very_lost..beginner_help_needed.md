---
title: "So very lost..beginner help needed"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by calicat on 2008-06-04
I installed Ubuntu yesterday (and did it way wrong so I lost everything I had previously) so today I thought, Oh well, I'll just start all over again.  And now I'm overwhelmed.  I have the basics down (email, messaging, internet...) but I can't seem to do any of the extras.  I searched for some answers and one suggestion was to run compiz-check, I did that and it wouldn't do a scan for me, it came up that two graphic cards were found and aborted.  I haven't been able to find where you would look to see your hardware installed to see what it means as I'm pretty 100% positive that I don't have two.  I haven't been able to figure out how to add any of the "eye candy" stuff and I can't seem to figure out how to use the terminal.

I've been reading documentation for hours now and am just so lost.  Any helpful suggestions, insight or tips?  

Btw, my computer seems to be running so much faster then it did yesterday before I installed this software, thats a HUGE plus! :)

---

### Post by drs305 on 2008-06-04
> **calicat said:**
> I haven't been able to find where you would look to see your hardware installed to see what it means as I'm pretty 100% positive that I don't have two.  

The * Search* function of this forum is your friend. For hardware found on your machine, here is a command that will put an html file on your desktop:
```
sudo lshw -html > ~/Desktop/hardware.html
```
sudo will ask for your password. You won't see it as you type but it is there. Hit enter once you have entered it.

Here are some good links for newbies:

How to install ANYTHING in Ubuntu!:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Ubuntu Guide: Hardy
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Root Sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by wolfen69 on 2008-06-04
what extras do you want to install? please be specific as to what you want.

---

### Post by calicat on 2008-06-04
The problems started when I tried to install a sidebar screenlet...I had seen Ubuntu on a friends computer and thats why I decided to get it, they recommended it.  There computer looked neat with sidebars and cubes.  That was the effect I was trying to go for.  I like to have everything right there on the desktop for quick access.  I ran a hardware check earlier today but it showed everything working fine...

---

### Post by Tom Mann on 2008-06-04
Hi Calicat,

I can help with the eye candy - if you click on the system menu at the top left of the screen, select preferences, then appearance a dialog will come up. Select the visual effects tab and you will have some basic options for switching on compiz fusion.

If you want to change settings, open a terminal (Accessories > Terminal) and type

sudo apt-get install simple-ccsm (you will be asked for your password)
and somewhere in system > preferences you will have an 'advanced desktop effects settings' item and a 'simple compizconfig settings manager' item. Both will let you tweak in different ways. Enjoy!

---

### Post by calicat on 2008-06-04
> **drs305 said:**
> The * Search* function of this forum is your friend. For hardware found on your machine, here is a command that will put an html file on your desktop:
```
sudo lshw -html > ~/Desktop/hardware.html
```
sudo will ask for your password. You won't see it as you type but it is there. Hit enter once you have entered it.

Here are some good links for newbies:

How to install ANYTHING in Ubuntu!:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Ubuntu Guide: Hardy
[http://ubuntuguide.org/wiki/Ubuntu:Hardy](http://ubuntuguide.org/wiki/Ubuntu:Hardy)

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Root Sudo:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Thanks for the links, Ill go check em' out

---

### Post by AOZ on 2008-06-04
if you want to manage your desktop effects the simplest way is to go System->preferences>appearance goto visual effects and select extra. but if your really want to play around in another easy way is to go applications->add remove programs and search for Advanced Desktop Effects Settings. that will give you an option under System->preferences> to manage all the cool add-ons you can think of

---

