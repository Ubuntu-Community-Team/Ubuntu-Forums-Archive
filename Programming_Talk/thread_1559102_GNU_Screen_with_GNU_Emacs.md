---
title: "GNU Screen with GNU Emacs"
date: 2010-08-23
forum: Programming Talk
---

### Post by matthew.ball on 2010-08-23
Don't know if anyone has tried these two applications with each other, but it has taken me a long time to finally get GNU Emacs "working" inside GNU Screen - sure it would work previously, but the display would go horribly wrong. Not that I had ever really looked for a solution before.

I had a bit of spare time today and wondered if perhaps it was my choice of shell which made things go wrong. I experimented with a few different shells only to have the same result each time, so the issue was obviously elsewhere. I ended up finding a relatively simple solution. If anyone's interested I can post my .screenrc file. I'm very happy with the outcome, and just figured it might be useful for some people here (though, perhaps the interested parties already know the solution).

---

### Post by monkeyking on 2010-08-23
How was emacs not working from within a screen?

Ive been using emacs in a screen for quite sometime and its working fine.
But maybe Ive just gotten used to the random garbage that "overwrittes" my text, but a quick ctrl+z followed by fg. Seems to fix that.

---

### Post by matthew.ball on 2010-08-24
Yeah, the random garbage was my issue.

I almost gave up on emacs and had a go at the vim tutorial I'm such a picky bastard (but decided it would be easier to look for solutions to the garbage then learn vim).

I never tried (or thought of) suspend and resume as a fix, but makes sense. However, that's far more effort then I am willing to go to.

If you're getting annoyed with the constant resuming/suspending, rebind your screen key to C-Z in the .screenrc file (I can't explain why this works, and you could change it to another key, C-Z just fits more with emacs I think).

If you go with C-Z, you can't suspend anymore, but I haven't actually suspended anything since discovering screen (originally I would suspend nano, compile, run app, resume nano, etc).

---

