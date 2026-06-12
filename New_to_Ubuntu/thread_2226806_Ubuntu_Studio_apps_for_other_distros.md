---
title: "Ubuntu Studio apps for other distros"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by venkatramsam on 2014-05-29
I use ubuntu 14.04 on my laptop. I want to know if the PPAs for ubuntu studio apps can be added to the normal 14.04 desktop.

---

### Post by su:bhatta on 2014-05-29
Ubuntu studio apps can be installed using the following commands :
```
sudo apt-get install ubuntustudio-audio
sudo apt-get install ubuntustudio-video
sudo apt-get install ubuntustudio-desktop
sudo apt-get install ubuntustudio-recording
sudo apt-get install ubuntustudio-audio-plugins
sudo apt-get install ubuntustudio-photography
sudo apt-get install ubuntustudio-publishing
sudo apt-get install ubuntustudio-graphics
```
Doesn't require any ppa's. You will get all the apps that are default in Ubuntu Studio if you use those commands.

If you want audio production, you might require the low-latency kernel, which comes as default in Ubuntu Studio.
If you dont want to use commands, you can install those meta packages  using Software Center Or Synaptic, where they are listed too.


This [page]("https://help.ubuntu.com/community/Ubuntu%20Studio%20Upgrade%20from%20Ubuntu") describes the entire process in detail.

Edit: Not quite sure what you meant by other distros but this method works for all Ubuntu flavors as well as Ubuntu based distros , like Linux Mint, Elementary, etc .

---

