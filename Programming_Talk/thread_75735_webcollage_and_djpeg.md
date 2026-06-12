---
title: "webcollage and djpeg"
date: 2005-10-14
forum: Programming Talk
---

### Post by agger on 2005-10-14
Okay, a stupid question:

I want to fiddle a bit with the "webcollage" screen saver, so I look at the source code, a Perl script.

Fine and good, and easy enough to read and change. So I tried to run it from the command line, and it said it couldn't find the "djpeg" program.

The screensaver runs just fine when run from xscreensaver, so my path must be wrong/insufficient, I thought.

So, let me just find it, so I'll set up my path:

[FONT="Courier New"]sudo find / -name 'djpeg' -print[/FONT]

Only: Nada. Nothing is found.
Oh well, perhaps it's part of some Perl library, so it's called "djpeg.pl" (as opposed, strangely, to "jpegtopnm" and similar functions which *do* exist) or something, so let's be more exhaustive:

[FONT="Courier New"]sudo find / -name '*djpeg*' -print[/FONT]

Only, I still find nothing. What am I doing wrong here? And how can the webcollage script find [FONT="Courier New"]djpeg[/FONT] when running from *xscreensaver* when it can't when I run from the command line?

Any help would be appreciated.

regards
Carsten

---

### Post by agger on 2005-10-14
Well, I'll answer the question myself:

I needed to install the programs from the jpeg-lib from the IJP. I have no idea whatsover where the instance of webcollage running my screensaver found its djpeg ...

---

