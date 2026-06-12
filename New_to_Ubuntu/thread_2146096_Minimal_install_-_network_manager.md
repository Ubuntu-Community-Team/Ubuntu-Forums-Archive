---
title: "Minimal install - network manager"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by pangeh on 2013-05-17
Hi,

Maybe a silly question but I installed ubuntu 12.04 minimal install over ubuntu server 12.04 for a basic gui using the sudo apt-get install --install-no-recommends ubuntu-desktop.

After installing I was configuring the network in /etc/network/interfaces. When browsing /etc I noticed that there was no network manager folder.

I just wanted to confirm that this is the case - that network manager is not installed with the no-recommends install of Ubuntu 12.04 or with Ubuntu server 12.04??

Thanks in advance for your kind help

regards
P.

---

### Post by Paqman on 2013-05-17
Yep, as you can see from the [list of packages in ubuntu-desktop]("http://packages.ubuntu.com/precise/ubuntu-desktop"), network-manager-gnome is a recommended package, not a dependency.

---

### Post by pootan on 2013-05-17
Gnome network manager pulls in quite a few packages so perhaps see if you can get wicd working first. I've installed it on my xubuntu-desktop --no recommends build and it works fine
[B][URL="https://help.ubuntu.com/community/WICD"]

WICD[/URL][/B]

---

