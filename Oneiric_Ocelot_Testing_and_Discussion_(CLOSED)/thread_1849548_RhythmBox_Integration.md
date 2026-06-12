---
title: "RhythmBox Integration?"
date: 2011-09-24
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by patryk77 on 2011-09-24
I personally prefer RhythmBox to Banshee as a media player (it's much faster to update my library, and the interface is generally slower on Banshee).

Is there an easy way anyone knows of to get RhythmBox to be the default Music Player in the Unity menu?

---

### Post by VinDSL on 2011-09-24
System settings -> System Info -> Default Applications -> Music (and/or Video)


[INDENT](Click to expand)
[[IMG]http://vindsl.com/images/vindsl-desktop-24-sep-2011(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-24-sep-2011.png")[/INDENT]

---

### Post by patryk77 on 2011-09-24
Awesome, thanks. Weird place to put it IMO (System Info?), but good to know. (And figured it was something simple)

Will give Banshee another try, but I still think I will stick with RhythmBox.

---

### Post by VinDSL on 2011-09-24
> **patryk77 said:**
> Will give Banshee another try, but I still think I will stick with RhythmBox.[...]
Yeah, I hear ya!   I have a love/hate relationship with Banshee.  

I never have found a player that I like.  IMO, Banshee is no better or worse than the rest.  They all have their quirks and foibles.

I run a shell script at startup, which automagically loads Banshee into mem:

```

#!/bin/bash
sleep 30
banshee --hide --redirect-log

```

This speeds up Banshee considerably.  Might want to try that, too...  ;)

---

### Post by patryk77 on 2011-09-24
I might, but I still hate not having an option to (easily) listen to music from one genre, without making playlists.

At least if genres are disabled by default in RhythmBox's view, it takes 5 clicks to enable them...

And it's not really Banshee's loading time that irks me... It's just slow when I click on one artist

---

### Post by sgage on 2011-09-25
I could live with Banshee if it didn't (continue to) have a tendency to suddenly start using 100% CPU. This is a known bug that has been going on for months, if not years.

And yes, it is dog slow. I use Rhythmbox.

---

