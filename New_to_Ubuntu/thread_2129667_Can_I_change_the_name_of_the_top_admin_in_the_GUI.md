---
title: "Can I change the name of the top admin in the GUI"
date: 2013-03-26
forum: New to Ubuntu
---

### Post by MickeyPilgrim on 2013-03-26
I made an error with the set-up; your name, computer name... Can it be changed without getting into the terminal?

---

### Post by Kopkins on 2013-03-26
You should be able to change your name without terminal use, you should be able to go to settings > user accounts and then should be able to unlock and click your name to change. At least in the recent releases of Ubuntu. Which flavor and version are you using? Kubuntu, lubuntu, Ubuntu? 12.04, 12.10?

For the hostname you'll have to go into the terminal.
You should edit two files, but you can do this through the GUI. You can open a terminal and type ```
gksudo gedit /etc/hosts
```
and change the computer name to what you want. Then; ```
gksudo gedit /etc/hostname
``` and change it there too.

Then you'll probably have to reboot.

If someone could confirm this that would be great, I don't have ubuntu running right now, I installed arch over my 12.04 and don't have ubuntu in a VM yet, so I'm going from memory.

---

