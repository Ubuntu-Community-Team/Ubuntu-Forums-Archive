---
title: "Musescore bombed after upgrade."
date: 2023-04-14
forum: New to Ubuntu
---

### Post by huffmanp on 2023-04-14
I was trying to get back into Ubuntu just to use Musescore.  I repurposed an old desktop PC for which my wife couldn’t remember the password, found an old Ubuntu 20.04 install CD, installed, received some system upgrades, and was stable for a few weeks.  I had a picture of a panther on the desktop. I did a few projects in Muscore, my printer worked fine, and I could air drop to my iPad.  Today, I took the option presented to me to upgrade Ubuntu. Ended up with a jellyfish. Now Musescore startup gives me a black window.  I don’t know what it means that the Musescore program circle icon on the left margin of the desktop is rocking. Already tried powering down and restarting.  Can I fix this? Can I roll back to an OS version that was working for me.  Or should I reinstall from the CD again? I have backups of my Musescore projects on Dropbox so I could be back in business pretty quickly, but I do have a gig tonight.

---

### Post by DuckHook on 2023-04-14
Were I in your shoes, I would do a new install with 20.04, do a quick restore and be operational ASAP rather than try playing detective hunting down the issue. It's more important to get to a production environment than looking for answers right now. Once you have more time, that's when you can sleuth for solutions.

Alternatively, you just stick with Focal (20.04). It still has two years of life left and there's really nothing wrong with sticking with a LTS release to the end if it works for you. You can even sign up for Ubuntu Pro and get 10 years of support, although that might apply only to the base OS and not to Musescore itself.

A third option would be to install a fresh install of 22.04 and install Musescore from the new repos. Your problem could be due to inheriting Musescore config files from 20.04 that don't quite work properly in 22.04. As mentioned, chasing down such issues is time consuming and frustrating, so best to work with a known good configuration for now until your time pressure is off.

Incidentally, I can't do music to save my life, but Musescore looks like an interesting app.

---

### Post by DuckHook on 2023-04-14
Upon further research, this might be your problem:
```
duckhook@Zeus:~$  apt show musescore
Package: musescore
Version: 2.3.2+dfsg4-15
Priority: optional
Section: universe/sound
Source: musescore2
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Thorsten Glaser <tg@mirbsd.de>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 16.6 MB
Provides: musescore2
Depends: libasound2 (>= 1.0.16), libc6 (>= 2.29), libfreetype6 (>= 2.5.2), libgcc-s1 (>= 3.3.1), libportaudio2 (>= 19+svn20101113), libportmidi0, libpulse0 (>= 0.99.1), libqt5core5a (>= 5.15.1), libqt5gui5 (>= 5.14.1) | libqt5gui5-gles (>= 5.14.1), libqt5help5 (>= 5.6.0~beta), libqt5network5 (>= 5.14.1), libqt5printsupport5 (>= 5.0.2), libqt5qml5 (>= 5.4), libqt5quick5 (>= 5.6.1) | libqt5quick5-gles (>= 5.6.1), libqt5svg5 (>= 5.6.0~beta), libqt5widgets5 (>= 5.14.1), libqt5xml5 (>= 5.0.2), libqt5xmlpatterns5 (>= 5.0.2), libsndfile1 (>= 1.0.20), libstdc++6 (>= 5.2), libvorbisfile3 (>= 1.1.2), zlib1g (>= 1:1.1.4), desktop-file-utils, fonts-freefont-ttf, qml-module-qtquick-controls, qml-module-qtquick-dialogs, qml-module-qtquick-layouts, qml-module-qtquick2, shared-mime-info, xdg-utils, musescore-common (>> 2.3~), musescore-common (<< 2.4~)
Recommends: libmp3lame0
Suggests: pulseaudio-utils
Homepage: https://musescore.org/en
Download-Size: 5,195 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu jammy/universe amd64 Packages
Description: cross-platform multi-lingual music composition and notation, v2
 MuseScore is an Open Source (GNU GPL) music notation software that runs
 on all platforms supported by Qt5 (GNU/Linux, MacOS X, Windows), and is
 available in over forty different languages. It features an easy to use
 WYSIWYG editor with audio score playback for results that look and sound
 beautiful, rivaling commercial offerings like Finale and Sibelius.
 .
 This package provides MuseScore 2. [B]You can install multiple versions of
 MuseScore in parallel, and upstream recommends doing so, because [COLOR="#FF0000"]each
 major version has a new, incompatible, layout engine, and changing old
 scores without relayouting them fully with the new version can only be
 done by the old version.[/COLOR] Install the musescore3 package for MuseScore 3
 and expect a musescore4 package to show up in Debian bookworm.[/B]

--snip--
```
Note the portion that I've highlighted. In other words, different versions of the app are indeed incompatible with each other. Therefore, your data produced in the version that comes with Focal may not work with the version in Jammy. Since you are attempting to restore from Focal, definitely stick with reinstalling Focal for now and resist that urge to upgrade until you have fully figured out how to move your data nicely.

---

### Post by huffmanp on 2023-04-16
hey, thanks, I didn't know if anyone had responded to my question.  A few days ago,  I re installed from my 20.04 CD and yesterday reinstalled Musescore.  I was a bit confused when I didn't find Musescore this time in the Ubuntu software store.  Somehow the way I got to the software listing, Musescore wasn't presented.  I went to the Musescore site and downloaded an AppImage file for Musescore 4. Then I looked up what to do  with an AppImage file.  The AppImage file started the program but didn't run well.  Then I looked in the App Store from the icon on the left side bar of my Ubuntu desktop, and Musescore was listed as an Editor's Choice.  I installed that and it seems to be running well.  I installed Dropbox and got my projects back and did a little more work on them.  However, this is Musescore 3.6.2 and in the top bar of the program window it says (3.6.2 unstable). that has me worried. Also it is putting my projects, reading and writing them to $home/documents/Musescore4/Scores rather than ../../Musescore3Development.  I'm guessing the AppImage made the 4 tree and the install from store made the 3 tree.  

Not sure if I want to try updating the OS or programs again. Maybe I caused my first problem by upgrading the OS when I still had Musescore running.  Now I get that the little orange circles on the left mean something is running.  

I used to run Solaris systems when I was working. I had installed Ubuntu back in 2021 on a couple systems, but I am unfamiliar with its ways.

---

