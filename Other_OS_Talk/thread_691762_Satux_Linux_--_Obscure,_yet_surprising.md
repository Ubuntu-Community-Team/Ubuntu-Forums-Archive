---
title: "Satux Linux -- Obscure, yet surprising"
date: 2008-02-08
forum: Other OS Talk
---

### Post by bwhite82 on 2008-02-08
I recently discovered a Debian-based distro called [Satux]("http://www.satux.org.br/").

Per the [Wiki page]("http://en.wikipedia.org/wiki/Satux"):

> Satux is a 100% Brazilian Linux distribution. It was and is mainly developed by the Institute of Technology JRSC (iTJRSC), establishment of research and development with it's headquarters in Manaus and São Paulo.

The Satux has the philosophy to practicity, intensifying the user experience in interface and usability, reaching out (or even surpassing) the simplicity of use of the Microsoft Windows operating systems.

The Satux can be downloaded from the Internet, through [http://www.satux.org.br/](http://www.satux.org.br/), and also can be acquired in the purchase of CCE Info, Bluesky, Nextera and Acteon Digital desktop and laptop computers.

And yes, they've delivered on that promise to be Windows-esque. Even if you despise Windows, you have to admit that they have done good at mimicking it when, upon install, you are presented with an ala Windows type graphical installer which gives you no options whatsoever. I mean none. Not what disk (let alone partition) to install to, no username and password entry, nothing except accepting license terms (which I could not read -- Portugeuse). All I had to do was click next 3 times and was installed. Had I not been installing this with VirtualBox, this would have been scary, because it would have formatted my entire disk.

At any rate, all of the usual suspects are present, customized bootsplash, gdm, and desktop (screenshots attached). Like I said, no users were created upon install, so you login (automatically) as root. The gnome-terminal app is missing from the menu, so I had to open it via ALT+F2. It has its own repos, which from what I can surmise are based off of Debian Etch.

It did VERY well at detecting my hardware: Sound, video, wireless all were detected and configured upon first boot. All in all, this is an excellent distro targeted toward Windows users who still want to use Windows but don't want the added garbage that accompanies it (spyware, adware, viruses). Satux makes them feel right at home. I would recommend this distro to: Ages 60+ and Ages 10- and those who can't quite leave that familiar Windows interface behind.

Edit: I've managed to get most of it into English now, some of the gnome customizations (made by Satux) weren't changed however nor has the firefox ui.

---

### Post by HappyFeet on 2008-02-09
Ok

---

### Post by RAV TUX on 2008-02-09
> **Soldierboy said:**
> I recently discovered a Debian-based distro called [Satux]("http://www.satux.org.br/").

Per the [Wiki page]("http://en.wikipedia.org/wiki/Satux"):

And yes, they've delivered on that promise to be Windows-esque. Even if you despise Windows, you have to admit that they have done good at mimicking it when, upon install, you are presented with an ala Windows type graphical installer which gives you no options whatsoever. I mean none. Not what disk (let alone partition) to install to, no username and password entry, nothing except accepting license terms (which I could not read -- Portugeuse). All I had to do was click next 3 times and was installed. Had I not been installing this with VirtualBox, this would have been scary, because it would have formatted my entire disk.

At any rate, all of the usual suspects are present, customized bootsplash, gdm, and desktop (screenshots attached). Like I said, no users were created upon install, so you login (automatically) as root. The gnome-terminal app is missing from the menu, so I had to open it via ALT+F2. It has its own repos, which from what I can surmise are based off of Debian Etch.

It did VERY well at detecting my hardware: Sound, video, wireless all were detected and configured upon first boot. All in all, this is an excellent distro targeted toward Windows users who still want to use Windows but don't want the added garbage that accompanies it (spyware, adware, viruses). Satux makes them feel right at home. I would recommend this distro to: Ages 60+ and Ages 10- and those who can't quite leave that familiar Windows interface behind.

Edit: I've managed to get most of it into English now, some of the gnome customizations (made by Satux) weren't changed however nor has the firefox ui.

Nice find, Thanks for sharing. ;)

Here is their webpage translated into English by Google:
[URL="http://translate.google.com/translate?hl=en&sl=pt&u=http://www.satux.org.br/&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3Dsatux%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DBbn"]
Satux [/URL]

---

### Post by seanc7 on 2008-02-09
It logs you in as root by default? Oi... Security problems just waiting to happen.

A part of Linux's security and Unix-based systems in general is the user doesn't run as root.

They emulated Windows too much.

---

### Post by bwhite82 on 2008-02-10
Yeah, I wouldn't use the distro myself. Could be good for newbies though, anything is better than Windows (IMO). Thanks for the translation page, RAV.

-Cheers

---

### Post by r4ik on 2008-02-10
I tried to download it and my Ram went straight up to max 1.5 G
My CPU would not go below 90 and my fan went crazy,
Anybody else noticed this little annoyers ?

---

### Post by SunnyRabbiera on 2008-02-10
> **seanc7 said:**
> It logs you in as root by default? Oi... Security problems just waiting to happen.

A part of Linux's security and Unix-based systems in general is the user doesn't run as root.

They emulated Windows too much.

yeh sure looks like it...

---

### Post by riverlinux on 2008-02-26
Hi all,

I have tried "Satux" and it looks great. By the way, it logs you as satux not as root user [-X ... 

;) See you...

---

### Post by revertex on 2008-03-22
I didn't tried it yet, but it's developed to run on some el cheapo laptops sold in brazil by cce, acteon and others.

Maybe it's tailored to run better on some specific hardware.

I don't understand why instead reinvent the wheel they don't develop their customized interface to run on top a big distro like ubuntu.

It will benefit a lot more people, and will make their  distro much more reputable.

The mix of kde  vistaish icons with old gnome ones is really bad taste, maybe they can hire Everaldo to draw a new ones.

apropos, does satux means "satan linux" or something like this?

This name kinda freak me out.

---

### Post by jseiser on 2008-03-24
> **revertex said:**
> I don't understand why instead reinvent the wheel they don't develop their customized interface to run on top a big distro like ubuntu.


They are based of a large distro, debian.  They enjoy the same upstream as ubuntu.

---

