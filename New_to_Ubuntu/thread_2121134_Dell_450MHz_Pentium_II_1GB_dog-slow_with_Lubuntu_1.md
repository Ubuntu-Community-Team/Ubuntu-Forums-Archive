---
title: "Dell 450MHz Pentium II 1GB dog-slow with Lubuntu 10.04.4"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by Micronta on 2013-03-01
Hello all,

I'm a Linux newbie (but have been reading and burning midnight oil for some four weeks now) so when I don't know something, please don't throw any heavy objects in my general direction. ;)

I have an older DELL 450MHz PII desktop, 1GB of RAM and a 80GB disk. I had the idea of using it as a personal web server with Apache2. XP worked but was on the slow side, although not too bad. So I looked around, did some reading and ended up installing Lubuntu 10.04.4 on it. But what I thought was much lighter turned out to be MUCH, MUCH slower. To the point that it's practically unusable. When typing in the terminal, I often make a mistake, thinking that I didn't type a symbol and retype it when I actually did and now the symbol pops up multiple times. It sort of accepts what I typed, thinks about a little and then spits out it's opinion. There are no error messages that I can identify, it least it hasn't said anything bad, no panic or anything like that. I have reinstalled the same Lubuntu version multiple times from different media (USB/CD) with the same result. The bigger Ubuntu 10.04.4 works too, it's even bit faster but I would like to try to get the lightweight to work.

I have fair amount of technical experience, it's just been with Microsoft systems. That box DOES have the parameters I stated before anyone here starts wondering. IMHO the soft just doesn't understand the hardware.

When I started the project I thought this oldie can still do something, all I have to do is to through something lighter on it.

Maybe someone here can give me pointers as to what to check or other ideas. I have kind of grown to like Lubuntu, as strange as it may seem.

---

### Post by nwalkey on 2013-03-01
You have any reason for running a DE on it?? You don't really need one to run a web server and you can configure it so that you can do all your management for it remotely or even just ssh to it. If you install ubuntu server edition on it and it still lags then there is something weird with the hardware(maybe failing drive or bad stick of ram?) I wouldn't bother with a gui on that machine with that purpose unless you have other plans for it...

---

### Post by mastablasta on 2013-03-01
like nwalkey said. use server edition, install maybe webmin (GUI for server) and LAMP to it and then connect from other computer via SSH or via webmin (through browser) to it.

you do not need a desktop environment (DE) on a server. you never metnioned you graphics card. but anyway. if you really do want a desktop on this maschine you could try icewm or openbox for this mashcine. furthermore 10.04 support stops in April this year (no further security updates). you might want to think about it if you plan on attaching it on internet.

GUI server OS (oyu connect to server from another maschine via browser and a nice GUI) that might interest you:
Zentyal (Ubuntu based)
ClearOS (red hat based)

---

### Post by mapes12 on 2013-03-01
I've installed a full Ubu installation and had it running fast on a similar system. You didn't say if you installed the desktop or server variant of Lubu? How did you wipe your HDD ready for the installation? Are you dual booting? etc, etc.

---

### Post by nwalkey on 2013-03-01
Agreed with mastablasta, don't use 10.10, go with 12.04. It shouldn't run any slower if setup right and def go with server edition and if you need a gui use openbox, icewm, flux, or something like webadim/ispconfig3 to manage your server from outside. Also if you are running a gui make sure that you graphics are running in the right mode... use ```
sudo lshw -c display
``` to see what display driver is in use.

---

### Post by Micronta on 2013-03-01
Thanks to all.

I WAS going to get rid of LXDM too but only after everything else was done and configured as pure CLI is still a bit of pain for me. I know I'm not supposed to gripe but it is HARD. Wait a minute, did I gripe? :confused:

As for the new release, I had tried NEWER Ubuntu proper but that was slow too. Until the issues is resolved I see no particular reason to rush. And I see the whole project as a learning opportunity so in that sense the current version doesn't matter.

IMHO the problem is not with display driver but I could be wrong of course. When I CTL+ALT+F2 into a full screen mode and type, the same weird delay occurs. For example, say I intend to type "ls -la". I hit "l', it thinks for about a second and out pops an "l". I hit "s", it thinks a second and out pops an "s". I go on to type the space, -, another l, a and finally enter. It pauses, again for a second, and spits out the list. I thought maybe the GUI is a problem and tried to pass the "quiet splash text" to the kernel at boot to stop the LXDM from starting but no dice. Still slow.

But I will post the display driver results as asked when I get off and go home.

Thanks,

Micronta

---

### Post by mastablasta on 2013-03-01
> **Micronta said:**
> 
As for the new release, I had tried NEWER Ubuntu proper but that was slow too. Until the issues is resolved I see no particular reason to rush. And I see the whole project as a learning opportunity so in that sense the current version doesn't matter.


the problem is your CPU. Ubuntu desktop is not so light on resources. not anymore.

so you want to use a server and use a gui to find your way arorund it so you don't have to type everything. btu oyu want to access it form same mashicne not remotely (e.g. via browser and webmin).

do it it like this then:
install server edition
then install some widnows manager (for example icewm).

or if you have fast enough internet try this:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

this will give you just the basics. you can install LAMP (server for internet websites) via tasksel:
[https://help.ubuntu.com/community/Tasksel](https://help.ubuntu.com/community/Tasksel)

or you only install server edition and then type these commands:
```

sudo apt-get update
sudo apt-get install xorg xterm gdm icewm menu firefox gksu synaptic --no-install-recommends
	sudo service gdm start
```

---

### Post by zrdc28 on 2013-03-02
What you have is fine for a server, What you need to do is as suggested above, get the ubuntu server, install it with out a gui, you do not need a gui on a server anyway.
Have it hooked to the network and do an install, then just check ifconfig to find your ip address. Next ssh your ip from your laptop and do what you want.

---

