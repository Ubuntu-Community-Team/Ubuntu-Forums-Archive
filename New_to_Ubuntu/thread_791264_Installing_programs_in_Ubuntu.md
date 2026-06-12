---
title: "Installing programs in Ubuntu"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by hka on 2008-05-12
Friends
I am new to Ubuntu and need help to install some programs in Ubuntu. I know that many of the programs are already installed, but when I tried to play some mp3 files, it wouldn't work. How what do i need to do?

BTW, I dont have a net connection at home, where I have my Ubuntu machine. I have to download the programs I need thru my ofice net, and then install it at home from my pendrive. I tried with Real Player (realplayerGOLD10.bin)... it didnt work

Also, when I viewed my pictures (saved in another partition) one file titled thumbs.db was showing. I think it is either a virus or something, and also tried deleting it but it says "U have no permission to complete the action" or something similar. What do I do? I actually want to format the whole partition containing these files since i have copied it to the Ubuntu desktop.
Will the virus if any spread??
Help.
:confused:

---

### Post by tamoneya on 2008-05-12
first of all i think whatever thread you saw about realplayerGOLD10.bin was a hoax and a scam.  Im not positive but that is my best guess since I saw one of those earlier today.

MP3's: for all of my music I use VLC( i use this for video as well).  It can be installed by typing the following command into terminal and then entering you password:```
sudo apt-get install vlc
```Another common program is xmms2 which can be installed with ```
sudo apt-get install xmms2
```Try these programs and if they dont work try to provide a specific error and we will help solve it.

Pictures: thumbs.db is a windows file that allows thumbnails to be quickly display in file manager.  This is not a virus and if you really want to delete it you should hit alt-F2 and type ```
gksudo nautilus
```Then navigate to the file and you should be able to delete it.

---

### Post by Jake90 on 2008-05-12
Tamoneya gave good advice, I'm just going to add one more option. You can also type ```
sudo apt-get install ubuntu-restricted-extras
``` which should install the codecs you need to play music on any player.
The problem that comes up is that you said your ubuntu machine has no access to the internet. That means that what we said so far won't work unless you find a way to connect. I don't know how to download the programs and transfer them (I'm still pretty new to this) but someone else might

---

### Post by 10Digits on 2008-05-12
First of all Welcome to the world of UBUNTU!!!!
The first thing that we ahve to know is that do you have windows on the other partition if u do then do not worry. thumbs.db is just used by windows for thumbnail viewing of picture files. also ubuntu will not be affected by any virus. 

As for the matter of mp3 files. I will suggest u convert ur mp3 files to .OGG . I suggest u use AIMP2 . download it thru softpedia.com. Otherwise doing it manually will require a lot of time and it is a very very messy job...

jake mentioned a very important point. Ubuntu is gr8 with the net but tends to be frustrating if u do not have the net. but I am sure you will find some one who has way for all of this on this forum, I hope so.

---

### Post by Zerocool10482 on 2008-05-12
This will give you everything you need.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Canis familiaris on 2008-05-12
For offline installation of packages, visit:

[http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)

---

