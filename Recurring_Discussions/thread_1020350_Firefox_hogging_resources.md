---
title: "Firefox hogging resources"
date: 2008-12-24
forum: Recurring Discussions
---

### Post by magmon on 2008-12-24
Firefox is absolutely EATING my resources. Im actually, amazingly getting lag o.O

This happening to anyone else?

---

### Post by wolfen69 on 2008-12-24
no.

---

### Post by rajeev1204 on 2008-12-24
For me too its very laggy and seems to constantly seek hard disk .

Any ideas how i can reduce that?








raj.

---

### Post by magmon on 2008-12-24
No idea lol. I just installed opera and the lag magically disapeared. Maybe I have too many add-ons, but it would freeze in the middle of typing and spike in resource use. I guess, the solution is either run a virgin firefox or opera.

---

### Post by jrusso2 on 2008-12-24
Firefox has always been a hog.

---

### Post by magmon on 2008-12-24
> **jrusso2 said:**
> Firefox has always been a hog.

While I do agree, this lag is new to the past few days.

---

### Post by chucky chuckaluck on 2008-12-24
> **magmon said:**
> While I do agree, this lag is new to the past few days.

were any of your extensions or themes updated recently?

---

### Post by kerry_s on 2008-12-24
in userContent.css put:

```

/* Smooth Scrolling: Disable Fixed Background Images */
body {
background-attachment: scroll !important;
}

```

turn off:
**browser.cache.memory.enable**

---

### Post by niceguy123 on 2008-12-24
> **jrusso2 said:**
> Firefox has always been a hog.

What browser do you suggest using?

---

### Post by DrHackenbush on 2008-12-24
Firefox may be a piggy but it sure beats IE on the Windows box I'm using at work.

---

### Post by billgoldberg on 2008-12-24
Firefox has lots of tweaks to reduce it's memory usage.

Google for them.

At first it was really, really slow on my Asus eeepc 900.

After 5 minutes of tweaking (well, following instructions from some website), it ran really well.

Now, I still switched to Epiphany on my netbook. :p

---

### Post by jrusso2 on 2008-12-24
> **niceguy123 said:**
> What browser do you suggest using?

I use Firefox but Opera is less of a hog.

---

### Post by init1 on 2008-12-24
> **magmon said:**
> Firefox is absolutely EATING my resources. Im actually, amazingly getting lag o.O

This happening to anyone else?
Yeah, Firefox takes up to 200MB RAM at times. It was so bad on my system that I had to upgrade my RAM from 512MB to 1GB.

---

### Post by magmon on 2008-12-24
> **kerry_s said:**
> in userContent.css put:

```
body
{
background-attachment:
scroll!important
}

```

turn off:
**browser.cache.memory.enable**

Slowed it more, but I found a tweak that worked wonders. Thanks for the suggestion, anyway.

---

### Post by dannytatom on 2008-12-24
> **niceguy123 said:**
> What browser do you suggest using?

Swiftfox.  It's firefox but takes about half the memory to run.  If you already has firefox, it'll transfer all your addons, settings, bookmarks, etc during install.

---

### Post by magmon on 2008-12-24
> **dannytatom said:**
> Swiftfox.  It's firefox but takes about half the memory to run.  If you already has firefox, it'll transfer all your addons, settings, bookmarks, etc during install.

Oddly, it runs slower for me than firefox xD

---

### Post by dannytatom on 2008-12-24
Haha, well I guess "about half the memory" is only for me. ;x

---

### Post by kerry_s on 2008-12-24
> **magmon said:**
> Slowed it more, but I found a tweak that worked wonders. Thanks for the suggestion, anyway.

what tweak? come on man share! :lolflag:

---

### Post by magmon on 2008-12-24
Could be, actually now that Ive compared them, firefox spikes but uses less memory when idle, and swiftfox uses a medium amount of memory constantly, with short spikes when loading. Over all, swift fox is faster, but not twice as fast lol.

---

### Post by kerry_s on 2008-12-24
ooh, just found 1 that seems to work great.see pic

---

### Post by magmon on 2008-12-24
> **kerry_s said:**
> what tweak? come on man share! :lolflag:

I turned off pipelining, lol. Id rather have 1 second loading time than constant freezes xD

---

### Post by kerry_s on 2008-12-24
> **magmon said:**
> I turned off pipelining, lol. Id rather have 1 second loading time than constant freezes xD

oh okay, i use pipelining, but i don't jack it up, just change to true and that's all.

---

### Post by magmon on 2008-12-24
> **kerry_s said:**
> oh okay, i use pipelining, but i don't jack it up, just change to true and that's all.

Change to false, it takes like half the memory.

---

### Post by kerry_s on 2008-12-24
> **magmon said:**
> Change to false, it takes like half the memory.

i don't get a change in memory use, so i'll just leave mine true.

---

### Post by jrusso2 on 2008-12-25
I have tried all those "tweaks" and still Firefox uses a lot of memory.

---

### Post by igknighted on 2008-12-25
pipelining should help load times quite a bit... and shouldn't effect ram usage either.  All it does is let FF download more than one thing at a time (the html, the css, the images, the ads...), especially nice when something high up on the page doesn't want to load and you don't sit there waiting.  It's all stuff that is going to get downloaded into ram anyways, may as well get it over with.

Now if you let it cache everything and it constantly wants to write to the disk, that's what would start causing some major hang ups.  Especially on a laptop (slower HD typically).

---

### Post by magmon on 2008-12-25
Eh, dunno, worked for me lol.

---

### Post by getaboat on 2008-12-25
I've been having a few issues with FF recently - just irritations - and speed was one of them. So I've tried Opera again and this time I've tried to spend some more time with it - as I don't think it is as intuitive as FF.

However, I'm very impressed with basically everything so far and I'm going to persist with it.

---

