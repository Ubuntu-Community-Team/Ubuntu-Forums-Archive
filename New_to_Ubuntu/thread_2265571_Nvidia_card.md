---
title: "Nvidia card"
date: 2015-02-16
forum: New to Ubuntu
---

### Post by Lica_Bogdan on 2015-02-16
Hi everyone! I am sorry if I ask a question that is stupid or was on the forum,but I didn't succeed to solve it.I installed ubuntu 14.04,on my laptop: I7-3517U,1.9GHz, 8 GB RAM,SSD Samsung 840 Pro and nvidia GeForce GT 635m 2gb,if this is relevant.I installed the nvidia card from their official website ,but I have a problem.If I start a program like is Lightworks,I want it to be opened with nvidia,not intel.I do not thing it is opened with the nvidia card,because if i put there 2 short clips and hit "play",it is jerky.Can you help me to open it with the nvidia card? Thank you in advance. :p

---

### Post by buzzingrobot on 2015-02-16
Be sure you've set your machine's BIOS to use the Nvidia instead of the Intel.

---

### Post by Lica_Bogdan on 2015-02-16
I do not want to hate the nvidia card to run on all apps,I want only on some of them that I choose.

---

### Post by Bashing-om on 2015-02-16
Lica_Bogdan; Hi !

> **Lica_Bogdan said:**
> I do not want to hate the nvidia card to run on all apps,I want only on some of them that I choose.

In this case you are looking at purging the current graphics drivers, installing a propriatary Nvidia graphics driver along with nvidia-prime and nvidia-settings. In nvidia-settings you can choose the graphics set to use.
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)

For instance, if the 340 driver version works for your situation:
Check and make sure you have no other 3rd party PPAs enabled on your system, disable 1st if present, and ->
NVIDIA 340.46 driver for Linux
```

sudo apt-get purge nvidia*
sudo apt-get install --reinstall ubuntu-desktop
sudo add-apt-repository ppa:mamarley/nvidia
sudo apt-get update
sudo apt-get install nvidia-340

```
Check and make sure the installer installed 'nvidia-prime' and nvidia-settings.
```

dpkg -l nvidia-prime
dpkg -l nvidia-settings

```

[INDENT][INDENT][INDENT]finer than a frog's hair ?
[/INDENT][/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-02-16
You might also be interested in Nvidia prime indicator.

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

The latest Nvidia drivers that come with Ubuntu 14.04 will let you switch hybrid graphics between Nvidia and Intel graphic adapters but only through the Nvidia settings utility which is installed at the same time as the Nvidia driver or through a utility such as Prime Indicator.

The Nvidia drivers do not as yet provide automatic switching between video adapters.

Regards.

---

