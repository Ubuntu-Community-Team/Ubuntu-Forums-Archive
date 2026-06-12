---
title: "How to install drivers. wireless card won't work"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by stephenmathies on 2008-10-10
[FONT="Tahoma"][SIZE="4"][SIZE="4"]I'm new to this xbuntu, I installed it on a IBM thinkpad t61. The funny thing is that ubuntu worked fine, detected the wireless card and everything. No problems at all. Then I started all over, installed ubuntu, kubuntu and had the same problems. No Wireless connection. My question is what do I use to install drivers to get the wireless card working? the sound, etc. do I download the drivers from the ibm site? and if so do I have to use the manager to install them? I'm trying to learn this so I can have a choice between windows and linux. I have the dual boot option and I can boot up with either, win xp or xbuntu. My only problem is installing drivers which shouldn't be a hard problem if explained to me how to go about it. Not sure if this was the correct place to post this so if it's not direct me to the right place. Thanks for reading.[/SIZE][/SIZE][/FONT]

---

### Post by saru411 on 2008-10-10
I'm unsure of how xbuntu interface looks. In ubuntu you can System>Administration>Hardware_Drivers. Of course you should connect your laptop to an Ethernet cable in order to d/l the driver packages.

---

### Post by hyper_ch on 2008-10-10
what does
```

iwconfig

```
return?

---

### Post by stephenmathies on 2008-10-10
Yes, the e/cable does connect and you can surf the net. Trying to figure out where or if that is the only way to install drivers on linux is by the packages. Like I said, very new to this. If so, when you connect and push update and it updates like all the new drivers shouldn't that work? or do you have to tell it which packages to update, and if so how do you know which ones will work with your laptop? On that note, why on the ibm site do they have a "thinkpad configuration for linux". maybe I'm not asking the right questions. I'm just trying to get an understanding because if I do I'm sure I can figure the rest out. Just need to be pointed in the right direction. and where do you enter this? into the terminal? "iwconfig" sounds like IPCONFIG so I'm sure it does the same thing...   [email]stephenmathies2008@yahoo.com[/email] thx.

---

### Post by stephenmathies on 2008-10-11
I did this: In ubuntu you can System>Administration>Hardware_Drivers. and it says no propitary drivers found on machine.. or something to that.

---

### Post by GambleMe on 2008-10-21
iwconfig returns:

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

---

### Post by stephenmathies on 2008-10-21
I got it working thank you!

---

