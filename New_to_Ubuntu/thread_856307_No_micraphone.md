---
title: "No micraphone"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by Dougpol1 on 2008-07-11
i'm using a 64bit dual processor machine with ubuntu 8.04. My realtech micraphone does not work. IT is plugged in.  I tested it in ekiga and in sounder recorder and could not get to work. there seems to be no input.  Doug

---

### Post by tenjin1 on 2008-07-11
Open a terminal and type:
```
alsamixer
```
Make sure your microphone is turned on in that interface. Should be a option for Line In/Microphone. You want Microphone. Use arrow keys to change and navigate.

you can also double-click your Volume Control icon in system tray and make sure your Microphone is selected there too.

---

### Post by dracayr on 2008-07-11
this worked for me (whilst the normal alsamixer didn't):

```
sudo apt-get install gnome-alsamixer
gnome-alsamixer &
```

dracayr

---

