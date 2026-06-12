---
title: "Totem error: Location not found"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by dat311 on 2008-05-19
When I put an audio cd into its drive, Totem launches, but gives me this:  Error: Location not found.

I've followed the Medibuntu instructions from the multi-media how-to, but still the problem persists.

So, is Totem still launching the wrong version of Totem (there's two on my system now - one refers to gstream iirc - I'm not at my computer at the moment) and if so, how to change it?  Or should I just chuck it, download and run Rythmbox (and if so, I guess the answer to question 1 will suffice for question 2?). 

k3b has no problems recognising the drive - which is a Pioneer DVD burner.

---

### Post by mc4man on 2008-05-20
> but gives me this: Error: Location not found.

i've only tried xubuntu for a little bit but that certainly is the default behavior. Totem is not a very good anything anyway. You could certainly use  Rythmbox to play, i'm not to sure it would auto play though it can auto start. If you fool around with launch command in settings manager -> removable drives....-> multimedia, maybe. What does work well with 1 or 2 drives is amarok. In removable drives -> media replace totem cdda:/ with ```
amarok -cdplay %d
``` Note; playback doesn't start till cd is loaded fully in playlist.
For dvds i'd install vlc, and replace totem dvd:/ with ```
vlc %m
```
(after adding the medibuntu repo to software sources and installing libdvdcss2 )

---

