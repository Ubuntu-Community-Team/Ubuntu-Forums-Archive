---
title: "Messed up streaming vids"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by TooRight on 2008-06-20
If it's not broke, don't fix it!!!

Why don't I ever listen? lol *sigh*

I had my Hardy working great, all vids except for divx were playing properly in my browser, but I had to be greedy and push for the divx :(

I copied and pasted some stuff in the terminal, following various guides, BUT, not only do the divx vids still NOT play in firefox, but the vids on sites like zshare.net don't play like they used to...instead it shows a black area with the words Mplayer in it and buffering so-many percent. Then the SOUND of the video starts along with showing the video path, but that's it, no video :(

Is there anyway to get my comp back the way it was before I got fiddling with it? lol

---

### Post by Dynaflow on 2008-06-20
What, exactly, were you pasting into the terminal, and which guides were you following?

---

### Post by ajgreeny on 2008-06-20
If you can't remember your commands in terminal go to the hidden file in /home called **.bash_history** or simply type ```
history
``` in terminal.  This may help you to undo whatever you did.

---

### Post by TooRight on 2008-06-20
I was following this one here:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

and my history is this:

> 
  122  sudo apt-get remove totem-mozilla
  123  sudo apt-get install mplayer-mozilla vlc
  124  sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
  125  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
  126  gksudo gedit /etc/apt/sources.list
  127  sudo apt-get remove totem-mozilla
  128  sudo apt-get install mozilla-plugin-vlc
  129  sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre && sudo apt-get install alsa-oss libflashsupport libk3b2-extracodecs liblame0 libtunepimp5-mp3 libxine1-ffmpeg sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs
  130  sudo apt-get install alsa-oss libk3b2-mp3 liblame0 libtunepimp5-mp3 libxine1-ffmpeg sun-java6-fonts sun-java6-jre sun-java6-plugin unrar w32codecs
  131  sudo apt-get remove totem-mozilla mozilla-plugin-vlc xine-plugin kaffeine-mozilla helix-player mozilla-helix-player
  132  sudo apt-get install mplayer mozilla-mplayer
  133  gedit $HOME/.mplayer/mplayerplug-in.conf
  134  rm $HOME/.mozilla/firefox/pluginreg.dat
  135  sudo apt-get update




with the line numbers removed, of course... mannn, what a mess I made of it all, lol

---

