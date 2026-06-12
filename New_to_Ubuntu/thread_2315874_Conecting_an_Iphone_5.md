---
title: "Conecting an Iphone 5"
date: 2016-03-03
forum: New to Ubuntu
---

### Post by dusktumult on 2016-03-03
Hi ok i am running ubuntu 14.04 64bit on a toshiba satalite I am trying to connect an iphone 5 with the latest update and I am getting a number of errors. When I plug in my iphone and click trust computer i get an error:

***Unable to mount (...)***
[B][I]Unhandled Lockdown Error (...)
[/I][/B]
sometimes the lockdown error is (-16) other times its (-20)

As advised [here]("http://www.upubuntu.com/2012/02/fix-unhandled-lockdown-error-when.html") I tried these steps:
1. Unplug your iPhone or any iOS5 device from your computer, then start the terminal and install first the libimobiledevice-utils and ifuse packages:

```
sudo apt-get install libimobiledevice-utils ifuse
```

2. Connect now your device to your computer and run this command:

```
idevicepair unpair && idevicepair pair
```

and got
```
:~$ idevicepair unpair && idevicepair pair
ERROR: Device ... is not paired with this host
```

any help?

not sure if it matters but im using banshee as my music player/manager.

---

### Post by mörgæs on 2016-03-03
Hi, welcome to the fora.

I have Lubuntu 15.10, and an Iphone 5 connects directly without the need for any installs.

---

### Post by dusktumult on 2016-03-09
Ok well I installed ubuntu 15.10 to see if that would help. Banshe recognizes my phone and i can put music on it but my Iphone doesn't recognize the music. It doesn't showup in my music app.

---

### Post by mörgæs on 2016-03-10
It seems like it all works for the Buntu part but the Iphone is restricting what the user can see and use. 

Can't help you here, sorry. I use Apple gear as little as possible.

---

