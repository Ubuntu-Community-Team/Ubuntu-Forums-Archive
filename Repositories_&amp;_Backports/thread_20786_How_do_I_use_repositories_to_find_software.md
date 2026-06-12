---
title: "How do I use repositories to find software?"
date: 2005-03-18
forum: Repositories &amp; Backports
---

### Post by audax321 on 2005-03-18
Hello,

    Let me start off by saying that I've been using SuSE for two years and have never used APT for anything. I just installed warty on my laptop and was very impressed by the OS itself, but APT is driving me insane. With SuSE it was possible to add a few sources (from SuSE as well as other users who built their own RPMs for SuSE) in YaST and then practically upgrade your entire computer (e.g. SuSE provides KDE and Gnome upgrades) and find up-to-date RPMs for practically anything using search engines like [http://rpm.pbone.net](http://rpm.pbone.net).

In Ubuntu (I'll be installing Kubuntu 5.04-Preview later today) it seems like the software is older and I have no clue how to search for repositories that contain the software that I want to install. For example, I was trying to install something yesterday (don't remember what it was though) and I couldn't because one package that it depended on was out of date on the server. I keep seeing people using Debian repositories, but at the same time Ubuntu says that this is bad (which makes sense). But where else should I get the software from? Is there a Ubuntu software search engine that will find repositories that contain the software I need? Just searching google for repositories seems kind of time consuming.

If I can just get used to installing software from APT, I might finally have a reason to scrap my SuSE installation for something more streamlined like Ubuntu.

Thanks for any help.  ](*,)

---

### Post by bored2k on 2005-03-18
System Admin > Synaptic [upper panel]

There click settings > repositories > settings > show disabled > checkmark on everyone disables > then clic add > check everything there .

Save, it will reload sources, and you got thousands of apps to install here .

The whole debian aim is to avoid searching for stuff in rpm bone for example [I used Mandrake and AuroX, ive used rpmbone;)]. There you will find supported packages...thousands and thousands of them with resolving dependencies by theirselves.

There are other sources, but as you grow l33t you will need them ;) .

---

### Post by audax321 on 2005-03-18
> **bored2k]System Admin > Synaptic [upper panel]

There click settings > repositories > settings > show disabled > checkmark on everyone disables > then clic add > check everything there .

Save, it will reload sources, and you got thousands of apps to install here .

The whole debian aim is to avoid searching for stuff in rpm bone for example [I used Mandrake and AuroX, ive used rpmbone said:**
> . There you will find supported packages...thousands and thousands of them with resolving dependencies by theirselves.

There are other sources, but as you grow l33t you will need them ;) .

Do you mean, Settings > Repositories > (Check everything in the repository list) > Click OK?

There is no settings button for me after I go from Settings > Repositories. Also I already enabled all the universe and multiverse repositories if that was what you were getting at. Probably should have mentioned that earlier ;) 

I understand how repositories and installing applications work, I just have no idea where to get more repositories from. I guess what I should be asking is what are some good repositories, that will be around between upgrades of Ubunto for things like Java, multimedia codecs, and KDE applications etc.

Thanks. I guess I'm a bit too picky :)

---

### Post by bored2k on 2005-03-18
> **audax321]Do you mean, Settings > Repositories > (Check everything in the repository list) > Click OK?

There is no settings button for me after I go from Settings > Repositories. Also I already enabled all the universe and multiverse repositories if that was what you were getting at. Probably should have mentioned that earlier  said:**
> 
 Ubuntuguide.org

Java :
deb [http://ubuntu.tower-net.de/ubuntu/](http://ubuntu.tower-net.de/ubuntu/) warty java
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
> sudo apt-get install sun-j2re1.5debian

MPlayer, Video Streaming, Windows avi/divx/etc codecs, Avidemux and more:
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main
[QUOTE]sudo apt-get install mozilla-mplayer w32codecs


There is no place for other sources. Since we can use the Debian repositories every author of an applications might point to his special repository link. For example xfce.org has its own updated source link, Enlightenment, etc .

---

