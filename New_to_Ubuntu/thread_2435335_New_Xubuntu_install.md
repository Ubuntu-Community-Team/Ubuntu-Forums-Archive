---
title: "New Xubuntu install"
date: 2020-01-19
forum: New to Ubuntu
---

### Post by fefniir2 on 2020-01-19
I have a fresh Xubuntu lts install on an AMD Ryzen 3 2200G with Vega 8 system. Does anyone have advice/tips/tools I might want to install to keep this build running smoothly?

---

### Post by mastablasta on 2020-01-20
such as? you can install AMD GPU pro if you feel is necessary. otherwise if things work well as they are just leave them be.

*buntu systems are known to come with sane default settings so there is not much messing around needed after install. you can add your favourite apps, add a PPA or two if you need some latest versions of favourite apps (might cause instability; but depends on what you are doing), and finally if you are security oriented you can harden the install. other than that, don't try and fix it if it works.

---

### Post by Autodave on 2020-01-20
This ain't Windows.  Only advice that I can give is to *not* install anything from the web.  Everything that you will probably ever need is in the repositories.  If you are looking to replace a particular Windows program that you just have to have, ask here what a *buntu equivalent would be.

---

### Post by CorporateMonkey on 2020-01-21
You should probably consider installing **amd64-microcode** package.

---

### Post by deadflowr on 2020-01-21
amd64-microcode (and intel-microcode) are default packages,
they are tied to the kernel now.
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259]("https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/1738259")

---

### Post by jim Kane on 2020-01-21
install "synaptic package manager" which dosent seem to come with new install now

---

### Post by industryhonolulu on 2020-01-22
thanks, this worked for me

---

### Post by mastablasta on 2020-01-23
by the way do these vega (less than 10) work out of the box well? i see some users had issues with vega 8 and vega 3 in Linux. at least to get all the features the chip offers. but mostly it's from older threads.

---

### Post by fefniir2 on 2020-01-24
So far I've only had one very minor graphical glitch while running 18.04 LTS. I was running spotify and upon opening the app, the entire app window was covered in small green dots. They eventually went away and haven't shown back up since, so only a very (brief) minor annoyance. Of note: on 19.10 I had major screen tearing issues, but after installing 18.04, I've had no screen tearing whatsoever.

---

### Post by daniewicz on 2020-01-24
Ubuntu newb here.

With my fresh install of 19.10, the default NetworkManager did not perform as well as wicd for my wireless. So fefniir2 if your wireless download speeds seem slow you might consider wicd.

---

### Post by CelticWarrior on 2020-01-27
> **daniewicz said:**
> So fefniir2 if your wireless download speeds seem slow you might consider wicd.

**No, you absolutely should not!**

---

### Post by yetimon_64 on 2020-01-27
> **CelticWarrior said:**
> **No, you absolutely should not!**

**+1**, this I agree with. 

@OP, IF you continue to have download speed problems there is a [[COLOR=#0000ff]--Networking and Wireless--[/COLOR]]("https://ubuntuforums.org/forumdisplay.php?f=336") (link in blue text) sub forum here you should check out; particularly the third sticky thread at the top. IF you are on a wireless connection this sticky has troubleshooting instructions using the wireless-info script. Other wired networking issues can be researched/addressed on the N & W sub forum as well.

Network manager is pretty heavily integrated into the system and if ripped out and replaced may leave your system in a mess. I have used wicd many years ago and found it nowhere near as full featured as NM, it may be of use to some more advanced users (or lucky new users, like myself back when I used it) but is not a path I'd ever advise a new starter on ubuntu to go down (here be dragons ;)).

If, as I suspect, you are new to Ubuntu/Linux I definitely advise you to stick to a stock standard installation so when problems arise you will find it far easier in getting assistance here. In my opinion sticking with NM will give you better odds of getting good/more timely help. There is NO guarantee randomly replacing a networking utility is going to fix the problem but it carries a VERY high risk of messing up your installation if you make a mistake in the process.

Regards, yeti.

---

### Post by mastablasta on 2020-01-27
i read that some wi-fi chips are simply poor. so they have bad review even when win 10 is installed. if this is a desktop PC, a cheap solution is well supported wi-fi USB or even a PCI card. raspberry pi stores sell those USB that got thoroughly tested in linux.

cheapest ones (those small tiny ones) are about 7 EUR but you can get stronger ones for about 16-18 EUR. they work well enough and are just plug and play.

---

