---
title: "What is the best option for installing anyway?"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by bilbo.san on 2008-05-09
First, I have to thank all of you guys for all the support, tips and suggestions to make this switching to Ubuntu process quite cool.

Now, I read in many different threads tips for installing stuff... use Synaptic, or use Add/Remove Programs or use the Terminal... but what is the best and what is the difference between them?... perhaps the combination of all is good... but I am sure that there is one that should be the best or more stable perhaps.


Thanks again.
b.

---

### Post by Joeb454 on 2008-05-09
The all do the same thing.

The terminal is just the easiest way to do it if you know the package name (which I tend to use most often). You can do this by entering ```
sudo aptitude install <package>
``` <package> could be any number of things here :)

Add/Remove is nice and User Friendly - it lives in the Applications menu

Synaptic gives more detail about the packages (like the version number etc.) and it lives in System > Adminstration :)

I hope this helps (if only a little)

---

### Post by zach382 on 2008-05-09
Yeah they all do the same thing. They all technically use the synaptic package management system. Just different ways of interfacing with it. If you even want another way type sudo aptitude in your terminal and youll get another way as well.

---

### Post by bilbo.san on 2008-05-09
ok... I think I have it more clear. But, if using the terminal... how would know the name of the package?... how can you tell?

b.

---

### Post by Xiong Chiamiov on 2008-05-09
You would only know because you saw it somewhere.  For instance, someone tells you, "You should try amarok", so you try
```

sudo apt-get install amarok

```
because that's most likely it.

Aside from installing through apt, there are a few other options.  Debian files (.deb) will install into apt, so you'll be able to remove them just like anything else; they just won't update themselves automagically.  The second most common is compiling from source, which won't appear in Synaptic or get updated by itself (read, I forget it's installed).  When you get to installing stuff, there's a super-excellent guide [here]("http://monkeyblog.org/ubuntu/installing/").

---

### Post by amingv on 2008-05-09
Or:
```
user@local:~$ **apt-cache search amarok**
amarok - versatile and easy to use audio player for KDE
amarok-xine - xine engine for the Amarok audio player
kopete - instant messenger for KDE
vorbisgain - add Replay Gain volume tags to Ogg Vorbis files
amarok-engines - output engines for the Amarok audio player
exaile - flexible audio player, similar to Amarok, but written in GTK+
gnome-do-plugin-amarok - Extra functionality for GNOME-Do launcher (Amarok plugin)
ipodslave - kio-slave for ipods
kamefu - KDE All Machine Emulator Frontend for Unix - binary files
kamefu-data - Data files for Kamefu
kopete-kde4 - instant messenger for KDE 4
libkamefu-dev - Development headers for Kamefu
libkamefu0 - Libraries for Kamefu
lineak-kdeplugins - LinEAK KDE plugins
minirok - a small music player written in Python and inspired by Amarok
moodbar - Analysis program for creating a colorful visual representation of an audio file
pidgin-musictracker - Plugin for Pidgin which displays the current music track in your status
syncropated - An application for syncing music player playlists with mass storage devices
user@local:~$
```

Also, tab-completion is your friend.

---

### Post by tir109xo on 2008-05-09
Somewhere I read that using one of the installers over another made uninstalling more clean.  Not sure where I read that, but that may make a difference if you don't know if you want to keep an app for very long.  I'll look around and see if I can find where I read that.

---

### Post by Xiong Chiamiov on 2008-05-09
amingv: ah yes, I forgot that.

I believe that uninstalling using the command aptitude (as opposed to apt-get) will removed unused packages as well.  When using apt-get, you have to run 
```

sudo apt-get autoremove

```
But sometimes you don't want to remove the dependcies.

---

### Post by tir109xo on 2008-05-09
Found where I read a short discussion on apt-get vs. aptitude:

[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

looks like at one point aptitude was better at removing dependencies but after fawn or so, it doesn't make a diffence.

---

### Post by Joeb454 on 2008-05-10
> **Xiong Chiamiov said:**
> The second most common is compiling from source, which won't appear in Synaptic or get updated by itself (read, I forget it's installed).

Not quite, if you do ```
sudo make install
``` then yes it will, however if you install *checkinstall* then I believe this add's it to the updater.

I'm not 100% sure on this, but I compiled aMSN from source, and used checkinstall, there was an update for it a day or 2 after.

To use checkinstall, the command is run **after** the make command ```
sudo checkinstall
```

---

