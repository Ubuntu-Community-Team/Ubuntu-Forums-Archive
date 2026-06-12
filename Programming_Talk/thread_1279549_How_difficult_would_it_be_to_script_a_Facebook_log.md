---
title: "How difficult would it be to script a Facebook logger?"
date: 2009-09-30
forum: Programming Talk
---

### Post by Chingpow on 2009-09-30
Please be patient with me, as I am a newb. :confused: I realize this may not be asked in the right place, but probably you guys in this section would have a good idea... so here goes:

I'm wondering how hard it would be to script(or even if there already is) a program that would download the source code from someone's Facebook page periodically, and make logs of what changed on their page. 

For some background info: This is mostly of out curiosity. There are some friends of mine that don't have many settings on Facebook changed from default, so when they make a change to their profile, it'll say so on their wall.... and so they will delete these changes manually, minutes after they have changed a part of their profile. I think it'd be cool if a script could catch those changes, and log them. Probably it'd have to be checking the person's page every few minutes in order for it to work... correct me if I am wrong.

Think it would be easy enough to script?

Edit: I'm guessing there isn't already a suitable way to do this, so probably I will have to make something on my own. I'm also hoping that I could be pushed in the right direction - via tutorials, etc... as I have near zero experience programming.

---

### Post by slavik on 2009-10-01
not difficult at all
look into curl

---

### Post by G|N| on 2009-10-01
Take a look at specto, it periodically gets information from facebook (wall, messages, requests,...) and shows a balloon if something has changed.

I think the code is a good place to start.

[http://bazaar.launchpad.net/~specto/specto/main/annotate/head%3A/spectlib/plugins/watch_sn_facebook.py](http://bazaar.launchpad.net/~specto/specto/main/annotate/head%3A/spectlib/plugins/watch_sn_facebook.py)

---

### Post by staticextasy on 2009-10-01
Interesting...

So its kind of like an RSS Feed for facebook profiles?

---

### Post by Chingpow on 2009-10-01
> **staticextasy said:**
> Interesting...

So its kind of like an RSS Feed for facebook profiles?

If you mean specto, yes, it does appear to work like an RSS feed - but better. RSS feeds on Facebook only alert you of so many things... I don't think that a regular RSS feed could do all that I want it to - like make logs of whether someone clicked "like" on a picture or a status, just before they manually removed that activity from their wall. I'll post an update if I make progress.

---

