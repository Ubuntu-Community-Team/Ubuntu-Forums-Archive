---
title: "Absolute noob to Ubuntu"
date: 2013-09-26
forum: New to Ubuntu
---

### Post by kmb9205 on 2013-09-26
Brand new to Ubuntu and having some trouble with software updating. I tried to put playonlinux on my system but it keeps failing to install. My internet connection is also pretty slow (wired to modem). I was wondering if anyone out there could point me in the right direction about seeing all the hardware the OS is seeing (device manager for lack of knowing the proper term). I have an older desktop (Dell Optiplex 745) which is the reason I thought I would try this. I have installed 12.04.3 alongside XP. All the partitioning went well and the system boots up as advertised. Any help would be greatly appreciated. ty

---

### Post by ibjsb4 on 2013-09-26
I too have an old Optiplex and even though its dual core/2G ram, I found Xubuntu to be a better choice for it because of the crappy on board graphics.  Xubuntu runs much faster.

[http://xubuntu.org/](http://xubuntu.org/)

---

### Post by mastablasta on 2013-09-26
i believe there are quite a few GUI tools in ubutnu that will provide oyu with systems specifications. if not there are more in software cneter.

you can also just use command to list hardware:
```
lshw
```

---

### Post by grahammechanical on 2013-09-26
You can run this command

```
sudo lshw -html > hardwareprofile.html
```

That will put a list of all your hardware detected by Linux into a file called hardwareprofile.html. It will be in the /home folder and if you click on it then the default web browser will open showing you the contents of the file.

Regards.

---

### Post by ibjsb4 on 2013-09-26
In case your wondering what in the hell these guys are talking about :)

You need to [open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (copy & paste) the code.

---

### Post by kmb9205 on 2013-09-26
thanks to all

---

### Post by mörgæs on 2013-09-26
If this solves your problem please mark the thread so (using Thread Tools).

---

### Post by oldos2er on 2013-09-26
If you prefer a GUI, try ```
sudo apt-get update && sudo apt-get install lshw-gtk && lshw-gtk
```

---

