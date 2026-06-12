---
title: "[SOLVED] flash not working/youtube was working"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by Joshfan on 2008-08-02
i have installed Gnash/adobe flash and previously it was working, know it will not play anything the Youtube page is blank, how do i get it to work?
The only way to see vids is to go in Terminal and type: youtube-dl and then the url and then i can watch them.

---

### Post by sdowney717 on 2008-08-02
how about uninstall gnash and adobe flash and then reinstall just adobe flash non free.
You can use synaptic for this

---

### Post by Joshfan on 2008-08-02
worked great i can now watch vids but know it is slow it runs choppy like it is in slow motion. how do I get a good stream going again.

---

### Post by tuxxy on 2008-08-02
Using Opera?

---

### Post by Joshfan on 2008-08-02
No, I use fir fox, why does it work better in the Opera browser?

---

### Post by Locke_99GS on 2008-08-02
I gave up on Firefox crashing in Youtube, and choppy fullscreen viewing. Perhaps someday I'll get it figured out properly.

In the meantime, I just use the Youtube plugin with Totem - never crashes and fullscreen viewing is smooth.

---

### Post by sdowney717 on 2008-08-02
I have smooth viewing in FF for youtube vids.

how smooth are the BBC flash videos? For me they are great.
CNN is not perfect and FOX is worse than CNN

---

### Post by Joshfan on 2008-08-02
how do you get this plugging for totem and FF I am using Ubuntu 7.10.
Does that make a difference?

---

### Post by Locke_99GS on 2008-08-02
If you have a recent version of Totem (the default "Movie Player" in Ubuntu) you can open it, goto the "edit" menu, then "Plugins...", and enable the Youtube plugin. It will allow you to search for and stream Youtube videos from within the movie player (Totem). 

This won't affect Firefox in any way.

---

### Post by Joshfan on 2008-08-02
checked and apparently i have the current version and I checked the pluggin's and there is no youtube plug-in just what is in the screen shot:

[IMG]http://i276.photobucket.com/albums/kk23/joshfantoo/Screenshot-ConfigurePlugins.png[/IMG]

---

### Post by Locke_99GS on 2008-08-02
You'll want Totem 2.22+ I believe, plus you'll need *gstreamer0.10-plugins-bad* 0.10.6 package.

[ATTACH]79905[/ATTACH]

---

### Post by Garyhans on 2008-08-02
For what it's worth I had the problem in FF with choppy video and no full screen NVidia 6600.(Latest Flash Release) Out of a guess I right clicked the video and unchecked hardware acceleration and has worked well since.

---

