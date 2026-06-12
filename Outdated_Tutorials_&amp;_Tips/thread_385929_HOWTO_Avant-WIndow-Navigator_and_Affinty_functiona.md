---
title: "HOWTO: Avant-WIndow-Navigator and Affinty: functional eye-candy"
date: 2007-03-16
forum: Outdated Tutorials &amp; Tips
---

### Post by reacocard on 2007-03-16
This thread is depreciated, because it took too long to go through the moderation system (for which there is no feedback, which would be *extremely* helpful *hint,hint*). Please use this thread instead:

[[SIZE="4"] HOWTO: functional eye-candy with Avant-Window-Navigator and Affinity[/SIZE]]("http://ubuntuforums.org/showthread.php?t=385981")

Thank you.

---

### Post by dbbolton on 2007-03-22
thanks for posting this !

however, aptitude gave this error: *couldn't find package affinity*

---

### Post by reacocard on 2007-03-23
> **dbbolton said:**
> thanks for posting this !

however, aptitude gave this error: *couldn't find package affinity*

The package is either affinity-tracker or affinity-beagle, depending on the searching backend you want to use. I recommend Tracker, you can get Ubuntu packages for it here: [http://www.gnome.org/projects/tracker/start.html](http://www.gnome.org/projects/tracker/start.html)

---

### Post by reacocard on 2007-03-23
Gah. This FINALLY went through? Mods, please delete/merge this thread, I got fed up with waiting for approval and posted it here instead: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

There REALLY needs to be some way to see what the status for your guide's approval is. The current situation only leads to double-threads like this. Even just a PM saying 'Your thread is currently being considered.' and later 'Your thread has been approved/rejected' would be a BIG help.

---

### Post by BOBSONATOR on 2007-03-25
When you guys are done configuring, post your settings [here!]("http://ubuntuforums.org/showthread.php?p=2352391#post2352391")

---

### Post by PaulFXH on 2007-04-08
I've used AWN for about 2 months and like it a lot. The first screenshot is how it looks on my desktop.

Given how much I liked AWN, I tried Affinity a few days ago but it really doesn't do what I had expected.
So while typing "apps:beryl" immediately gives me all of the Beryl apps on my computer, if I type "music:.mp3" I get nothing at all in spite of the fact that I have a lot of .mp3 files in my Home directory. Indeed, if I go the Home directory/folder and search for .mp3 files all of them come up almost instantaneously.
So why can't Affinity do that?

Another (although lesser) annoyance with Affinity is that if I launch it from AWN a small icon appears in the upper panel on the RHS (you can see this in the second screenshot).
If I shut Affinity down from AWN and open it again, a SECOND small icon shows up in the upper panel.
Pretty soon, after a lot of use of Affinity, there's a bunch of these little icons up there.
Anybody know how to eliminate these Affinity annoyances?

---

### Post by reacocard on 2007-04-08
> **PaulFXH said:**
> I've used AWN for about 2 months and like it a lot. The first screenshot is how it looks on my desktop.

Given how much I liked AWN, I tried Affinity a few days ago but it really doesn't do what I had expected.
So while typing "apps:beryl" immediately gives me all of the Beryl apps on my computer, if I type "music:.mp3" I get nothing at all in spite of the fact that I have a lot of .mp3 files in my Home directory. Indeed, if I go the Home directory/folder and search for .mp3 files all of them come up almost instantaneously.
So why can't Affinity do that?

Another (although lesser) annoyance with Affinity is that if I launch it from AWN a small icon appears in the upper panel on the RHS (you can see this in the second screenshot).
If I shut Affinity down from AWN and open it again, a SECOND small icon shows up in the upper panel.
Pretty soon, after a lot of use of Affinity, there's a bunch of these little icons up there.
Anybody know how to eliminate these Affinity annoyances?

Keep in mind affinity is ALPHA software: there are still lots of bugs. The mp3 thing is because affinity doesn't do filenames yet, I think (I wish it did too.)  As for the panel issue, yes that happens, affinity doesn't prevent dual instances yet. However, you can get it back without launching another instance by clicking the panel icon, or by pressing affinity's key combo, CTRL+ALT+A by default. To quit affinity completely, right-click the icon and choose 'Close'.

---

### Post by PaulFXH on 2007-04-08
Thanks for the reply, reacocard.
OK, it's always a relief to learn that the problem is not due to something silly I was doing (or NOT doing).
Nevertheless, I'm still a little puzzled about how ALPHA Affinity really is. In your guide, you show a screen shot where the words "music:loose" are typed and a bunch of stuff with "loose" in the album name appears.
Now, I have tried quite a number of means to try to get "music:" to show me something in Affinity (artist name, words from album or song title) but nothing works. I have also tried with with the other default filter for music stuff which is "audio" with the same negative result.
Can I assume that Affinity is still in such a tender stage of its development that what works on one computer may not necessarily work on another?

---

### Post by reacocard on 2007-04-08
> **PaulFXH said:**
> Thanks for the reply, reacocard.
OK, it's always a relief to learn that the problem is not due to something silly I was doing (or NOT doing).
Nevertheless, I'm still a little puzzled about how ALPHA Affinity really is. In your guide, you show a screen shot where the words "music:loose" are typed and a bunch of stuff with "loose" in the album name appears.
Now, I have tried quite a number of means to try to get "music:" to show me something in Affinity (artist name, words from album or song title) but nothing works. I have also tried with with the other default filter for music stuff which is "audio" with the same negative result.
Can I assume that Affinity is still in such a tender stage of its development that what works on one computer may not necessarily work on another?

Odd.  A lot of people have been using affinity, if this were common I ought to have heard of it. Which search backend are you using? Affinity doesn't search by filenames, but if the term is in the music tag it should turn up. It works fine for me with Tracker. Does searching with your search backend's default interface turn up the expected results?

---

### Post by PaulFXH on 2007-04-08
I have tracker installed (but also beagle). In addition to tracker, I have the following:
affinity-tracker-svn, libtrackerclient0, tracker-search-tool and tracker-utils. Note that during the install using your guide on libtracker file was not found.

If I run tracker and type in .mp3, it DOES pick up all of my mp3 files. However, while it will find all songs by a given artist if i type the WHOLE name, typing only a part of the name doesn't work.

Any clues what I have missed?

---

### Post by reacocard on 2007-04-08
> **PaulFXH said:**
> ...libtracker file was not found.

Do you have libtrackerclient-dev installed? If not, install it then recompile.

---

### Post by PaulFXH on 2007-04-09
Hi reacocard

Yes, it's the libtrackerclient-dev file that I'm missing simply because I couldn't install it.
Now, I've tried again and get a message about unresolvable dependencies and recommends that I make sure that all required repositores are available.

Here's the detail from this error message:
> libtrackerclient-dev:
  Depends: libtrackerclient0 (=0.5.4-1) but 0.5.4-5 is to be installed
 Depends: libdbus-1-dev but it is not going to be installed
 Depends: libdbus-glib-1-dev but it is not going to be installed

I presume it's referring to some third party stuff but which ones do I need? The two deb packages mentioned in your guide are included in my sources.list

I also tried to install libtrackerclient-dev from the Debian site but again got into an unending sequence of missing dependency error messages.

Can you please let me know what additional deb packages I need to get this file installed?

BTW, I installed beagle-dev without problems but still Affinity doesn't do anything when I type "music:" and whatever other names/titles etc.

I really woudl like to get Affinity working and would be grateful for your advice.

Thanks
Paul

---

### Post by reacocard on 2007-04-09
> **PaulFXH said:**
> Hi reacocard

Yes, it's the libtrackerclient-dev file that I'm missing simply because I couldn't install it.
Now, I've tried again and get a message about unresolvable dependencies and recommends that I make sure that all required repositores are available.

Here's the detail from this error message:

> libtrackerclient-dev:
Depends: libtrackerclient0 (=0.5.4-1) but 0.5.4-5 is to be installed
Depends: libdbus-1-dev but it is not going to be installed
Depends: libdbus-glib-1-dev but it is not going to be installed

I presume it's referring to some third party stuff but which ones do I need? The two deb packages mentioned in your guide are included in my sources.list

I also tried to install libtrackerclient-dev from the Debian site but again got into an unending sequence of missing dependency error messages.

Can you please let me know what additional deb packages I need to get this file installed?

BTW, I installed beagle-dev without problems but still Affinity doesn't do anything when I type "music:" and whatever other names/titles etc.

I really woudl like to get Affinity working and would be grateful for your advice.

Thanks
Paul

Here's a direct link to the package: [http://debs.michaelbiebl.de/dists/edgy/main/binary-i386/libtrackerclient-dev_0.5.4-1_i386.deb](http://debs.michaelbiebl.de/dists/edgy/main/binary-i386/libtrackerclient-dev_0.5.4-1_i386.deb)
Just install it with Gdebi or dpkg. I have no idea why you're getting that error from the repos as there is no 0.5.4-5 version, but installing 0.5.4-1 manually should fix it.

---

### Post by PaulFXH on 2007-04-09
Hi reacocard
Thanks for your patience in helping me out with this problem but it's really starting to turn into one of these ](*,) things.
OK, I took out the libtrackerclient0 0.5.4-5 and installed the 0.5.4.1 version (I have no idea why the version I had in Synaptic was 0.5.4-5).

Then, after downloading the libtrackerclient-dev package from the link you provided, I tried to install it with Gdebi but got an error message saying "Cannot install 'libdbus-1-dev'".

Then I went into synaptic and marked libdbus-1-dev for installation but got another error message saying "Could not mark all packages for installation or upgrade." Then followed the same stuff about unresolved dependencies and making sure the required repositories are available.
More details are here:
> libdbus-1-dev:
  Depends: libdbus-1-3 (=0.93-0ubuntu3.1) but 1.0.2-1 is to be installed
I've searched in Google for the stated version of libdbus-1-3 but I can't find it.
Any clues?

---

### Post by reacocard on 2007-04-09
> **PaulFXH said:**
> Hi reacocard
Thanks for your patience in helping me out with this problem but it's really starting to turn into one of these ](*,) things.
OK, I took out the libtrackerclient0 0.5.4-5 and installed the 0.5.4.1 version (I have no idea why the version I had in Synaptic was 0.5.4-5).

Then, after downloading the libtrackerclient-dev package from the link you provided, I tried to install it with Gdebi but got an error message saying "Cannot install 'libdbus-1-dev'".

Then I went into synaptic and marked libdbus-1-dev for installation but got another error message saying "Could not mark all packages for installation or upgrade." Then followed the same stuff about unresolved dependencies and making sure the required repositories are available.
More details are here:

I've searched in Google for the stated version of libdbus-1-3 but I can't find it.
Any clues?


Gah. Could you post your /etc/apt/sources.list? There's probably just something in there screwing up all your dependencies here.

---

### Post by PaulFXH on 2007-04-09
One /etc/apt/sources.list coming up:

> deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse
deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://br.archive.ubuntu.com/ubuntu/](http://br.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-backports restricted main universe multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) edgy avant-window-navigator
deb [http://severance.homelinux.org/falcon](http://severance.homelinux.org/falcon) main scripts
deb-src [http://severance.homelinux.org/falcon](http://severance.homelinux.org/falcon) main scripts
deb [http://debs.michaelbiebl.de/](http://debs.michaelbiebl.de/) edgy main


---

### Post by reacocard on 2007-04-09
> **PaulFXH said:**
> One /etc/apt/sources.list coming up:

```
deb http://br.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ edgy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://br.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse
deb-src http://br.archive.ubuntu.com/ubuntu/ edgy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://br.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://br.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://br.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-proposed restricted main universe multiverse
deb http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ edgy-backports restricted main universe multiverse
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://ubuntu.beryl-project.org/ edgy main
deb http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
deb http://severance.homelinux.org/falcon main scripts
deb-src http://severance.homelinux.org/falcon main scripts
deb http://debs.michaelbiebl.de/ edgy main
```

> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main universe multiverse
edgy-proposed? That could well be the problem. Try commenting those two lines out, then apt-get updating. Look in synaptic, downgrade any packages that were affected (they'd be under 'local or obsolete'), apt-get update again, then try once more.

---

### Post by PaulFXH on 2007-04-09
Thanks reacocard
OK, I did that and after the update I have about 10 packages in Installed (Local or Obsolete) in Synaptic. These include pretty essential things like Opera 9.10 (this is the browser I use), apt, Synaptic, libdbus-1-3).
So, I want to be sure what you meant when you said "downgrade" these packages.  Did you really mean "uninstall" them?

---

### Post by reacocard on 2007-04-09
> **PaulFXH said:**
> Thanks reacocard
OK, I did that and after the update I have about 10 packages in Installed (Local or Obsolete) in Synaptic. These include pretty essential things like Opera 9.10 (this is the browser I use), apt, Synaptic, libdbus-1-3).
So, I want to be sure what you meant when you said "downgrade" these packages.  Did you really mean "uninstall" them?

No, just downgrade. Use the 'Force Version' option in the Package menu to install the older version.

---

### Post by PaulFXH on 2007-04-09
Absolutely fantastic!
Very many thanks for your expert guidance, reacocard.
Affinity working perfectly now

Best wishes
Paul

---

