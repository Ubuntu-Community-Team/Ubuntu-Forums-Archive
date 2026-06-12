---
title: "[SOLVED] bypass login screen, add startup programs"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by quraid on 2008-07-06
[B]EDIT: whoops. sorry. after some tinkering i just found out how. both of my questions are now answered. the OS is really quite userfriendly. i was worried that i would have to create scripts and stuff for them.

i do however have another issue i need help with.
[/B]



Hi guys
my very first post here. i switched to linux 2 days ago.
vista finally drove me mad and a friend convinced me to try ubuntu instead of going back to xp. it has been a mixed experience so far. while i find the OS on the whole much peppier and better than vista, i do miss many of my windows softwares.

anyway, i have some questions that i hope the community here will be able to help me with. while i considered myself a beast on xp, remember, i am an absolute nub when it comes to linux, so don't scare me off please.

i use this computer of mine mainly for downloading stuff. we have a lot of powercuts here and everytime i would set something for download during the night or while i was at work, after a powercut the downloads sto.
in xp, to work around this, firstly i set my bios to boot automatically after every cold shutdown. i had put utorrent and other download softwares in the startup. so say there is a powercut when i am away at work. computer switches off. power comes back and computer boots itself. xp starts and the startup programs load up and my downloads start merrily afterwards.

in ubuntu my first barrier is the login screen. yes, yes, i know it is the cornerstone of security in linux. but i am the only user on this machine and i really don't need anything other than 1 account. if there is a way to autologin or to bypass the login screen, please let me know.

secondly, does ubuntu have anything similar to xp's startup (startup folder in the start menu)?

anyway, thank for reading so far. i know i love using a sentence where a sentence might suffice.

regards.

---

### Post by aysiu on 2008-07-06
For automatically logging in, try this:
[https://help.ubuntu.com/community/AutoLogin](https://help.ubuntu.com/community/AutoLogin)

For startup items, go to System > Preferences > Sessions

---

### Post by DezSP on 2008-07-06
Welcome. :)

Have a look at [this guide](http://blog.mypapit.net/2006/11/howto-bypass-ubuntu-login-screen.html) for setting up automatic login.

Ubuntu has several startup jobs, much as Windows has its startup folder, registry, services etc. For user-level processes like BitTorrent (Deluge?) it's probably best to add them to your session

Go to System -> Preferences -> Sessions

Click Add, type in any name you want, the command to run (if you're not sure, add the progam lancher to your panel and right click it and choose properties), and a description if you want. Then close it all and you should be done. :)

As an afterthought, have you considered investing in a UPS? Powercuts don't do PCs any good at all, and if you get them a lot it may be worthwhile buying one, they tend to be reasonably cheap and usually reliable.

---

### Post by quraid on 2008-07-06
thanks guys but i found out how to by tinkering a bit.

> As an afterthought, have you considered investing in a UPS? Powercuts don't do PCs any good at all, and if you get them a lot it may be worthwhile buying one, they tend to be reasonably cheap and usually reliable.
i do have an ups. but the powercutrs usually happen for a couple of hours. my ups can hold on only for 15-20 mins.

i have another problem. when i boot up i get duplicate entries in my grub.
ie.
boot>>
Windows Vista
Ubuntu
      >>Ubuntu Generic
      >>Ubuntu safe mode
      >>ubuntu memtest mode
      >>Ubuntu Generic
      >>Ubuntu safe mode
      >>ubuntu memtest mode


i hope that gives the idea. the problem started when i disapproving of the grub bootup manger's ploy to be the default boot manager, instead recreated vista's master boot record. then i lost ubuntu's link in the windows bootloader. so i had to use a 3rd party app in windows to create a customized windows boot loader which had a link to grub. now in grub every option is repeated twice.

---

### Post by DezSP on 2008-07-06
Ah well, at least you have some warning I guess. :P

Check the version numbers on those entries. If they differ, then you probably have two kernel versions installed -- the solution is simply to go into Synaptic once booted and remove the older version (and make sure you boot into the newer!). If not, then it's probably just a GRUB bug and you can delete the entries by hand in /boot/grub/menu.lst (but make a backup of that file first).

---

