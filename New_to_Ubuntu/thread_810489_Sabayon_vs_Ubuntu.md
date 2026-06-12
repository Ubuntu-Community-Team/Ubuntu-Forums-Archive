---
title: "Sabayon vs Ubuntu"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by Mr dirt on 2008-05-28
I am coming from sabayon which I have been using for about a month and while I love all the eye candy it has preinstalled I am somewhat upset that many times I cant update my system without everything getting bogged down or not working at all. I am not sure if its a problem with Gentoo or what and am wondering how Ubuntu fares in comparison.I have a copy of Hardy so I am contemplating if this will be an easy transition. To people that have or at least tried both what are your opinions on this comparison? Which is more user friendly, and which is more stable OS? I am guessing Ubuntu is more stable because its been around much longer and is more popular but is it more user friendly, what do you guys think?

---

### Post by Vadi on 2008-05-28
You're free to boot into the LiveCD and try Ubuntu out, without installing it. It'll be quite slow from the cd though.

---

### Post by quelx on 2008-05-28
I've used Gentoo extensively and still do, it is a great distribution, but I've found myself using it for special projects only (recording boxes, routers, specialized servers) or when I wanted complete control over the services it ran.  For a desktop system and full blown http/smtp/mysql servers I've found Ubuntu or Centos a better fit because updates don't break things the way the do in Gentoo (admittedly I'm at fault for some of those breaks, but Ubuntu/Centos have been more forgiving)

---

### Post by Mr dirt on 2008-05-28
Easy to get used to and upgraded and running? I tried the live cd and it doesnt respond well and you cant really understand and OS unless you start really playing with it. Is it more solid, robust, stable? How about getting programs to install  like, compiz, wine, open office, is that a drag as well?

---

### Post by quelx on 2008-05-28
Ubuntu is cake.  Most configuration can be done from the graphical interface, and underneath is all the goodies any other distribution has.

[https://help.ubuntu.com/](https://help.ubuntu.com/) details the *Ubuntu Way* for managing systems (installing software and updates and more).

The Live CD is slow because it's running off the CD.  A hard drive installation is much faster.

---

### Post by Golem XIV on 2008-05-28
> **Mr dirt said:**
> Easy to get used to and upgraded and running? I tried the live cd and it doesnt respond well and you cant really understand and OS unless you start really playing with it. Is it more solid, robust, stable? How about getting programs to install  like, compiz, wine, open office, is that a drag as well?

Well, it will obviously be slower since it's running off of the CD.  No idea if it's any more stable/robust/solid than Sabayon, but from the distros I tried (and I'm a Linux newb) I found it very easy to get into.

Compiz and OpenOffice come pre-installed.  Wine can be installed with **sudo apt-get install wine**; include the Wine repository if you want the latest and greatest.

From what I've heard and read, software installation is a lot faster than in Gentoo.  From what I've seen, it's a lot faster and more intuitive than Mandriva or OpenSuSE.

---

### Post by robalcorn on 2008-05-28
I use to run Sabayon myself and enjoyed it alot. In regards to optaining software you mentioned its easier and much faster with Ubuntu.

---

### Post by Mr dirt on 2008-05-29
> **Golem XIV said:**
> Well, it will obviously be slower since it's running off of the CD.  No idea if it's any more stable/robust/solid than Sabayon, but from the distros I tried (and I'm a Linux newb) I found it very easy to get into.

Compiz and OpenOffice come pre-installed.  Wine can be installed with **sudo apt-get install wine**; include the Wine repository if you want the latest and greatest.

From what I've heard and read, software installation is a lot faster than in Gentoo.  From what I've seen, it's a lot faster and more intuitive than Mandriva or OpenSuSE.
When you say compiz and Open comes preinstalled can you just open ccsm upon installation? If not what commands do you need to enter to get it up and running?

---

### Post by shifty_powers on 2008-05-29
ccsm is not preinstalled, you just have three buttons to choose from, none, basic and advanced iirc.

but then all you do is

```
sudo apt-get compizconfig-settingsmanager
```

in the terminal, or go on synaptic ;)

---

### Post by Golem XIV on 2008-05-29
> **Mr dirt said:**
> When you say compiz and Open comes preinstalled can you just open ccsm upon installation? If not what commands do you need to enter to get it up and running?

Compiz comes pre-installed, but ccsm does not.  No idea why, maybe ccsm is not part of the original package.

You can install ccsm through the Synaptic package manager or via terminal: ```
sudo apt-get install compizconfig-settings-manager
```
It takes a couple of minutes to download and install.  Once it is finished it will appear on the System -> Preferences menu as "Advanced Desktop Effects Settings".

OOo is also pre-installed - word processor, spreadsheet, presentation manager, drawing program and formula generator.  OOo database has to be installed separately.

---

### Post by Mr dirt on 2008-05-29
Thanks guys I did it through synaptic. Everything is looking good so far but only one problem. When I open terminal and put in a su command it asks me for a password I type one that I know works for other apps in Ubuntu (the one I set up upon installation) and it dont work. What is the problem here?

---

### Post by jimrz on 2008-05-29
in ubuntu, you need to use "sudo" rather than "su"

---

### Post by Mr dirt on 2008-05-29
Why when I enter su it asks me to enter a password that it eventually does not take?

---

### Post by quelx on 2008-05-29
**su** tries to change to the root user but in Ubuntu the root account is disabled

**sudo** on the otherhand just elevates the current users priveledges

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by buntunub on 2008-05-30
> **quelx said:**
>   For a desktop system and full blown http/smtp/mysql servers I've found Ubuntu or Centos a better fit because updates don't break things the way the do in Gentoo (admittedly I'm at fault for some of those breaks, but Ubuntu/Centos have been more forgiving)

This is classic for someone coming from Gentoo/Sabayon. I know because I also migrated over from there myself. It is quite typical for devs from those distro's to blame the users for problems that crop up. The community tends to take this tack as well, creating quite the cycle of cynicism and negativity. Hate to say these things, as Gentoo really was once a truly great Distro. Things change. For this reason, amongst a long list of others, I would never recommend Gentoo or Sabayon to anyone. Stick with Ubuntu or especially Debian for rock solid stability and well run Repo's.

---

### Post by Mr dirt on 2008-05-30
Yea man Ubuntu is really awesome so far. Thanks for all the comments and recommendations, I had this thing up and running in no time. Synaptic was real easy to use and I just need some more time with it before I can migrate almost totally from xp, thanks!

---

