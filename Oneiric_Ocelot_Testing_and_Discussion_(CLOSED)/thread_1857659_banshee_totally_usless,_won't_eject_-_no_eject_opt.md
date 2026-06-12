---
title: "banshee totally usless, won't eject - no eject options"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-10-10
Trying out the CD player side of Oneiric and that cat just won't roar. No eject option. Will not eject manually!

??

---

### Post by LinuxFan999 on 2011-10-10
I have 2 possible solutions:

1. When you are done using Banshee, close Banshee, then use the     eject button on the drive itself to eject the disc.

2. Install a different media player.

---

### Post by ventrical on 2011-10-10
> **LinuxFan999 said:**
> I have 2 possible solutions:

1. When you are done using Banshee, close Banshee, then use the     eject button on the drive itself to eject the disc.

2. Install a different media player.

1. Tried this and no way !

2. Looks like I'll have to.

3. But that does not explain the <no_eject> option :)

---

### Post by sgage on 2011-10-10
> **ventrical said:**
> Trying out the CD player side of Oneiric and that cat just won't roar. No eject option. Will not eject manually!

??

Over the years, I have tried to "like" Banshee, but it is still a bloated, bugridden sack of bloat and bugs.

I will not use it, because months (years) after being first reported, it still runs away with the CPU after a while - I mean pegs it, 100%. It's slow. It's glitchy. 

I use Rhythmbox, which has become quite solid. I use gpodder to catch podcasts, and audacious to listen to them because you can save your place.

Banshee is a mess. Also, mono-dependent.

---

### Post by ventrical on 2011-10-10
> **sgage said:**
> Over the years, I have tried to "like" Banshee, but it is still a bloated, bugridden sack of bloat and bugs.

I will not use it, because months (years) after being first reported, it still runs away with the CPU after a while - I mean pegs it, 100%. It's slow. It's glitchy. 

I use Rhythmbox, which has become quite solid. I use gpodder to catch podcasts, and audacious to listen to them because you can save your place.

Banshee is a mess. Also, mono-dependent.\

I use rythmbox on all my other installs (audacious and others too) but I think I am Uboontooed out .. and it just escaped me for a moment as to why I just don't install rythmbox.

 This Banshee is sumthing else.

---

### Post by ventrical on 2011-10-10
rBox worked great.

---

### Post by garvinrick4 on 2011-10-10
eject /dev/sr0

---

### Post by effenberg0x0 on 2011-10-10
You can associate eject to a keyboard shortcut or, if your keyboard has them, a multimedia key.

- Using dash / keyboard / shortcuts / Sound and Media
- Using ccsm / commands

Regards,
Effenberg

---

### Post by mc4man on 2011-10-10
> **ventrical said:**
> Trying out the CD player side of Oneiric and that cat just won't roar. No eject option. 

??
Where are you looking for the 'eject option'

couple of  ways here - 
r. click on the audio cd in banshee's left side box > eject
with focus on banshee when cd tracks are displayed > shift+delete or edit > eject disc

---

### Post by techvish81 on 2011-10-10
using rythmbox,  I never liked banshee,  it is not working,  freezes, fails to respond for ages.

---

### Post by Harry33 on 2011-10-11
It was simply a mistake for Ubuntu to default to Banshee.
Not only because it did pull in a lot of mono stuff.
But also because it really is most of the time broken.

Personally, I use VLC for videos and for music. :D

---

### Post by directhex on 2011-10-11
> **ventrical said:**
> Trying out the CD player side of Oneiric and that cat just won't roar. No eject option. Will not eject manually!

??

Presumably you already filed a wishlist bug about this?

---

### Post by ventrical on 2011-10-11
> **directhex said:**
> Presumably you already filed a wishlist bug about this?
No, I have not.

My apologies. I think I was just firing off a loose comment on the fly. Iv'e ben doing a lot of beta testing on some things and letting some things just fly by.. so I thought I would try some of the new stuff - and looks like there is a long way to go for some of the programs.

---

### Post by ventrical on 2011-10-11
> **mc4man said:**
> Where are you looking for the 'eject option'

couple of  ways here - 
r. click on the audio cd in banshee's left side box > eject
with focus on banshee when cd tracks are displayed > shift+delete or edit > eject disc


Ahhh.. there it is ! :)

---

### Post by mc4man on 2011-10-11
Well if you really think a standalone eject button should be included I guess that could be a wishlist
Otherwise eject is available when appropriate though not as a 'button'

---

### Post by ralfarof on 2011-10-11
> **sgage said:**
> Over the years, I have tried to "like" Banshee, but it is still a bloated, bugridden sack of bloat and bugs.

I will not use it, because months (years) after being first reported, it still runs away with the CPU after a while - I mean pegs it, 100%. It's slow. It's glitchy. 

I use Rhythmbox, which has become quite solid. I use gpodder to catch podcasts, and audacious to listen to them because you can save your place.

Banshee is a mess. Also, mono-dependent.

Have you tried Clementine? It rocks!

I purged Banshee and it's .NET junk off my hard drive \\:D/

---

### Post by mc4man on 2011-10-11
> **ralfarof said:**
> Have you tried Clementine? It rocks!

I purged Banshee and it's .NET junk off my hard drive \\:D/

In the context of this thread - audio cd's,  clementine is pretty poor, myself use vlc which is much better & can be adjusted for a proper autorun/autoplay  from 1 or more drives if desired

Add. -  atm clementine, at least here, shows extremely bad  behavior when trying to exit
[https://bugs.launchpad.net/ubuntu/+source/clementine/+bug/864666](https://bugs.launchpad.net/ubuntu/+source/clementine/+bug/864666)

---

