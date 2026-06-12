---
title: "how do i use wine"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by kobra_877 on 2008-09-08
how do i use the windows emulator wine to run a windows based program on my linux laptop

---

### Post by tuxxy on 2008-09-08
[https://wiki.ubuntu.com/Wine](https://wiki.ubuntu.com/Wine)

---

### Post by fauzie on 2008-09-08
Check the wine application database first before wasting any time configuring the system. Most of the time, after wine is installed, you just need to double click the .exe program you want. The configuration, if any, usually involved copying some dll files from windows, so you might need a windows machine. The wine application database should tell you what to do for a particular program.

What program are you trying to run anyway? Are sure there is no Linux-native substitute.

---

### Post by BenAshton24 on 2008-09-08
Darn i clicked on this thread hoping for a chance to say "you pour it out and drink :P" but alas you went into further detail :P

Basically it's really simple, click on applications --> Accessories --> terminal. Once the terminal has opened, type the following command and press enter:
> sudo apt-get update && sudo apt-get install wine && winecfg
Once you have done this, you will be asked to enter your password, enter it and wine should install 

note: you may be prompted to confirm the installation, simply press the letter "y" and then press enter

After the installation a window should open, in this window you will have the option to configure wine, select your favorite preferences and close the window

note: If your not sure what to do then chances are it will work without any configuration so just close it straight away.

Last but definitely not least you will have to download / get the windows executable and double click it (just like you would in windows) and it should automatically open with wine.

note: if you are installing software from a disk then you will have to goto Places --> CD Drive and locate setup.exe or similar

note: Not all programs will work perfectly in wine, head over to [http://appdb.winehq.org/](http://appdb.winehq.org/) and search the program you want to install before installing it to check that it will work as well as you want it too.

Hope this helps :D
Ben.

---

