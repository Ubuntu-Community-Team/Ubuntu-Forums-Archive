---
title: "Ubuntu 12.04 (Precise) - Sound control panel crash"
date: 2012-04-29
forum: New to Ubuntu
---

### Post by sonicarg on 2012-04-29
Hi everyone! My name is SonicARG, and I'm writing from Argentina.

I would consider myself an intermediate user of Ubuntu because I'd started using it since 3 years ago (only using LiveCD feature, didn't have where to install), and since one and a half years ago with a full featured installation. Before Ubuntu, I was a advanced user of Windows (since 10 years); nowadays I'm a hybrid user, as I use to say "I like and use Linux mostly, but some things that are better in Windows should stay in Windows".

I decided to start a thread here because I had a problem on using latest Ubuntu 12.04 ("Precise Pangolin"). As I didn't know where to start the thread, I hanged it here (if I'm wrong, please let me know).

My problem started when I upgraded my computer from 11.10 ("Oneiric Ocelot") to the current version using the built-in version upgrader. Installation went out well (it took 4 hours approx) and startup of new version was excellent.
These days, I was watching a movie using VLC Player and I wanted to know if my PC Speakers' volume was at 100%. I knew that, if you enter the Sound Control Panel, you'd get a volume slider that has three important points: silenced, 100% and max. The problem is that, when  I try to enter either from the Control Panel or the top bar icon, the control panel crashes and does not show up the window I want to check.

Do you have experienced the same problem?

Let me know if I need to post more info. Thanks in advanced!

SonicARG

PS: My mother language is Spanish. Even if I had several years of English language studies, mistakes can still be made. If something is still not clear, let me know. Thanks.

---

### Post by sonicarg on 2012-06-04
Hi everyone, I'm back again.

Seems that the problem was some self-compiled libraries that had some conflicts with the Pangolin. I had to install several apps some months ago, and I had to compile this libs:

[LIST][*][COLOR="Red"]libogg[/COLOR]
[*][COLOR="Red"]libvorbis[/COLOR]
[*][COLOR="Red"]libvorbisenc[/COLOR]
[*]libxml2
[*]libxlst
[/LIST]

and the Pangolin didn't like them (specially [COLOR="Red"]red-coloured ones[/COLOR]); so I had to recompile & install them again from sources. And worked. :)

Thanks for now, this thread can now be tagged as solved.

SonicARG

---

### Post by s.fox on 2012-06-06
Thread closed at OP request.

---

