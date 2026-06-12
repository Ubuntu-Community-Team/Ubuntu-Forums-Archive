---
title: "desktop not loading on boot up"
date: 2013-12-01
forum: New to Ubuntu
---

### Post by desberwado2 on 2013-12-01
Hello, 

can anyone please give me some advice.
I have an old Pentium 4 2660MHz
Cache 512k
RAM 512M
Chipset intel i848 FSB 133MHz
I use it for office work and researching on the net. It has been running winxp.
I decided to take the plunge and go for ubuntu 13.10.
It loaded and looks normal up to the point where I enter my password
After that, the background loads but no desltop functions. I can get files to open but cant close them as each window doesn't have the top bar.
None of the desktop functions are visible either. 
I have re installed but no change.

Can anyone please offer me some advice

Many thanks in anticipation

---

### Post by westie457 on 2013-12-01
Welcome to the Forum.

Open a terminal by pressing Ctrl+Alt+T at the same time.

Type in and run these commands```
sudo apt-get update

sudo apt-get upgrade

sudo reboot
```
You will be asked for your password, nothing will show on the screen as you type it.

This should fix your issue.

Now to go off topic.... With only 512MB of RAM the system will run slowly.

Either get more memory or consider a lighter distro: Xubuntu or Lubuntu are very light on system resources.

---

### Post by desberwado2 on 2013-12-01
westie457 thank you very much for your quick reply.
I have gone through the code you suggested but it hasn't worked. It is booting up just as it did.

Is there anything else I could try?

Many thanks in anticipation

---

### Post by westie457 on 2013-12-01
Just in case there is something that did not install properly the first time try this.```
sudo apt-get install -f

sudo reboot
```
If still the same try ```
sudo dpkg --configure -a

sudo reboot
```

If still not sorted after that we will be getting into areas that I know very little about, not that I know much in the first place.

It might be a Graphics card issue.
After you have tried the above could you post the output of ```
lshw -C display
```

Thank you

---

### Post by desberwado2 on 2013-12-03
Hello Westie457,  thank you for your advice. I have tried all that you suggested to no avail. I have now also upgraded the RAM. I did get the PC running lubuntu which was fine.
The output from the last suggestion:
description:VGA compatible controller
product: 82865G Integrated graphics controller
vendor: Intel corporation
physical id: 2
width: 32 bits
clock: 33MHz
capabilities:vga_controller bus_master cap_list rom
configuration: driver=915 latency=0
resources: irq:16 memory f0000000-f7ffffff memory:fc40000-fc47ffff ioport:14eo(size=8)

Hope this provides an answer?

Thanks again for your time and knowledge

---

### Post by westie457 on 2013-12-03
Did your screen originally look similar to this?  See attached picture.

---

### Post by desberwado2 on 2013-12-03
Hi westie457, 

no is the answer. I get to the password stage of bootup. The top bar loads, clock, language and wifi icons show. As soon as I enter my pwd it all dissapears and I'm left with a blank background. I can access the control panel by right clicking and taking the option change the background. but ant window I open can't be closed as the top bar doesn't load with it.

??

---

### Post by jimmyh1972 on 2013-12-03
You can install another Desktop enviorment...

open terminal (ctrl + alt +t)
sudo apt-get install gnome-desktop
or...
sudo apt-get install cinnamon
at the next log-in choose another desktop than unity (click the icon near the password box).
BUT - it looks like you are "squeezing" the latest Ubuntu sys (which is quite heavy)  on a very old hardware, might get very poor preformance

---

### Post by mörgæs on 2013-12-05
Agree on the latest post.
Lubuntu 13.10 (with the Intel modification as mentioned in my signature) is a better choice than Ubuntu.

---

### Post by desberwado2 on 2013-12-06
Thank you all very much for your advice. 

It's the weekend - guess what I'll be doing :-)

Many thanks again

---

### Post by Danny_Olson on 2013-12-10
I have been following this thread because I have the same issues. great desktop picture with only the right click change desktop background like where I can get to ubuntu one (and this fourm)  other than that I only have one untitled folder icon.  I have tried all the suggestions listed and dont know how to rebuild this dual boot machine without damaging my windows partition.  It seems to be functional but no menu system and it cant find the gnome-desktop listed above. cinimon fails outright, so how to I reinstall without damaging the rest of my partitions?

1GB Memory
Intel® Celeron(R) CPU 2.60GHz 
20GB HD
Gateway E2100 Standard
19inch monitor

---

### Post by mörgæs on 2013-12-10
Please begin with a complete hardware description.

---

