---
title: "NVIDIA GeForce GT 630M and Ubuntu 13.04?"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by chrscrlsn on 2013-04-26
Hello,

I have an Acer Aspire V3-571G-6407 with an NVIDIA GeForce GT 630M graphics card and something called "NVIDIA Optimus". What do I need to install to take advantage of these under Ubuntu? Are they even supported at the moment? Any info would be much appreciated. :)

---

### Post by junctionIV on 2013-04-26
You will want to insatll the Nvidia Graphics drivers, which at the moment seems to be a nightamre.  I just spent about 2 hours trying to insatll the drivers and keep unity running as well.  You might try checking out some other threads before you get into this but I had to do the following as the Additonal drivers would not load the nvidia drivers for me:
> sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install linux-headers-generic
sudo reboot
sudo apt-get install nvidia-current
sudo nvidia-xconfig
sudo reboot


note this caused my tower to reboot with no uinty, just a blank desktop.  I had to then ctr-alt-t to open the termial and ran the following:
> sudo dconf reset -f /org/compiz
gnome-session-quit
and then logged back in

Im not sure if the "Nvidia Optimus" is supported yet, you might try there website to see about insalling in in Ubuntu/linux.  Don't try insatlling the drivers unless you have ample time to fix any problems.

---

### Post by chrscrlsn on 2013-04-26
Thanks for the reply. Is this only a problem with Ubuntu 13.04? Or is installing NVIDIA drivers under any version of Ubuntu a nightmare? :confused:

---

### Post by junctionIV on 2013-04-26
> **chrscrlsn said:**
> Thanks for the reply. Is this only a problem with Ubuntu 13.04? Or is installing NVIDIA drivers under any version of Ubuntu a nightmare? :confused:
It was really 12.10 the had the most recent issues but I had the same problems updating from 12.10 to 13.04, but with new errors :/
Some people have said that the issue of not being able to use the additional drivers GUI was fixed in 13.04 but my display wouldn't show anything after the update so i used the method above.  I know other people were having the same problem as mine in 13.04 but i can't say for a 100% that every one has the same problem.

I intially used the info I found here:
[http://askubuntu.com/questions/285074/is-it-safe-to-install-the-nvidia-drivers-in-ubuntu-13-04](http://askubuntu.com/questions/285074/is-it-safe-to-install-the-nvidia-drivers-in-ubuntu-13-04)

Idk if that will help or not...

---

### Post by screening on 2013-04-26
I don't shure, but, to take advantage of this hibryd card you need to install Bumblebee:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I got a Nvidia 635M and works like a charm, the time of duration of the battery duplicate with that

---

### Post by 3rdalbum on 2013-04-27
It is unusual to have problems with the Nvidia driver. Usually, you just install it and it works.

Optimus (switching GPUs) requires Bumblebee to be installed. If you are happy just using the Nvidia card you don't need Bumblebee.

---

### Post by martin72 on 2013-05-25
> **screening said:**
> I don't shure, but, to take advantage of this hibryd card you need to install Bumblebee:

[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

I got a Nvidia 635M and works like a charm, the time of duration of the battery duplicate with that

I have a laptop with a Nvidia 630M card. I have the same problems as the other persons in this topic: after installing Nvidia driver in Ubuntu 13.04 the Unity interface is gone and the resolution is 640x480 and i cannot change this.
please can you tell me what have you done to let your 635m card work in Ubuntu 13.04.

Ps. I have the same problem with Ubuntu 12.04.

---

### Post by Odin Overland on 2013-06-20
When I installed Ubuntu GNOME 13.04 64 bit on an ASUS with GEFORCE GT 635M my system reads this even after installing bumblebee - is this normal?

---

### Post by Odin Overland on 2013-06-20
Also since following the bumblebee instructions my battery is reading at 0% and battery LED is flashing orange - but still runs off of battery power.  Also the fan is running high and blowing out cool air.

---

### Post by mehdi5 on 2014-04-13
Hi junctionIV
I followed your command codes in the first of this thread, but when I reboot my system I saw a blank desktop :(
I followed:
> [COLOR=#000000]*sudo dconf reset -f /org/compiz*[/COLOR]
[COLOR=#000000]*gnome-session-quit*[/COLOR]

but the blank desktop still exists :'(
can you help me???
I have Ubuntu 13.10

---

