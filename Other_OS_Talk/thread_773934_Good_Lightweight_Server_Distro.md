---
title: "Good Lightweight Server Distro?"
date: 2008-04-29
forum: Other OS Talk
---

### Post by amtur_poet on 2008-04-29
I'm looking for a server distro for my school. I want it to have an easy GUI, but to still be fast, running at or under 128 MB. I'm going to have it being run as a thin client.

---

### Post by twright on 2008-04-29
you could use bog standard ubuntu LAMP server with webmin (a complete web based server administration suite)

if you want a gui on the server you could use the fluxubuntu-desktop package as a base

---

### Post by depele on 2008-04-29
do I understand you?

Do you want to run your server as a thin client?

may be you have to tell a bit more?

grtz

---

### Post by Twitch6000 on 2008-04-29
by 128mb do you mean ram or hard drive.Sorry its just some people still have that low of specs lol.

---

### Post by amtur_poet on 2008-04-29
I'm referring to the Ram. Well, The computers in my school are currently nonstandard. Some have 1 GB of memory and run windows XP, and some are really old and run Windows 98, and I don't know how much memory those have. And there are some computers in the building that have 2 GB of ram. The most-used ones, however, are the first 2 mentioned.

---

### Post by Twitch6000 on 2008-04-29
I would suggest debain then.Probably stable.

---

### Post by stream303 on 2008-04-29
Say no more - Grab an Ubuntu Server install image.  Then, add just a dash of xorg, xdm, and some lightweight apps and you're in business, wether you want to use it specifically as a server, or just a very lightweight desktop machine.

Some great details here.  I found it to be a lot of fun.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by jrusso2 on 2008-04-30
I would probably go with Debian also with a light weight gui like ICEWM or Fluxbox if you have to use a gui.

---

### Post by regomodo on 2008-04-30
Debian Stable - if you need a minimal gui install grab the xfce version. It has very few apps and services installed/running by default so by using rcconf can strip it down to a cli system (which is what i'd do)

---

### Post by notwen on 2008-04-30
+1 Debian Etch.  I run a very trimmed down version for my home file server.  Just do a netinstall of Etch, add what services you're wanting and drop XFCE or a lighter DE/WM on top.  Very stable, secure distro and easy to customize.  Best of luck w/ this.  =]

---

