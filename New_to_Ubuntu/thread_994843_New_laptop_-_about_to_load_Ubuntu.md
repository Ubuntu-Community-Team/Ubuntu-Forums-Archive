---
title: "New laptop - about to load Ubuntu"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by figi22 on 2008-11-27
I just got a new laptop for my mother, and I'm going to load up Ubuntu for her to use (she only uses the internet and hates all Windows antivirus and firewall programs).

A couple of questions:

What is the best Flash plugin to use for Firefox?   E.g. one that works well with BBC websites.

The laptop has a webcam - will I be able to get this working using Ubuntu?   I'd like her to be able to use Skype with video.

---

### Post by MrWES on 2008-11-27
> **figi22 said:**
> I just got a new laptop for my mother, and I'm going to load up Ubuntu for her to use (she only uses the internet and hates all Windows antivirus and firewall programs).

A couple of questions:

What is the best Flash plugin to use for Firefox?   E.g. one that works well with BBC websites.

The laptop has a webcam - will I be able to get this working using Ubuntu?   I'd like her to be able to use Skype with video.

Ibex 8.10 comes with flash 10

Also, I would consider a separate /home partition. Makes fresh installs of future versions easier; It'll allow you to keep all you configuration files..

Bill

---

### Post by figi22 on 2008-11-27
I installed ubuntu 8.10 (is that the same as Ibex?) on an old brick, and I still had to install some plugin for Firefox.

Please can you give a wee bit more info on partitioning the disk?   I was going to do that anyway to keep Windows in case of disaster.  It has 250GB and she won't use anything like that, so there's plenty of room.

---

### Post by mapes12 on 2008-11-27
> I installed ubuntu 8.10 (is that the same as Ibex?)Yes it is.

> Please can you give a wee bit more info on partitioning the disk? I was going to do that anyway to keep Windows in case of disaster. It has 250GB and she won't use anything like that, so there's plenty of room.

This is how to plan your partitions in Ubu: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

then use the menus on the left of the pstchocats site to help you out with anything else you may need.

If Firefox finds media where additional plugins are required it will tell you and present download options. My understanding is that 8.10 has been configured with BBC streaming video in mind, but anything that requires iPlayer such as streaming radio is not supported as yet (or at least I still can't get it to play....if you can please PM me).

Mark

---

### Post by damis648 on 2008-11-27
> **MrWES said:**
> Ibex 8.10 comes with flash 10

It does in fact not. The best option is Flash 10 straight from Adobe (get the Ubuntu DEB): [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

Also, webcams in laptops usually work OTB, so I would not worry about that. As far as Skype goes, just [enable the medibuntu repos]("https://help.ubuntu.com/community/Medibuntu") and do
```
sudo apt-get install skype
```

And yes, 8.10 is Intrepid Ibex.

EDIT: Also, for partitioning, the Installer will guide you through that. There is a step which asks you what you want to do. Just select to resize the Windows partition and move the slider to your liking.

---

### Post by figi22 on 2008-12-02
Well, what happened in the end was that I tried the suggested partitioning, but there was an error and that failed.  So I ended up just loading up on the entire disk.   I still have the Vista disks if I need to go back and reload, but why would I want to do that?   Even 2 minutes of Vista was enough to drive my crazy.

I got the Flash from Adobe - I hadn't understood what nonfree meant when I went to put it on another machine, but I get what that means now.

The webcam and Skype are working fine - I just had to adjust sound settings.

The only thing I have failed at is loading iTunes.   I read a magazine article that suggested this was easy with WINE 1.0 and iTunes 7.2, but it proved otherwise, and I've now removed the entire WINE installation to clean up the computer from the repeated installations of Quicktime and iTunes - I'd forgotten how much trouble that had caused me on my old PC, having been a Mac user for some time.  Made me feel like Apple are as bad as Microsoft.   I suppose they are...

---

