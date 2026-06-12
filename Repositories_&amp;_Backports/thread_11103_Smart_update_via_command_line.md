---
title: "Smart update via command line?"
date: 2005-01-13
forum: Repositories &amp; Backports
---

### Post by JackDog on 2005-01-13
How do I perform a smart update via the command line?

---

### Post by Rancoras on 2005-01-13
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by catalina on 2007-10-17
Just wanted to say thank you for the clear concise response!

Dean.

---

### Post by Jaramia on 2007-12-15
Hey, I was looking all over the place for these commands. I've been stuck with a fresh install that keeps crashing for what seem to be hardware related problems.

It was nice to have the necessary commands spelled out. Something I'd would like to see in the documentation. (I couldn't find it if it was there...)

Thanks

---

### Post by Majorix on 2007-12-15
This will only work if you haven't already deleted the ubuntu-desktop or whatever desktop package you may have. Doing a
[PHP]sudo apt-get update; sudo apt-get upgrade[/PHP]
will make sure you upgrade to the latest stable release.

---

### Post by PsychoNix on 2009-05-22
thanks dude working like a charm heheheee

---

### Post by WitchCraft on 2009-05-31
> **JackDog said:**
> How do I perform a smart update via the command line?
 
 
apt-get upgrade & apt-get dist-upgrade will perform most updates.
 
But sometimes, smart update is required.
 
Smart update is performed by aptitude, and usually is only necessary if you want to update glibc.

---

### Post by Wtower on 2011-01-27
I have been always wondering, how can someone check which updates are available before performing a apt-get upgrade?

---

### Post by towheedm on 2011-01-27
> **Jaramia said:**
> Hey, I was looking all over the place for these commands. I've been stuck with a fresh install that keeps crashing for what seem to be hardware related problems.

It was nice to have the necessary commands spelled out. Something I'd would like to see in the documentation. (I couldn't find it if it was there...)

Thanks

It's documented in the apt-get manual pages.
```

man apt-get
```

or

or search 'man apt-get in the Ubuntu help center.

---

### Post by towheedm on 2011-01-27
> **Wtower said:**
> I have been always wondering, how can someone check which updates are available before performing a apt-get upgrade?

I believe the -s option should do it.  Have never used it though.

---

### Post by Wtower on 2011-01-27
> **towheedm said:**
> I believe the -s option should do it.  Have never used it though.

Thumbs up, thanks.

---

### Post by dschlesak on 2011-02-23
I have tried to upgrade from Ubuntu 10-04 to 10-10 and it seems to crash when it gets to: 
Calculating upgrade... Failed
The following packages have unmet dependencies:
  libdrm-nouveau1: Breaks: xserver-xorg-video-nouveau (< 1:0.0.16) but 1:0.0.15+git20100219+9b4118d-0ubuntu5 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

I tried the upgrade from the command line as suggested but it also failed.

Any suggestions what I need to install and how>

---

### Post by malarie on 2011-03-06
apt-get clean then redo your command. Do you have the same error?

---

### Post by matey3 on 2011-03-12
Thanks for the thread and the QA. I was just wondering whats the difference between apt-get update and apt-get upgrade?
When I use apt-get update it seems it only downloads the update files but it does not install them? Is that true?

I really want to stay away from (GUI) Update Manager since I have had few bad experiences with it before in fact this is a fresh install because the update manager crashed my ubuntu install 3 or 4 times & the last time I used it, I could not boot at all and lost a lot of files.
So basically I want to do the same thing in the command line.

---

### Post by airborne_rodent on 2011-07-27
Well, depends on what you mean by "update files". In fact, what apt-get update does is downloading lists of new available packages from all repos (set in /etc/apt/sources.list) to find out whether any of the packages installed on your computer needs update or not. It does not 'download' anything apart from that lists. 
When you do apt-get upgrade, that is the moment when you download actual packages, and install them. It asks you if you want to download & install before it does anything, so if you short of fast connection, you can just see the list and exit. 
regards

---

### Post by boeckelr on 2011-10-16
I know this is an old thread - but I have a question about using "apt-get update" and "apt-get upgrade" -

What if I have compiled some apps from source?

Prior to compiling them, I ran "apt-get update" and "apt-get upgrade", but in the time since there are new packages that have updates.

Will updating them break my compiled applications?

Thanks.

---

### Post by towheedm on 2011-10-16
There is no simple way to answer this.  Depending on how the app was compiled, it may or may not.

'apt-get upgrade' upgrades packages from the repos listed in your [COLOR=Blue]/etc/apt/sources.list[/COLOR] files.  These packages are by default built with '[COLOR=Red]prefix=/usr[/COLOR]'.  Most packages you build from source will by default have prefix set to [COLOR=Red]/usr/local[/COLOR].  In this case, installing your newly built app will not remove any existing versions and issuing an apt-get upgrade will upgrade only a previously installed version leaving the version you built intact.

If you specified '[COLOR=Red]prefix=/usr[/COLOR]' when you built your app, then if it's older than the one in the repo, it will be upgraded when you issue the apt-get upgrade command.

There may be a little more to it than that, nut that's it in a nutshell.

Remember also, there is a difference between apt-get upgrade and apt-get dist-upgrade, see the apt-get man pages for details.

To prevent a package from being upgraded, you can place a 'hold' on it.  You can place a 'hold' on packages with the dpkg --set-selections command:
```
echo "pkg-name hold" | sudo dpkg --set-selections
```And to remove the hold:
```
echo "pkg-name install" | sudo dpkg --set-selections
```To see the status of all packages:
```
dpkg --get-selections
```

---

### Post by boeckelr on 2011-10-17
Hi Towheedm,

Thank you very much for your help.  

OK so if I compiled Wireshark from source....and used a prefix of /usr/local....

And then later on there was an update for one of Wireshark's dependencies - like libpcap - I would be ok doing "apt-get update" and "apt-get upgrade".....(I know "apt-get dist-upgrade is a different animal).

But if I installed Wireshark into /usr, then I better put a hold on libpcap and any other wireshark dependencies????

Mike

---

### Post by towheedm on 2011-10-17
> But if I installed Wireshark into /usr, then I better put a hold on libpcap and any other wireshark dependencies????

I'm not familiar with Wireshark, but keep in mind, it may have dependencies that are also dependencies of other applications.  So placing a hold on those, may also prevent those other apps from being updated.

---

### Post by svendhhh on 2012-05-17
> **Jaramia said:**
> Hey, I was looking all over the place for these commands. I've been stuck with a fresh install that keeps crashing for what seem to be hardware related problems.

It was nice to have the necessary commands spelled out. Something I'd would like to see in the documentation. (I couldn't find it if it was there...)

Thanks

I don't know if this has been added to the documentation yet (after 5 years), but I think it would make sense that the message when logging in over SSH, that currently reads

"**3 packages can be updated. update is a security update.**"

Would include something like

"**type: 'sudo apt-get update; sudo apt-get dist-upgrade' to perform the update**"

similar to the message you get when you enter a command included in a package that you haven't got installed.

---

### Post by vcell on 2012-07-14
> **Rancoras said:**
> ```
sudo apt-get update
sudo apt-get dist-upgrade
```
Excellent response, Rancoras. Thanks.

---

### Post by mark1234s on 2013-02-22
In my case for apt-get, bash returns command not found, also for sudo. I login as root but the same. The beginning of the problem is update from 12.04 to 12.10 and after login in graphic mode the screen is unreadable with horizontal lines. My system is kernel 3.7.3-101.fc17.x86_64, with C61 GeForce 6150SE nForce430 rev.02. What to do if apt-get is not working?

---

