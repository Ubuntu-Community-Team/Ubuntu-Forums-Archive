---
title: "What to do about dead projects that you have a patch for"
date: 2007-12-27
forum: Packaging and Compiling Programs
---

### Post by vek on 2007-12-27
Hi there.  
I've been using linux/ubuntu for a while now, and have managed to get a couple patches together.  Mostly small fixes, since I spend most of my time using the operating system to get done, not tinkering with it or fixing it, unless something is in the way.  (Sorry).

Sometimes I submit a patch upstream, but I've found that most of the time, the patch just sits there, because the particular project is dead, or the maintainer (upstream) doesn't actually maintain it anymore.

I'm just wondering what the procedure is, in those situations, when ubuntu is using a project that the upstreamer maintainer hasn't really touched in years, and the patches are piling up in that projects upstream repository, but aren't ever accepted or used.

Sure, I can just keep the patches to myself and reapply them every time I upgrade / reinstall.   But that seems to defeat the whole community-based linux open source thing, doesn't it?  

So as a matter of curiosity, when upstream is dead, but things still need fixing, what happens?  Do the ubuntu packages have their own layers of patches they apply after or in addition to upstream patches in this scenario?  If so, where do they go?  I've asked around the IRC and generally just get told to "Submit it upstream".  But what if upstream is dead?

---

### Post by plugwash on 2008-01-01
there are mechanisms in place for patches to be added by debian and ubuntu. Ubuntu afaict tends to pick up most changes made by debian.

Generally it is better to go to debian than ubuntu given the choice as packages there are more likely to have proper maintainers.

The above especially applies to packages that are in both debian and ubuntu.

As for where to put the patches the normal way would be to submit a bug report with the patch attatched or attactch the patch to an existing bug report. Both debian and ubuntu have bugtrackers.

---

### Post by vek on 2008-01-05
So even tho its a bug in one of the software packages that debian and ubuntu uses, and not an actual debian/ubuntu bug... its okay to submit bug patches to the debian tracker?

(Even if the software in question has its own tracker, but its growing cobwebs?)

---

### Post by Sukarn on 2008-01-05
> **vek said:**
> So even tho its a bug in one of the software packages that debian and ubuntu uses, and not an actual debian/ubuntu bug... its okay to submit bug patches to the debian tracker?

(Even if the software in question has its own tracker, but its growing cobwebs?)

Yes, its ok to do that, especially if upstream is *dead*.

---

### Post by plugwash on 2008-01-05
generally it is a good idea to test on debian sid and the development version of ubuntu before submitting your bug report. Reports of bugs that have already been dealt with tend to just cause annoyance.

If it affects sid I would report it on the debian bugtracker. If it affects the development version of ubuntu and not sid I would report it on the ubuntu bugtracker. If it doesn't affect either sid or the development version of ubuntu then there isn't much point in reporting it as both debian and ubuntu have obviously already dealt with it.

---

### Post by dholbach on 2008-01-07
[https://wiki.ubuntu.com/SponsorshipProcess](https://wiki.ubuntu.com/SponsorshipProcess) is the process to get patches uploaded. If you've gone through it a couple of times and your sponsors have only good things to say about you, you can think about becoming a MOTU yourself. ([http://wiki.ubuntu.com/MOTU/GettingStarted](http://wiki.ubuntu.com/MOTU/GettingStarted))

---

