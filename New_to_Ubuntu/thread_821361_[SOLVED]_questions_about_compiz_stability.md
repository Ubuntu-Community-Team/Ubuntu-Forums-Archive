---
title: "[SOLVED] questions about compiz stability"
date: 2008-06-07
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-07
hello

 I followed this link...[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
for help after a fresh install, and it quickly led me to compiz stuff which I felt comfortable to install, as there are no warnings about it being BETA software, and then I clicked a link at the bottom of someones post with very scary warnings, 

So, is it still beta, how dangerous is it to cause damage that a noob cant fix?

---

### Post by forestpixie on 2008-06-07
What link was it? People have all sorts of stuff in their sigs.

---

### Post by wdaniels on 2008-06-07
You don't really need to worry about changing compiz settings. If you configure something a certain way and then you don't like it, or it doesn't behave quite as expected or whatever, just go back into the config manager and set it back to default. There's nothing really to worry about - breakage usually comes when you start blindly following a guide somewhere that's telling you to compile and install things manually, or start mixing in 3rd party repositories - just stick to what's available in the standard repos, and the settings you can alter in CCSM and you'll be fine.

There's no magic stamp or wholly determinable set of criteria for 'beta' or 'stable' software, it's just a consensus viewpoint, which can vary with context. Compiz is probably no more 'beta' quality than a lot of stable branded software, but it does still have it's occasional quirks. In any case it's shipped in Ubuntu (and other distributions) as standard, so there's nothing dangerous about it.

---

### Post by Paqman on 2008-06-07
Compiz is pretty stable. It's been included in Ubuntu for the last couple of versions and is well tested. I wouldn't worry about it.

---

### Post by Dutch70 on 2008-06-07
Great, that's a relief, thought I was going to have to remove it. I'm sure I will soon enough anyway, but for now I'd like to keep it, without having to worry. 

the link in another post I mentioned was just a warning that it is beta and if it breaks...you get to keep both pieces...:lolflag: 
just freaked me out a little.

Thanks!

---

### Post by billgoldberg on 2008-06-07
Compiz is not beta software!

I've been running compiz fusion with loads of effect on 2 computer ever since gutsy gibbon came out, never had any problems with it *(well expect for 3d gaming)*.

---

### Post by Paqman on 2008-06-07
> **billgoldberg said:**
> Compiz is not beta software!


Actually, it is. Latest version is 0.5.2.

Bit of a meaningless term though. It's pretty stable and all the desktop distros are using it.

---

### Post by philinux on 2008-06-07
The version in my synaptic is 1:0.7.4

---

### Post by Paqman on 2008-06-07
That'll teach me to be lazy. I googled Compiz, not Compiz Fusion.

Looks like Compiz Fusion is stable actually, starting with 0.6.0. Maybe the packaging bods have stuck the 1 at the front to reflect that?

I'm beginning to think "beta" is a pretty meaningless term these days anyway. Gmail describes itself as "beta", for example (?!?)

---

### Post by Dutch70 on 2008-06-07
Well, thats even better....Thanks Again!

---

### Post by wdaniels on 2008-06-07
> **Paqman said:**
> I'm beginning to think "beta" is a pretty meaningless term these days anyway. Gmail describes itself as "beta", for example (?!?)

Alpha and Beta labels, at least traditionally, are not meant as a direct measure of stability. They refer to things like feature completeness and release status. Obviously, these things tend to correlate strongly with stability anyway, but not always. To use your example, GMail probably still carries a beta label only because the availability is still restricted by invitation only. So in this case it is just a marker for release progress, which is most likely due to the invitation only system working better than complete general availability, not because it is deemed too unstable for a full public release.

It used to be, when I first started programming, that "alpha" meant internal testing (and often *not* feature complete), "beta" a restricted group for testing "in the field" (i.e. feature complete but needing testing in a broader range of environments), then a stable public/production release. Nowadays we tend to have "public betas" and also "release candidates" and "service packs" etc. Even things like unit testing start to blur the lines at the other end too.

So really it only applies to open source stuff as a loose suggestion of stability and/or to indicate certain freeze points for APIs and stuff. The trouble with using these labels in many open source projects is that "feature complete" doesn't exactly fit with the development model and widespread public use is common even in early development stages. In bigger, more structured projects like Ubuntu, it has some meaning, but things like Compiz (especially with all the forking and merging that's gone on there) a consistent measure of stability is quite hard to pin down.

(Hmm, that wasn't meant to be an essay, it just sort of happened :D Basically I just meant to say "I agree")

---

### Post by Paqman on 2008-06-08
> **wdaniels said:**
> GMail probably still carries a beta label only because the availability is still restricted by invitation only.

That's the thing that makes me laugh about Gmail, it's now open to everyone. No invite needed.

So it's been deployed to the whole world, features are stable, and millions of people use it as their primary email, and yet it's still a beta? Strange.

---

