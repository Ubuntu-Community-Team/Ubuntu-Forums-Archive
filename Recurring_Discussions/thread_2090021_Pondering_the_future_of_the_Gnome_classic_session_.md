---
title: "Pondering the future of the Gnome classic session beyond Ubuntu Precise"
date: 2012-12-01
forum: Recurring Discussions
---

### Post by kansasnoob on 2012-12-01
First things first, a brief explanation of how and why I got here:

I maintain a few dozen individual PC’s, mostly for my fellow seniors, and many of their boxes won’t support Compiz so I’ve typically used the Ubuntu LTS releases with the Metacity window manager ever since Hardy (8.04). All were currently running personalized versions of Ubuntu Lucid (10.04) when Unity was introduced as the default DE. During the Natty & Oneiric dev cycles I began showing Unity to these users and about 2/3 to 3/4 quite vocally rejected the notion of learning to use the Unity DE, so I’d planned on using Lubuntu which had just recently earned “official” status as an Ubuntu flavor. Lubuntu is very light and simple due to using the Openbox window manager, and it’s also very simple to create a minimal Lubuntu install and then install only the desired apps.
 
But then Lubuntu announced early in Precise development that they would not be doing an LTS release, and Xubuntu would be doing only a 3 year LTS, whereas the desktop version of Ubuntu would be a five year LTS, meaning it would be supported until April 2017. That meant I could potentially skip 14.04 and wait for 16.04 if I so wished. Game on! Since Precise was in very early development I began by trying to get a Gnome classic DE running on top of the Metacity window manager using the “classic (no effects)” session:

