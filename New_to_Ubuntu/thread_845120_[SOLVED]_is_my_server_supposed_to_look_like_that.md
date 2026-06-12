---
title: "[SOLVED] is my server supposed to look like that?"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by TriedAndTested on 2008-06-30
[COLOR="Blue"]Hi,

I previously installed Ubuntu desktop, worked very well.

I have now installed Ubuntu server from ISO image and when it started it only has a command line interface. Is this correct?
I've tried the docs but most refer to GUI stuff.
Do I have to start GNOME manually? Do I need to use GNOME at all?

My aim is to run a web server/site on this server. 

Thanks,
Billy.[/COLOR]

---

### Post by overdrank on 2008-06-30
> **TriedAndTested said:**
> [COLOR="Blue"]Hi,

I previously installed Ubuntu desktop, worked very well.

I have now installed Ubuntu server from ISO image and when it started it only has a command line interface. Is this correct?
I've tried the docs but most refer to GUI stuff.
Do I have to start GNOME manually? Do I need to use GNOME at all?

My aim is to run a web server/site on this server. 

Thanks,
Billy.[/COLOR]

HI and welcome, yes a sever edition is command line only
if you would like a GUI you can install it with the command 
```
sudo apt-get install ubuntu-desktop
```
or replace ubuntu with xubuntu for the XFCE desktop and so on.

---

### Post by WRDN on 2008-06-30
The server edition is command line only, as had been stated, and many would argue, on a server, the CLI (Command Line Interface) is the quickest way of performing tasks.
If you want a GUI though, you should NOT install GNOME as it isn't lightweight- its possible but not recommended. Instead, you should install a more lightweight desktop environment such as [Fluxbox]("http://fluxbox.sourceforge.net/") or [LXDE]("http://lxde.org/")

---

### Post by TriedAndTested on 2008-06-30
Thanks for quick responses.
Is the ubuntu desktop too fat? Is ubuntu desktop GNOME? or do I need the thin desktops mentioned, Fluxbox or LXDE.

Thanks,
Billy.

---

### Post by overdrank on 2008-06-30
> **TriedAndTested said:**
> Thanks for quick responses.
Is the ubuntu desktop too fat? Is ubuntu desktop GNOME? or do I need the thin desktops mentioned, Fluxbox or LXDE.

Thanks,
Billy.

Hi and that is up to your system specs and preference. :)

---

### Post by ibutho on 2008-06-30
> **TriedAndTested said:**
> Thanks for quick responses.
Is the ubuntu desktop too fat? Is ubuntu desktop GNOME? or do I need the thin desktops mentioned, Fluxbox or LXDE.

Thanks,
Billy.

The default desktop is GNOME. Its not that its too fat, but you will end up with lots of desktop oriented applications that have no place on a server.

---

### Post by WRDN on 2008-06-30
> **overdrank said:**
> Hi and that is up to your system specs and preference. :)

It is true that if you have a high spec machine, you could run an environment such as GNOME. However, often a server will be left running unattended for long periods of time. Thus, it is a waste of resources to use GNOME rather than a more lightweight environment, regardless of system specs.

If I had to choose, I would recommend LXDE, but it would be even better to learn the CLI instead, as it would allow for any problems to be found rapidly (rather than being hidden by a GUI).

---

### Post by JillSwift on 2008-06-30
Depends on what you're doing with your server. If it's a production machine seeing real use, stick with the CLI or pick a very light desktop (Xfce, etc).

My server sees little traffic, so I want ahead and installed my fave desktop, KDE. But, I also removed KDM so that it presents me with a text login, and I have to use startx to get to KDE after I log in. This lets me choose how much of the server's resources I'm going to take up when working (ok, playing) on it.

---

### Post by Canis familiaris on 2008-06-30
If it is indeed a server, and you wish that GUI is installed, I would seriously recommend that you  to try editing the default runlevel in the   /etc/inittab file so that you boot to a command line by default.

[http://en.wikipedia.org/wiki/Runlevel](http://en.wikipedia.org/wiki/Runlevel)

If you wish to start the GUI, just type:
```
startx
```

---

### Post by Inxsible on 2008-06-30
First and foremost, you need to decide what you are going to use that compter for. If it is going to be a server, then not having a GUI is the best way. Why waste resources by instantiating apps that you are not going to use.

If this is a desktop which you are going to use for web browsing and such, you need to install the desktop version which is more aligned towards desktop usage.

Gnome - IMO, is fat. the default ubuntu-desktop metapackage, which points to all the apps to be installed is even worse.

If you want a minimalist desktop, have a look at my signature where a bunch of lightweight Window managers and apps are listed. You can build your own system on debian core or ubuntu minimal.

LXDE - is light definitely. but it is still in development and there are a lot of features still missing.

---

### Post by hyper_ch on 2008-06-30
if you really want to operate a server you don't need a gui... it doesn't help you at all at setting up the server...

however if you want to use it as desktop machine which server ability then you mgiht want to install a gui.

For setting up a complex webserver have a look at [http://www.howtoforge.com](http://www.howtoforge.com) --> search for perfect ubuntu hardy server

---

### Post by TriedAndTested on 2008-06-30
Hi,

Thanks to everyone for their quality advice. :D
Its going to be a pure server. I already have another comp for home use (this one).

I will stick with CLI as as I want best performance.

I just realised I installed version 6.whatever. Moving on up to 8.04, complete reinstall rather than upgrade because I forgot which password I used already LOL. Too many passwords to remember.

Thanks again,
Billy.

---

### Post by jamesrfla on 2008-06-30
I just use Ubuntu 8.04 Desktop Edition and install all my server stuff after. It doesn't take much time to install server components in Linux. Both of the editions are basically the same except the server edition has a command line and uses less resources. The desktop edition uses more resources and comes with more stuff and a GUI.

---

