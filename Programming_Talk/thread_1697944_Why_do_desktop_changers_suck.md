---
title: "Why do desktop changers suck?"
date: 2011-03-01
forum: Programming Talk
---

### Post by Kralizec on 2011-03-01
Hello all, it's been a while since I've posted here.

The subject question has been nagging me for a long time. Why are "random" desktop wallpaper changers so terrible at being random? Or perhaps they're just *too* random for me.

What I mean by this is that whenever I use a wallpaper switcher I see the same wallpapers over and over again. I have a cache of over 700 different wallpapers, but I am presented with about 50 of these with much higher frequency than all the others (just now I had the same wallpaper twice within three switches; it, another, then it again). I would go so far as to say I have several hundred wallpapers that I have never seen beyond when I first downloaded them.

Can anyone explain to me why this is the case? Is it just a side-effect of the pseudorandom generator, or is the selection algorithm poor in the changer I use, or is it something else? 

I've used several different changers on both Ubuntu and Windows (including, currently, the built-in Win7 changer and on my Ubuntu box, Wally) all to the same effect.

Also, I would be interested if anyone knew how to programatically change the desktop background in Windows (I'm sure it is fairly well documented in Linux), as I would like to try my hand at a switcher myself.

---

### Post by Vaphell on 2011-03-01
possible reasons i can think of:
- very bad luck
- seeding RNG with the same number
- some hand-made RNG with lousy entropy

i guess i'd go with standard RNG and add a list of last X wallpapers and check the random pick against it - if the pick is already there, it gets discarded and the wallpaper is chosen again. Even if algorithm is truly random people perceive frequent repetitions badly so that would be a safeguard.
Or I'd use approach similar to that of audio players shuffling files around so the order is random but individual files won't repeat until the end of list.

No idea about windows though.

---

### Post by Kralizec on 2011-03-01
That's about what I thought for the reasons. 

Nice idea with the list of recently viewed wallpapers/putting wallpapers to the end of the list. If I ever get around to writing a changer myself, I'll definitely do that.

---

### Post by Simian Man on 2011-03-01
[IMG]https://mywebspace.wisc.edu/lnmaurer/web/minirng/Dilbert0001.jpg[/IMG]

---

### Post by cguy on 2011-03-01
Wallpaper changers suck for the same reason the random song feature in EVERY music player sucks. :D

---

