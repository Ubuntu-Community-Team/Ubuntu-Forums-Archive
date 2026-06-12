---
title: "Silverlight/python in browser"
date: 2010-03-21
forum: Programming Talk
---

### Post by soltanis on 2010-03-21
Despite the fact that Javascript was my first language, having been through other languages and seen what they offer, Javascript is overall pretty disappointing. Only recently in HTML 5 did it actually get the teeth to *do anything* through the Canvas element, but of course no one supports HTML 5 properly (as demonstrated by the fact that still no one can agree on a formatting standard for video and audio embedded).

Everyone seems to be in love with Web 2.0, and I am in love with Python (uh mostly, lots of stuff could still use improvement). So I was like, hey, how can we get Python in a browser (execute some client side code with some Python?).

Right. Silverlight. Microsoft. Question is, is that the only way to do it? If the free software community is so opposed to the idea of proprietary plugins -- Flash, Silverlight -- why haven't we come up with a competent answer? How do you develop browser plug ins, even -- I know for a fact, for example, that Quake Live is a plug in for browsers executing a modified Quake 3 engine, which is a pretty genius move by id -- but when you Google around, Mozilla and Chrome don't really make it clear how you write *plug-ins* for rich media so much as *extensions* (which are not so rich, as I understand it).

---

### Post by Can+~ on 2010-03-21
The main problem with plug-in dependance, is that it's totally popularity-dependant; main reason why web developers had to coup with IE6 loose standards and many bugs, because a great majority never moved from it.

So the thing is, whenever you build a site, you try to aim to the largest sector, and attach to the most general things, javascript, flash, are all there because they were first, and then people haven't moved since. And won't move until there's a necessity to do so, and informed properly. It's not so easy convincing everyone to install a new extensions, specially when malware is such a common occurrence in the internet.

This forms a vicious circle, developers won't use any tool outside the general ones, because people won't be able to see the site. And people won't install new things because what they have now already works.

With this in mind, I think the only way that opensource can hope to grab a new standard, is being the first one on that, and what's better than 2D flashes? Yes, of course, 3D animation on your browser, that's why we should support WebGL.

And I agree with you, Javascript is deeply disappointing. Have you tried it with Jquery and the like?

---

### Post by soltanis on 2010-03-21
Well, I agree with you that web developers like to target the biggest market. Personally, I've always developed personally useful tools or small experiments, so I never had a problem with supporting only a non-popular platform such as Linux.

I disagree that we should target only the next evolution of plugins. I work as a techie at my university's radio station, developing Internet radio (which is another deeply disappointing field of non-innovation, let me tell you) and we have exactly 2 options -- Icecast/SHOUTcast (which doesn't work for any of us) and then Flash. The web dev who I work with opted for Flash because it "just works" everywhere.

Of course, this means we need to use Adobe Flash Media Server and other related (expensive) tools. We use a 3rd party provider for that right now. We stream in MP3 only, which is a shame, because I think we should be taking advantage of aoTuV Vorbis or AAC+ at the very least.

If there were just some lightweight, open media framework that ran inside a browser that used a language people knew and just worked, I don't think people would have a problem installing it.

---

