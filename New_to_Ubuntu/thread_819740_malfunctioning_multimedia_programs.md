---
title: "malfunctioning multimedia programs"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by pranayama on 2008-06-05
I don't know when it happened but my sound and audiovisual files have become a problem to play.

Trying to play flac with Amarok gives the error message:

[i]Audio output unavailable; the device is busy.

xine parameters:[/i]

Totem Movie Player plays the first second of flv and wma files, then stops, saying:

*Invalid argument: failed to connect to stream*

VLC is working fine and the Applian free FLV player is working in Wine.

I don't normally use Rhythmbox but that won't play anything either.

Any ideas?

---

### Post by original_jamingrit on 2008-06-05
I have a friend who just phoned me with the same problems with totem with .avi and .wav files (that were working before), given the same *failed to connect to stream* error.  I suggested VLC and he's cool for now, but I'd like to fix it for real next time I'm over at his place.  He told me totem worked fine before the most recent update?

---

### Post by pranayama on 2008-06-06
It did work fine before the *second* most recent update. I installed another set of updates almost 24 hours ago, wondering if they might fix things...

Since that second last update I did fiddle with the login window a little and I tried out some KDE sounds which the Gnome desktop didn't like for one session, but that's all gone away of its own accord.

---

### Post by DM was on fire! on 2008-06-06
Not sure about amaroK, but if there are multiple people having a problem with Totem after the update, I'd say it's a bug in the latest version. 
Did you upgrade amaroK recently as well?

---

### Post by pranayama on 2008-06-29
Bump. Still no solution has popped up. I've given up on Totem and Rhythmbox, I tried installing Exaile and Banshee but they wouldn't play a single song either.

For Amarok, I have done sudo apt-get --purge remove, apt-get clean, apt-get autoclean, updatedb, then hunted down and deleted the files with amarok in the title that still remained, and reinstalled.

Amarok still didn't ask for reconfiguration. The same error message comes up.

I wish I could figure it out, curiosity's sake.

---

