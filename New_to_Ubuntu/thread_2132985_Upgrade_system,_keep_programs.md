---
title: "Upgrade system, keep programs"
date: 2013-04-06
forum: New to Ubuntu
---

### Post by ViliX64 on 2013-04-06
Hi, is there any way to upgrade ubuntu based linux system, but keep all settings, programs, files. I have Xubuntu 12.10 and I want to prepare for 13.04. And I want to know, if I have to reinstall whole system or is there better way.

---

### Post by sandyd on 2013-04-06
> **ViliX64 said:**
> Hi, is there any way to upgrade ubuntu based linux system, but keep all settings, programs, files. I have Xubuntu 12.10 and I want to prepare for 13.04. And I want to know, if I have to reinstall whole system or is there better way.

You just use the upgrade manager which will keep the settings/programs/files. They will be updated to the latest version though.

---

### Post by ViliX64 on 2013-04-06
So when 13.04 is released, I will update a lot of things in my upgrade manager and it changes my system version into 13.04? It seems too easy..

---

### Post by ViliX64 on 2013-04-06
"Upgrade manager" is it possible, that in Xubuntu it is called "Software updater" ?

---

### Post by Cheesemill on 2013-04-06
You won't see the Upgrade Manager until 13.04 has been released, the program doesn't have an entry in your application menu.

When the time comes you should be asked whether or not you wish to upgrade.

---

### Post by arpanaut on 2013-04-06
Follow this to get you there after the 25th:
[http://docs.xubuntu.org/migrating-upgrading.html#upgrading](http://docs.xubuntu.org/migrating-upgrading.html#upgrading)

---

### Post by Bresser on 2013-04-06
Never used Xubuntu but if its like other buntu distros then open terminal (Ctrl-Alt-T):
```

sudo apt-get update

```
A alert should come up stating that there is a newer version and will offer to install for you. It will be no change to your files as it is just some added features and security updates. Also some bug fixes.

---

### Post by arpanaut on 2013-04-06
@ Bresser, the OP is talking about upgrading to the next release 13.04.
Different process.

---

### Post by mörgæs on 2013-04-07
If something goes wrong in the upgrade:

You can do a fresh install of 13.04 and later install all applications as you had in the old version. More advice in my signature.

---

### Post by ViliX64 on 2013-04-07
I don't know.. it is my style to format disk and reinstall whole system, but I don't know if it worth the effort..
So, what are the major changes in 13.04 against 12.10?

---

### Post by mörgæs on 2013-04-07
There are only few. Best is to run a live boot and judge for yourself.

---

### Post by ViliX64 on 2013-04-07
Yes, but could you please list the major ones?

---

### Post by Cheesemill on 2013-04-07
I don't think that there are any major changes between 12.10 and 13.04, they both use XFCE version 4.10 for a start so there will be no real changes to the DE.
Most of the changes will just be small version bumps for your installed software.

For an official list of the changes between versions, you should take a look at the release notes which will be available to look at when 13.04 is released.
As an example you can find the release notes for Xubuntu 12.10 here...
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/Xubuntu](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/Xubuntu)

There will be a similar page available for Xubuntu 13.04 on the 25th when it is available for download.

---

### Post by ViliX64 on 2013-04-07
Ok, how often does xfce enviroment changes? (is it years, months.. ?)

---

### Post by 3rdalbum on 2013-04-07
Almost no change from 12.10 to 13.04. For a Xubuntu user there is probably little reason to upgrade.

Note that the Xubuntu installer also has an Upgrade option. It is a fresh install, but preserving your programs, files and settings.

---

### Post by Cheesemill on 2013-04-07
The main stable version of XFCE (which is what Xubuntu uses) gets a new version every year or two at the moment.

You can see which version of XFCE different versions of Ubuntu are using at the moment by searching the Ubuntu package database...
[http://packages.ubuntu.com/search?keywords=xfce4&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=xfce4&searchon=names&exact=1&suite=all&section=all)

---

