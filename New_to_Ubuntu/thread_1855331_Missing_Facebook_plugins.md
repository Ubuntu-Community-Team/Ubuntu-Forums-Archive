---
title: "Missing Facebook plugins"
date: 2011-10-06
forum: New to Ubuntu
---

### Post by Cu Rua on 2011-10-06
Installed Ubuntu a few days ago and have been going nuts on the synaptic package manager trying to get all my stuff updated (working from a disc made in 2006) and Facebook intermittantly tells me to grab more plugins. I just updated Java and Flash yesterday-- what does it want from me?! ](*,)

---

### Post by amjjawad on 2011-10-06
> **Cu Rua said:**
> Installed Ubuntu a few days ago and have been going nuts on the synaptic package manager trying to get all my stuff updated (working from a disc made in 2006) and Facebook intermittantly tells me to grab more plugins. I just updated Java and Flash yesterday-- what does it want from me?! ](*,)

From Terminal:
```
sudo apt-get update && sudo apt-get install flashplugin-installer
```If this already done, then blame failbook don't blame Ubuntu :)

What release of Ubuntu are you using?
What Browser? What version?

---

### Post by fantab on 2011-10-06
> **Cu Rua said:**
> Installed Ubuntu a few days ago and have been going nuts on the synaptic package manager trying to get all my stuff updated** (working from a disc made in 2006)** and Facebook intermittantly tells me to grab more plugins. I just updated Java and Flash yesterday-- what does it want from me?! ](*,)

What do you mean you are "working form a disc made in 2006? 

[QUOTE=amjjawad]What release of Ubuntu are you using?
What Browser? What version? [/QUOTE]

---

### Post by Cu Rua on 2011-10-07
> **amjjawad said:**
> From Terminal:
```
sudo apt-get update && sudo apt-get install flashplugin-installer
```If this already done, then blame failbook don't blame Ubuntu :)

What release of Ubuntu are you using?
What Browser? What version?

Hardy Heron I believe, if that's any help at all.... also, it gives me an "install missing plugins" button with the message that I'm not good enough, but then fails to find the required plugins. My terminal didn't like your commands either: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
**E: Couldn't find package flashplugin-installer**
My E drive is my CD ROM, if that gives you any idea. My browser is Firefox, I'm not sure how to tell which version, fairly sure I told it to update in the package manager. Yeah.

---

### Post by -kg- on 2011-10-07
Hardy has gone beyond its support cycle, but I'm sure you know that, seeing that you're already linked to the archived libraries.  I don't know that flash-plugin is still updated for that version of OS or Firefox, unless you've upgraded Firefox from the PPAs.

One thing you might try doing is to install the ["Flash-Aid"]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") FF plugin and run it.  That might upgrade the Flash plugin to a version that will work with FB (and others...are you having the same trouble with Youtube or other sites?).

---

### Post by amjjawad on 2011-10-07
> **Cu Rua said:**
> **Hardy Heron I believe**, if that's any help at all.... 
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I'm not sure what makes you use an out dated version but if you are using an OLD machine then [www.lubuntu.net](www.lubuntu.net), period.

If your machine 1-2GB RAM or more then either to install Ubuntu 10.04 or wait until the final release of Ubuntu 11.10.

If you don't like Unity then Ubuntu 10.04 OR Lubuntu. Lubuntu current version is 11.04 and the next will be 11.10 and there is NO Unity :)


> also, it gives me an "install missing plugins" button with the message that I'm not good enough, but then fails to find the required plugins. My terminal didn't like your commands either: 

```
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security Release.gpg
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/main Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security Release          
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/main Packages    
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy Release.gpg      
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/restricted Translation-en_US
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/restricted Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/main Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/restricted Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/universe Packages
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/universe Sources
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/multiverse Packages
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy Release 
Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") hardy-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates Release              
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com]("http://us.archive.ubuntu.com/") hardy-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-installer

```

I'm not sure how to deal with outdated Ubuntu. IMHO, it's useless. Better to go for newer versions.

> 
My browser is Firefox, I'm not sure how to tell which version, fairly sure I told it to update in the package manager. Yeah.

Firefox > Help > About Firefox
That will tell you what version you are currently using.

---

### Post by amjjawad on 2011-10-07
On a side note, please make sure to wrap up your terminal output with "CODE" tags ;)

[IMG]http://ubuntuforums.org/picture.php?albumid=2161&pictureid=8148[/IMG]

---

### Post by Cu Rua on 2011-10-09
Ah, the 'old computer' thing... to be perfectly honest, I replaced Windows '98 on this machine. That's how old it is. I was told it was too ancient to handle IPv6 with a Windows OS, though that may have just been the Windows Curse. 
On the plus side, all my tinkering in the last few days doing totally unrelated updates, optimizing, prelinking and such, has gotten rid of the stupid "missing plugins" message. 
So the moral of the story comes from Yahtzee's review of Halo Wars: "... make enough tanks to embarrass General Pattin, steamroll from one end of the map to the other, and hope that the objective was one of the things that died along the way." Thanks for all the help anyway. 

BTW, sorry about the code formatting thing, will try to chop it down should the need arise again.

---

### Post by CaptainMark on 2011-10-09
ah well you should always use an up to date operating system if you intend on surfing the net, its just safer that way, lubuntu is a version of ubuntu designed to run well on older machines and will give you the best performance [follow this link]("http://lubuntu.lafibre.info/11.04/lubuntu-11.04-desktop-i386.iso") to download it, burn it to a cd using brasero which you shoould already have installed under applications > sound and video, then re-install it over ubuntu, make sure to back up precious files first

---

### Post by amjjawad on 2011-10-09
> **Cu Rua said:**
> Ah, the 'old computer' thing... to be perfectly honest, I replaced Windows '98 on this machine. That's how old it is. 

> **amjjawad said:**
> I'm not sure what makes you use an out dated version but if you are using an OLD machine then [www.lubuntu.net]("http://www.lubuntu.net/"), period.

> BTW, sorry about the code formatting thing, will try to chop it down should the need arise again.

Don't worry about it :)

---

### Post by Cu Rua on 2011-10-10
> **CaptainMark said:**
> ah well you should always use an up to date operating system if you intend on surfing the net, its just safer that way, lubuntu is a version of ubuntu designed to run well on older machines and will give you the best performance [follow this link]("http://lubuntu.lafibre.info/11.04/lubuntu-11.04-desktop-i386.iso") to download it, burn it to a cd using brasero which you shoould already have installed under applications > sound and video, then re-install it over ubuntu, make sure to back up precious files first

Interesting. I'll take a look at that if my computer continues to act old and kirmudgeony. Getting CDs burned is kind of a hassle for me right now. Only reason why I got Ubuntu at all is it was the only version of Linux at the library with the word "Beginner's" in the title and a disc in the back of the book. Annoying that they had 15 copies of Sharepoint manuals but only two battered old Linux books, one of which was just a command dictionary.

---

### Post by amjjawad on 2011-10-10
Nothing could be easier than creating Live CDs or Live USB.

[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

If your machine doesn't boot from USB then: [http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

---

