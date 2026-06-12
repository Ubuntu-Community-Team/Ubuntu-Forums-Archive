---
title: "I can not install handbrake"
date: 2013-12-10
forum: New to Ubuntu
---

### Post by mikejones3 on 2013-12-10
I tried all these terminal commands:

[COLOR=#555555][FONT=consolas]sudo add-apt-repository ppa:stebbins/handbrake-releases
[/FONT][/COLOR][COLOR=#555555][FONT=consolas]sudo apt-get update

but when I try and install it I get this:

[/FONT][/COLOR]mike@mike-XPS-M1530:~$ sudo apt-get install handbrake-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package handbrake-gtk
mike@mike-XPS-M1530:~$

---

### Post by kostkon on 2013-12-10
It isn't available for 13.10 yet, but you can download the deb file for 13.04 from [here]("https://launchpad.net/~stebbins/+archive/handbrake-releases/+sourcepub/3206335/+listing-archive-extra").

---

### Post by monkeybrain20122 on 2013-12-11
For 13.10 you need the snapshot ppa [https://launchpad.net/~stebbins/+archive/handbrake-snapshots](https://launchpad.net/~stebbins/+archive/handbrake-snapshots)
When you find a ppa you can find out which Ubuntu release it is for by checking the "published in" drop down box.

---

