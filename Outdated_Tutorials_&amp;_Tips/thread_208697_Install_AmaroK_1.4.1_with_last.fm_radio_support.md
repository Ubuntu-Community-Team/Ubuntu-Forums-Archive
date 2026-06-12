---
title: "Install AmaroK 1.4.1 with last.fm radio support"
date: 2006-07-04
forum: Outdated Tutorials &amp; Tips
---

### Post by eqisow on 2006-07-04
**Update: The Kubuntu.org repositories have been updated to amaroK 1.4.1. I suggest you guys use that instead of this HOWTO. For help adding that repository, see the [amaroK wiki]("https://help.ubuntu.com/community/Amarok#head-c33c648c0ea0118764ef47028eece1a710e060a8").**

To install AmaroK 1.4.1, which has support for last.fm radio streams, enter the following at the command line.

```
wget http://thepiratecove.org/files/amarok-1.4.1_i386.deb
sudo apt-get remove amarok
sudo dpkg -i amarok-1.4.1_i386.deb
rm amarok-1.4.1_i386.deb
sudo apt-get -f install
```

[B]Warning: If you are upgrading from 1.3.x, you will have to rebuild your collection.

Warning: This AmaroK package was compiled with MySQL support. If you use MySQL for your database you will have to rebuild your collection. If you don't know what database you use, you're not using MySQL.[/B]

To remove this version of amaroK and go back to using the repository version, simpy do the following at the command prompt:

```
sudo apt-get remove amarok-1.4.1
sudo apt-get install amarok amarok-engines
```

---

### Post by !nkubus on 2006-07-04
Thanks for the package :)

---

### Post by sandpaperback on 2006-07-04
Worked perfectly!  Thank you!

And for those who - like me - couldn't quite figure out why the lyrics wouldn't work, a simple

sudo apt-get install ruby

will let you enable the lyrics plugins.

---

### Post by barbarian on 2006-07-04
Works under Kubuntu, but with lot of unment dependencies, so I'll better wait for backport..

---

### Post by eqisow on 2006-07-04
barbarian, what version of Kubuntu are you running? I compiled the program on my Kubuntu Dapper system, so if you're on that, dependencies shouldn't be an issue. The 'apt-get -f install' should take care of it.

---

### Post by barbarian on 2006-07-04
Hi, i have Kubuntu Dapper also, and i have Amarok 1.4.0 from here:
deb [http://kubuntu.org/packages/amarok-14](http://kubuntu.org/packages/amarok-14) dapper main

---

### Post by bluenova on 2006-07-04
> sudo apt-get remove amarok
Will I lose all my ratings etc if I do this?

---

### Post by eqisow on 2006-07-04
bluenova:

No, you will keep your old library, ratings, etc.

---

### Post by erfus on 2006-07-04
I don't know about ratings, but my collection had to be rebuilt after I did this. Thanks for the howto.

---

### Post by eqisow on 2006-07-04
Really erfus? My collection carried over fine. Were you using something other than SQL Lite for your database perhaps?

It seems results may be somewhat inconsistent. Hopefully we get an official backport soon.

---

### Post by claydoh on 2006-07-04
the package does not seem to have been built with mysql support, so if you use that (as I do) you will need to rebuild your collection, and you will have to redo your podcast setups over again :(, though going back to 1.4 will fix that.

---

### Post by zenwhen on 2006-07-04
Worked for me, though I don't use KDE. Figured I would report my results.

---

### Post by briguy on 2006-07-04
I use the amarok-svn script from amarok.  Works great, I always have the latest version :)

[http://amarok.kde.org/amarokwiki/index.php/Installation_HowTo#Amarok-svn](http://amarok.kde.org/amarokwiki/index.php/Installation_HowTo#Amarok-svn)

---

### Post by ykpaiha on 2006-07-04
Worked fine here included my playlists
thanks

---

### Post by bluenova on 2006-07-05
yep everything went smoothly for me thanks.

---

### Post by chris_pmf on 2006-07-05
[quote=erfus]I don't know about ratings, but my collection had to be rebuilt after I did this. Thanks for the howto.[/quote]
This should normally only happen when you upgrade from 1.3.x

---

### Post by aristotlewilde on 2006-07-05
Will Amarok handle podcast downloading the same way iTunes does?  

My iPod is the second to last reason I have to even boot into Windows now.  I have been having the hardest time getting it to play well with Ubuntu.

If anyone knows of an iPod how to for Ubuntu/Linux, let me know please.

If I can get this working, BF2 will be my only windows necessity.

---

### Post by eqisow on 2006-07-05
I'm not sure how iTunes handles podcast, so I'm afraid I can't answer your question. However, amarok *does* support podcast subscriptions as well as iPods, so it's worth a try. If this is your first amaroK experience, however, you should try the official version of amaroK instead of my package.

Other programs you could try for iPod handling are Banshee and gtkPod.

---

### Post by eqisow on 2006-07-05
The Kubuntu.org repositories have been updated to amaroK 1.4.1. I suggest you guys use that instead. For help adding that repository, see the [amaroK wiki]("https://help.ubuntu.com/community/Amarok#head-c33c648c0ea0118764ef47028eece1a710e060a8").

---

### Post by aristotlewilde on 2006-07-05
Thanks for the assist.  I am toying with the idea of completely reformatting my iPod so that it will syncc up fresh with whichever program I use.  It has video, so that support is necessary as well.

Do any of these programs take out duplicate files?  From changing my partitions, I have several dupe files

---

### Post by eqisow on 2006-07-05
I'm afraid I actually don't own an iPod, so I have no idea. Maybe one of these other guys will know though.

---

### Post by barbarian on 2006-07-05
Yes, already in official repos, just updated, thanks anyway!

---

### Post by Thund3rstruck on 2006-07-07
Be careful if you use this method to install.

If you decide to add the amarok repository into sources.lst it will break apt. 

After installing via the deb package (and adding the repository) I started getting this error:
dpkg: error processing /var/cache/apt/archives/amarok-xine_2%3a1.4.1-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/share/services/amarok_xine-engine.desktop', which is also in package amarok-1.4.1
dpkg: error processing /var/cache/apt/archives/amarok_2%3a1.4.1-0ubuntu1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/kde3/libamarok_void-engine_plugin.la', which is also in package amarok-1.4.1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/amarok-xine_2%3a1.4.1-0ubuntu1_i386.deb
 /var/cache/apt/archives/amarok_2%3a1.4.1-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I had to uninstall via the deb package and then run apt-get install -f to repair.

---

### Post by eqisow on 2006-07-08
It didn't really break anything, the amaroK package linked to on this thread just has a different package name. Thus, it needs to be removed before going back to the repository version.

I'll be sure to update the post to explain this though.

---

### Post by Evoreth on 2006-07-08
The star rating doesn't show up in the OSD anymore. Did they remove this feature? :-k

---

### Post by bluenova on 2006-07-11
> **Evoreth said:**
> The star rating doesn't show up in the OSD anymore. Did they remove this feature? :-k
I had to enable it again in the prefs.

:edit:
Ah the OSD, havn't seen that and not at home at the mo.

---

### Post by Maupertus on 2006-07-12
Any reason why the update to 1.4.1 doesn't show in my list.
I'm using Xubuntu, but it should use the same rep, no?

---

### Post by Jeff250 on 2006-07-12
Have you added the Amarok 1.4.1 repo to your /etc/apt/sources.list?
[http://kubuntu.org/announcements/amarok-1.4.1.php](http://kubuntu.org/announcements/amarok-1.4.1.php)

---

