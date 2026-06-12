---
title: "I am trying to play audio, but failing"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by EFobes on 2008-05-27
Hi

I am trying to play audio, but failing. When I did a fresh install of Hardy I backed  up my music on CD. After Hardy was installed I proceeded to insert the back up CDs and copy/paste the files into the MUSIC folder. Then I imported the files into Rhythmbox and they wouldn't play. Nor would They play in Amarok, or any pre-installed DVD players.

To answer some anticipated questions:

I am 100% sure I backed up the Cds properly

I have looked through reassuringlyoffensive's very helpful guide (THANKS=))
and executed the following

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss compizconfig-settings-manager faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll liblame0 sun-java6-fonts sun-java6-jre sun-java6-plugin pulseaudio-utils unrar w32codecs

Funnily, when I did that, suddenly everything worked. I played some music and watched a DVD. But now, two days later suddenly I am back to square one... Except for the fact that VLC will show video but audio of the same DVD I watched 2 days ago. Rhythmbox however won;t even track across the progress line let alone play anything.

Thanks in advance for any help.

Ed

---

### Post by EFobes on 2008-05-27
Rebooted and it seems fine. Wonder if it will hold.

---

### Post by sayakb on 2008-05-27
Do mark the thread as solved. :)

---

