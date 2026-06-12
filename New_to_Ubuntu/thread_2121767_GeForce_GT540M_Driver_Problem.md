---
title: "GeForce GT540M Driver Problem"
date: 2013-03-03
forum: New to Ubuntu
---

### Post by von Corax on 2013-03-03
I'm trying to get my (borrowed) laptop (Lucid LTS) set up to work with the Nvidia CUDA 5 toolkit, but the driver can't seem to find the card (GeForce GT540M). I can see that the driver is loading, and I can see the card on the PCI bus, but they can't seem to find each other. Can anyone help me with this?

Please don't hesitate to ask for whatever supplemental info you need.

---

### Post by oldfred on 2013-03-04
I do not know optimus, but that is what you have.

       Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
[http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889](http://ubuntuforums.org/showthread.php?t=2121707&p=12540889#post12540889)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)

---

### Post by Mr. Shannon on 2013-03-04
You actually don't need bumblebee for CUDA.  You can see how to do this here: [http://samiux.blogspot.com/2011/05/howto-nvidia-cuda-toolkit-40-on-ubuntu.html](http://samiux.blogspot.com/2011/05/howto-nvidia-cuda-toolkit-40-on-ubuntu.html).  NOTE: I have no experience with CUDA, just enabling optimus with bumblebee, so I cannot vouch for this solution.

---

### Post by von Corax on 2013-03-06
Got it! I stumbled across [http://ubuntuforums.org/showthread.php?t=1510283](http://ubuntuforums.org/showthread.php?t=1510283), which gave me the clue: apparently the CUDA installer never created any device nodes for the card. When I ran the commands
```
sudo mknod -m 666 /dev/nvidia0 c 195 0
sudo mknod -m 666 /dev/nvidiactl c 195 255
```
the CUDA calls executed with no problem.

Now I just need to automate that, and I should be shiny. :)

---

