---
title: "gnome-dictionary no-window problem"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by nguchet on 2008-11-06
It seems like the option -n or --no-window of gnome-dictionary doesnt work at all, kinda stupid and i think it s pretty much of a pain in the *** every time you need to look up for a word just quick from term, thus no other way around but to open the GUI Gnome-Dict in only 5sec :confused:
Anyone here got this problem? please help:confused::(. i m on Hardy

---

### Post by Poyntz on 2008-11-06
what version of gnome-dictionary do you have?

ie, in terminal type: gnome-dictionary --version

I have 2.24.1 and I don't have that option :/

---

### Post by nguchet on 2008-11-06
I have Gnome-dic 2.20.0.1, i tried to uninstall it and reinstall again, it is in the gnome-utils pckage, gnome-utils = garbage included:(,  i wonder if we can install it individually? , oh this s a very common problem and maybe in gnome-dic higher version this option was cut off already, booo :(

---

### Post by Poyntz on 2008-11-07
This should be a later release of gnome-utils which should include a more updated gnome-dictionary: 
[http://ftp.gnome.org/pub/GNOME/sources/gnome-utils/2.24/gnome-utils-2.24.0.tar.gz](http://ftp.gnome.org/pub/GNOME/sources/gnome-utils/2.24/gnome-utils-2.24.0.tar.gz)
Only do this after you've tried **sudo apt-get update**, given ubuntu a chance to prepare the packages and used: **sudo apt-get upgrade** to install the updates. 

It's better if you use apt, so we can avoid source code if we can possible help it. If apt doesn't update gnome-utils you may have to install the tarball from above.

Usually you would **tar zxvf gnome-utils-2.24.0.tar.gz** to unpack this, move to the directory using **cd <directory path>** and then 
**./configure --prefix=/usr/local && make && make install**. 

If there's no configure file, look for a **README** in the file which may contain installation details. 

Personally I have no idea if gnome related updates should be downloaded from source, but you could always try. Other than that I'd recommend updating to the latest ubuntu distribution :/

---

