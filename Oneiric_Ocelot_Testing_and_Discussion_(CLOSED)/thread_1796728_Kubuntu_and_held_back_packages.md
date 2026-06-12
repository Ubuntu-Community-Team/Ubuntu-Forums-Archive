---
title: "Kubuntu and held back packages"
date: 2011-07-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Arla on 2011-07-04
May be a stupid question, this time round I'm testing Kubuntu since I don't really like the new interface, and I've been finding more and more that I use mostly KDE designed programs it seemed to make sense.

The one question I'm having (having tested the last three releases in Gnome) is that I seem to have WAY more held back packages when using the normal "sudo apt-get upgrade", is this normal for KDE? Anyone know, or is testing 11.10 in Kubuntu a worthless exercise (for reasons that I'm not yet aware of).

---

### Post by buzzmandt on 2011-07-04
it's normal and not worthless. I've tested the last 4 releases with kubuntu almost exclusively.  If you're brave you can do a sudo apt-get dist-upgrade BUT pay close attention to anything being removed.  if nothing is to be removed then do it.  That's what i have to do quite often when testing kubuntu.  Again, be careful of what might be removed.

added:  to be quite honest I'm really quite bored this testing time around.  Most of it is unity and gtk3 stuff.  I'm waiting for the big drop for kubuntu as of yet.  My system is dist-upgraded and purring fine.

---

### Post by tghe-retford on 2011-07-04
I test Kubuntu and I tend to use [FONT="Courier New"]sudo aptitude safe-upgrade[/FONT] as a safer compromise. Now there will be a time now and again where a few packages won't upgrade and you have to use [FONT="Courier New"]sudo aptitude dist-upgrade[/FONT] to work out which packages are being held back and what solutions it offers. Sometimes you have to remove and install updated packages, sometimes you have to wait a bit.

I have to say, I haven't noticed any difference between Ubuntu and Kubuntu - in fact if anything, KDE feels more stable and less troublesome for me during testing. Your experience may differ.

---

### Post by bennachie on 2011-07-04
+1 for Kubuntu Oneiric being in better shape than its Ubuntu counterpart.I have experienced and reported a couple of minor glitches involving Plasma (plenty time to sort those out before release), but otherwise Kubuntu is behaving very well indeed.

---

### Post by nerdopolis on 2011-07-05
Kubuntu Oneiric seems to still be using KDE 4.6 packages. Its supposed to be using 4.7, but it seems to have yet to hit the repos...

---

