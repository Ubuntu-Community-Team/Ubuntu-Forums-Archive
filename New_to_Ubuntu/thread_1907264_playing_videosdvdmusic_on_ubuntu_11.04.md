---
title: "playing videos/dvd/music on ubuntu 11.04"
date: 2012-01-11
forum: New to Ubuntu
---

### Post by monsterwizard on 2012-01-11
Ok, I looked up how I can play videos on my ubuntu natty and a website told me to insert this into the terminal
sudo apt-get install ubuntu-restricted-extras
I did and there were no error messages and it did its thing real quick, then it had a second step,
sudo /usr/share/doc/libdvdread4/install-css.sh
and the terminal spat out this message,
owner@ubuntu:~$ sudo /usr/share/doc/libdvdread4/install-css.sh
[sudo] password for owner: 
sudo: /usr/share/doc/libdvdread4/install-css.sh: command not found
owner@ubuntu:~$ 


Im not sure what to do, but my goal is to obviously be able to play videos, dvd, and listen to music on my fairly newly installed natty
help would be greatly appreciated,
Scott

---

### Post by mastablasta on 2012-01-11
you might have missed one command
 
sudo apt-get install libdvdread4
 
See here:
 
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by monsterwizard on 2012-01-12
Ok, thanks, I think I know my problem, my package manager is broken, Im trying to figure out how to fix that right now in another thread.  Once I fix that Ill do what you said, I saved the link.
Much appreciated mister masablasta

---

### Post by bindraj on 2012-01-12
you might have missed one command
 
sudo apt-get install libdvdread4
 
See here:
 
[https://help.ubuntu.com/community/Re...ts/PlayingDVDs]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by bindraj on 2012-01-12
The perfect place to post for your Ubuntu support if you are new to Linux.

---

