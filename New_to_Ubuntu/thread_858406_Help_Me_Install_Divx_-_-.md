---
title: "Help Me Install Divx -_-"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by kulote on 2008-07-13
I dont know what to do with the package i got from the web-page ... and i want to get the codes and or player CALLED DIVX...

If ure in the mood of helping me ill really appreciate it ... 

Maybe u already realized that i posted another thread with the same problem but no one payed attention to it ... 

thanks for reading i hope u could help ...

---

### Post by k420 on 2008-07-13
[http://ubuntuforums.org/showthread.php?p=1600723]("http://ubuntuforums.org/showthread.php?p=1600723")
This should help

---

### Post by Terry of Astoria on 2008-07-13
I don't know if there is a "player" called divx for Linux. I know there is a Divx player for Windows. I can tell you that most players in Linux can play divx files (movies, etc) already. There are lots of resources here on the forums for information about multimedia. You can try using VLC player. It's able to play divx files straight out of the box (straight out of the repository.) To install VLC type in the terminal:
<code>
sudo apt-get install vlc
</code>
and then hit enter. You should be able to install VLC that way.
  VLC stands for Video Lan Client. It was originally designed to play movies over a network connection.
  One other suggestion is please look in the Synaptic Package Manager program under your Ubuntu Admin menu. You can search for divx in there and see what you get.

---

### Post by LowSky on 2008-07-13
go to ternial and tpe the following commands in order

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2 w32codecs ubuntu-restricted-extras vlc mplayer mozilla-plugin-vlc  
```

---

### Post by kulote on 2008-07-13
u rock guys ty so much =D

---

