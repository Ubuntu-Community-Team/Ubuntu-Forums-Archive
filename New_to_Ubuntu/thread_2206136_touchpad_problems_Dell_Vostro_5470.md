---
title: "touchpad problems Dell Vostro 5470"
date: 2014-02-17
forum: New to Ubuntu
---

### Post by 3uchl0 on 2014-02-17
[COLOR=#333333][FONT=Verdana][COLOR=#000000][FONT=Lucida Grande]Hi,
I have recently installed xubuntu 13.10 on my laptop Dell Vostro 5470 and my touch-pad right button is not working at all. Other functions work properly.
When I log in to windows 7 everything works fine.

The touch-pad is listed in the xinput command output as ETPS/2 Elantech Touchpad. I have performed xinput test and there was no response to the right button at all.

Please help. Thank you. 


Intel® Core™ i5-4200U processor (3M Cache, up to 2.6 GHz)
4GB Single Channel DDR3L 1600MHz (4GBx1)
500GB 5400 rpm SATA Hard Drive
NVIDIA® GeForce® GT 740M 2GB DDR3
[/FONT][/COLOR]
[/FONT][/COLOR]

[RIGHT][COLOR=#333333][FONT=Verdana][/FONT][/COLOR][/RIGHT]

---

### Post by sammiev on 2014-02-17
Hi and welcome to the forums. :)

Easy try this.

---

### Post by sandyd on 2014-02-17
**moved to absolute beginners section**

---

### Post by 3uchl0 on 2014-02-17
That's not the issue, touch-pad is enabled, left button and movement works perfectly fine. The right button is not recognized. Switching it on/off does not help.

---

### Post by sammiev on 2014-02-17
> **3uchl0 said:**
> That's not the issue, touch-pad is enabled, left button and movement works perfectly fine. The right button is not recognized. Switching it on/off does not help.

Do you have another OS installed like Windows? Does it work with any other OS?

---

### Post by Vladlenin5000 on 2014-02-17
> **sammiev said:**
> Do you have another OS installed like Windows? Does it work with any other OS?

This isn't one of your days, is it? Twice you missed vital information in th OP like this one: *[COLOR=#333333][FONT=Verdana][COLOR=#000000][FONT=Lucida Grande] When I log in to windows 7 everything works fine.[/FONT][/COLOR][/FONT][/COLOR]*

---

### Post by sammiev on 2014-02-17
You want to read this [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1188025"), it sounds like the same problem.

---

### Post by 3uchl0 on 2014-02-18
Yes I've red the report before, you are right it is the same problem but still I don't see any solution.
Please anyone else can you help me?

---

### Post by 3uchl0 on 2014-02-19
problem solved, seems that linux mint forum people are better :p

[http://forums.linuxmint.com/viewtopic.php?f=49&t=157436&p=825476#p825476](http://forums.linuxmint.com/viewtopic.php?f=49&t=157436&p=825476#p825476)

thank you anyway

---

### Post by simormate on 2014-07-09
Here is the solution, based on the linux mint forum:

Step 1
```
cd ~ && wget [url]http://people.canonical.com/~acelan/bugs/lp1188025/mouse.tgz
```

Step 2
```
sudo gedit /etc/rc.local
```

Step 3
Before "exit 0", add:
```
cd /home/your--------user---name/mouse && make && sudo cp psmouse.ko /lib/modules/`uname -r`/kernel/drivers/input/mouse/psmouse.ko && sudo rmmod psmouse && sudo modprobe psmouse
```

Step 4
Restart the system

---

