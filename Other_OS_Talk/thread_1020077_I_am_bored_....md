---
title: "I am bored ..."
date: 2008-12-23
forum: Other OS Talk
---

### Post by dj_ee3 on 2008-12-23
Hi people, I have been using Ubuntu for a while now and everything is great so far which is a part of a problem. I am an adventure guy and I want to give a try of new things and solve problems. That's why I am bored with my ubuntu because everything runs fine. I had some problems with the microphone but I solved them for less then an hour. After that everything was perfect and after few weeks of using ubuntu it started to bore me. I am just saying that I need something to play around with. Some kind of problem which can keep me awake long nights in solving it. So, I think I need a new OS... just don't know which one to choose.

---

### Post by albinootje on 2008-12-23
> **dj_ee3 said:**
> Hi people, I have been using Ubuntu for a while now and everything is great so far which is a part of a problem. I am an adventure guy and I want to give a try of new things and solve problems. That's why I am bored with my ubuntu because everything runs fine. I had some problems with the microphone but I solved them for less then an hour. After that everything was perfect and after few weeks of using ubuntu it started to bore me. I am just saying that I need something to play around with. Some kind of problem which can keep me awake long nights in solving it. So, I think I need a new OS... just don't know which one to choose.

Arch Linux -> [http://www.archlinux.org](http://www.archlinux.org) A fresh approach.

And of course Gentoo Linux too, with distcc :)

And try VirtualBox and qemu! That'll be hours of experimenting with different OSes (BSD, Linux, Minix)

---

### Post by logos34 on 2008-12-23
> **dj_ee3 said:**
> That's why I am bored with my ubuntu because everything runs fine. I had some problems with the microphone but I solved them for less then an hour. After that everything was perfect and after few weeks of using ubuntu it started to bore me. I am just saying that I need something to play around with. Some kind of problem which can keep me awake long nights in solving it.

hah, reminds me of the Maytag commercial...

---

### Post by albinootje on 2008-12-23
> **logos34 said:**
> hah, reminds me of the Maytag commercial...

Maytag commercial ? You have a link ? :|

It reminded me of this article ("Linux is boring") :
[http://www.linux.com/feature/141546](http://www.linux.com/feature/141546)

---

### Post by logos34 on 2008-12-23
> **albinootje said:**
> Maytag commercial ? You have a link ? :|

It reminded me of this article ("Linux is boring") :
[http://www.linux.com/feature/141546](http://www.linux.com/feature/141546)

It was a famous American TV commercial by the washing machine appliance company (ca. 1970's). although I saw an recent version not long ago.  

[http://www.tvacres.com/admascots_maytag.htm](http://www.tvacres.com/admascots_maytag.htm)

---

### Post by jflaker on 2008-12-23
> **dj_ee3 said:**
> Hi people, I have been using Ubuntu for a while now and everything is great so far which is a part of a problem. I am an adventure guy and I want to give a try of new things and solve problems. That's why I am bored with my ubuntu because everything runs fine. I had some problems with the microphone but I solved them for less then an hour. After that everything was perfect and after few weeks of using ubuntu it started to bore me. I am just saying that I need something to play around with. Some kind of problem which can keep me awake long nights in solving it. So, I think I need a new OS... just don't know which one to choose.

You could go back to Windows...actually, try Vista, that has some problems you can solve.

But seriously, Get Virtual Box and you can try other distros or even load up windows again....

---

### Post by sportscrazed2 on 2008-12-23
not me the less time i spend defragging, virus scanning, and rebooting just to install updates i won't notice, the more time i have to goof off on these forums

---

### Post by ushimitsudoki on 2008-12-23
An alternative to trying a new distro is to improve this one. If you really like to solve problems, why not take a stroll through [Launchpad and try to help clear some bugs]("https://bugs.launchpad.net/")?

---

### Post by albinootje on 2008-12-23
Actually, yesterday at work the other sysadmin asked me a question about iptables for his home network.
He was about to go home, so I quickly wanted to show him how it would look like "simulated" in VirtualBox.
I installed the VirtualBox 2.1 PUEL version on an Ubuntu 8.04 machine, quickly did a minimal Debian installation.
Cloned the new Debian vdi, so I ended up with two instances.
(And I think i changed the hostname to be different on both)
Gave the 1 Debian-VM a bridged with host interface + a virtual NIC with "local network" to be able to communicate "privately" with the second Debian-VM.
The second Debian-VM got just the "local network" for the virtual NIC.
At the first Debian-VM i performed the 
```

echo 1 > /proc/sys/net/ipv4/ip_forward

```
and did the
```

iptables -t nat -A POSTROUTING -s 192.168.2.0/24 -j MASQUERADE

```
And at the second Debian-VM i performed a "mtr www.com", which worked ... but crashed the first Debian-VM !
I tried this at least another two times, and it kept crashing!
My coworker was laughing, and I was surprised.
I've almost never seen VirtualBox crashing.
Of course I can try to reproduce this at home in the near future to see what is really going on, but I just wonder whether VirtualBox 2.1 was rushed out the door a bit too quickly ?

---

### Post by dj_ee3 on 2008-12-23
> **ushimitsudoki said:**
> An alternative to trying a new distro is to improve this one. If you really like to solve problems, why not take a stroll through [Launchpad and try to help clear some bugs]("https://bugs.launchpad.net/")?
Thank you... I think I am going to do that.....

---

### Post by 2hot6ft2 on 2008-12-23
This should keep you busy, entertained and preoccupied for quite some time. Lots to try out here. [http://www.livecdlist.com/](http://www.livecdlist.com/)

---

### Post by Sorivenul on 2008-12-23
I also agree with the VirtualBox suggestion - it is a great way to try new systems without dealing with changing your current HD configuration or burning discs that will become coasters after one use. 

For your entertainment I agree with Arch, just go to DistroWatch and pick a few that look interesting (some in the lower half of the Top 100 are usually good for a few headaches). Try the BSD systems, try Minix, try systems like Syllable, AROS, ReactOS, and MenuetOS. There are so many choices, and, IMO, the only way to learn and to find what is right for you is to keep trying new things.

Good luck!

---

### Post by icecruncher on 2008-12-24
or you could help with documentation. start a project (if you know some code)

give back to the community

---

### Post by Tux Aubrey on 2008-12-24
Sounds like you need a dose of e17 - from svn

Hours of fun for those who like the challenge of a bleeding edge WM that keeps changing.  

Do it on Ubuntu or join us at [CafeLinux/OzOS]("http://www.cafelinux.org/forum/") so you have other nutters to discuss it with.

---

### Post by handy on 2008-12-24
You could go & pick up a PII or PIII from the rubbish dump for near no cost & create an [***_IPCop_***]("http://www.ipcop.org/") firewall, add [***_Copfilter_***]("http://www.copfilter.org/") & apart from all of the other options that you will have you can run [***_Privoxy_***]("http://www.privoxy.org/") & [***_ClamAV_***]("http://www.clamav.net/") (I know we don't really need anti-virus for Linux) without slowing down your internet browsing.

You could also use one of these cheap boxes to make a [***_FreeNAS_***]("http://www.freenas.org/") / [***_torrent slave_***]("http://sourceforge.net/forum/forum.php?thread_id=1953847&forum_id=507589").

All good fun, great learning experience & at nearly no cost for hardware.

---

