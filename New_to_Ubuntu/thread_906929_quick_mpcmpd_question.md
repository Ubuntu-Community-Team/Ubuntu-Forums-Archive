---
title: "quick mpc/mpd question"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by supersonicdarky on 2008-08-31
I set it all up and it works just fine but how would I go about adding single files to the playlist? It's easy enough with a gui like gimmix but w/out tab-autocomplete for the mpd db it seems impossible. The only thing I can do is add a folder.
```
mpc add Trance
```
but what if I wanted song #5 in folder #22 but didn't know the filename?
it seems I can't do
```

mpc ls Trance

```
or
```

mpc add Trance/[tab][tab]

```

thnx

---

### Post by ~LoKe on 2008-09-01
Eh?

> mpc ls In\ Flames
In Flames/Black Ash Inheritance
In Flames/Clayman
In Flames/Colony
In Flames/Come Clarity
In Flames/Demo '93
In Flames/Lunar Strain - Subterranean
In Flames/Reroute to Remain
In Flames/Reroute to Remain- Fourteen Songs of Conscious Insanity
In Flames/Soundtrack to Your Escape
In Flames/The Jester Race
In Flames/The Jester Race - Black-Ash Inheritance
In Flames/The Quiet Place
In Flames/Trigger
In Flames/Unreleased
In Flames/Whoracle
> mpc ls In\ Flames/Clayman
In Flames/Clayman/Another Day in Quicksand.mp3
In Flames/Clayman/Brush the Dust Away.mp3
In Flames/Clayman/Bullet Ride.mp3
In Flames/Clayman/Clayman.mp3
In Flames/Clayman/Only for the Weak.mp3
In Flames/Clayman/Pinball Map.mp3
In Flames/Clayman/Satellites and Astronauts.mp3
In Flames/Clayman/Square Nothing.mp3
In Flames/Clayman/Suburban Me.mp3
In Flames/Clayman/Swim.mp3
In Flames/Clayman/World of Promises.mp3
> mpc listall
Is good, too.

---

