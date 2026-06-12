---
title: "Where would I find the Ubuntu desktop download"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by jacatone on 2008-05-03
I'm currently running Kubuntu 7.10 but wanted to learn Ubuntu as well. When I type "sudo apt-get install ubuntu desktop" in Konsole it's a 13+ hour download on my dialup connection. Where would I download just the ubuntu desktop .deb file? I have broadband at work and could just get it there. Thanks.

---

### Post by ad_267 on 2008-05-03
You could download the ubuntu CD and then add the cd to your list of package sources.

---

### Post by SunnyRabbiera on 2008-05-03
Yeh its actually a combo package, sorry.
The ubuntu desktop install tries to install many other files along with the updater, some stuff from gnome and all sorts of other junk.
but if you use a live CD then you can get what you need

---

### Post by aysiu on 2008-05-03
You need to download the Ubuntu Alternate CD (*not* the Desktop CD) and then paste these commands into the terminal in Kubuntu: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.dialup
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo mv /etc/apt/sources.list /etc/apt/sources.list.cd
sudo mv /etc/apt/sources.list.dialup /etc/apt/sources.list
```

---