### Post by buzzmandt on 2011-07-05
4.7 is scheduled to release 
> 1.21 Wednesday, July 27, 2011: KDE 4.7 Release
[http://techbase.kde.org/Schedules/KDE4/4.7_Release_Schedule](http://techbase.kde.org/Schedules/KDE4/4.7_Release_Schedule)


I'm very much looking forward to this.  They keep making it better and better.  Add to that the integration with grub 2 and I think it's gonna be awesome
> A small but great feature is the possibility of restarting your computer into the operating system of your choice, if you have more than one installed. KDE can get a list of OSs available from Grub2 and allow users to choose one from the log off dialog.
[http://news.softpedia.com/news/KDE-SC-4-7-Beta-1-Adds-Grub2-Integration-202373.shtml](http://news.softpedia.com/news/KDE-SC-4-7-Beta-1-Adds-Grub2-Integration-202373.shtml)

---

### Post by tghe-retford on 2011-07-06
> **nerdopolis said:**
> Kubuntu Oneiric seems to still be using KDE 4.6 packages. Its supposed to be using 4.7, but it seems to have yet to hit the repos...
I have to second this - normally, Kubuntu updates to the forthcoming release around beta time. This time, we've past that stage with 4.7 and we are still using 4.6. Not sure why, I haven't see any reasoning unless I have missed something.

---

### Post by xeizo on 2011-07-06
Fedora uses 4.7 in rawhide, just tested it seemed nice, but I can't stand Fedora as you aren't allowed to do practically anything without extensive workarounds. I understand it is supposedly for security reasons, as that seems to be a big thing in the Fedora community. But it makes it a pain for a power user to just use it. Ubuntu is an ocean of freedom in comparison, which is rather funny as Fedora is much more strict about using only free software  :)

---

### Post by inportb on 2011-07-08
4.6.90 (4.7 rc1) has hit the repos, it appears. w00t!

---

### Post by xebian on 2011-07-08
> **inportb said:**
> 4.6.90 (4.7 rc1) has hit the repos, it appears. w00t!

I thought RC2 should have been released 2 days ago?
[http://techbase.kde.org/Schedules/KDE4/4.7_Release_Schedule](http://techbase.kde.org/Schedules/KDE4/4.7_Release_Schedule)

---

### Post by PaulW2U on 2011-07-08
> **inportb said:**
> 4.6.90 (4.7 rc1) has hit the repos, it appears. w00t!

Well some of it. I have 60 packages that aptitude is showing as 'held back', I think there ought to be several hundred packages available if 4.70 was currently downloadable in full. It took several days for 4.63 to filter through.

> **xebian said:**
> I thought RC2 should have been released 2 days ago?
[http://techbase.kde.org/Schedules/KDE4/4.7_Release_Schedule](http://techbase.kde.org/Schedules/KDE4/4.7_Release_Schedule)

I hope they release when it's ready and not before. Final release is due on 27th July so if RC2 is a few days late it won't matter too much.

---

### Post by inportb on 2011-07-08
I don't see an announcement for rc2... [just rc1]("http://kde.org/announcements/announce-4.7-rc1.php"). At any rate, it takes time (2 weeks, apparently) for these things to get packaged.

---

### Post by buzzmandt on 2011-07-08
from the kubuntu-dev mailing list
> Salute mes amis!

Perhaps you have noticed that there is no Kubuntu alpha 2
announcement. The reason for this is that we were hard at work to get
KDE 4.6.90 (aka 4.7rc1) packaged. Currently we are fixing up some
remaining issues and prepare for upload to the Ubuntu archive.

Now, KDE 4.6.90 is implementing a partially split source tarball
distribution. Meaning what previously was kdegraphics are now okular,
gwenview, kolourpaint etc.. For additional information on this change
you can surely find sufficient amount of information via Google, so I
am not going into detail here.

Long story short: KDE stuff may break over the next couple of days, so
unless you want to take you chances you might want to hold back on
upgrades.

regards,
Harald

helps explain some of it anyway

and, oh ya, in case you missed it......
> Long story short: KDE stuff may break over the next couple of days, so
unless you want to take you chances you might want to hold back on
upgrades.

---

### Post by buzzmandt on 2011-07-10
Looks like kubuntu finally is getting in on that breakability.....

wooohooo  :)

anyone done it yet?

```
buzzmandt@buzzmandt-Compaq-Presario-CQ60-Notebook-PC:~$ sudo apt-get dist-upgrade
[sudo] password for buzzmandt: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  kde-window-manager kdebase-bin kdebase-data kdebase-runtime-data kdebase-workspace kdebase-workspace-bin
  kdebase-workspace-kgreet-plugins kubuntu-desktop libplasmaclock4abi1 libtaskmanager4abi1 nepomukcontroller
  plasma-widget-lancelot plasma-widget-smooth-tasks plasma-widgets-addons ubiquity-frontend-kde
The following NEW packages will be installed:
  kde-baseapps-bin kde-baseapps-data kde-runtime kde-runtime-data kde-workspace-kgreet-plugins
  libkwineffects1abi2 libplasmaclock4abi2 libsolidcontrol4abi2 libsolidcontrolifaces4abi2 libtaskmanager4abi2
The following packages will be upgraded:
  dolphin kaccessible kdebase-runtime kdepasswd kdm kfind khelpcenter4 kinfocenter klipper kmag kmousetool
  konq-plugins konqueror konqueror-nsplugins konsole kopete kppp ksysguard ksysguardd ksystemlog
  libkdecorations4 libkephal4abi1 libkscreensaver5 libksgrd4 libksignalplotter4 libkworkspace4
  libplasma-geolocation-interface4 libplasmagenericshell4 libprocesscore4abi1 libprocessui4a libweather-ion6
  okular plasma-dataengines-workspace plasma-desktop plasma-netbook plasma-scriptengine-javascript
  plasma-widgets-workspace systemsettings
38 upgraded, 10 newly installed, 15 to remove and 0 not upgraded.
Need to get 24.5 MB of archives.
After this operation, 23.6 MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

---

### Post by tghe-retford on 2011-07-10
> **buzzmandt said:**
> Looks like kubuntu finally is getting in on that breakability.....

wooohooo  :)

anyone done it yet?
I wouldn't recommend it. Base KDE packages have been renamed and it's causing havoc at the moment with packages which haven't had their dependencies updated yet.

Using aptitude safe-upgrade is keeping tons of packages held back but no breakage for now.

---

### Post by buzzmandt on 2011-07-10
ya, i've done the safe upgrades, so far i'm holding back on the others... don't know how long i an keep my ankles chained far enough away from the laptop to resist it though lol....

---

### Post by xebian on 2011-07-10
I've done the dist-upgrade and just need to install kde-workspace(because it used to be kdebase-workspace) to get a useable desktop session.

---

### Post by buzzmandt on 2011-07-10
I use the plasma smooth tasks and it's gonna get removed.  kinda waiting on that one to say upgraded instead.  might be a few days i know... lol

---

### Post by bennachie on 2011-07-10
I've decided to live dangerously on one of my installations, and update progressively using Muon. So far, so good - the Desktop widget is AWOL at the moment, but everything else still seems to working fine. I promise not to complain if it all falls in a heap - we've had fair warning!

---

### Post by caryb on 2011-07-11
Strange I have two lists of "stuff" to remove kpackagekit wants to remove Nvidia-current and aptitude wants to hose 128 files. The Kpackagekit has been stuck on that for 2 weeks.


Cary

---

### Post by inportb on 2011-07-11
The way I see it... if it's going to kill kubuntu-desktop, I'm not doing it. Otherwise, anything goes :)

---

### Post by buzzmandt on 2011-07-11
> **caryb said:**
> Strange I have two lists of "stuff" to remove kpackagekit wants to remove Nvidia-current and aptitude wants to hose 128 files. The Kpackagekit has been stuck on that for 2 weeks.


Cary

Kpackagekit is being replaced with muon software center.  I've been using it for a while now and really like it.  the rest is up to you

---

### Post by inportb on 2011-07-12
It looks like nothing's getting held back now. *nepomukcontroller* and *plasma-widgets-addons* are getting removed and do not have replacements, but I'm going to bite the bullet :P

---

