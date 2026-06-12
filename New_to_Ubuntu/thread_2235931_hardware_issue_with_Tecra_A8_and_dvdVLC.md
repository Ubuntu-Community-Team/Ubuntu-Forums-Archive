---
title: "hardware issue with Tecra A8 and dvd/VLC"
date: 2014-07-23
forum: New to Ubuntu
---

### Post by bnjmnlrd on 2014-07-23
Greetings all. I'm just getting started here so here goes. 

I installed Xubuntu on my aging Tecra A8 all seems to work except for the dvd player. I've tried other media players with no success. What I do get with VLC is this error.

 [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/srO".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvd:///dev/srO'. Check the log for details.

any assistance would be appreciated. 

FYI, major noob alert.
[/COLOR]

---

### Post by MidnightGrey on 2014-07-23
It sounds like your DVD Drive is either incorrectly mounted, or not being mounted at all.
First lets take a look at what VLC is logging:

1. Create a blank file somewhere (like your home dir).
2. in VLC > Preferences > Show Settings: ALL > Advanced > Logging > Select your newly created file > Save.
3. try to open your dvd again and then copy/paste the error output here so we can see what happening.

---

