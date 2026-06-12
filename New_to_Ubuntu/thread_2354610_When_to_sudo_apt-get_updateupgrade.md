---
title: "When to sudo apt-get update/upgrade?"
date: 2017-03-04
forum: New to Ubuntu
---

### Post by dunya on 2017-03-04
I am still trying to understand the major differences from windows softwares. When a software has a new version in windows, it generally automatically pops up a warning about that. However, as far as I got, in Linux we have to manually "sudo apt-get update" and follow it with "upgrade" command manually to get the new versions of apps. Is it correct? Also, sometimes I install apps from different ppa's, does the commands I mention also checks for the available new versions/updates from all ppa's+ubuntu software center packages?

---

### Post by Autodave on 2017-03-04
You can set it up automatically to run updates: done in *Settings.   *You can do it either way.

---

### Post by Perfect Storm on 2017-03-04
> does the commands I mention also checks for the available new versions/updates from all ppa's+ubuntu software center packages?

Yes.

---

### Post by Impavidus on 2017-03-04
You can make it work automatically. In the latest releases, this is how it works by default (unattended upgrades). All software that has been installed from repositories (so that's everything from ubuntu software, apt, including PPAs) will be upgraded simultaneously by the same tools.

---

### Post by oldfred on 2017-03-04
It used to be that when you installed a version, you only got back ported security fixes.
Your version of software with a version of Ubuntu was frozen.

But then they started updating Firefox and a few other applications. May be easier to test & release full version than attempt to back port fixes.
But most software is still the same version.

A ppa then may offer a newer version. Your apt application looks at all enabled sources and installs the most current it finds. With a ppa it is up to that distributor to make sure it works, but may not test other applications that use the same lower level tools/software and that may cause issues. That is why a distribution stays with one version including all related software and tests that.

A few distributions are rolling releases. Or as soon as software is released they will offer it.
Ubuntu does the LTS for stability, so that if your system works with current LTS, you do not have to worry that updates may cause issues.
I typically install (total new install) the most current LTS as main working install and also install newest version to see differences. 

If upgrading from older version, you must turn off ppa and any proprietary drivers or upgrade may fail due to incompatible versions. Each ppa is designed for version you install it into.

---

### Post by dunya on 2017-03-04
> **Impavidus said:**
> You can make it work automatically. In the latest releases, this is how it works by default (unattended upgrades). All software that has been installed from repositories (so that's everything from ubuntu software, apt, including PPAs) will be upgraded simultaneously by the same tools.

Could you please tell me how can I make it work automatically?

---

### Post by dunya on 2017-03-04
> **oldfred said:**
> It used to be that when you installed a version, you only got back ported security fixes.
Your version of software with a version of Ubuntu was frozen.

But then they started updating Firefox and a few other applications. May be easier to test & release full version than attempt to back port fixes.
But most software is still the same version.

A ppa then may offer a newer version. Your apt application looks at all enabled sources and installs the most current it finds. With a ppa it is up to that distributor to make sure it works, but may not test other applications that use the same lower level tools/software and that may cause issues. That is why a distribution stays with one version including all related software and tests that.

A few distributions are rolling releases. Or as soon as software is released they will offer it.
Ubuntu does the LTS for stability, so that if your system works with current LTS, you do not have to worry that updates may cause issues.
I typically install (total new install) the most current LTS as main working install and also install newest version to see differences. 

If upgrading from older version, you must turn off ppa and any proprietary drivers or upgrade may fail due to incompatible versions. Each ppa is designed for version you install it into.

Thanks for the clarifying information. Things do get really complicated with PPA then. Good to know that I should stick on the software center rather than PPA's unless I have no other choice.

---

### Post by lila on 2017-03-04
> **dunya said:**
> Could you please tell me how can I make it work automatically?

Hello,

you need to look in settings.  Is your computer running in English?  If yes, instructions in this forum are easier to follow.  Mine is in French, so I sometimes struggle to find the equivalent.  
Settings is called "paramètres" in French.  The symbol is a cogwheel with a spanner across it.  Once you have found it, if it isn't in your side bar all the time, right click it and choose the option to keep it there permanently, at least in the beginning, it's very useful until you are settled.  

In settings, you want to go into the "System" section and choose "Software and updates" (at least that it what it is called in French, I hope it's the same in English - in case it isn't, the symbol is a cardboard box with a planet Earth in front of it).

When you click on Software and updates,  window will open which has several tabs.  Open the one that says "updates", check all three boxes of types of updates you want and choose how often you want the system to check for updates and how often you want to be told if there are some.

The last line asks if you want to be told about new versions of ubuntu becoming available.  Tell it to only tell you about long term support versions.  At this stage, you don't want the other ones.  

Hope this helps!  All the best with your ubuntu experience!  I've used nothing else since 2004 and I haven't looked back.  And I am NOT a computer person...  If I can do it, so can anyone.

---

### Post by dunya on 2017-03-04
> **lila said:**
> Hello,

you need to look in settings.  Is your computer running in English?  If yes, instructions in this forum are easier to follow.  Mine is in French, so I sometimes struggle to find the equivalent.  
Settings is called "paramètres" in French.  The symbol is a cogwheel with a spanner across it.  Once you have found it, if it isn't in your side bar all the time, right click it and choose the option to keep it there permanently, at least in the beginning, it's very useful until you are settled.  

In settings, you want to go into the "System" section and choose "Software and updates" (at least that it what it is called in French, I hope it's the same in English - in case it isn't, the symbol is a cardboard box with a planet Earth in front of it).

When you click on Software and updates,  window will open which has several tabs.  Open the one that says "updates", check all three boxes of types of updates you want and choose how often you want the system to check for updates and how often you want to be told if there are some.

The last line asks if you want to be told about new versions of ubuntu becoming available.  Tell it to only tell you about long term support versions.  At this stage, you don't want the other ones.  

Hope this helps!  All the best with your ubuntu experience!  I've used nothing else since 2004 and I haven't looked back.  And I am NOT a computer person...  If I can do it, so can anyone.

Thank you very much for your efforts. I ticked the boxes and glad that I won't have to enter those commands everyday for an update.

---

### Post by lila on 2017-03-04
:p You're welcome!

---

### Post by mörgæs on 2017-03-04
At least it ought to work like this. There has been some bugs regarding automatic application of updates so better to try the commands once in a while to be sure that nothing is missed.

---

