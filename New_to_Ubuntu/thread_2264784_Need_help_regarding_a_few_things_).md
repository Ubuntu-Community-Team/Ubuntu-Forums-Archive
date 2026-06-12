---
title: "Need help regarding a few things :)"
date: 2015-02-10
forum: New to Ubuntu
---

### Post by Zlash on 2015-02-10
Hello!

First of all, id like to say that im not new to computers, nor am i new to the terminal. I am however, new to linux. Linux is such an alien language to me compared to the windows i know. It doesnt change the fact that I hate the road windows has choosen. Hence the switch,

I am running ubuntu 14.04 on dual boot on my 

ZENBOOK UX32VD

it has
Core i7 Quad 1.9 Ghz (Up to 2.2)
GeForce GT 620M 1gig
4 (soon 6) Gigs of ram

PROBLEM 1:
How do I check if everything runs as it should? I know how to do this in windows and i usually check up on everything. But on ubuntu, right now I dont know how much of my hardware runs as it should!

PROBLEM 2:
Currently, these are the "erors" I have:

- Cant connect to dormitory wireless altho settings are the same as friends with ubuntu. I can connect to all other wireless networks.
- When starting ubuntu I get: "ERROR too many voltage retries, give up". After that, everything starts up as it should.
- Battery life is halved compared to windows (normally i can run 4-5 hours. Ubuntu runs 2hours. I have installed TLS)
- I am trying to install MAPLE software, but I cannot activate it. I get "Missing HOST ID for license server". I have installed lsb-base and lsb-core. (Note that I do not know if the installation is in affect, but i did reboot after installation).
- CPU is running at average 20% when idle, vs windows running at average 10% when idle. Cannot see why, and as of drivers, I have no idea how to check if things are as it should be. (I have tried a few terminal commands found on the internet, some of them just gave errors and i stopped at that, and now I have a feeling that my "Ubuntu" is not as clean as it could be).


If I can get some help, that would be great! :)

Thanks in advance!

Tommy




[COLOR=#000000][FONT=Helvetica]** *ERROR* too many voltage retries, give up**[/FONT][/COLOR]

---

### Post by mastablasta on 2015-02-10
> **Zlash said:**
> 

- When starting ubuntu I get: "ERROR too many voltage retries, give up". After that, everything starts up as it should.


Where is this error? where does it appear? before or after bootloader

dmesg command should show any errors during boot. you can post here using code tags.

> 
- Battery life is halved compared to windows (normally i can run 4-5 hours. Ubuntu runs 2hours. I have installed TLS)
- CPU is running at average 20% when idle, vs windows running at average 10% when idle. Cannot see why, and as of drivers, I have no idea how to check if things are as it should be. (I have tried a few terminal commands found on the internet, some of them just gave errors and i stopped at that, and now I have a feeling that my "Ubuntu" is not as clean as it could be).


do you have nVidia optimus? if so, you need to look at bumblebee project.

---

