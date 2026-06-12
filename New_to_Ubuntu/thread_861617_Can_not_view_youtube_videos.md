---
title: "Can not view youtube videos"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by XxUn70ucHaBlExX on 2008-07-16
Well here it goes, my explanation on what's going on.

- Youtube won't load any videos.
- Flash says it's installed and everything.

So can anyone help me completely remove flash and the flash plugin in firefox or whatever in order to do a complete reinstall?

I would love it if someone could write out every step for uninstalling, then install again in order for flash to work 100%.

Thanks in advance!!:)

---

### Post by tuxxy on 2008-07-16
Open Synaptic and search for " flashplugin-nonfree " 

Once you find it you can try to re-install the driver and if no luck remove it and just install the ubuntu-restricted-extras multiverse package :)

[http://packages.ubuntu.com/hardy/ubuntu-restricted-extras](http://packages.ubuntu.com/hardy/ubuntu-restricted-extras)

---

### Post by carandraug on 2008-07-16
1. Go to the menu "system" in the top right corner of the monitor. In the submenu "administration" choose "synaptic package manager".
2. Search the name flashplugin-nonfree. It should appear with a green box if it's really installed.
3. Right click on it and choose "Mark for complete removal".
4. Click on apply (one of the option in the top of the window.

To install it again it's exactly the same thing but this time the box should appear white and you choose "Mark for installation" .

If when when uninstalling the box doesn't appear green but firefox says a flash plugin is installed, maybe you have Gnash (open source alternative to Adobe's flash plugin that used to have problems with youtube and the like) installed. If that's the case, uninstall gnash and then install flashplugin-nonfree.
Other reason for not playing youtube movies may be that you accidentaly installed some extension that blocks everything that's flash.

---

### Post by bumanie on 2008-07-16
I too have been having trouble with youtube. Just installed flash 10 from [here]("http://labs.adobe.com/downloads/flashplayer10.html") and it now works.

---

### Post by RomeReactor on 2008-07-16
> **XxUn70ucHaBlExX said:**
> Well here it goes, my explanation on what's going on.

- Youtube won't load any videos.
- Flash says it's installed and everything.

So can anyone help me completely remove flash and the flash plugin in firefox or whatever in order to do a complete reinstall?

I would love it if someone could write out every step for uninstalling, then install again in order for flash to work 100%.

Thanks in advance!!:)

There should be no need to reinstall, or to install Flash from Adobe's site; the problem could be Gnash being installed also and interfering with the Flash plugin. To remove Gnash, close Firefox, open a terminal (Applications->Accessories->Terminal) and paste this:
```
sudo aptitude purge mozilla-plugin-gnash
```
The open Firefox again and see if Flash is working now.

---

### Post by edwin2105z on 2008-07-17
i had the same problem. go to youtube then try watching a video at the top of the screen under the address bar a faded yellow bar will appear and just click on that and follow the step by step instructions.

---

### Post by kansasnoob on 2008-07-17
I view a lot of "flash" video and basically video of every sort, and I've had few problems. I start by installing the Medibuntu repository, I'll leave it to you to choose which repo is right for your Ubuntu, and **remember to add the GPG key!**

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

After that's done I open Synaptic and go to Settings > Repositories which opens Software Resources. Make sure it looks like this:

[ATTACH]77995[/ATTACH]

[ATTACH]77996[/ATTACH]

[ATTACH]77997[/ATTACH]

Now, once that's done, click on the Reload button in the upper left hand corner of Synaptic. When the "wizard" is done running you'd be wise to look at the lower tool-bar and see if anything is identified as "broken", needing "upgrade", etc. If so click on "Mark all Upgrades" and then "Apply" but read the list! I just like to look and know what I'm installing or upgrading, etc. Sometimes I even make notes just in case everything blows up it's helpful with troubleshooting.

Then I start installing goodies that have always worked for me. I just use the "search" button to find what I want rather than scrolling through the list which is incredibly long! My list:

gstreamer  (ALL gstreamer, good, bad, and ugly - if it starts with   "gstreamer" install it!)

totem
totem-common
totem-gstreamer
totem-mozilla
totem-plugins
totem-plugins-extra
totem-xine

NOTE: I also search for mplayer and remove ALL mplayer. Some people disagree and would go as far as removing all totem and installing all mplayer, this is simply what's worked best for me! Choices, choices, eh:confused:

sun-java6  (ALL sun-java6 except -doc and -source, -doc is unnecessary and -source breaks things!)

vlc (needed libraries are normally "pulled in")

flashplugin-nonfree

ubuntu-restricted-extras

non-free-codecs

acroread   (ALL acroread, if it starts with acroread just install it, this is Adobe!)

vlc-plugin-pulse
libflashsupport   (both of these are needed for Pulse audio support in Hardy)

Then just click install, you'll be asked a few simple questions, and you'd be wise to run a simple 

```
sudo apt-get update
```

and then restart but it works for me.

---

### Post by Cotopaxi on 2008-07-17
Eventually the instructions in the following link are just the repetition in the instructions of previous posts, but following these instructions worked marvellously well for me (Kubuntu Hardy & Opera):

[http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html](http://wvarner.blogspot.com/2008/05/firefox-crashing-on-youtube-in-ubuntu.html)

The following link discribes my instructions for making the Flash 10 work under opera:

[http://my.opera.com/community/forums/topic.dml?id=239966](http://my.opera.com/community/forums/topic.dml?id=239966)

Good luck!

---

### Post by joegiard1408 on 2008-10-03
RomeReacter1
Worked For Me Thanks!!!!!!:D

---