[http://ubuntuforums.org/showthread.php?t=1873765](http://ubuntuforums.org/showthread.php?t=1873765)

That worked out well enough that I published this compilation of “tweaks and tricks” for Oneiric:

[http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

And later a similar compilation for Precise:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

The latter one has now been “wikified” by ***cortman***:

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

Now, you’ll notice that the Community Documentation says, “&#65279;**This guide is written for Ubuntu 12.04 LTS, which is a five year support version. With the removal of support in 12.10 for Unity 2D and Metacity, the future of the Gnome classic option looks doubtful.** Therefore this wiki cannot be guaranteed to work on any later version of Ubuntu- it may work, but proceed at your own risk!”

**[COLOR="Red"]That’s a good starting point for this discussion.[/COLOR]**

Beginning with Quantal (12.10) Ubuntu dropped the Unity-2D session so Metacity is no longer installed by default. That has to do with the introduction of ‘llvmpipe’:

[http://www.phoronix.com/scan.php?page=news_item&px=MTIxMTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIxMTg)

Sadly the many boxes I maintain with P4M800 graphics just won’t run with “compiz + llvmpipe” so installing (or upgrading to) Ubuntu 12.10 falls flat on it’s face. Now, ‘metacity’ is still in the repos so I can get it to work, but why bother? Ubuntu Quantal (12.10) is only supported until April 2014 whereas Precise (12.04) is an LTS and it’s supported until April 2017.

So then I began to shift my focus to  “ubuntu-GNOME-remix” Quantal which still includes ‘metacity’ by default:

[http://ubuntuforums.org/showthread.php?t=2073181](http://ubuntuforums.org/showthread.php?t=2073181)

It actually requires even less tweaking but remember that it’s not yet an official flavor!

Now the plot thickens!

The Gnome devs recently announced that they’ll also be dropping ‘metacity’ in favor of using “llvmpipe + mutter”:

[http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html](http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html)

They will however be introducing a new classic session via “gnome shell extension(s)”:

[http://www.webupd8.org/2012/11/gnome-shell-38-to-get-classic-mode.html](http://www.webupd8.org/2012/11/gnome-shell-38-to-get-classic-mode.html)

Based on recent experience though I doubt that will work acceptably with P4M800 graphics. **[COLOR="Red"]So what now?[/COLOR]**

Well first and foremost; **I’ll be keeping most of my production machines running Precise (12.04) because I’m 99.9% certain that the “classic (no effects)” session will continue to work throughout it’s lifespan.** In fact if it breaks you can bet that I’ll quickly find a work-around.

Second I’ll be shifting my focus back to Lubuntu during the next couple of dev cycles in hopes that their 14.04 might be an LTS. It uses the Openbox window manager which also runs quite well on lower-end hardware.

In no specific order beyond that I’ll be giving all of the following a more serious look:

* Xubuntu - it is what it is, certainly no better or no worse than Lubuntu. It’s simply a matter of choice.

* Ubuntu with Cinnamon - they’ve forked a version of Mutter renamed Muffin for use with the Cinnamon DE which does include a “2D” session, but I’ve tested it on a box with P4M800 graphics and the performance is horribly sub-par compared to Metacity or Openbox.

* Ubuntu with Mate - they’ve forked a version of Metacity renamed Marco but it’s designed to work only with Mate’s forked Gnome 2 DE. That’s probably the least desirable to me because there already were annoying problems with the old ‘gnome-panel’ and I worry about being able to integrate newer and more secure apps.

* Be patient - things just keep changing! Besides the changes in desktop environments and window managers many other controversial changes are occurring such as recent changes to Nautilus:

[http://www.webupd8.org/2012/08/ubuntu-1210-might-ship-with-nautilus-34.html](http://www.webupd8.org/2012/08/ubuntu-1210-might-ship-with-nautilus-34.html)

&#65279;And Gnome's Vincent Untz has already called on the community to fork and maintain the “fallback-session” including ‘metacity’ and ‘gnome-panel’:

[http://www.phoronix.com/scan.php?page=news_item&px=MTIzMzE](http://www.phoronix.com/scan.php?page=news_item&px=MTIzMzE)

You’ll notice there that he says, “&#65279;Things will improve with time, obviously, and 3.10 will solve more and more issues; hence I would recommend to people hitting such issues to stay with 3.6 for a few more months." 

Well Ubuntu Precise (12.04) uses Gnome 3.2.1, and it’s supported until April 2017, so why not just kick back and relax while the devs decide what to do next?

In the meanwhile I’ll continue testing in a multi-boot arrangement:

[ATTACH]227976[/ATTACH]

Others may prefer testing in a VM but I want to see how things work with actual hardware :)

Anyone have plans of their own to share?

---

### Post by tea for one on 2012-12-01
Good afternoon

I stumbled on this article on the World of Gnome site:-

[http://worldofgnome.org/gnome-classic-will-be-a-separate-session-in-3-8/](http://worldofgnome.org/gnome-classic-will-be-a-separate-session-in-3-8/)

They don't seem to like the name Gnome Classic so I think that they should call it "Gnome Too"

Kind regards

---

### Post by snowpine on 2012-12-01
> **kansasnoob said:**
> But then Lubuntu announced early in Precise development that they would not be doing an LTS release, and Xubuntu would be doing only a 3 year LTS, whereas the desktop version of Ubuntu would be a five year LTS.

I've given this a lot of thought, and here are my thoughts: Lubuntu/Xubuntu users will get the exact same updates to kernel, libraries, and applications as Ubuntu users, for the full 5 years of support. The only packages that won't get LTS support are a few desktop-specific packages that are never run as root user. What is the worst-case scenario? How likely is it for a mission-critical stability/security bug to mysteriously appear in lxappearance (for example) years after release?

---

### Post by kansasnoob on 2012-12-01
> **tea for one said:**
> Good afternoon

I stumbled on this article on the World of Gnome site:-

[http://worldofgnome.org/gnome-classic-will-be-a-separate-session-in-3-8/](http://worldofgnome.org/gnome-classic-will-be-a-separate-session-in-3-8/)

They don't seem to like the name Gnome Classic so I think that they should call it "Gnome Too"

Kind regards

Correct, but the new classic session will still use the Mutter window manager. Based on my testing of the Mint/Cinnamon fork (which is called Muffin) support for P4M800 graphics pretty much stinks.

Maybe things will improve by Gnome version 3.10 as Vincent Untz says :)

---

### Post by kansasnoob on 2012-12-01
> **snowpine said:**
> I've given this a lot of thought, and here are my thoughts: Lubuntu/Xubuntu users will get the exact same updates to kernel, libraries, and applications as Ubuntu users, for the full 5 years of support. The only packages that won't get LTS support are a few desktop-specific packages that are never run as root user. What is the worst-case scenario? How likely is it for a mission-critical stability/security bug to mysteriously appear in lxappearance (for example) years after release?

Well, I'm sticking with Ubuntu/Gnome classic (no effects) on these P4M800 boxes for 12.04 and I'm reasonably sure that no security or recommended updates will break things.

---

### Post by monkeybrain2012 on 2012-12-01
> **snowpine said:**
> I've given this a lot of thought, and here are my thoughts: Lubuntu/Xubuntu users will get the exact same updates to kernel, libraries, and applications as Ubuntu users, for the full 5 years of support. The only packages that won't get LTS support are a few desktop-specific packages that are never run as root user. What is the worst-case scenario? How likely is it for a mission-critical stability/security bug to mysteriously appear in lxappearance (for example) years after release?

Good point. I have installed lubuntu 12.04 on some friends' old machine, set up a few ppas so they get updated vlc and a few applications, I don't really want to update the OS next year as I have had a hard time getting the wireless to work (and it works nicely now)

---

### Post by kansasnoob on 2012-12-02
Regarding security in 12.04 I tend to think we should trust Lubuntu when they say it's supported 18 months, Xubuntu when they say it's supported for 3 years, and Ubuntu when they say it's supported for 5 years :)

The question actually came up towards the end of the Precise dev cycle and I convinced ***sudodus*** to ask here:

[http://ubuntuforums.org/showthread.php?t=1954702&highlight=lubuntu+precise+LTS](http://ubuntuforums.org/showthread.php?t=1954702&highlight=lubuntu+precise+LTS)

But I guess the question should be, "how well can the packages in the repos be trusted"?

I don't know for sure but an issue recently arose on the Lubuntu QA mailing list regarding the Chromium browser:

[ATTACH]228074[/ATTACH]

Since I don't use Chromium I didn't follow it all but if you wish you can read through all of the posts here:

[https://lists.launchpad.net/lubuntu-qa/](https://lists.launchpad.net/lubuntu-qa/)

When I wrote [this]("http://ubuntuforums.org/showthread.php?t=1966370") I actually did take security into account. The basic procedure only installs:

> alacarte
cups-pk-helper
gir1.2-gconf-2.0
gir1.2-panelapplet-4.0
gnome-applets
gnome-applets-data
gnome-panel
gnome-panel-data
gnome-session-fallback
indicator-applet-complete
libpanel-applet-4-0 python-gmenu

All of which are supported by Gnome and/or Ubuntu for 12.04 so I think it should be safe :)

That said I do use PPA's when desired so how can I be sure I'm secure? Well I generally research the source of the PPA just a bit - not hard to do really using Launchpad.

But ultimately we must all make our own decisions :guitar:

---

### Post by tartalo on 2012-12-02
Kansasnoob,

Personally I'd go for Lubuntu, but I understand why you prefer a LTS.

You don't mention Kubuntu, did you consider it? You might find this interesting: [http://blog.martin-graesslin.com/blog/2012/11/fallback-mode-in-kde-plasma-workspaces/](http://blog.martin-graesslin.com/blog/2012/11/fallback-mode-in-kde-plasma-workspaces/)

> The first thing to notice is that KDE Plasma workspaces do not have a non-composited fallback mode in the way GNOME Shell or Unity used to have. The main difference is that our window manager (KWin) is able to act as a non-composited, XRender based compositor and OpenGL (ES) based compositor. This means that we do not have to maintain two window managers in order to provide non-composited setups.

The second major difference is that the Desktop Shell (either KDE Plasma Desktop, KDE Plasma Netbook or KDE Plasma Active) is not a plugin to the compositor but a separate application running in an own process. This allows to use a completely different window manager together with the Desktop Shell. 

I don't know if it's still the case, but in previous releases compositing had to be manually disabled for P4M800

```
Add to the .kde4/share/config/kwinrc (.kde/share/config/kwinrc)

[Compositing]
Enabled=false
```

Another must-read "How to make Kubuntu (KDE) blazing fast and optimise it for performance" (thanks to kio_http): [http://ubuntuforums.org/showthread.php?t=1889034](http://ubuntuforums.org/showthread.php?t=1889034)

---

### Post by kansasnoob on 2012-12-02
> **tartalo said:**
> Kansasnoob,

Personally I'd go for Lubuntu, but I understand why you prefer a LTS.

You don't mention Kubuntu, did you consider it? You might find this interesting: [http://blog.martin-graesslin.com/blog/2012/11/fallback-mode-in-kde-plasma-workspaces/](http://blog.martin-graesslin.com/blog/2012/11/fallback-mode-in-kde-plasma-workspaces/)



I don't know if it's still the case, but in previous releases compositing had to be manually disabled for P4M800

```
Add to the .kde4/share/config/kwinrc (.kde/share/config/kwinrc)

[Compositing]
Enabled=false
```

Another must-read "How to make Kubuntu (KDE) blazing fast and optimise it for performance" (thanks to kio_http): [http://ubuntuforums.org/showthread.php?t=1889034](http://ubuntuforums.org/showthread.php?t=1889034)

The last time I actually "used" anything KDE based was when Linspire was still alive (based on Ubuntu 7.04?).

I've always just felt that KDE/Kubuntu was too bloated, but I did play a bit when they introduced this:

[http://ubuntuforums.org/showthread.php?t=1765479](http://ubuntuforums.org/showthread.php?t=1765479)

Ain't it fun to play  :lolflag:

---

### Post by MadmanRB on 2012-12-02
Well there is always Linux mint and MATE

---

### Post by kansasnoob on 2012-12-02
> **MadmanRB said:**
> Well there is always Linux mint and MATE

I did mention both Cinnamon and Mate in my OP :)

I personally dislike Mint itself because of how they've chosen to handle kernel updates that Ubuntu considers "security level" updates but Mint does NOT!

And Cinnamon's Muffin window manager is not an acceptable alternative to Metacity.

The kindest thing I can say about Mate is, "why not just use Lucid with a newer kernel"?

I have serious security concerns with Mate!!!

---

### Post by exploder on 2012-12-02
> I personally dislike Mint itself because of how they've chosen to handle kernel updates that Ubuntu considers "security level" updates but Mint does NOT!

You are free to use Synapic to install kernel updates if you want. Mint Update is there to help new users from having breakage they may not know how to fix.

> And Cinnamon's Muffin window manager is not an acceptable alternative to Metacity.

What is wrong with Muffin?

> The kindest thing I can say about Mate is, "why not just use Lucid with a newer kernel"?

Mate is just a desktop environment. The underlying system is just as new and up to date as any given release.

> I have serious security concerns with Mate!!! 

Mate is just as secure as any other desktop environment. Mate actually has fixed many of the longstanding bugs that were in the Gnome 2x series.

Certainly Ubuntu is going to be more popular on the Ubuntu forum, that's a given but to say that there are security issues with Mate or Cinnamon is unfounded. Mint is based off Ubuntu and is just as secure by default.

---

### Post by Cheesemill on 2012-12-02
> **exploder said:**
> What is wrong with Muffin?
From the OP:
> * Ubuntu with Cinnamon - they’ve forked a version of Mutter renamed  Muffin for use with the Cinnamon DE which does include a “2D” session,  but I’ve tested it on a box with P4M800 graphics and the performance is  horribly sub-par compared to Metacity or Openbox.

---

### Post by exploder on 2012-12-02
There have been some bug fixes since Mint 14 was released. There were problems found in the themes that have been fixed. It might be worth taking another look. 

Lubuntu looks to be the most promising solution for these particular computers and users though. Peppermint being based on Lubuntu might also be something to consider.

---

### Post by Cheesemill on 2012-12-02
Have you considered a distro switch?

This thread has mainly been about Ubuntu (+Mint) so far but one option would be to switch to Debian. The current Debian Stable still uses the original Gnome 2 as a DE and still has a couple of years left in it, there is no official EOL date yet but it will be 1 year after Wheezy becomes stable.

If you really want to go extreme then take a look at Scientific Linux. The latest version which is a rebuild of Red Hat Enterprise Linux 6 uses Gnome 2 as its DE and will be supported until November 2020.

---

### Post by snowpine on 2012-12-02
And don't forget Fuduntu, with Gnome 2 desktop and "rolling release" updates so you never need to reinstall.

---

### Post by Uncle Spellbinder on 2012-12-02
> **snowpine said:**
> And don't forget Fuduntu, with Gnome 2 desktop and "rolling release" updates so you never need to reinstall.
Indeed. Great, stable distro for me. never any breakage and all the apps I use are available. Great distro, in my opinion.

---

### Post by monkeybrain2012 on 2012-12-02
I install lubuntu on some machines for only one reason, namely that these machines are so weak that only lubuntu is light enough to give good perfomance so something like kde is out of the question (maybe xubuntu too but if lubuntu works why bother)  I love Unity so there is no desire to stick to some retro DE on my part. 

As snowpine said as long as the main security stuffs are getting updated through Ubuntu 12.04's repository and software through ppa it is not an issue any more. I always remove chromium and install Firefox anyway so that is not an issue either.

---

### Post by kansasnoob on 2012-12-03
> **exploder said:**
> You are free to use Synapic to install kernel updates if you want. Mint Update is there to help new users from having breakage they may not know how to fix.



**[COLOR="Red"]What is wrong with Muffin?[/COLOR]**



Mate is just a desktop environment. The underlying system is just as new and up to date as any given release.



Mate is just as secure as any other desktop environment. Mate actually has fixed many of the longstanding bugs that were in the Gnome 2x series.

Certainly Ubuntu is going to be more popular on the Ubuntu forum, that's a given but to say that there are security issues with Mate or Cinnamon is unfounded. Mint is based off Ubuntu and is just as secure by default.

Muffin is super slow with the aforementioned P4M800 graphics ............. I mean "get up and walk around waiting" slow :)

It's the equivalent of rolling back to dial-up from DSL.

I really have no further comment regarding Mint, I prefer Ubuntu. I find it odd that you'd use Ubuntu's water cooler to discuss or promote another distro :(

---

### Post by sudodus on 2012-12-03
I think I understand your situation. I also prefer LTS versions and I was disappointed, when Lubuntu 12.04 was not an LTS version.

Anyway, you have 4 years to go until you have to start to upgrade the systems for yours friends. By that time, some of their computers have probably broken and been replaced, and some of them, for example those without pae, should be possible to replace with nicely priced newer second-hand computers (or 'inherited' from younger relatives).

At that time, maybe it will be feasible to use some desktop environment of the new [KLX]Ubuntu LTS. ***Let us hope and work for full long time support of all flavours.*** As was written in this thread, there are rather few packages, that need to be included for Lubuntu to get LTS.

---

### Post by Peter Maunder on 2012-12-05
kansasnoob,

Thank you first of all for your Precise Classic Tweaks and Tricks, it is invaluable. 

I have also pondered what to do to look after myself and my friends systems. They are all retired, a mixture of English and French and use their systems for the classical functions browser, email, office (writer + calc), photos (library + slideshow), skype. They do not play computer games.

A system without a screensaver / slideshow is a non starter. Linux Mint Maya Mate comes with a basic screensaver / slideshow. It may be trivial to install but it does mean that out of the box Ubuntu nolonger has this basic function. The Software Centre does not even have an entry for SCREENSAVER, you need to enter XSCREENSAVER to find one.

I guess we will be staying with 12.04 so all my users will have the same software. I do tell them that they are using LINUX - UBUNTU so if I need to change to Mint say in the future it will still be a consistent choice.

---

### Post by vasa1 on 2012-12-05
> **kansasnoob said:**
> ... I find it odd that you'd use Ubuntu's water cooler to discuss or promote another distro :(

There's no gain in preaching to the converted :)
That's how I interpret the numerous, totally altruistic posts here extolling other distros and proprietary software.

---

### Post by kansasnoob on 2012-12-05
> **vasa1 said:**
> There's no gain in preaching to the converted :)
That's how I interpret the numerous, totally altruistic posts here extolling other distros and proprietary software.

I just get frustrated with the constant recommending of other distros :(

Anyone that took the time to read my OP would know that I have a plan:

Option #1: stick with 12.04

Option #2: switch to Lubuntu or Xubuntu

Option #3: be patient and see what works best over the course of the next few dev cycles.

BTW it's fairly obvious that I still love Ubuntu (regardless of flavor), but I don't go posting at the Mint forums (or others) recommending they switch to my preferred concoction :)

To me that would be like hanging around a Chevy showroom and telling everyone how much you love Ford :D

---

### Post by kansasnoob on 2012-12-05
> **Peter Maunder said:**
> kansasnoob,

Thank you first of all for your Precise Classic Tweaks and Tricks, it is invaluable. 

I have also pondered what to do to look after myself and my friends systems. They are all retired, a mixture of English and French and use their systems for the classical functions browser, email, office (writer + calc), photos (library + slideshow), skype. They do not play computer games.

A system without a screensaver / slideshow is a non starter. Linux Mint Maya Mate comes with a basic screensaver / slideshow. It may be trivial to install but it does mean that out of the box Ubuntu nolonger has this basic function. The Software Centre does not even have an entry for SCREENSAVER, you need to enter XSCREENSAVER to find one.

I guess we will be staying with 12.04 so all my users will have the same software. I do tell them that they are using LINUX - UBUNTU so if I need to change to Mint say in the future it will still be a consistent choice.

Thanks. I actually posted this in part because I'm either going to request some edits to that thread or possibly post an entirely new, updated version after which I can request a simple edit to the original pointing to the new one.

And I probably will post a brief version for Quantal, but I didn't want to take up a great deal of space explaining what's being planned, what other options there are, etc.

This way I can just link to this thread for a more in depth explanation of why I recommend staying with 12.04 LTS. But right now I'm working on a decent version of this:

[http://ubuntuforums.org/showpost.php?p=12133196&postcount=43](http://ubuntuforums.org/showpost.php?p=12133196&postcount=43)

In that case it was an "upgrade via live CD/DVD/USB" but the procedure does also provide a "replace" option under the proper circumstances. My time has just been limited lately.

Basically I get things done when I get them done :)

---

### Post by vasa1 on 2012-12-06
> **kansasnoob said:**
> I just get frustrated with the constant recommending of other distros :(
... but I don't go posting at the Mint forums (or others) recommending they switch to my preferred concoction :)

To me that would be like hanging around a Chevy showroom and telling everyone how much you love Ford :D

Well, IMO, it's even worse than that. We've seen the forum slowing down. Whether the recent fix has improved things or not isn't clear. But a simple mind like mine thinks that the more threads, the more load; the longer the thread, the more the load.

---

### Post by KiwiNZ on 2012-12-06
> **vasa1 said:**
> Well, IMO, it's even worse than that. We've seen the forum slowing down. Whether the recent fix has improved things or not isn't clear. But a simple mind like mine thinks that the more threads, the more load; the longer the thread, the more the load.

Not a loading issue, the Forum can handle far greater load than we have experienced of late, back in 2009-2010 we could get up to 40,000 on line at a time.

---

### Post by kansasnoob on 2012-12-09
Just out of curiosity I tried installing Mate in Ubuntu-GNOME-Remix this evening and it's honestly not that bad, but it does install a lot of packages:

> lance@lance-VIA-desktop:~$ sudo apt-get install mate-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libreadline5
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  atril atril-common caja caja-common cpufrequtils engrampa engrampa-common
  eom eom-common ffmpegthumbnailer ffmpegthumbnailer-caja fuse-utils
  gtk2-engines-murrine libatril libcaja-extension libcpufreq0 libfam0
  libffmpegthumbnailer4 libglade2-0 libgtksourceview2.0-0
  libgtksourceview2.0-common libidl-common libidl0 libjpeg62 libmarco libmate
  libmate-common libmatecanvas libmatecomponent libmatecomponentui libmateconf
  libmatecorba libmatedesktop libmatekbd libmatekeyring libmatemenu
  libmatenotify libmatepanelapplet libmatepolkit libmateui libmatevfs
  libmateweather libmateweather-common libmatewnck libmatewnck-common librpm3
  librpmio3 libtasn1-3-bin libtiff4 libunique-1.0-0 libvte-common libvte9
  marco marco-common mate-applets mate-applets-common mate-backgrounds
  mate-conf mate-conf-common mate-control-center mate-corba mate-desktop
  mate-desktop-common mate-dialogs mate-icon-theme mate-keyring mate-media
  mate-media-common mate-media-gstreamer mate-menus mate-mime-data mate-panel
  mate-panel-common mate-polkit mate-power-manager mate-power-manager-common
  mate-screensaver mate-session-manager mate-settings-daemon
  mate-settings-daemon-common mate-settings-daemon-gstreamer
  mate-system-monitor mate-terminal mate-terminal-common mate-text-editor
  mate-themes mate-vfs mate-vfs-common mate-window-manager menu menu-xdg
  p7zip-full python-corba python-glade2 python-gtksourceview2 python-mate
  python-mate-desktop rpm-common rpm2cpio
Suggested packages:
  unrar mate-file-manager meld lha sharutils ncompress unace lzip lzop rzip
  unalz zoo arj murrine-themes fam xscreensaver-data rss-glx menu-l10n
  p7zip-rar python-gtk2-doc libgtksourceview2.0-dev rpm-i18n
The following NEW packages will be installed:
  atril atril-common caja caja-common cpufrequtils engrampa engrampa-common
  eom eom-common ffmpegthumbnailer ffmpegthumbnailer-caja fuse-utils
  gtk2-engines-murrine libatril libcaja-extension libcpufreq0 libfam0
  libffmpegthumbnailer4 libglade2-0 libgtksourceview2.0-0
  libgtksourceview2.0-common libidl-common libidl0 libjpeg62 libmarco libmate
  libmate-common libmatecanvas libmatecomponent libmatecomponentui libmateconf
  libmatecorba libmatedesktop libmatekbd libmatekeyring libmatemenu
  libmatenotify libmatepanelapplet libmatepolkit libmateui libmatevfs
  libmateweather libmateweather-common libmatewnck libmatewnck-common librpm3
  librpmio3 libtasn1-3-bin libtiff4 libunique-1.0-0 libvte-common libvte9
  marco marco-common mate-applets mate-applets-common mate-backgrounds
  mate-conf mate-conf-common mate-control-center mate-corba mate-core
  mate-desktop mate-desktop-common mate-dialogs mate-icon-theme mate-keyring
  mate-media mate-media-common mate-media-gstreamer mate-menus mate-mime-data
  mate-panel mate-panel-common mate-polkit mate-power-manager
  mate-power-manager-common mate-screensaver mate-session-manager
  mate-settings-daemon mate-settings-daemon-common
  mate-settings-daemon-gstreamer mate-system-monitor mate-terminal
  mate-terminal-common mate-text-editor mate-themes mate-vfs mate-vfs-common
  mate-window-manager menu menu-xdg p7zip-full python-corba python-glade2
  python-gtksourceview2 python-mate python-mate-desktop rpm-common rpm2cpio
0 upgraded, 100 newly installed, 0 to remove and 136 not upgraded.
Need to get 108 MB of archives.
After this operation, 271 MB of additional disk space will be used.

####################################################################

lance@lance-VIA-desktop:~$ sudo apt-get install mate-desktop-environment
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libreadline5
Use 'apt-get autoremove' to remove it.
The following extra packages will be installed:
  apache2.2-bin hddtemp libapache2-mod-dnssd libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap libmatebluetooth
  libmatesensorsappletplugin libnet-dbus-perl liboobs-1-5 libtie-ixhash-perl
  libxml-parser-perl libxml-twig-perl libxml-xpath-perl mate-bluetooth
  mate-calc mate-netspeed mate-sensors-applet mate-system-tools
  mate-user-share mate-utils mozo python-mate-menu python-support
  system-tools-backends
Suggested packages:
  ksensors libunicode-map8-perl libunicode-string-perl xml-twig-tools
  caja-sendto mate-sensors-applet-ati mate-sensors-applet-nvidia ntp
The following NEW packages will be installed:
  apache2.2-bin hddtemp libapache2-mod-dnssd libapr1 libaprutil1
  libaprutil1-dbd-sqlite3 libaprutil1-ldap libmatebluetooth
  libmatesensorsappletplugin libnet-dbus-perl liboobs-1-5 libtie-ixhash-perl
  libxml-parser-perl libxml-twig-perl libxml-xpath-perl mate-bluetooth
  mate-calc mate-desktop-environment mate-netspeed mate-sensors-applet
  mate-system-tools mate-user-share mate-utils mozo python-mate-menu
  python-support system-tools-backends
0 upgraded, 27 newly installed, 0 to remove and 136 not upgraded.
Need to get 19.5 MB of archives.
After this operation, 48.4 MB of additional disk space will be used.

It's certainly usable so it's worth watching what the Mate devs do going forward :D

---

### Post by kansasnoob on 2012-12-13
> **kansasnoob said:**
> Muffin is super slow with the aforementioned P4M800 graphics ............. I mean "get up and walk around waiting" slow :)

It's the equivalent of rolling back to dial-up from DSL.

I really have no further comment regarding Mint, I prefer Ubuntu. I find it odd that you'd use Ubuntu's water cooler to discuss or promote another distro :(

It appears that Mint recognizes the need I've addressed regarding Metacity:

[http://www.webupd8.org/2012/12/what-to-expect-in-linux-mint-15.html#more](http://www.webupd8.org/2012/12/what-to-expect-in-linux-mint-15.html#more)

> The Linux Mint roadmap was updated recently, pointing out what to expect in Linux Mint 15 for Cinnamon, Nemo, MDM or Mint Tools.

Linux Mint 15 is expected to ship with Cinnamon 1.8 which will include new features like:

    Desktlets (desktop widgets). Three such desklets should be available by available by default: System Monitor, Picture video & slideshow frame and Terminal
    Cinnamon Settings: ability to browse, install, remove and update Cinnamon themes, applets, extensions and desklets remotely
    Bumpmaps support (defines transparent textures which look like sculpted glass - see screenshot above)
    A Control Center that integrates both Cinnamon and GOME settings into one tool
    **[COLOR="Red"]Rethink Cinnamon 2D: fallback to a non-shadow CPU-less intensive session in software rendering mode. Muffin or OpenBox will be used.[/COLOR]**
    Configurable color schemes for themes
    Calendar events similar to KDE's implementation
    New/improved applets: upgrade Menu applet with mintMenu features, new email notifier and pulse-like RSS reader applets


This is why I say, just keep testing, watch for proposed changes by other dev teams, and otherwise enjoy the stability of 12.04 :D

Edit: Clem actually provides a clearer explanation:

> Rethink Cinnamon 2D, fallback to a non-shadow CPU-less intensive session in software rendering mode and/or Muffin/OpenBox **(whatever happens, the user should know he's not running the "real" Cinnamon, he should be told why, and he should find himself with a working WM ([COLOR="Red"]even a minimalistic one like OpenBox[/COLOR])**).

---

### Post by kansasnoob on 2013-01-18
And yet another option, Consort Desktop:

[http://www.phoronix.com/scan.php?page=news_item&px=MTI3NzM](http://www.phoronix.com/scan.php?page=news_item&px=MTI3NzM)

And the lead dev approves of an Ubuntu PPA:

[http://ubuntuforums.org/showpost.php?p=12461393&postcount=17](http://ubuntuforums.org/showpost.php?p=12461393&postcount=17)

So I can chill out with [Precise Classic (no effects)]("http://ubuntuforums.org/showthread.php?t=1966370") until a true winner emerges :D

---

### Post by Marzata on 2013-01-19
After 6 years with Ubuntu (Gnome DE) we migrated all our machines to [Xubuntu]("http://xubuntu.org/") 12.04.1 LTS (Xfce Desktop Environment). There is no single reason to look back at Gnome. Thank you, Xubuntu and Xfce teams!

---

### Post by kansasnoob on 2013-01-26
There's a sneak peek of the new GNOME "classic mode" including screen shots here:

[http://blogs.gnome.org/mclasen/2013/01/25/gnome-3-7-at-the-halfway-mark/](http://blogs.gnome.org/mclasen/2013/01/25/gnome-3-7-at-the-halfway-mark/)

But you shouldn't expect to see that in Ubuntu until 13.10 or beyond :)

---

### Post by kansasnoob on 2013-02-05
And now the components of the "fallback-session" have a new maintainer:

[http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/](http://jonathancarter.org/2013/02/05/gnome-panel-is-alive/)

I really like the sensible approach he's taking :)

---

### Post by sudodus on 2013-02-10
@kansasnoob

What do you think of the following idea to tweak the system to install pae kernels into computers with Pentium M CPUs without pae? Read the following thread

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2113826[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2113826")

Maybe it is a chance to continue using IBM Thinkpads and similar laptops beyond 12.04 :-)

---

### Post by kansasnoob on 2013-11-09
Do the mods mind if I revive this thread?

We know now that Edubuntu dev is likely to support what is now "flashback" at least into Trusty so I'd like to play with a follow up to this:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I tried doing so at Ubuntu +1 but I was told to limit the comments there to Trusty which does make sense:

[http://ubuntuforums.org/showthread.php?t=2184682](http://ubuntuforums.org/showthread.php?t=2184682)

I just need a place to play in hopes of creating something wiki-worthy so I can collaborate with someone else as i did here:

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

So I'd like to use this as a workspace if the mods are cool with it :)

---

### Post by kansasnoob on 2013-11-09
> **sudodus said:**
> @kansasnoob

What do you think of the following idea to tweak the system to install pae kernels into computers with Pentium M CPUs without pae? Read the following thread

[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=2113826[/COLOR]]("http://ubuntuforums.org/showthread.php?t=2113826")

Maybe it is a chance to continue using IBM Thinkpads and similar laptops beyond 12.04 :-)

I know this was an old request and I'm sorry I was not subscribed so I didn't see it :(

---

### Post by sudodus on 2013-11-09
There are two systems implementing it now, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") using tarballs, where there are versions with and without OEM-install based on

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

and the more specific fake-PAE systems

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

I'd be glad to cooperate with you with versions for Trusty ...

---

### Post by kansasnoob on 2013-11-09
> **sudodus said:**
> There are two systems implementing it now, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971") using tarballs, where there are versions with and without OEM-install based on

[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)

and the more specific fake-PAE systems

[https://help.ubuntu.com/community/Lubuntu-fake-PAE](https://help.ubuntu.com/community/Lubuntu-fake-PAE)

I'd be glad to cooperate with you with versions for Trusty ...

Cool, I'd be glad to add that advice to a comprehensive GNOME Classic/fallback/flashback thread.

I'm just sorry I didn't see your post many, many months ago :(

But we also know each other from Lubuntu QA so I hope you're not too mad at me.

---

### Post by sudodus on 2013-11-09
No worries :-)

Let me know what you intend to do now.

---

### Post by kansasnoob on 2013-11-10
> **sudodus said:**
> No worries :-)

Let me know what you intend to do now.

Step #1 is to write a factual history regarding GNOME classic/fallback/flashback. I sort of tried to get a head start on that here:

[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)

But I think that history should be more "inclusive"; possibly including changes to the release cycle, notes about the LTS Hardware Enablement Stack, changes in hardware support - including links to workarounds like yours, the addition of Ubuntu GNOME as an official flavor, etc, etc, etc.

Step #2 is to write a simple "alternatives" guide that can be linked to.

The ultimate goal is to create something that can be easily wikified so others can edit it as time goes along.

---

### Post by kansasnoob on 2013-11-10
BTW I rather liked where this was going:

[http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic-desktop](http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic-desktop)

But it kind of stalled here:

[http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic-desktop/284155#284155](http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic-desktop/284155#284155)

---

### Post by sudodus on 2013-11-10
Did I read correctly? "Upgrading from previous versions won't work to 13.10 (and probably not to 14.04)."

Do you know if keeping /home (as a separate partition) with a fresh install of Ubuntu Gnome will work, or is it necessary to make completely fresh install? And what kind of hardware (how old hardware) can run Ubuntu Gnome reasonably well? I'm thinking of speed as well as hardware drivers.

---

### Post by kansasnoob on 2013-11-10
> **sudodus said:**
> Did I read correctly? "Upgrading from previous versions won't work to 13.10 (and probably not to 14.04)."

Do you know if keeping /home (as a separate partition) with a fresh install of Ubuntu Gnome will work, or is it necessary to make completely fresh install? And what kind of hardware (how old hardware) can run Ubuntu Gnome reasonably well? I'm thinking of speed as well as hardware drivers.

I do not have a definitive answer regarding Ubuntu GNOME + fallback/flashback :(

I just sort of figured out that gdm is not playing well with flashback in Saucy:

[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1245209](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/1245209)

But during Saucy dev I did test both the standard upgrade path and the upgrade (image) path successfully with the default 'gnome-shell' DE and it was fine.

IMHO, whether we're talking about Ubuntu or any other flavor, one of the first things that must be mentioned is the change to a 9 month release cycle for the interim releases.

But that really does get off topic doesn't it?

---

### Post by kansasnoob on 2013-11-10
> **sudodus said:**
> Did I read correctly? "Upgrading from previous versions won't work to 13.10 (and probably not to 14.04)."

Do you know if keeping /home (as a separate partition) with a fresh install of Ubuntu Gnome will work, or is it necessary to make completely fresh install? And what kind of hardware (how old hardware) can run Ubuntu Gnome reasonably well? I'm thinking of speed as well as hardware drivers.

BTW where did you read that?

---

### Post by sudodus on 2013-11-10
at [http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic-desktop/284155#284155](http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic-desktop/284155#284155) but I may have misunderstood it.

> Can you add instructions how people can  install the desktop on their  existing computers? This makes it sound  like you need to reinstall a  new ISO to use GNOME Classic.     –          [Jorge Castro]("http://askubuntu.com/users/235/jorge-castro")     Apr 22 at 13:46

It does not sound like it... it is a new ISO install :wink:     –          [Rinzwind]("http://askubuntu.com/users/15811/rinzwind")     Apr 22 at 13:47

Ok so what about people with upgrades and who don't want to reinstall?  Does the 12.04 and newer answers still work?     –          [Jorge Castro]("http://askubuntu.com/users/235/jorge-castro")     Apr 22 at 13:59

13.04 & UP ? Fallback session will be  removed in 13.10 (because of  its gnome-settings-daemon dependency). On  13.04 anyone can install by  running sudo apt-get install gnome-session-fallback.     –          [Khurshid Alam]("http://askubuntu.com/users/11112/khurshid-alam")     Apr 27 at 12:19     

I installed Ubuntu Gnome yesterday.  I like it but it is nothing like the "Gnome Classic" desktop.     –          [Warren Hill]("http://askubuntu.com/users/107450/warren-hill")     Apr 28 at 13:11 


---

### Post by kansasnoob on 2013-11-10
> **sudodus said:**
> at [http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic-desktop/284155#284155](http://askubuntu.com/questions/58172/how-to-revert-to-gnome-classic-desktop/284155#284155) but I may have misunderstood it.

Ah, yes ........... but remember I said, "But it kind of stalled here":

[http://ubuntuforums.org/showthread.php?t=2090021&page=4&p=12843629#post12843629](http://ubuntuforums.org/showthread.php?t=2090021&page=4&p=12843629#post12843629)

Since I'd paid little attention to this session other than the renaming of the "classic" session since Precise I've missed a lot of stuff. Like I just discovered that 'gnome-tweak-tool' changed it's dependencies and then 'gnome-shell-common' changed it's dependencies so installing GNOME's own tweak tool is now safe and sensible in a fully updated Quantal as well as Saucy and Trusty.

Purely opinion, but the GNOME devs were kind of jerks for not just naming the new "gnome-shell-classic" session something different like "legacy" since we were already using "classic" :mad:

Don't get me wrong, I like GNOME, but sometimes they seem very heavy handed in their approach ;)

But as I look at this in Saucy and Trusty (so far) writing a guide for Trusty 'flashback' should actually be easier than it was in Precise.

Of course we have to wait for vUDS to be sure nothing substantial changes :D

---

### Post by kansasnoob on 2013-11-10
Just to clarify, this was FUD:

> 13.04 & UP ? Fallback session will be removed in 13.10 (because of its gnome-settings-daemon dependency). On 13.04 anyone can install by running sudo apt-get install gnome-session-fallback. –  Khurshid Alam Apr 27 at 12:19

---

### Post by sudodus on 2013-11-10
So, you will probably be able to make a nice tutorial to tweak gnome in a similar way as in Precise :-D

I'll be around and make 'easy to use systems', that can be installed with the One Button Installer and use Fake-PAE, when you have it ready for Trusty.

---

### Post by kansasnoob on 2013-11-10
> **sudodus said:**
> So, you will probably be able to make a nice tutorial to tweak gnome in a similar way as in Precise :-D

I'll be around and make 'easy to use systems', that can be installed with the One Button Installer and use Fake-PAE, when you have it ready for Trusty.

No guarantees. I was shocked when they dropped Unity-2D after Precise :(

Until the first Trusty vUDS we actually know less than nothing, but I've heard nothing from Edubuntu dev to indicate they'd drop the flashback session.

---

### Post by kansasnoob on 2013-11-17
I've just been trying to wrap my mind around the deprecation of 'gconf' in favor of 'dconf' so I need to post these sreenshots.

You can see there was some duplication of wm settings in Quantal:

[ATTACH=CONFIG]247893[/ATTACH]

[ATTACH=CONFIG]247894[/ATTACH]

But that duplication was fixed in Raring:

[ATTACH=CONFIG]247895[/ATTACH]

[ATTACH=CONFIG]247896[/ATTACH]

I believe that deprecation of gconf is nearly complete in Saucy but I'll follow up with that ASAP :D

---

### Post by kansasnoob on 2013-11-18
As suspected the deprecation of /apps/metacity in gconf is now complete in Saucy:

[ATTACH=CONFIG]247921[/ATTACH]

[ATTACH=CONFIG]247922[/ATTACH]

---

### Post by kansasnoob on 2013-11-18
And beginning with Quantal the "footprint" for 'gnome-tweak-tool' is quite small:

```
lance@lance-desktop:~$ sudo apt-get install gnome-tweak-tool
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
The following NEW packages will be installed:
  gir1.2-gdesktopenums-3.0 gir1.2-gnomedesktop-3.0 gnome-shell-common
  gnome-tweak-tool
0 upgraded, 4 newly installed, 0 to remove and 2 not upgraded.
Need to get 988 kB of archives.
After this operation, **7,625 kB of additional disk space will be used**.
```

Whereas in Precise the footprint was quite large:

```
lance@lance-desktop:~$ sudo apt-get install gnome-tweak-tool
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libjpeg-turbo-progs libgle3 libjpeg-progs
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gjs gnome-contacts gnome-icon-theme-full gnome-shell
  gnome-shell-common gnome-themes-standard libcaribou-common libcaribou0
  libclutter-1.0-0 libclutter-1.0-common libcogl-common libcogl-pango0
  libcogl9 libgjs0c libmozjs185-1.0 libmutter0 mutter-common
The following NEW packages will be installed:
  gir1.2-accountsservice-1.0 gir1.2-caribou-1.0 gir1.2-clutter-1.0
  gir1.2-cogl-1.0 gir1.2-coglpango-1.0 gir1.2-folks-0.6
  gir1.2-gdesktopenums-3.0 gir1.2-gee-1.0 gir1.2-gjsdbus-1.0 gir1.2-gkbd-3.0
  gir1.2-json-1.0 gir1.2-mutter-3.0 gir1.2-networkmanager-1.0
  gir1.2-telepathyglib-0.12 gir1.2-telepathylogger-0.2 gir1.2-upowerglib-1.0
  gir1.2-xkl-1.0 gjs gnome-contacts gnome-icon-theme-full gnome-shell
  gnome-shell-common gnome-themes-standard gnome-tweak-tool libcaribou-common
  libcaribou0 libclutter-1.0-0 libclutter-1.0-common libcogl-common
  libcogl-pango0 libcogl9 libgjs0c libmozjs185-1.0 libmutter0 mutter-common
0 upgraded, 35 newly installed, 0 to remove and 1 not upgraded.
Need to get 16.8 MB of archives.
After this operation, **38.1 MB of additional disk space will be used**.

```

That makes installing and using 'gnome-tweak-tool' a quite viable option :)

---

### Post by kansasnoob on 2013-11-25
I anticipate someone asking why the fallback-session was renamed flashback so I want to be able to point to the changelog for 'gnome-panel':

> gnome-panel (3.6.2-1) UNRELEASED; urgency=low

  * New upstream release
  * Moved gnome-session-fallback from gnome-session and rename to
    gnome-sesion-flashback:
    - debian/control.in
    - debian/gnome-session-flashback.*
    - debian/gnome-wm.desktop
    - debian/patches/01_gnome-wm.patch
    - debian/patches/02_flashback_desktop.patch
    - debian/scripts/
  * 00-Add-the-GNOME-Flashback-session.patch:
    - Backport patch to add session files for GNOME Flashback
  * debian/control.in:
    - Have gnome-session-flashback depend on nautilus >= 3.8
      and gnome-screensaver per .session file
    - Update build dependencies
  * debian/patches/git-build-with-gnome-desktop38*.patch
    - Fix build with gnome-desktop3 3.8
  * debian/patches/drop-gweather-xml-include.patch:
    - Fix build with libgweather 3.8
  * Backport several other fixes:
    - 90-remove_artifact_on_icon_animation.patch
    - 91-fix_panels_in_separate_screens.patch
    - 92-fix_sunrise-times.patch
  * Dropped patches applied in new version
    - 15_avoid_applet_loading_failures.patch
    - 16_remove_online_accounts_from_user_menu.patch
    - 17_avoid_double_forking.patch
    - 19_dconf_api_changes.patch

 -- Jeremy Bicha <jbicha@ubuntu.com>  Sat, 08 Jun 2013 21:11:02 -0400

The simple fact is that the decision was made upstream in Debian :)

---

### Post by kansasnoob on 2013-11-27
Someone posted [a perfectly a valid response]("http://ubuntuforums.org/showthread.php?t=2184682&page=12&p=12859006#post12859006") to a discussion in Ubuntu +1, **please DO NOT move it**, but my explanation could easily take that thread way off-topic so I'm posting a convoluted response here in order to keep that thread on topic :)

I actually liked the wording there:

> "**who's who in the gnome zoo**"

It really does relate to the general confusion surrounding the current "gnome-sessions".

First of all NEVER install the meta-package 'gnome' because it pulls in way too many unwanted packages:

```
lance@lance-desktop:~$ sudo apt-get install gnome
[sudo] password for lance: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  binfmt-support browser-plugin-gnash caribou caribou-antler cli-common
  dconf-tools desktop-base finger five-or-more four-in-a-row gdebi gdebi-core
  gedit-plugins gimp gimp-data gir1.2-gucharmap-2.90 gir1.2-zeitgeist-2.0 gksu
  gnash gnash-common gnome-chess gnome-core gnome-dictionary gnome-games
  gnome-klotski gnome-nettool gnome-nibbles gnome-packagekit
  gnome-packagekit-data gnome-packagekit-session gnome-robots gnome-tetravex
  gnuchess gnuchess-book gtk2-engines hamster-applet hamster-indicator iagno
  imagemagick imagemagick-common inkscape libamd2.2.0 libappindicator0.1-cil
  libappindicator1 libavahi-ui-gtk3-0 libbabl-0.1-0 libblas3 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libboost-iostreams1.53.0 libboost-program-options1.53.0
  libboost-thread1.53.0 libcaribou-gtk-module libcaribou-gtk3-module
  libdbus-glib1.0-cil libdbus1.0-cil libdiscid0 libgconf2.0-cil libgdict-1.0-6
  libgdict-common libgdiplus libgegl-0.2-0 libgfortran3 libgimp2.0 libgksu2-0
  libglade2-0 libglib2.0-cil libgmime2.6-cil libgnome2-0 libgnome2-bin
  libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra
  libgsl0ldbl libgtk-vnc-2.0-0 libgtk2.0-cil libgtkspell0 libgupnp-av-1.0-2
  libgupnp-dlna-2.0-3 libgvnc-1.0-0 libidl-common libidl0 libilmbase6
  libindicator7 libjavascriptcoregtk-1.0-0 liblapack3 liblinear-tools
  liblinear1 liblqr-1-0 libmagick++5 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmng1 libmono-addins-gui0.2-cil libmono-addins0.2-cil
  libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-i18n-west4.0-cil
  libmono-i18n4.0-cil libmono-posix4.0-cil libmono-security4.0-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil
  libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libnetpbm10 libopenexr6 liborbit2 librygel-core-2.0-1
  librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1
  libsdl1.2debian libsofia-sip-ua-glib3 libsofia-sip-ua0 libumfpack5.4.0
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwmf-bin libwnck-common
  libwnck22 lightsoff mono-4.0-gac mono-gac mono-runtime netpbm nmap
  perlmagick python-appindicator python-gconf python-gnome2 python-numpy
  python-pyatspi python-pyorbit python-uniconvertor python-wnck quadrapassel
  rdesktop rygel rygel-playbin rygel-preferences sound-juicer swell-foop tali
  telepathy-rakia tomboy tracker-gui vinagre whois
Suggested packages:
  browser-plugin-lightspark gimp-help-en gimp-help gimp-data-extras dia-gnome
  gnome-boxes gnucash libreoffice-evolution planner gnome-hearts
  gnome-system-tools gnome-packagekit-tools xboard eboard scid
  python-evolution imagemagick-doc autotrace curl enscript ffmpeg gnuplot
  grads hp2xx html2ps mplayer povray radiance texlive-base-bin transfig
  ufraw-batch ruby libsvg-perl libxml-xql-perl pstoedit libbonobo2-bin
  libdiscid0-dbg monodoc-gtk2.0-manual libgnomevfs2-bin gamin fam
  gnome-mime-data gsl-ref-psdoc gsl-doc-pdf gsl-doc-info gsl-ref-html
  libsvm-tools liblinear-dev libmono-i18n4.0-all libgamin0 sofia-sip-doc
  gstreamer1.0-ffmpeg python-gnome2-doc python-numpy-doc python-numpy-dbg
  python-nose python-dev gfortran python-pyorbit-dbg python-uniconvertor-dbg
  pcscd rygel-tracker rygel-mediathek tumbler gstreamer1.0-lame
  gstreamer1.0-plugins-really-bad tasque
The following NEW packages will be installed:
  binfmt-support browser-plugin-gnash caribou caribou-antler cli-common
  dconf-tools desktop-base finger five-or-more four-in-a-row gdebi gdebi-core
  gedit-plugins gimp gimp-data gir1.2-gucharmap-2.90 gir1.2-zeitgeist-2.0 gksu
  gnash gnash-common gnome gnome-chess gnome-core gnome-dictionary gnome-games
  gnome-klotski gnome-nettool gnome-nibbles gnome-packagekit
  gnome-packagekit-data gnome-packagekit-session gnome-robots gnome-tetravex
  gnuchess gnuchess-book gtk2-engines hamster-applet hamster-indicator iagno
  imagemagick imagemagick-common inkscape libamd2.2.0 libappindicator0.1-cil
  libappindicator1 libavahi-ui-gtk3-0 libbabl-0.1-0 libblas3 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libboost-iostreams1.53.0 libboost-program-options1.53.0
  libboost-thread1.53.0 libcaribou-gtk-module libcaribou-gtk3-module
  libdbus-glib1.0-cil libdbus1.0-cil libdiscid0 libgconf2.0-cil libgdict-1.0-6
  libgdict-common libgdiplus libgegl-0.2-0 libgfortran3 libgimp2.0 libgksu2-0
  libglade2-0 libglib2.0-cil libgmime2.6-cil libgnome2-0 libgnome2-bin
  libgnome2-common libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra
  libgsl0ldbl libgtk-vnc-2.0-0 libgtk2.0-cil libgtkspell0 libgupnp-av-1.0-2
  libgupnp-dlna-2.0-3 libgvnc-1.0-0 libidl-common libidl0 libilmbase6
  libindicator7 libjavascriptcoregtk-1.0-0 liblapack3 liblinear-tools
  liblinear1 liblqr-1-0 libmagick++5 libmagickcore5 libmagickcore5-extra
  libmagickwand5 libmng1 libmono-addins-gui0.2-cil libmono-addins0.2-cil
  libmono-cairo4.0-cil libmono-corlib4.0-cil libmono-i18n-west4.0-cil
  libmono-i18n4.0-cil libmono-posix4.0-cil libmono-security4.0-cil
  libmono-sharpzip4.84-cil libmono-system-configuration4.0-cil
  libmono-system-core4.0-cil libmono-system-drawing4.0-cil
  libmono-system-security4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libnetpbm10 libopenexr6 liborbit2 librygel-core-2.0-1
  librygel-renderer-2.0-1 librygel-renderer-gst-2.0-1 librygel-server-2.0-1
  libsdl1.2debian libsofia-sip-ua-glib3 libsofia-sip-ua0 libumfpack5.4.0
  libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwmf-bin libwnck-common
  libwnck22 lightsoff mono-4.0-gac mono-gac mono-runtime netpbm nmap
  perlmagick python-appindicator python-gconf python-gnome2 python-numpy
  python-pyatspi python-pyorbit python-uniconvertor python-wnck quadrapassel
  rdesktop rygel rygel-playbin rygel-preferences sound-juicer swell-foop tali
  telepathy-rakia tomboy tracker-gui vinagre whois
0 upgraded, 161 newly installed, 0 to remove and 0 not upgraded.
Need to get 106 MB of archives.
**[COLOR="#FF0000"]After this operation, 398 MB of additional disk space will be used.[/COLOR]**
Do you want to continue [Y/n]? n
Abort.

```

The only time I would use that meta-package is if I'm installing from a mini.iso wanting a somewhat more pure Debian experience.

Second, if you're starting with Ubuntu itself the only login option is Ubuntu, but explaining the "session" names is much easier for me beginning with Ubuntu GNOME (in this case I'm using Ubuntu GNOME Saucy). In these poor pictures you'll see four login options:

[ATTACH=CONFIG]248129[/ATTACH]   [ATTACH=CONFIG]248130[/ATTACH]

They are:

GNOME
GNOME Classic
GNOME Flashback
GNOME Flashback (no effects)

The standard GNOME session is gnome-shell. There are some fairly decent screenshots here:

[http://mylinuxexplore.blogspot.com/2013/10/ubuntu-gnome-1310-saucy-salamander.html](http://mylinuxexplore.blogspot.com/2013/10/ubuntu-gnome-1310-saucy-salamander.html)

In Saucy a new GNOME Classic session was introduced, but it is totally based on 'gnome-shell':

[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)

In either Ubuntu or Ubuntu GNOME if you install the package 'gnome-panel' it brings in the packages needed to provide the "flashback" options, but there has been some confusion surrounding the session renaming:

[http://ubuntuforums.org/showthread.php?t=2185161](http://ubuntuforums.org/showthread.php?t=2185161)

GNOME Flashback uses the Compiz window manager which I find incredibly problematic in Ubuntu because Unity is so reliant on Compiz, and Compiz must be installed in Ubuntu GNOME to use that session or you'll just boot to a blank screen.

GNOME Flashback (no effects) uses the Metacity window manager which I happen to prefer:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

Is this info helpful at all?

---

### Post by sudodus on 2013-11-27
> **kansasnoob said:**
> Is this info helpful at all?

Yes :-)

I tried Ubuntu Gnome recently, but only the default session. I'd better try GNOME Flashback (no effects) too. Chances are that I'll prefer it too at least for older computers.

---

### Post by kansasnoob on 2013-11-27
> **sudodus said:**
> Yes :-)

I tried Ubuntu Gnome recently, but only the default session. I'd better try GNOME Flashback (no effects) too. Chances are that I'll prefer it too at least for older computers.

While I find this almost painful to say, I find the Metacity session preferable to Lubuntu or Xubuntu, unless they break the heck out of it in Trusty :)

---

### Post by PJs Ronin on 2013-11-27
[QUOTE=kansasnoob]Is this info helpful at all?[/QUOTE]

Most definitely.   It also helps if I *read* what you're saying and not *assume* what you're saying.

From my perspective what I would need now is a road map as to what 'tweak' tools should be used for each gnome type.  I'd also pose the question, does gnome and its variants require GDM or will they work with LightDM?

---

### Post by kansasnoob on 2013-11-27
> **PJs Ronin said:**
> Most definitely.   It also helps if I *read* what you're saying and not *assume* what you're saying.

From my perspective what I would need now is a road map as to what 'tweak' tools should be used for each gnome type.  I'd also pose the question, does gnome and its variants require GDM or will they work with LightDM?

Tough but good questions :D

I'll address your last question first:

[http://ubuntuforums.org/showthread.php?t=2183871](http://ubuntuforums.org/showthread.php?t=2183871)

As you can see there I had to use 'lightdm' with the 'lightdm-gtk-greeter' to get things working with the flashback sessions in Ubuntu GNOME Saucy (and so far in Trusty).

Regarding the rest of it I think you need to just figure out what you want most out of your computer?

If Unity is working well for you then stick with it.

If not tell me what you do and don't like about it.

ATM I personally prefer Ubuntu GNOME out-of-box with the standard GNOME Shell DE, but I maintain nearly 50 individual PC's spread out over a 50 mile radius and preferences differ :)

It's pretty easy to find you-tube videos of how different DE's perform, or you could muck around with some different live iso's, or you could even try different distros in a VM.

What are you comfortable doing?

---

### Post by PJs Ronin on 2013-11-27
[QUOTE=kansasnoob]What are you comfortable doing?[/QUOTE]
                         I'm pretty comfortable doing anything (legal) and have 7 partitions with different flavours of Ubuntu with the occasional Mint thrown in as well. Just as well you didn't ask "What are you capable of doing?" because that's an entirely different matter. But let's have a go shall we.

Here is an image of the top of my browser. See those horrible window controls? I'm having a hell of a job changing them.
[IMG]http://i39.tinypic.com/6poylc.jpg[/IMG]

This partition is an insitu upgrade of Saucy to Trusty with Unity as standard and Gnome added. I've logged in with the "Gnome" option (gnome-shell right?) and am now trying to set some window features (themes). I've tried CCSM, gnome-tweak-tool, Ubuntu-tweak, Unity-tweak-tool and Unsettings. I know that some of these tools have no impact on gnome-shell at all, but desperate times call for desperate measures. The best I can get from any of these tools is some minor changes to the GTK+ Theme and the Current Theme... but nothing that makes my eyes light up.

My needs are simple, to have a DE that looks attractive and is easy to modify. So far, I can't see that happening with Gnome.

Btw, my gnoming is all from the standard repos.

---

### Post by kansasnoob on 2013-11-28
> **PJs Ronin said:**
> I'm pretty comfortable doing anything (legal) and have 7 partitions with different flavours of Ubuntu with the occasional Mint thrown in as well. Just as well you didn't ask "What are you capable of doing?" because that's an entirely different matter. But let's have a go shall we.

Here is an image of the top of my browser. See those horrible window controls? I'm having a hell of a job changing them.
[IMG]http://i39.tinypic.com/6poylc.jpg[/IMG]

This partition is an insitu upgrade of Saucy to Trusty with Unity as standard and Gnome added. I've logged in with the "Gnome" option (gnome-shell right?) and am now trying to set some window features (themes). I've tried CCSM, gnome-tweak-tool, Ubuntu-tweak, Unity-tweak-tool and Unsettings. I know that some of these tools have no impact on gnome-shell at all, but desperate times call for desperate measures. The best I can get from any of these tools is some minor changes to the GTK+ Theme and the Current Theme... but nothing that makes my eyes light up.

My needs are simple, to have a DE that looks attractive and is easy to modify. So far, I can't see that happening with Gnome.

Btw, my gnoming is all from the standard repos.

Very tough questions again, but deserving of a response. I'm glad to know that you know how to multi-boot, I do the same thing. But it's hard to know where to start.

Did you read my [post #53]("http://ubuntuforums.org/showthread.php?t=2090021&page=6&p=12859103#post12859103")? ** I clearly said there that installing the meta-package 'gnome' is the wrong way to approach this.**

Now I'm going to point out a few things in no particular order;

(1) Ubuntu Trusty is pre-alpha at this point:

[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)

(2) Trying to learn a new DE while also dealing with an unstable (or unpredictable) version of an OS is NOT a good idea. It's a bit like taking the second bite of an apple before chewing the first ;^) So I'd recommend using a stable release like Saucy for testing DE's and then compare the changes in the next dev release a bit later in the dev cycle.

(3) I'm not the best person to ask about 'gnome-shell' or 'unity'.  I loved Unity in Precise, particularly since there was a Unity-2D version to fall back on, but since then most of my hardware will NOT support Unity so I gave up. And I'd never really tried 'gnome-shell' until Raring when Ubuntu GNOME became an official flavor, so I'm the wrong person to ask about adding a "GNOME Shell" session to Ubuntu. Well, I do know it's best to just install 'gnome-session' or 'gnome-shell' rather than the 'gnome' meta-package, but that's about it.

(4) Ubuntu GNOME became an official flavor in Raring and I've been an iso-tester since 2008 so when I choose which iso's to test I look for those that are most in need. I did the same when Lubuntu became official some time back. It's called "helping the new kid on the block" :^) But while performing Ubuntu GNOME Saucy testing I truly fell in love with it, these screenshots are actually from Ubuntu GNOME Trusty which is quite buggy but it'll give you an idea how little I "tweak" just using 'gnome-tweak-tool':

[ATTACH=CONFIG]248162[/ATTACH]

[ATTACH=CONFIG]248163[/ATTACH]

[ATTACH=CONFIG]248164[/ATTACH]

[ATTACH=CONFIG]248165[/ATTACH]

[ATTACH=CONFIG]248166[/ATTACH]

(5) I've found converting from one DE to another is more and more complicated so I'm trying to focus on getting somewhat better integration but it's a huge challenge!!!! 

So, I'd suggest using a stable release like Saucy to find your desired DE, then you can post questions here:

[http://ubuntuforums.org/forumdisplay.php?f=329](http://ubuntuforums.org/forumdisplay.php?f=329)

But if you insist on using Trusty, which is at least unpredictable, you can post specific questions here:

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

I hope this is helpful.

---

### Post by PJs Ronin on 2013-11-28
very much... ty

---

### Post by kansasnoob on 2013-12-12
I'm playing with the [latest Caffeine]("http://www.omgubuntu.co.uk/2013/12/screensaver-stopper-caffeine-gets-first-update-two-years") in both Saucy and Trusty, but these specific screenshots apply only to Saucy:

[ATTACH=CONFIG]248556[/ATTACH]

Obviously I don't want to litter Ubuntu +1 with too much Saucy stuff, and this is not a support request, so I'm just posting the Saucy related stuff here. That way I can just link to it as I'm figuring out what to do in Trusty :)

---

### Post by kansasnoob on 2014-04-20
I didn't get this done before Trusty was released, and it's not yet ready for posting in Desktop Environments, so I'm sticking it here while I work out some issues ;)

My Trusty Flashback w/Metacity tweaks and challenges

I'm far from having this all worked out yet, thus the need for the word ***challenges*** in the title, but I began working on this during the [Trusty dev cycle]("http://ubuntuforums.org/showthread.php?t=2184682") so I suppose I should start with what I know, but **please be sure to browse this entirely before jumping in head first - [COLOR="#FF0000"]particularly the Challenges and Known Issues and please help if you can[/COLOR]** [-o<

There are changes to be aware of since I wrote [my Precise Classic notes]("http://ubuntuforums.org/showthread.php?t=1966370"):

First, there has been [continual session renaming]("http://ubuntuforums.org/showthread.php?t=2185161") since Precise to accommodate the new GNOME Classic session which is actually a GNOME Shell session with some cherry-picked extensions running on top of the Mutter window manager. No PPA is needed to test the new GNOME Classic session in Ubuntu GNOME Trusty but WebUpD8 still has the [best description I've found]("http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html").

Second, [metacity settings have now been totally deprecated from gconf]("http://ubuntuforums.org/attachment.php?attachmentid=247909&d=1384744892") in favor of dconf/gsettings so you'll notice quite a number of changes  in the commands required to apply theming tweaks such as moving the window management buttons.

Third, and perhaps most importantly, while the "flashback" session is no longer directly supported by the GNOME developers Flashback w/Metacity will continue to be supported by Edubuntu dev and [these dedicated people]("https://wiki.gnome.org/Projects/GnomeFlashback").

**My personal focus is on the Flashback w/Metacity session** which is [supported by Edubuntu]("http://edubuntu.org/sites/default/files/docimages/install-precise/030-edubuntu-options-oneiric.png") and both Ubuntu and Edubuntu Trusty are supported for a full 5 years. I should however say that the Flashback w/Metacity session can also be installed in Ubuntu GNOME Trusty but it's only supported for 3 years.

So what's needed to get started? Well that's still the same as Precise. 

**Step #1**: Simply install 'gnome-panel':

```
sudo apt-get install gnome-panel
```

Yep, that's it. In spite of session renaming that still installs all of the dependencies required and it has [quite a small footprint]("http://ubuntuforums.org/showthread.php?t=2184682&page=38&p=12986315#post12986315") in Ubuntu. The footprint in Ubuntu GNOME is a bit heavier because 'flashback' now uses 'unity-settings-daemon' and 'unity-control-center' instead of the GNOME versions of those same packages.

**Step #2**: Log out, [select the desired session]("http://ubuntuforums.org/showthread.php?t=2184682&page=27&p=12929682#post12929682"), and log back in.

**Step #3**: Enable the "[panel-run-dialog]("http://ubuntuforums.org/attachment.php?attachmentid=252566&d=1398598654")" which can be quite useful if you bork your panels and/or menus:

```
gsettings set org.gnome.desktop.wm.keybindings panel-run-dialog "['<Alt>F2']"
```

**Step #4**: Consider what additional packages you may want.

'**indicator-applet**' and/or '**indicator-applet-session**' - as [an alternative]("http://ubuntuforums.org/showthread.php?t=1966370&page=2&p=11900657#post11900657") to 'indicator-applet-complete'

'**gnome-tweak-tool**' - because it's quite convenient for general theming tweaks such as [having the old-style icons appear on the desktop]("http://ubuntuforums.org/attachment.php?attachmentid=251605"), [setting the key sequence for killing X]("http://ubuntuforums.org/attachment.php?attachmentid=251606"), and [changing themes]("http://ubuntuforums.org/attachment.php?attachmentid=251607").

'**shiki-colors-metacity-theme**' - because it provides a rather [URL="http://ubuntuforums.org/attachment.php?attachmentid=249048&d=1388468652"]retro window management button theme
[/URL]
'**sensors-applet**' - [to display system temps]("http://ubuntuforums.org/attachment.php?attachmentid=249045&d=1388463838")

'**dconf-tools**' which provides the dconf Editor UI.

'**caffeine**' which serves as a replacement for 'gnome-inhibit-applet' so the screensaver can be disabled while viewing flash videos just by clicking on [the "coffee cup" in the panel]("http://ubuntuforums.org/attachment.php?attachmentid=252307&d=1398053559"). It must initially be launched from the Accessories menu, but it's not in the standard Ubuntu repos so if you want it you'll have to install [this PPA]("https://launchpad.net/~caffeine-developers/+archive/ppa") and update the repos:

```
sudo add-apt-repository ppa:caffeine-developers/ppa
```

```
sudo apt-get update
```

Of those I know I personally want 'indicator-applet' because I prefer using it along with the standard clock applet, 'gnome-tweak-tool', 'shiki-colors-metacity-theme', 'sensors-applet', 'dconf-tools', and 'caffeine'. I can do that in just one more command since I've already installed the caffeine PPA and updated the repos:

```
sudo apt-get install indicator-applet shiki-colors-metacity-theme sensors-applet dconf-tools caffeine gnome-tweak-tool
```

**Note**: If I'm starting with Ubuntu GNOME I additionally install 'light-themes' because ATM only the Ambiance theme seems to work well enough for my liking, and I believe you'll find that both 'gnome-tweak-tool' and 'dconf-tools' are already installed in Ubuntu GNOME.

I can then begin configuring the panels and desktop to my liking. I prefer just one panel at the bottom but there is no "one size fits all":

[ATTACH=CONFIG]252269[/ATTACH]

**There are still a few things that must be done using either the dconf Editor or via CLI** (the highlighted links show the actual position in the dconf Editor):

**Step #5**: [Move the window management buttons to the right]("http://ubuntuforums.org/attachment.php?attachmentid=252325&d=1398092959") if you wish:

```
gsettings set org.gnome.desktop.wm.preferences button-layout :minimize,maximize,close
```

**Step #6**: [Disable the overlay scrollbars]("http://ubuntuforums.org/attachment.php?attachmentid=251984&d=1397309461") if you wish:

```
gsettings set com.canonical.desktop.interface scrollbar-mode normal
```

**Step #7**: [Disable the Unity webapps]("http://ubuntuforums.org/attachment.php?attachmentid=248456&d=1386605099") if you wish:

```
gsettings set com.canonical.unity.webapps integration-allowed false
```

**Step #8**: Restore the missing [menu]("http://ubuntuforums.org/attachment.php?attachmentid=252327&d=1398095646") and [button]("http://ubuntuforums.org/attachment.php?attachmentid=252328&d=1398095646") icons:

```
gsettings set org.gnome.desktop.interface menus-have-icons true
```

```
gsettings set org.gnome.desktop.interface buttons-have-icons true
```

That's about all I know so far.

**Challenges and Known Issues - [COLOR="#FF0000"]any help would be deeply appreciated[/COLOR]**

**#1**: This scares me the most - I've not found a truly reliable method of backing up and restoring a customized configuration, or even resetting all defaults to an out-of-box configuration. I'm sure I'll figure it out but I've borked things badly enough a few times that I've had to completely reinstall the OS, not a big deal for me but that would really make some people mad! I have figured out a few things:

**(a)** You can reset the panel configuration to it's defaults by running:

```
dconf reset -f /org/gnome/gnome-panel/
```

But that produces a false crash report so please don't file it. No log-out is needed but it takes at least one full minute for the panels to reset so please be patient.

**(b)** Optionally you can reset the panel configuration to it's defaults by running:

```
XDG_MENU_PREFIX="gnome-flashback-" gnome-panel --replace &
```

But that requires logging out or restarting via terminal or by the use of keyboard shortcut.

**(c)** You can reset most general theming and desktop tweaks to their defaults by running:

```
dconf reset -f /org/gnome/desktop/
```

**(d)** If you bork the Main Menu it can be launched using the command "alacarte" either in a terminal or using the "panel-run-dialog" - no sudo is needed - then it can be [reset to the default configuration]("http://ubuntuforums.org/attachment.php?attachmentid=252567&d=1398598654").

(e) You can also [launch the dconf Editor using the "panel-run-dialog"]("http://ubuntuforums.org/attachment.php?attachmentid=252568&d=1398598654") if you know exactly what you're looking for. [Here's one example]("http://ubuntuforums.org/showthread.php?t=2217817") where I found it quite useful.

**#2**:  The LibreOffice menu icons load very slowly. I've just been removing all but the main LibreOffice menu item, but I suppose a bug report should be filed?

**#3**: Some (maybe most) keyboard shortcuts are not set to their respective defaults. This is where dconf Editor comes in handy. [Here's an example]("http://ubuntuforums.org/showthread.php?t=2217877&p=12993104#post12993104").

**#4**: Many of the themes I've tried have various problems. I'm sure the theme devs just need some time to catch up with the changes between GNOME 3.8 and 3.10.

---

### Post by kansasnoob on 2014-04-21
Probably need to add a bit about caffeine:

[ATTACH=CONFIG]252307[/ATTACH]

---

### Post by kansasnoob on 2014-04-21
And wm button placement in dconf:

[ATTACH=CONFIG]252325[/ATTACH]

---

### Post by kansasnoob on 2014-04-21
And menu and button icons:

[ATTACH=CONFIG]252327[/ATTACH]

[ATTACH=CONFIG]252328[/ATTACH]

---

### Post by kansasnoob on 2014-04-27
Need to link a better description of the 'panel-run-dialog' and a picture is worth a thousand words:

[ATTACH=CONFIG]252566[/ATTACH]

Need to add two more:

[ATTACH=CONFIG]252567[/ATTACH]

[ATTACH=CONFIG]252568[/ATTACH]

---

### Post by EnglishElectricAndy on 2014-05-04
Regarding this
> I've not found a truly reliable method of backing up and restoring a customized configuration,
Have you investigated the 'fsarchiver' app, available in the repos?

With the caveat that I've only recently started using it, and of course future MMV, I backed up and experimentally restored my entire Xubuntu 13.10 partition complete with numerous XFCE tweaks and fiddles. The restoration experiment was completely successful, bringing back all my customizations. Since it operates at partition level I can't see it not working with a highly configured Gnome installation.

Hope this may be of help.

---

### Post by sudodus on 2014-05-04
> **EnglishElectricAndy said:**
> Regarding this
> I've not found a truly reliable method of backing up and restoring a customized configuration,
Have you investigated the 'fsarchiver' app, available in the repos?

With the caveat that I've only recently started using it, and of course  future MMV, I backed up and experimentally restored my entire Xubuntu  13.10 partition complete with numerous XFCE tweaks and fiddles. The  restoration experiment was completely successful, bringing back all my  customizations. Since it operates at partition level I can't see it not  working with a highly configured Gnome installation.

Hope this may be of help.

There is also the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), where you can make your own tarball.

---

### Post by kansasnoob on 2014-05-04
> **EnglishElectricAndy said:**
> Regarding this

Have you investigated the 'fsarchiver' app, available in the repos?

With the caveat that I've only recently started using it, and of course future MMV, I backed up and experimentally restored my entire Xubuntu 13.10 partition complete with numerous XFCE tweaks and fiddles. The restoration experiment was completely successful, bringing back all my customizations. Since it operates at partition level I can't see it not working with a highly configured Gnome installation.

Hope this may be of help.

I'll check that out. I recently created a backup with dejadup for the first time but I haven't yet tried restoring it because I got tied up with another project.

---

### Post by kansasnoob on 2014-05-04
> **sudodus said:**
> There is also the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), where you can make your own tarball.

I'll have to check that out sometime.

---

### Post by lauricat on 2014-08-29
This is a great thread Kansasnoob...many thanks.

I have follwed most of your tips/instructions via some other resources on the www, and here. 

Also, I have found some of settings you have changed using Ubuntu tweak, tweaks, then theme.

Cheers & thanks

~L.

---

### Post by kansasnoob on 2014-08-29
> **lauricat said:**
> This is a great thread Kansasnoob...many thanks.

I have follwed most of your tips/instructions via some other resources on the www, and here. 

Also, I have found some of settings you have changed using Ubuntu tweak, tweaks, then theme.

Cheers & thanks

~L.

I hope you saw this:

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

---

