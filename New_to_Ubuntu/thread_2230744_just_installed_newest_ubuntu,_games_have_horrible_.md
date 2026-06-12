---
title: "just installed newest ubuntu, games have horrible fps"
date: 2014-06-20
forum: New to Ubuntu
---

### Post by deezdrama on 2014-06-20
After getting a virus from the kids being on my computer i reformated with the latest ubuntu.

ive tried linux before and really l8ke it except for the games it doesnt support and that they run slow.

i just noticed steam for linux and installed it and the game "rust" that i us3d to play since its supported on linux.

now my system is old but by no means as slow as how the game is running.

i have a gigabyte ep45 mobo modded to run a xeon quadcore running at 4.6ghz stable with low vcore
8gb ddr2
gtx 650ti

my video card isnt the best but on windows could run this game on max settings with good framerates.

on ubuntu i cant even get 10 fps on LOWEST  settings.


is this just the nature of gaming on linux or is there drivers i can install or something i can do?

Thanks

---

### Post by papibe on 2014-06-20
Hi deezdrama.

What games?

Did you install the Nvidia proprietary driver?

Regards.

---

### Post by deezdrama on 2014-06-20
Only game i have thats supported is rust...

i only installed newest ubuntu and checked the option to dl updates when installing so ... no ... i didnt install nvidia drivers.
is it just running video off a generic driver right now?

---

### Post by grahammechanical on 2014-06-20
When you installed did you tick the box "install third party software?" If so, then you are running on a proprietary video driver. You can check by going to System Settings>Software and Updates>Additional Drivers tab. Allow the utility a little bit of time and it will show you some video drivers and tell what one is activated.

Regards.

---

### Post by deezdrama on 2014-06-20
Yes i did click that tab.... should i not of?

---

### Post by papibe on 2014-06-20
> **deezdrama said:**
> Only game i have thats supported is rust...
Which is?

Most games lately have same or even better performance in Ubuntu than Windows. Unfortunately, there are a few that were not properly ported and run in sort of a 'API translation' environment. For instance [The Witcher 2]("http://www.phoronix.com/scan.php?page=news_item&px=MTY5ODM") is not on the top performance list.
> **deezdrama said:**
> is it just running video off a generic driver right now?
Probably.

Could you open a terminal, run this command, and paste back the result?
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by deezdrama on 2014-06-20
The game is called "rust"

i entered the above command at terminal and it gives me a bunch of options
.display modes,display options, etc

i dont see any specific video driver info

im a noob to linux... what am i looking for?

---

### Post by deezdrama on 2014-06-20
Ok... i forgot a "-"

it reads...

vga compatible controller 0300 gk106 geforce gtx 650 ti 10de:11cd rev a1
subsystem: microstar int. Msi device 1462:2808
kernel driver in use : nouveau

---

### Post by JeQhdMD on 2014-06-20
Just click on the system settings icon in launcher, click on software and updates, and then click "additional drivers", and let Ubuntu scan your system for avail drivers and install.   Then restart and recheck the game(s).  (you currently are running generic, lower performance driver).

---

### Post by coldcritter64 on 2014-06-20
> **deezdrama said:**
> ....
kernel driver in use : nouveau

They are the open source graphics drivers; for best graphics performance on games you should install and activate proprietary drivers for your card via the "Additional Drivers" utility (see grahammechanical's post, #4, for "Additional Drivers" comments).

edit: beaten to the post :)

---

### Post by deezdrama on 2014-06-21
Thanks guys! Will give it a try today

---

### Post by deezdrama on 2014-06-21
Thanks guys!

runs butter smooth on highest settings now!


its too bad most games on steam that i play are not linux supported.

i would like to play dayz

ive read about a program called wine that emulates windows.... is this possible?

---

### Post by Vladlenin5000 on 2014-06-21
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=29534](http://appdb.winehq.org/objectManager.php?sClass=version&iId=29534)

---

