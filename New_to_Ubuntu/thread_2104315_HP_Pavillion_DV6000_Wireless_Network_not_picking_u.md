---
title: "HP Pavillion DV6000 Wireless Network not picking up"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by davidhitchen on 2013-01-12
Hi, just installed Ubuntu (11.10) for the first time. My wireless network card isn't recognized. I saw a thread that suggested a fix and tried it but It hasn't worked. The fix was to download a zip folder and put it on my desktop and enter the following command into the terminal

sudo mkdir /lib/firmware/b43
sudo cp Desktop/b43/* /lib/
firmware/b43
sudo rmmod -f b43
sudo rmmod -f ssb
sudo modprobe b43

But I get this...mkdir: cannot create directory `/lib/firmware/b43': File exists
admin1@ubuntu:~$ sudo mkdir /lib/firmware/b43
mkdir: cannot create directory `/lib/firmware/b43': File exists
admin1@ubuntu:~$ sudo cp Desktop/b43/* /lib/
admin1@ubuntu:~$ firmware/b43
bash: firmware/b43: No such file or directory
admin1@ubuntu:~$ sudo rmmod -f b43
ERROR: Removing 'b43': No such file or directory
admin1@ubuntu:~$ sudo rmmod -f ssb
ERROR: Removing 'ssb': No such file or directory
admin1@ubuntu:~$ sudo modprobe b43

Any suggestions (sorry I'm a total beginner so have no idea!)

---

### Post by Pjotr123 on 2013-01-12
Try this roadmap:
[https://sites.google.com/site/easylinuxtipsproject/internet](https://sites.google.com/site/easylinuxtipsproject/internet)

---

### Post by davidhitchen on 2013-01-12
Thanks, have you got those instructions for 11.10? It seems 12.04 is slightly different and I'm struggling to install the new drivers

---

### Post by Pjotr123 on 2013-01-12
Unfortunately not.... I suggest you do a clean upgrade to 12.04 LTS first, like this:
[https://sites.google.com/site/easylinuxtipsproject/reinstallation](https://sites.google.com/site/easylinuxtipsproject/reinstallation)

This may even be enough in itself to solve your problem. If not, you can apply the roadmap from a clean start, which is always best....

---

