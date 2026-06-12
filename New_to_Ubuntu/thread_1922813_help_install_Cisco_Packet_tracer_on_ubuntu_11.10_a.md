---
title: "help install Cisco Packet tracer on ubuntu 11.10 amd64"
date: 2012-02-09
forum: New to Ubuntu
---

### Post by rongdattien on 2012-02-09
help please !!

trunglv@trunglv-Admin:~/Downloads$ sudo su
root@trunglv-Admin:/home/trunglv/Downloads# sudo ./PacketTracer533_i386.bin
Self extracting archive...
./installer: line 24: rpm: command not found


Do you accept the terms of this EULA? (Y)es/(N)o
Y
You have accepted the terms to the EULA. Cisco Packet Tracer will now be installed.
Attempting to install package now
./installer: line 5: rpm: command not found


Thankyou so much !

---

### Post by sadaruwan12 on 2012-02-09
Welcome to the forum !

First of all please remove your email we don't use emails to give help.

For your issue you can use Wine it's a execution layer which will help you to run windows programs.

One of my friends had the windows version of the packet tracer and he used wine to get it installed it worked just like in windows.

to install wine use,

```

$ sudo apt-get install wine

```

And here are some links to rap your mind around wine.

[Link 1]("http://www.psychocats.net/ubuntu/wine")
[Link 2]("http://www.yolinux.com/TUTORIALS/LinuxTutorialRunMicrosoftExe.html")
[Link 3]("http://ubuntuforums.org/showthread.php?t=1180031")

---

### Post by Cheesemill on 2012-02-09
The installer that you are trying to run is meant for Red Hat systems, not Ubuntu.
It is failing because it is trying to use the rpm command which doesn't exist on Ubuntu/Debian systems.

---

### Post by sadaruwan12 on 2012-02-09
> **Cheesemill said:**
> The installer that you are trying to run is meant for Red Hat systems, not Ubuntu.
It is failing because it is trying to use the rpm command which doesn't exist on Ubuntu/Debian systems.

Cheesmill is right and from what I've seen it's better if you use the windows version with the wine layer or you need to find a installer program that is compatible with Debian / Ubuntu systems.

---

### Post by rongdattien on 2012-02-09
> **sadaruwan12 said:**
> Welcome to the forum !

First of all please remove your email we don't use emails to give help.

For your issue you can use Wine it's a execution layer which will help you to run windows programs.

One of my friends had the windows version of the packet tracer and he used wine to get it installed it worked just like in windows.

to install wine use,

```

$ sudo apt-get install wine

```And here are some links to rap your mind around wine.

[Link 1]("http://www.psychocats.net/ubuntu/wine")
[Link 2]("http://www.yolinux.com/TUTORIALS/LinuxTutorialRunMicrosoftExe.html")
[Link 3]("http://ubuntuforums.org/showthread.php?t=1180031")
I am newbie. You can help me? please sent Yahoo ! : trungkscntt 
Thanks !

---

### Post by uRock on 2012-02-09
I installed a 32bit ubuntu in a virtual machine for running PacketTracer.

I have found a thread in the past explaining how to install PT on 64bit and it worked, but Google isn't playing nice with me right now.

---

