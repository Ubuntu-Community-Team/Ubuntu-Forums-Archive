---
title: "adobe flash player"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-08-15
i want to install adobe flash player in ubuntu 8.04 for firefox 3.i downloaded thetar.gz file from adobe website,but i don't know how to proceed further.what should i do next?

---

### Post by t0p on 2008-08-15
It's better to use the version in the repos rather than one downloaded from adobe's site.  Open a terminal and type in:

```
sudo apt-get install flashplugin-nonfree
```

Or, to install a number of proprietary codecs and plugins such as mp3 and wmv as well as flash, do

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by coolbrook on 2008-08-15
Assuming it's on your Desktop, double click on it extract it to a folder

then open up terminal

```

cd ~/Desktop/name of the folder
./flashplayer-installer

```

Follow the instructions ensuring to close Firefox before or when prompted.

---

