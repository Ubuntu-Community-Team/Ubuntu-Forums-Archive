---
title: "TOTEM problem"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by nhovan on 2008-08-01
I am trying to play a dvd. when i put it in Totem comes up. but it just greys out and i have to force quit it. anyone know what i can do?

---

### Post by bobnutfield on 2008-08-01
The greying out is telling you the program has crashed.  I would try to open it from the command line, look at the error messages and that will give you a clue as to why it is crashing.

On a side note, I have never liked Totem as a DVD player.  I have always had much better service from VLC and it plays just about anything you can throw at it.

---

### Post by kansasnoob on 2008-08-01
Have you installed the Medibuntu repo:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Remember the gpg key!

Then add:

```
sudo apt-get install libdvdcss2
```

I'd include the code for Medibuntu but I'm not sure what version of Ubuntu you're using.

---

### Post by nhovan on 2008-08-01
ive got 8.04.     i tried vlc but it wont play it either. this is a standard dvd straight from netflix nothing special

---

### Post by bobnutfield on 2008-08-01
Type into a terminal:

> totem

When it crashes, the cause of the crash will be in the error messages as it crashes.

---

### Post by nhovan on 2008-08-01
ive got 8.04.     i tried vlc but it wont play it either. this is a standard dvd straight from netflix nothing special   and i try to install libdvdcss2 and it says the list of sources can not be read

---

### Post by nhovan on 2008-08-01
it says encrypted play is not possible

---

### Post by kansasnoob on 2008-08-01
OK, for 8.04 go to terminal and:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

Then click enter.

Then:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Enter again!

Then:

```
sudo apt-get install libdvdcss2

```

---

### Post by gobbles414 on 2008-08-01
Kansasnoob is correct. Furthermore, if you want to access DVD menus in Totem you'll need to install *totem-xine* from Synaptic. To make your life easier, you'll probably want to do a "Complete Removal" of *totem-gstreamer* (right-click on the package to mark it for complete removal).


PS: While not necessary for DVD playback, I recommend that you also install *ubuntu-restricted-extras*, *w32codecs*, *mozilla-acroread*, and *totem-plugins-extra*. These will all enhance your multimedia experience in Ubuntu.

---

