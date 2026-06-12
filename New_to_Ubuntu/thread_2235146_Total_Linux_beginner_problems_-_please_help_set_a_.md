---
title: "Total Linux beginner problems - please help set a screensaver"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by Neil_Dexter on 2014-07-19
I am totally new to Linux. I have heard about it and thought I would try it, so I installed it on a spare laptop (Ubuntu 14.04 only, no Windows).

How do I set a screensaver?

I have about a desktop called KDE and people have recommended it to me. Firstly, is it any good? Secondly how do I obtain it?

Thank you.

---

### Post by kc1di on 2014-07-19
Hi Neil_Dexter and Welcome to Linux and Ubuntu,

There is a bit of a learning curve with linux but once you get the hang of it it's a very powerful and great operating system. 
If you are currently using Ubuntu , with unity desktop - you can go to the system control panel and set up your screen saver the way you want, I believe it's under the power settings and the lock settings.
But not on my unity system at the moment.  There are several good desktop environments and it's mostly a matter of personal choice, KDE is infact a good one and it more like Windows than Unity. 
I like XFCE personally because it is quick and efficient.  Many like LXDE - which is very lightweight and works well on older hardware. 

If you want to try KDE there are a couple ways to do that, you can install it from the software center.  You can download[ Kubuntu ]("http://www.kubuntu.org/")and try it on a live DVD without installing it. remember it will run somewhat slower in live mode. But you can get a taste of what it's like.  you may also want to download[ xubuntu]("http://xubuntu.org/") and[URL="http://lubuntu.net/"] lubuntu 
[/URL]and give them a try then install the one you like the best. There are several other desktops available for linux also but those are the major ones. 
Happy hunting.  Enjoy ;)

---

### Post by TheFu on 2014-07-19
Welcome to the forums.

