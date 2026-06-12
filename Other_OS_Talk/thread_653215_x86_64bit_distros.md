---
title: "x86_64bit distros"
date: 2007-12-29
forum: Other OS Talk
---

### Post by Elvish Legion on 2007-12-29
I'm in need on a 64bit distro, and before you say ubuntu, they 64bit ubuntu has been really unstable on me, crashing and freezing a lot (the 32 bit too) I dunno what changed in the new release but somthing did.

I'm mostly toying with either opensuse or maybe fedora, but I'm open for suggestions.

So fire away with suggestions, hopefuly the next ubuntu relase is more stable....

Hows debian's 64 bit offering?

---

### Post by ditsch on 2007-12-29
Maybe you should take a look at [Arch Linux]("http://www.archlinux.org/").

---

### Post by fwojciec on 2007-12-29
> **ditsch said:**
> Maybe you should take a look at [Arch Linux]("http://www.archlinux.org/").

As much as I like Arch ... ;)

The 64bit version of Arch is designed as pure 64bit and while it is possible to achieve multilib environment on it (needed for flash, skype and so on) it is not officially supported and requires quite a lot of manual configuration.  Go for it if the prospect doesn't intimidate you but otherwise stick to something that provides a multilib environment by default.

---

### Post by Elvish Legion on 2007-12-29
Guess I'll give arch a try, seems their forums are pretty friendly (except on the eyes)

Thanks

---

### Post by benuski on 2007-12-29
Debian's 64 bit is good, and has support for flash through nspluginwrapper.  Just remember, if you try it, that its called amd64, not IA-64.

---

### Post by miggols99 on 2007-12-30
I haven't had any problems setting up flash on 64bit arch. All I had to do was install nspluginwrapper-flash from the AUR. I'm getting a few problems with it, and so are 32bit users, so it's Adobe's fault, not 64bit.

---

### Post by fwojciec on 2007-12-30
No problems with flash here - using 32 bit Arch + firefox.  I haven't had a browser crash since ages.  Occasionally it will get stuck for 20 seconds or so, mostly on ubuntuforums.org actually, but it always recovers fine by itself.

---

### Post by argie on 2007-12-31
Fedora FC8 perhaps?

---

### Post by Elvish Legion on 2007-12-31
Well so far I got arch installed, couldnt get my wifi working after a long day of working, thats a big no go for me.

So I'm looking at installing ubuntu/debian (minimal and building from there) Open Suse 10.3, Fedora Core 8...


Any other suggestions? I really liked arch it just had a couple of things right now that really got me.

---

### Post by fwojciec on 2007-12-31
> **Elvish Legion said:**
> Well so far I got arch installed, couldnt get my wifi working after a long day of working, thats a big no go for me.

So I'm looking at installing ubuntu/debian (minimal and building from there) Open Suse 10.3, Fedora Core 8...


Any other suggestions? I really liked arch it just had a couple of things right now that really got me.

It's too bad that you didn't have the patience to fix those minor problems you were having.  Your problem with wifi was easily fixable, I've looked at your post on Arch Forums and it seems that you were using "wlan0" instead "ath0" to identify the wireless card.  Oh well...

---

### Post by Elvish Legion on 2007-12-31
> **fwojciec said:**
> It's too bad that you didn't have the patience to fix those minor problems you were having.  Your problem with wifi was easily fixable, I've looked at your post on Arch Forums and it seems that you were using "wlan0" instead "ath0" to identify the wireless card.  Oh well...

So its just a matter of chanign wlan0 to ath0?  And then of course installing a wifi radar?

The pacman front ends...any like syn? I like to be able to search for the package if I don't know its name

---

### Post by fwojciec on 2007-12-31
> **Elvish Legion said:**
> So its just a matter of chanign wlan0 to ath0?  And then of course installing a wifi radar?

The pacman front ends...any like syn? I like to be able to search for the package if I don't know its name

Not sure if the interface name is the only thing that's wrong with the configuration, but in either case it should be easy to figure out - I also have the same wireless card as you, so I can post my working configuration in the thread on Arch forums - if you're interested - that should let you get the wireless working.

The most popular pacman front end is a little app called [yaourt]("http://www.archlinux.fr/yaourt-en/") - it lets you search both the official repos and the aur repository and automates install/build process.  It'll return all hits that match provided keyword - it matches against package name and package description.  You can also search for packages using arch website/aur website.

I don't use wifi radar, but it should be easy to install - here is the [wiki page]("http://wiki.archlinux.org/index.php/Wifi_Radar") for it; alternatively you could try [wicd]("http://wiki.archlinux.org/index.php/Wicd") for example.  Arch is all about choices.

You will run into questions and problems in your first days with Arch, but you can always find help on Arch forums, even if things move a little slower there than here on Ubuntu forums.

---

### Post by Elvish Legion on 2007-12-31
> **fwojciec said:**
> Not sure if the interface name is the only thing that's wrong with the configuration, but in either case it should be easy to figure out - I also have the same wireless card as you, so I can post my working configuration in the thread on Arch forums - if you're interested - that should let you get the wireless working.

The most popular pacman front end is a little app called [yaourt]("http://www.archlinux.fr/yaourt-en/") - it lets you search both the official repos and the aur repository and automates install/build process.  It'll return all hits that match provided keyword - it matches against package name and package description.  You can also search for packages using arch website/aur website.

I don't use wifi radar, but it should be easy to install - here is the [wiki page]("http://wiki.archlinux.org/index.php/Wifi_Radar") for it; alternatively you could try [wicd]("http://wiki.archlinux.org/index.php/Wicd") for example.  Arch is all about choices.

You will run into questions and problems in your first days with Arch, but you can always find help on Arch forums, even if things move a little slower there than here on Ubuntu forums.

Well I'm going to give it another shot, I gotta get some mouts for my router and its eth wires (thats the main reason for not wanting to wait, the eth cable cross our hall way and the girlfriend didn't like it)

---

### Post by fwojciec on 2007-12-31
OK, I've posted my network config in your thread on Arch forums - it's not a wifi-radar or wicd config -- I only connect to a single network so I don't need those -- it should work nevertheless.  Hopefully it'll help you get rid of that cable from the hallway at least :D

---

