---
title: "Cranking RSS field entries into something my ereader can handle"
date: 2012-04-30
forum: Ohio Team - US
---

### Post by skellat on 2012-04-30
I don't like the way Calibre downloads feeds and bundles them into EPUB files.  Right now I read my RSS feeds by reading twice-a-day HTML dumps produced by rawdog.  Those HTML dumps don't convert nicely to EPUB via Calibre either.

I've got quite a few feeds in the rawdog config file.  There are probably tools that can be scripted together including rsstail perhaps.  Taking rsstail output and transmogrifying it to epub might be simplest BUT getting from start to finish isn't sorted.

What's a way forward to start with?

---

### Post by skellat on 2012-04-30
The way I think I can start is this:

rsstail to pull recent posts

THEN

pandoc to convert the output of rsstail to EPUB

THEN

calibre to move the ebook to the Pandigital 6 inch novel reader I own that doesn't play at all with Amazon's blog subscriptions thingie.

The thing is that that flow above only handles one feed.  I want to combine a bunch of feeds into one ebook to read.

---

### Post by skellat on 2012-06-05
Well, that procedure did not work.  Back to the drawing board...

---

### Post by imbrandon on 2012-07-16
So if I understand you correctly you would like to specify multi ( lets say 3 to 5 as an example ) RSS / ATOM feeds from sources ... then have them spliced togather into one  and dumped into an ePub file that you can then sync to your device ?

I can make that happen, I have some code that I wrote a few months back for a project that does something very very similar. I've got the time this afternoon so I'll yank those bits out into its own stand-alone app that you could run, like say on a crontab.

As long as I understood you correctly, do let me know and I'll crank it out as I'm sure others could use something similar as well so once you're statisfied as the guiney pig I'll toss it on LP / PPA for everypone else :)

---

### Post by skellat on 2012-07-26
> **imbrandon said:**
> So if I understand you correctly you would like to specify multi ( lets say 3 to 5 as an example ) RSS / ATOM feeds from sources ... then have them spliced togather into one  and dumped into an ePub file that you can then sync to your device ?

I can make that happen, I have some code that I wrote a few months back for a project that does something very very similar. I've got the time this afternoon so I'll yank those bits out into its own stand-alone app that you could run, like say on a crontab.

As long as I understood you correctly, do let me know and I'll crank it out as I'm sure others could use something similar as well so once you're statisfied as the guiney pig I'll toss it on LP / PPA for everypone else :)

I apologize for the delay in replying.  I would be interested in testing this.  :KS

---

