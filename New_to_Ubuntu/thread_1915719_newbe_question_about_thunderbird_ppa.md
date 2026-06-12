---
title: "newbe question about thunderbird ppa"
date: 2012-01-26
forum: New to Ubuntu
---

### Post by werty2010 on 2012-01-26
did a fresh reinstall(11.10) recently and wanted to add lightning but the site says the version of my thunderbird is old. so i googled a little and found [this]("http://support.mozillamessaging.com/en-US/kb/installing-thunderbird-ubuntu-linux?s=ubuntu++ppa&as=s#w_install-the-newest-release")

so my question: is this the way to go? meaning is this ppa for 11.10?

---

### Post by hhh on 2012-01-26
That looks like an official Mozilla PPA, Mozilla is an  old and trusted Open Source organization and those instructions are for Ubuntu versions 10.04 and newer. I say go for it.

---

### Post by werty2010 on 2012-01-26
just did it and it gave this error after "sudo apt-get install update":


```
W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/source/Sources  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/oneiric/main/binary-i386/Packages  404  Not Found
```

---

### Post by Krytarik on 2012-01-26
Right now, users of Oneiric 11.10 are - ironically - worst off among the users of all current Ubuntu versions; that's because

[LIST]
[*]the official repos for Oneiric were supposed to include the most recent versions of Thunderbird, which they did before, and possibly have done with v9 intermittently too, and therefore
[*]that PPA doesn't provide packages for Oneiric.
[/LIST]
So the only way to install Thunderbird 9 conveniently via packages in Oneiric is probably through "Ubuntuzilla":

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page)

Regards.

---

### Post by hhh on 2012-01-26
@Krytarik, thanks for the info. It's Thunderbird 10 he needs, though, Thunderbird 9 is in Oneiric, unless I'm reading this wrong...
[http://packages.ubuntu.com/oneiric/thunderbird](http://packages.ubuntu.com/oneiric/thunderbird)

@werty2010, sorry that didn't work. You'll want to edit the Mozilla line out of your sources.list so you don't continue to get errors. In a terminal, run...```
sudo gedit /etc/apt/sources.list
```
After you remove the line and save the file, run...```
sudo apt-get update
```

You could see if these instructions for the lates T-bird work in Oneiric...
[http://www.liberiangeek.net/2011/03/install-latest-version-thunderbird-ubuntu-10-10-maverick-meerkat/](http://www.liberiangeek.net/2011/03/install-latest-version-thunderbird-ubuntu-10-10-maverick-meerkat/)

---

### Post by Krytarik on 2012-01-26
> **hhh said:**
> @Krytarik, thanks for the info. It's Thunderbird 10 he needs, though, Thunderbird 9 is in Oneiric, unless I'm reading this wrong...
[http://packages.ubuntu.com/oneiric/thunderbird](http://packages.ubuntu.com/oneiric/thunderbird)
No, that's perfectly right, it wasn't there just a few days ago, and I didn't re-check that now. Yay! :P

For installing Lightning, I'd simply install it from the official repos also:
```
sudo apt-get install xul-ext-lightning
```> **hhh said:**
> @werty2010, sorry that didn't work. You'll want to edit the Mozilla line out of your sources.list so you don't continue to get errors. In a terminal, run...```
sudo gedit /etc/apt/sources.list
```
PPAs usually aren't added to "/etc/apt/sources.list", but with their own files under "/etc/apt/sources.list.d". So either remove them from there or via "Software Sources -> Other Software".

Btw., don't use "sudo" for graphical apps, use "gksudo" instead (or at least in Ubuntu also "gksu", as it's symlinked to it):

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by hhh on 2012-01-26
> **Krytarik said:**
> PPAs usually aren't added to "/etc/apt/sources.list", but with their own files under "/etc/apt/sources.list.d". So either remove them from there or via "Software Sources -> Other Software".
Ok, I wasn't sure about that. I haven't used Ubuntu in some time (moved to Debian).

> Btw., don't use "sudo" for graphical apps, use "gksudo" instead (or at least in Ubuntu also "gksu", as it's symlinked to it):
Right, but I've had some weirdness with text editors and gksu. For example, gksu leafpad (on Debian, at least) opens an unresponsive instance of Leafpad while sudo leafpad opens it right up. Confusing. -edit- gksudo leafpad works fine.

Anyway, good looking out. Thanks!

---

### Post by Krytarik on 2012-01-26
> **hhh said:**
> I haven't used Ubuntu in some time (moved to Debian).
[..]
Right, but I've had some weirdness with text editors and gksu. For example, gksu leafpad (on Debian, at least) opens an unresponsive instance of Leafpad while sudo leafpad opens it right up. Confusing. -edit- gksudo leafpad works fine.
Yeah, that's because "gksu" does not necessarily the same as "gksudo" in distros other than Ubuntu, usually it's said to have an effect similar to "su", but I really can't imagine how this could ever work out, since if you close an app, the graphical session is gone too, so how could you ever proceed with running apps with root rights similar to using "su" at the command line without having to invoke "gksu" again, or "gksudo", for that matter.

---

