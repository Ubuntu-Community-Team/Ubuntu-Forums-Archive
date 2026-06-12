---
title: "Sound card and overheating issues"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by hul on 2008-06-28
My computer overheated a few days ago.  Since then, my speakers have been buzzing.   Things are fine when the computer first boots up, but after about five or ten minutes the buzzing sets in.  I'm pretty sure it's my soundcard, not my speakers, as I've tried another set of speakers and headphone and the buzzing still happens.

I'm also pretty sure it's related to the computer getting too hot, as it's only when the computer really starts working that the buzzing starts.

I have no idea how to proceed from here.  I knew how to diagnose hardware issues on my old laptop and monitor the temperature, but I don't know anything about my desktop.  Is there a way to diagnose hardware issues in Ubuntu?  Is there a way to monitor the temperature of my computer?  What should my next step be?

---

### Post by Diabolis on 2008-07-22
Theres an applet for gnome-panel that does this.
```
sudo apt-get install hardware-monitor
```

---

### Post by northern lights on 2008-07-22
As for the hardware monitoring, I'd look into "conky" - [http://conky.sourceforge.net/]("http://conky.sourceforge.net/").

Has the card worked fine under your current distribution before, or was that the case under a different OS only?

Make & model?

In case u don't know, can you post the output of ```
cat /proc/asound/cards
```

---

