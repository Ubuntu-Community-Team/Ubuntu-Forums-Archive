---
title: "Do I need to / Should I re install"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Twizzle on 2008-11-26
I have installed Ubuntu 8.04 Server edition and and onto that Webmin, Zoneminder, Samba and then spent some time playing with an email / groupware server. I tried Citadel, Zimbra and finally settled on Zarafa. Then I installed getmail before removing it and using fetchmail. I am currently playing round with postfix (but thats another story....)

My questions really is, is Linux (specifically Ubuntu) better at removing programs / settings that Windows was?

Because I have installed and removed a fair bit on what is a web facing server, now that I have it (almost) working as I want, should I reinstall and setup just what I need? My concern is that I may have left something 'open' that would be a security issue, or unnecessarily left my system 'bloated'. If it was windows, I would reinstall no questions but that that tended to 'bloat' quite quickly. I followed guides on installing and removing, but being quite new to the Linux world, I don't really know where to look to see if something is still doing something that should not be...

Any help / suggestions would be appreciated.

---

### Post by Idefix82 on 2008-11-26
Ubuntu should uninstall most things without leaving any traces, provided you use the purge option which also gets rid of your personal settings. You can also use the command
```
sudo apt-get autoremove
```
to remove packages that were installed automatically as dependencies of something but are not needed any more since you uninstalled that something.

---

### Post by Titan8990 on 2008-11-26
Only tip I can give, if you used apt-get or Synaptic Package Manager then use the --purge flag to remove config files. Example for samba:


sudo apt-get remove --purge samba


will remove config files


sudo apt-get remove samba


may leave config files behind.

---

### Post by Twizzle on 2008-11-26
Thanks for the suggestions, unfortunately neither Citadel or Zimbra were apt-get installed, BUT I did follows the guide on the website to remove it. To check, should it be as easy as looking for any directories with that programs name and removing?

Also, are there any log files I can / should look at to see if one of them it trying to run something?

---

### Post by Titan8990 on 2008-11-26
Almost all your logs should be stored in the /var/log directory.


You can search to the if the processes are running:


ps aux | grep citedel


Assuming that is the name of the process...

---

