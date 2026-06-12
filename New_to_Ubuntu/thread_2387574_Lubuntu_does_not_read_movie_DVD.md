---
title: "Lubuntu does not read movie DVD"
date: 2018-03-20
forum: New to Ubuntu
---

### Post by vicof on 2018-03-20
I installed Lubuntu 17.10.1.  When I insert a DVD of a movie into the laptop the window of Gnome MPV opens but stays black. If   I use VLC (version 2.2.6 set, for example, as /dev/dvd)  I  can hear the movie audio for the entire time the DVD plays. But I can see a  very corrupted video image only for about two  minutes at the beginning of the  movie, afterwards the VLC screen is black. I had no problem to watch movies on DVD with the VLC  version for Windows XP before installing Lubuntu.
Thanks for your help.

---

### Post by mc4man on 2018-03-20
In a terminal run
```
sudo apt install libdvd-pkg
```
You'll get a pop up, press enter , another pop up, press enter.
Then back at terminal run 
```
sudo dpkg-reconfigure libdvd-pkg 
```
At pop up press enter to do the actual install.
Then try vlc again (- for dvd's you'll find vlc better suited than mpv..

---

### Post by vicof on 2018-03-21
It worked! VLC now plays the DVD without problems. Good job. Thank you very much.

---

