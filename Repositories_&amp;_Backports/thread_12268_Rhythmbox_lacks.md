---
title: "Rhythmbox lacks"
date: 2005-01-23
forum: Repositories &amp; Backports
---

### Post by andreasDK on 2005-01-23
I installed Warty yesterday and was extremely pleased with it so I ripped some of my cds with soundjuicer to ogg vorbis and had no problem playing them.

When I booted the PC today none of my songs would play. Not using Rhythmbox nor Totem.

The system has been fully updated using the apt-get dist upgrade.

What am I missing here??

The system sounds as well as CdPlayer works fine.

---

### Post by andreasDK on 2005-01-23
Reinstalled Rhythmplayer using Synaptics - no change

---

### Post by Quest-Master on 2005-01-23
sudo apt-get install gstreamer0.8-mad

Do that in the terminal and MP3s will work fine with Rhythmbox.

---

### Post by andreasDK on 2005-01-23
Done, but my problem is the ogg files.

Somehow I doubt the format is the problem - more likely Rhythmbox hence it skips to the next sogn after  2 - 10 secs.

---

### Post by Quest-Master on 2005-01-23
[QUOTE=andreasDK]Done, but my problem is the ogg files.

Somehow I doubt the format is the problem - more likely Rhythmbox hence it skips to the next sogn after  2 - 10 secs.[/QUOTE]
 Just do this.

sudo apt-get install beep-media-player

Plays both MP3s and OGGs as well as many other formats. Plus, it uses GTK2. :D

---

### Post by Psy on 2005-01-23
But beep lacks a media library, which makes rhythmbox superior IMO, and not really a solution. :-)

---

### Post by Humboldt on 2005-01-23
Open a console and try "gst-register-0.8"
This update your gstreamer settings in your home directory.

---

### Post by andreasDK on 2005-01-23
None of the above ideas worked.

Starting to wonder whether I should reinstall the darn thing...

Is this a normal problem or am I just unlucky?

---

### Post by relux on 2005-01-23
[QUOTE=Psy]But beep lacks a media library, which makes rhythmbox superior IMO, and not really a solution. :-)[/QUOTE]

I would take a look at amarok.kde.org.  Yes, it's a QT application. But I have used it for quite awhile now in gnome.  I like it because of the equalizer. If rhythmbox had a eq I would use it.

---

