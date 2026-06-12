---
title: "Looking for a lightweight Linux distro with several requirements"
date: 2007-07-05
forum: Other OS Talk
---

### Post by Ebuntor on 2007-07-05
Hi,
 
 I'm looking for a lightweight Linux distro to run on hopelessly old PC.  
 The only purpose of this PC will be to run [a script]("http://ubuntuforums.org/showthread.php?t=492018") I've written that automatically prints forms selected by the user. The printer is an old HP Laserjet II.
 The PC should have a Pentium 2 120 Mhz, with a 500 MB HDD. I don't know how much memory but it probably won't be much.
 
 Requirements:  
 - The disto will have to be installed on the HDD.
 - Since it has to be absolutely foolproof booting the distro will have to be simple. (For example having to type &#8220;startx&#8221; in Slax is too complex but pressing enter when booting Knoppix is ok).  
 - The script will have to automatically start at startup and the disrto will need to have good hardware support for the printer. (I'd prefer Gnome or xfce)
 
 Of course I'd prefer (X)Ubuntu but I assume that is out of the question in this case unfortunately.
 I understand Knoppix' hardware detection is excellent but I read that installing on the HDD can be difficult.
DSL might an option but I dunno how it's printer support is or if I can easy configure it to run that script at startup.

 Which distros could I choose from? 

Thanks in advance

---

### Post by reckless2k2 on 2007-07-05
i would say that old hardware seems to work VERY well using slackware. if you are not that much of a hardcore linux person, slackware might be a little bit of a learning curve. other than that, damn small linux runs great on old old hardware. you can install it to a HD and can run on very little RAM.

---

### Post by Ebuntor on 2007-07-05
> **reckless2k2 said:**
> i would say that old hardware seems to work VERY well using slackware. if you are not that much of a hardcore linux person, slackware might be a little bit of a learning curve. other than that, damn small linux runs great on old old hardware. you can install it to a HD and can run on very little RAM.

I'd prefer to use DSL, I have some experience with it. But can it be configured to run that script at startup? If there's no GUI option could it be done via the terminal.

---

### Post by ThinkBuntu on 2007-07-05
Debian or Slackware should be great, as reliability will be vital to this task. Zenwalk would also be a suitable OS, although maybe with too many features for your purpose.

---

### Post by Ebuntor on 2007-07-05
> **ThinkBuntu said:**
> Debian or Slackware should be great, as reliability will be vital to this task. Zenwalk would also be a suitable OS, although maybe with too many features for your purpose.

Do you think Debian would really work? With such inferior hardware? It would be great if it worked but I kinda doubt it.

---

### Post by reckless2k2 on 2007-07-05
debian would be a good choice too. as far as running your script, you just have to make it executable and put it to run in the right place. that is a different topic getting your script to run. like using a bash script...etc..

you can place it in a few different places and make symbolic links...etc...and it'll be part of the boot process after everything has started if you wish. simple. 

all in all....you can use debian if you feel comfortable with it. you'd have to have a lightweight gui or none at all. DSL or slackware is probably best though.

---

### Post by Ebuntor on 2007-07-05
> **reckless2k2 said:**
> debian would be a good choice too. as far as running your script, you just have to make it executable and put it to run in the right place. that is a different topic getting your script to run. like using a bash script...etc..

you can place it in a few different places and make symbolic links...etc...and it'll be part of the boot process after everything has started if you wish. simple. 

all in all....you can use debian if you feel comfortable with it. you'd have to have a lightweight gui or none at all. DSL or slackware is probably best though.

Ok, thanks. :) I'm downloading Debian and DSL now. Otherwise I'll try Slackware.

---

### Post by Nikron on 2007-07-05
> **Ebuntor said:**
> Ok, thanks. :) I'm downloading Debian and DSL now. Otherwise I'll try Slackware.

Just make the system auto log a user on, and they automatically start x.  It's not hard to do at all.

---

### Post by energiya on 2007-07-05
[http://wiki.laptop.org/go/Minimal_Linux_distros](http://wiki.laptop.org/go/Minimal_Linux_distros)

---

### Post by Rumor on 2007-07-05
Arch Linux would be able to handle what you're after. Booting could be keystroke free. You'd start your WM/DE as a daemon or through initab or through .xinitrc. Set up auto-login and you'd be set.

[http://www.archlinux.org/](http://www.archlinux.org/)

I am running Arch on a P2/400 with 128 ram and it runs Gnome fine. It's no speed demon, mind you, but it has an uptime of several months and keeps on chugging along.

---

### Post by init1 on 2007-07-07
> **Ebuntor said:**
> Hi,
 
 I'm looking for a lightweight Linux distro to run on hopelessly old PC.  
 The only purpose of this PC will be to run [a script]("http://ubuntuforums.org/showthread.php?t=492018") I've written that automatically prints forms selected by the user. The printer is an old HP Laserjet II.
 The PC should have a Pentium 2 120 Mhz, with a 500 MB HDD. I don't know how much memory but it probably won't be much.
 
 Requirements:  
 - The disto will have to be installed on the HDD.
 - Since it has to be absolutely foolproof booting the distro will have to be simple. (For example having to type “startx” in Slax is too complex but pressing enter when booting Knoppix is ok).  
 - The script will have to automatically start at startup and the disrto will need to have good hardware support for the printer. (I'd prefer Gnome or xfce)
 
 Of course I'd prefer (X)Ubuntu but I assume that is out of the question in this case unfortunately.
 I understand Knoppix' hardware detection is excellent but I read that installing on the HDD can be difficult.
DSL might an option but I dunno how it's printer support is or if I can easy configure it to run that script at startup.

 Which distros could I choose from? 

Thanks in advance
It seems like you want X support, right?

---

### Post by Ebuntor on 2007-07-08
> **Rumor said:**
> 
[http://www.archlinux.org/](http://www.archlinux.org/)

I am running Arch on a P2/400 with 128 ram and it runs Gnome fine. It's no speed demon, mind you, but it has an uptime of several months and keeps on chugging along.

Sounds good, how much HD space does it take? There's only 500 MB on that old PC. I can't find the system requirements anywhere on the ArchLinux website.

I think I'll just buy a cheap 4 or 5 GB HD from ebay, 500 MB is just not enough.

> **init1 said:**
> It seems like you want X support, right?

X support? Do you mean that X is installed on a distro? :confused:

---

### Post by Rumor on 2007-07-08
> **Ebuntor said:**
> Sounds good, how much HD space does it take? There's only 500 MB on that old PC. I can't find the system requirements anywhere on the ArchLinux website.

I think I'll just buy a cheap 4 or 5 GB HD from ebay, 500 MB is just not enough.



I think the base system is under 200 MB if you change the default partition sizes and then  just go with all the default packages during the install. But you're probably better off getting a cheap used drive.

---