Start here: [https://ubuntu-manual.org/](https://ubuntu-manual.org/)

KDE is just 1 of the GUIs for Linux. It is like Unity or LXDE or XFCE or Mate or Cinnamon or ..... 20 others.  They all work fine, but they all have tiny issues.  Google found these instructions: [http://askubuntu.com/questions/452083/how-to-install-kde-along-unity](http://askubuntu.com/questions/452083/how-to-install-kde-along-unity)  It is a reputable source that I would follow myself.

As a beginner, you really only want to install software from the package manager.  Do not download files separately like those other OSes.  If it isn't in the package manager, you don't want it. There are 20K offerings, so don't worry.

There are specific Ubuntu distros with different GUIs. These are intended to reflect the needs of an average user of the different GUI - lite-weight GUI means an average user probably wants a lite word processor, etc.  That may not be the case.  Good news - installing a different release just to have a different GUI or set of programs is NOT NECESSARY.

I used KDE for a year or so in the late 1990s - it was fine, but my knowledge isn't current on how to install it.  I can say that to install LXDE and XFCE here are the commands:
```
sudo apt-get install lxde
sudo apt-get install xfce4
```
You can load as many as you like to try out.  Google for "ubuntu DE options" to learn about others and the install process for each. Most are that easy - 3-5 minutes, logout, toggle the new choice, then login.  All the old programs you know are still there. Just the main desktop GUI is changed. There is a small risk of different GUIs using the same configuration files and corrupting settings from other tools, so you may want to create a different user account to test each out. If you find that a GUI is NOT wanted, just remove it.

If you want to learn more about Linux, find your local LUG (google your city name and "linux group" to find them).  My metro area has over 5 different Linux groups. Most meet monthly, but 1 meets weekly and is especially beginner friendly.

---

### Post by grahammechanical on 2014-07-19
Ubuntu is open source and it is built upon other open source projects. So, Ubuntu uses the Gnome desktop environment (DE) of Gnome 3. But it does not use the shell (user interface) that comes with Gnome 3 (DE). Ubuntu has a user interface crafted by Ubuntu developers and it is called Unity. These developers are of the opinion that a screensaver is no longer necessary.

Because Ubuntu is open source it has been possible from early days for programmers to take the Ubuntu code and modify it by using another desktop environment. Some of these projects have officially become  part of the Ubuntu family. They are both dependant and at the same time independent.

So, we have Xubuntu using Xfce ; Kubuntu using KDE; Lubuntu using Lxde; Ubuntu Gnome using Gnome 3 shell. And a project has just been started to bring the Mate user interface to Ubuntu. We can download these "flavours" and install them in the same way we downloaded and installed Ubuntu.

[http://xubuntu.org/](http://xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

[http://www.kubuntu.org/](http://www.kubuntu.org/)

[http://ubuntu-mate.org/](http://ubuntu-mate.org/)

And then there are specialist remixes

[https://www.edubuntu.org/](https://www.edubuntu.org/)

[http://ubuntustudio.org/](http://ubuntustudio.org/)

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

Download an ISO image, burn it to DVD/USB and run a live session. Make decisions based upon your preferences and not upon the opinions of others. This is the freedom we have when we use Free and Open Source Software (FOSS).

Regards and have fun.

---

### Post by Rob Sayer on 2014-07-19
I don't really feel comfortable using multiple desktops.  They can cause hard to diagnose problems, for one thing because both may use the same system program in different versions.  But a system with KDE and a GTK based desktop like unity or most other DEs shouldn't cause too many problems because they use different libraries.

My netbook didn't work nearly as well with the older LTS 12.04 so I desktop/distro hopped a bit before 14.04 came out.  Now it runs Xubuntu 14.04 (my laptop I usually use at home runs Kubuntu 12.04).  Nevertheless I've largely lost any fear of installing, and more experienced linux geeks than I tend to recommend reinstalling over doing a version upgrade.

BTW there are several ways to install KDE but if you want the full kubuntu experience it'd be kubuntu-desktop.  I'd use synaptic package manager (if you don't have this install it and learn how to use it) or the terminal.  It's been quite some time since I used the software centre.

If you use synaptic you should always hit the reload sources button to update them before installing anything.

In the terminal it'd be:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kubuntu-desktop

```

You can get more minimal KDE versions but the full kubuntu would probably get better support here, which is pretty important for newbies.

Before actually installing KDE I'd recommend you get the kubuntu live CD and burn it and boot it.  Then try the KDE desktop and see how you like it.  USB is way, way better for this because it's much faster than an optical disc if you can do this.

I'd still recommend reinstalling over multiple DEs on the same machine.  In my netbook distro hopping adventures I found that when installing it's much better if you set the HD up with a separate partition for your /home folder.  Then you can reinstall the system (when upgrading versions for example) without losing your data or program settings.  As long as you tell it not to format the /home partition of course ... and you should still, as always, have your data backed up first.

That may sound daunting but it's not that hard.  There's a lot of good info on installing with a separate /home partition.

Which DE also kind of depends on your hardware.  Unity is pretty heavy and frankly I find it too slow .  KDE is also quite heavy but you can configure it to be a *lot* faster.  Which you can't  really do with unity.  Kde can be configured almost to a fault.

XFCE (Xubuntu) is also good, especially on old/slow hardware.  LXDE (Lubuntu) is even faster but I frankly wasn't impressed with lubuntu 14.04.  It was too buggy for me, and the development is slow.  Maybe lubuntu 14.04.1 will be better but I'd rather wait for LX-Qt (which is what LXDE  is developing into) to be finished.

---

### Post by The Cog on 2014-07-19
> **Rob Sayer said:**
> Before actually installing KDE I'd recommend you get the kubuntu live CD and burn it and boot it.  Then try the KDE desktop and see how you like it
I second that. In fact, you can do that with all the other versions (I know you have already installed Ubunt): 
Kubuntu (uses KDE)
Xubuntu (uses XFCE)
Lubuntu (uses LXDE)
They all look and feel quite different. They all have their own strengths and weaknesses. Spend a little time with each. Then you can install the one you prefer.

It is possible to install all the different desktops on one machine, but I'm not sure how much their settings might interfere with each other.

---

### Post by sammiev on 2014-07-19
> **The Cog said:**
> I second that. In fact, you can do that with all the other versions (I know you have already installed Ubunt): 
Kubuntu (uses KDE)
Xubuntu (uses XFCE)
Lubuntu (uses LXDE)
They all look and feel quite different. They all have their own strengths and weaknesses. Spend a little time with each. Then you can install the one you prefer.

It is possible to install all the different desktops on one machine, but I'm not sure how much their settings might interfere with each other.

+1 and if you have a few USB sticks you can spend a few days with each one without even installing it OS to the HD.

---

### Post by yancek on 2014-07-19
I read a post recently indicating that you could install some software to have a screen saver but can't remember if it is int repositories or a PPA or elsewhere.  You can set a background image from System Settings, Appearance if you want.  Either those that come default or add your own.

---

### Post by kc1di on 2014-07-19
Unity only comes with lightlocker - you can install gnome-screensaver or xscreensaver if you like, they are both in the repositories.

---

### Post by Dennis N on 2014-07-19
> **Neil_Dexter said:**
> I am totally new to Linux. I have heard about it and thought I would try it, so I installed it on a spare laptop (Ubuntu 14.04 only, no Windows). How do I set a screensaver?


The only real screensaver (with screensaver animations) is **xscreensaver**. The others provide only an blank screen and screen locking. You would have to install xscreensaver through the software center or with a package manager.

Tips: 
Disable or remove any other installed screensaver if you use xscreensaver.
The five data packages providing the actual screensavers are separate: 
xscreensaver-data (this one gets automatically installed with xscreensaver)
xscreensaver-data-extra
xscreensaver-gl
xscreensaver-gl-extra
rss-glx

---

### Post by LastDino on 2014-07-19
Whether you should install KDE or not depends on your taste and your available hardware compatibility. Even though, it is customizible to bone, it's probably not yet your time to go that way, so I would +1 to trying out LiveDVD/USB. I do the same, in fact, I've array of SD cards lying around which all have one version or another of Ubuntu live set-up on it. It has saved my ass many times.

I would +1 to Xscreensaver too. Its pretty cool! But, if you intend to save more power as this is laptop we are talking about, stick with the Black screen of light-locker. There is reason why it was considered to be the optimum option.

---

### Post by Neil_Dexter on 2014-07-20
Thank you for all your replies, I shall have a look through them all to find what would best suit me.

A separate question - When I downloaded Ubuntu, it starts up with the name Lubuntu. I have downloaded a different version, or is that what it is called now?

Thanks.

---

### Post by coffeecat on 2014-07-20
> **Neil_Dexter said:**
> A separate question - When I downloaded Ubuntu, it starts up with the name Lubuntu.

You didn't download Ubuntu - you downloaded Lubuntu, one of the official variants or "flavours" of Ubuntu. It comes with the Lxde desktop. 

[http://www.ubuntu.com/about/about-ubuntu/derivatives](http://www.ubuntu.com/about/about-ubuntu/derivatives)

Have a look at some of the earlier posts which tell you about the different variants and their desktops. Since we now know which desktop you are using, this will affect the advice about using a screensaver. The fact that there are so many different desktops that you can use in Ubuntu is confusing when you first come from the Windows world, but I do recommend that you are clear in any thread you start which Ubuntu variant and hence which desktop you are using so that people can give appropriate advice. There are thread prefixes which can help, and which you can set at the time of first posting your thread, or edit later.

**EDIT**: I should have added. Everyone has made the reasonable assumption that you were running Ubuntu with the Unity desktop. If you haven't tried it yet, and you have sufficiently beefy hardware, I do recommend you try it. You may not like it, or perhaps you may like it - it seems to bring out strong reactions either way in different people. It's a dock-based desktop which you use in a similar way to MacOS, whereas Lubuntu/Lxde and Xubuntu/Xfce are menu based desktops, vaguely akin to Windows in their use. KDE is - well - KDE! :wink:

Sorry - /jk. KDE is really a menu based desktop but is incredibly configurable, as mentioned earlier, and as such could be a bit overwhelming for a newcomer.

---

### Post by Neil_Dexter on 2014-07-20
When I went to ubuntu.com and downloaded ubuntu, I thought it would have been the true ubuntu. As soon as I went to the download section, I got the option to download 14.04 version. It did not mention it was a variant or it had a different name. How can I get the Ubuntu with Unity desktop?

---

### Post by coffeecat on 2014-07-20
If you went to the main ubuntu.com site - [http://www.ubuntu.com/](http://www.ubuntu.com/) - you would have downloaded Ubuntu with the Unity desktop. But you say in post #12 that it starts up with the name Lubuntu. As far as I am aware, you can download Lubuntu from only a few places, [http://lubuntu.net/](http://lubuntu.net/) and [https://help.ubuntu.com/community/Lubuntu/GetLubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu) -  the first links to the second anyway - and [http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/). The latter two are ubuntu.com subdomains so I wonder if that is where you got Lubuntu, or why you think you went to the main ubuntu.com site.

Anyway, there is an easy way to see whether you are using Ubuntu or Lubuntu.

Ubuntu with Unity looks like this: [https://help.ubuntu.com/14.04/ubuntu-help/index.html](https://help.ubuntu.com/14.04/ubuntu-help/index.html)

Lubuntu with Lxde looks like this: [http://en.wikipedia.org/wiki/Lubuntu#mediaviewer/File:Lubuntu_14.04_LTS_English.png](http://en.wikipedia.org/wiki/Lubuntu#mediaviewer/File:Lubuntu_14.04_LTS_English.png)

---

### Post by TheFu on 2014-07-20
> **Neil_Dexter said:**
> When I went to ubuntu.com and downloaded ubuntu, I thought it would have been the true ubuntu. As soon as I went to the download section, I got the option to download 14.04 version. It did not mention it was a variant or it had a different name. How can I get the Ubuntu with Unity desktop?

The GUI is NOT the OS.  Assuming it really is Lubuntu, then you are running Ubuntu now, just with slightly different GUI and default applications.  No need to reinstall or download 650+G of data to correct that.

**sudo apt-get install ubuntu-desktop**
Should get what you want. [http://packages.ubuntu.com/search?keywords=ubuntu-desktop&searchon=names&suite=trusty&section=all](http://packages.ubuntu.com/search?keywords=ubuntu-desktop&searchon=names&suite=trusty&section=all)  Yep. That's it. Then just logout, click the "gear" and choose the desktop environment you want for the next login, then login again. Poof - Unity. I wouldn't switch desktops too often under the same userid.

Of course there are 100 different ways to the solution and downloading another complete copy is one of the options too.

---

### Post by Neil_Dexter on 2014-07-21
I have the first image as my GUI (the Unity one). When Ubuntu starts, it does say Lububtu.

---

### Post by coffeecat on 2014-07-21
> **Neil_Dexter said:**
> I have the first image as my GUI (the Unity one). When Ubuntu starts, it does say Lububtu.

We won't belabour this point, but the only way I can see for a system that you installed from the Ubuntu ISO to tell you that it is Lubuntu, is if you installed the lubuntu-desktop package subsequent to the initial installation. That's one of the disadvantages of installing one of the other desktops to any variant - or at least it used to be. The latest desktop metapackage to be installed hijacks the bootup graphics. Perhaps you did install lubuntu-desktop (or just the lxde metapackage) and mentioned this earlier and I missed it, but I can't think of any other way offhand for Ubuntu to announce itself as Lubuntu. Can anyone else?

---

### Post by TheFu on 2014-07-21
> **coffeecat said:**
>  but I can't think of any other way offhand for Ubuntu to announce itself as Lubuntu. Can anyone else?

I agree.  The last installed DE appears to set the login background regardless of which DE is actually used currently or was set as the default.

---

