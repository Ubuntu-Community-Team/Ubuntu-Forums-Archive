---
title: "How to make Lubuntu even lighter"
date: 2012-04-13
forum: New to Ubuntu
---

### Post by Penguin360 on 2012-04-13
I installed Lubuntu 11.10 on an old machine and it runs ok. I am wondering what I can do to make it even lighter? Any suggestions?

Thanks a lot.

---

### Post by raja.genupula on 2012-04-13
what are the unwanted services for you find out them and disable them at start up .

---

### Post by Jake5 on 2012-04-13
I agree with Raja, as always, but I think a safe place to start would be to purge the game packages.
Then if you have no use for the calculator or xfburn or abioffice I would purge those next.

---

### Post by cortman on 2012-04-13
Log in using Openbox only. You can do this with Fedora, not sure about Lubuntu, but Openbox is one of the fastest and most user friendly WMs I've used.

---

### Post by bodhi.zazen on 2012-04-13
IMO it is much easier to do a minimal install and add on then it is to start removing things from lubuntu.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

And build up

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

### Post by 23senick on 2012-04-14
If you're determined to go even lighter, yes a fresh minimal install is best. However, you have to know what you're doing, in my experience (not exactly a noob but no tekkie either) there can be gaps. I decided to add xfce desktop as Lubuntu won't have LTS in 12.04, but haven't been able to get xfce sessions to work (perhaps I should be posting that one myself...)

---

### Post by verymadpip on 2012-04-14
+1 for a minimal install & building from there.

---

### Post by mörgæs on 2012-04-14
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)

---

### Post by Penguin360 on 2012-04-14
> **raja.genupula said:**
> what are the unwanted services for you find out them and disable them at start up .

Thanks. I decided to start with this option. If this not work as I expected, I will try a minimal install.

How do you disable a service in Lubuntu? I use Task Manager to kill some services I don't need, but I don't know where to disable those services from running next time I reboot.

---

### Post by bodhi.zazen on 2012-04-14
> **23senick said:**
> If you're determined to go even lighter, yes a fresh minimal install is best. However, you have to know what you're doing, in my experience (not exactly a noob but no tekkie either) there can be gaps. I decided to add xfce desktop as Lubuntu won't have LTS in 12.04, but haven't been able to get xfce sessions to work (perhaps I should be posting that one myself...)

Same applies when you start removing things. You can not randomly remove things you do not understand any easier then you can add the things you need to add to a minimal install.

If you want to customize your install in this way, you will have some reading to do. No none can do the work for you as most of the customizations are personal choice.

---

### Post by Penguin360 on 2012-04-14
Never mind my last question. There is no GUI for managing start up services (correct me if I am wrong). I have to use command update-rc.d to modify my start-up services.

---

### Post by snowpine on 2012-04-14
> **CodingBeaver said:**
> I installed Lubuntu 11.10 on an old machine and it runs ok. I am wondering what I can do to make it even lighter? Any suggestions?

Thanks a lot.

Use the terminal command **top** to see the top processes consuming RAM (if you want to be "lighter" on RAM) or CPU (if you want to be "lighter" on CPU). Then look for lightweight alternatives to these processes (or eliminate them entirely).

---

### Post by I2k4 on 2012-04-14
FWIW, after substantial testing via Live USB I found all, repeat all, the 11.x and beyond are noticeably more demanding than 10.x versions of Ubuntu, Lubuntu, etc. so when it came time to install a version on my little netbook's hard drive, I went with Lubuntu 10.10 instead of 11.x.  

Obviously some will say you should always run the latest but as a practical matter I haven't seen anything 11.x can do better on my machine.  Highly recommend the Live USB test route for different versions.  As far as I can tell, the move from 10.x to 11.x and beyond was a big one for Ubuntu and related distros, and reminds me of the jump in resource requirements from Windows XP to Vista.  Ubuntu will get better over time on the new platform, but never quite as "light" for old or weak machines again.

---

### Post by snowpine on 2012-04-14
> **I2k4 said:**
> FWIW, after substantial testing via Live USB I found all, repeat all, the 11.x and beyond are noticeably more demanding than 10.x versions of Ubuntu, Lubuntu, etc. so when it came time to install a version on my little netbook's hard drive, I went with Lubuntu 10.10 instead of 11.x.  

Obviously some will say you should always run the latest but as a practical matter I haven't seen anything 11.x can do better on my machine.  Highly recommend the Live USB test route for different versions.  As far as I can tell, the move from 10.x to 11.x and beyond was a big one for Ubuntu and related distros, and reminds me of the jump in resource requirements from Windows XP to Vista.  Ubuntu will get better over time on the new platform, but never quite as "light" for old or weak machines again.

You can use 10.04 if you like (support through April 2013) but 10.10 is obsolete and end-of-life:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Ubuntu's hardware requirements increase with every release due to the inevitability of Moore's Law:

[http://en.wikipedia.org/wiki/Moore%27s_law](http://en.wikipedia.org/wiki/Moore%27s_law)

Upgrading your hardware every couple of years will ensure you can always run the latest Ubuntu. :)

---

### Post by I2k4 on 2012-04-15
When somebody can make my little netbook obey Moore's Law, I'll upgrade.

---

