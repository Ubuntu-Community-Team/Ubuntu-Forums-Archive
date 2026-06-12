---
title: "drivers for geforce gt 630m?"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by DragonGirl123 on 2013-05-09
Does anyone know how i get drivers for geforce gt 630m i cant seem to find them. Also does my intel integreated graphics card need drivers too?

---

### Post by papibe on 2013-05-09
Hi DragonGirl123.

Do you have a laptop or a desktop?

Could you open a terminal, run this command, and post its result?
```
lspci -nnk | grep -iA2 eth
```
Regards.

---

### Post by DragonGirl123 on 2013-05-09
[http://postimg.org/image/jqihkd4rh/](http://postimg.org/image/jqihkd4rh/) here is the picture that i took of the result. I got some display options etc

---

### Post by papibe on 2013-05-09
That doesn't seem to the output of the command.

Could you try again?

To make it easier, you can paste it from the browser into the terminal.

Regards.

---

### Post by DragonGirl123 on 2013-05-10
ok i copied and pasted to the the terminal.I Dont know if this matters ,but im using LXTerminal from Lubuntu. Here is the result [http://postimg.org/image/oc8gic169/](http://postimg.org/image/oc8gic169/). Sorry for the long time that it took to reply just i made this thread when it was over midnight so i fell asleep behind my laptop.

---

### Post by pqwoerituytrueiwoq on 2013-05-10
you can highlight then then middle click (mouse wheel/top right corner of mousepad or left+right click at same time) to paste it
first found that out using dsl (dam small linux)

not sure why papibe asked for info on your nic when you asked about your gpu driver, this will get the graphics chip info
```
lspci -nnk | grep -iA2 VGA
```
if you have nvidia optimums you need to look at the bumblebee project otherwise look in software sources in the last tab

---

### Post by DragonGirl123 on 2013-05-10
yes i do have nvidia optimus.Here is the thing i got from terminal [http://postimg.org/image/qfx0rwbqb/](http://postimg.org/image/qfx0rwbqb/). What should i do?

---

### Post by 3rdalbum on 2013-05-10
Go into Ubuntu Software Center and go to Edit menu > Software Sources.

The last tab in the new window that opens up, is the place where the driver options appear. You can install the driver there.

Note, this is just for the Nvidia GPU.

---

### Post by DragonGirl123 on 2013-05-10
i did what you said 3rdalbum ,but it only shows my wifi card. Im installing bumblebee right now.I finished installing bumblebee and rebooted my computer ,is there any way of checking if now everything works fine?

---

### Post by DragonGirl123 on 2013-05-10
Also one thing is that in monitor settings i have 1024x768. Instead of 1366x768. And i cant change to any other resolution.

---

### Post by pqwoerituytrueiwoq on 2013-05-10
since you have nvidia optimus
[https://wiki.ubuntu.com/Bumblebee#Installation](https://wiki.ubuntu.com/Bumblebee#Installation)

be sure to purge the nvidia driver
```
sudo apt-get purge nvidia*;sudo rm /etx/X11/xorg.conf
```

---

### Post by DragonGirl123 on 2013-05-10
did what you said. Also before you only had [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get purge nvidia* Should i do the other thing too? [/FONT][/COLOR]

---

### Post by DragonGirl123 on 2013-05-10
I did everything you said ,is there any way of checking if it works? Also my resolution is still only 1024x768 and i cant change that.Any help with that?

---

### Post by papibe on 2013-05-10
> **pqwoerituytrueiwoq said:**
> not sure why papibe asked for info on your nic
Oopsy :oops: my mistake. Thanks pqwoerituytrueiwoq :D

---

### Post by pqwoerituytrueiwoq on 2013-05-10
did you reboot after running that command and installing bumblebee?
i am not very familiar with that project, as i have never used it

---

