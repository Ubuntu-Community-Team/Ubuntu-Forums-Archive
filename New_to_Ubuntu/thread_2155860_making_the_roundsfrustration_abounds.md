---
title: "making the rounds/frustration abounds"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by sarge1957 on 2013-06-19
Good afternoon,
Yup!!! I just fell off the turnip truck. That should give you an idea of what I know about Linux. I have managed to install Ubuntu 13.04 but I'm at a loss in how to install a simple screen saver. It downloads fine but where to go from there ? I haven't got a clue. I have also tried to install Tor with the same result. Any help will be greatly appreciated.  Thanks, sarge1957

---

### Post by DogMatix on 2013-06-19
You may find this manual useful [Ubuntu Manual](http://ubuntu-manual.org/)

If you are interested with Tor & privacy you may find [Tails](https://tails.boum.org/download/) distro. worth a look.

---

### Post by sum1nil on 2013-06-19
Sorry but I do not use screen savers, but I would install Synaptic, click all categories filter then do a quick find for 'screen savers. To install
Synaptic at a terminal enter 'sudo apt-get install synaptic'. 
l am interested in how you installed Tor. I got mine from: [https://www.torproject.org/projects/torbrowser.html.en](https://www.torproject.org/projects/torbrowser.html.en)

I made an 'opt' folder in my home directory( opt for optional) and extracted it using 'file-roller' ( if you doublle click it should open) the extractor browse to your new 'opt' folder and extract. In the Tor browser folder there is a start program. If double clicking does not work simply use the terminal and cd to ~/opt/tor-browser.

A few things to remember about Tor setup. Unless you got haveplenty of bandwidth do not 'mirror' if you make a relay. Also take advantage of the auto port forwarding. Please enter a name for the relay, if you choose to use it. please read the Tor help file.
Best of luck.

---

### Post by ajgreeny on 2013-06-19
Probably **sudo apt-get install xscreensaver** for your screensaver application, and maybe remove gnome-screensaver if it's installed at the moment.

I'm using Xubuntu 12.04 and use xscreensaver to display a random selection of my photos which I can choose from any folder on my machine.  I do this, not because modern machines need a screensaver, but because it's a very good way of seeing old photos that I have nearly forgotten I've taken.

xscreensaver is so much better a screensaver application than gnome-screensaver as it is very much more configurable.  Give it a try!

---

