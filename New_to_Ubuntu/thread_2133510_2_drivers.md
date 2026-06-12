---
title: "2 drivers"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by hbaus on 2013-04-08
Hello i am completely new to ubuntu. thats why i posting here.I have installed ubuntu along side windows so that I have internet on windows. I have the Graphics drivers for my gt 640 on a disc but i need to know how to install it, secondly  i need to know how to install the drivers for my internet card (it is a PCIE card).Detail is very important please help.

---

### Post by Mark Phelps on 2013-04-08
Basically, you can't install Windows drivers in Linux; you need Linux drivers.

---

### Post by Bashing-om on 2013-04-08
hbaus;

Different operating system (ubuntu) -> different concepts. In ubuntu downloading and installing outside (oem) drivers is a means of last resort. The kernel within ubuntu , most of the time, finds and loads the needed drivers.
In the event that something does not work upon initial install then:
With a wired internet connection available, ->
Software sources; 3rd party software sources enabled;
ubuntu Software Center; update and upgrade installed packages,[INDENT]alternately - from the Command Line Interface (aka: terminal),
```
 sudo apt-get update
sudo apt-get upgrade
```
[/INDENT]
Now one opens up the "Additional Drivers" utility (location of that utility varies with installed version) and install any recommended drivers.[INDENT=3]
just as easy as that

[/INDENT]

---

