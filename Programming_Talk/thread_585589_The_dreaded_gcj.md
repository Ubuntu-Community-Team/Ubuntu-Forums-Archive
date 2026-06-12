---
title: "The dreaded gcj"
date: 2007-10-21
forum: Programming Talk
---

### Post by tenmillionmilesaway on 2007-10-21
Hi,

I tend to post about Java problems, and a large percent of them seen to be caused because people aren't using the correct version of java.  They either havent installed the sun java at all, or have done and havent done the update alternatives step, usually because they see that they can type java and don't realise that there is a different version.

It seems to me that the gcj shouldn't be installed at all as it only causes problems to people that are unfamiliar to ubuntu.  My reasoning is that no Java is better than a Java that needs replacing anyway since this will lead to less confusion.  I'm not saying that the sun java should be installed by default as its not open source (yet) and I know that many people would not agree with this.

Does the gcj actually get used for anything anywhere?  Does it have any advantage over the sun one (apart from open source)?

What are peoples views on this?  We could try and add this to the idea pool for hardy if people think its a good idea.

Also maybe we should make a sticky about the gcj thing so that it is clear to new users?

Richard.

---

### Post by Engnome on 2007-10-21
I've been thinking the same thing, all it ever does for me is get in the way :/ Would be interesting knowing if it's actually used. Maybe write a short python/bash/perl/whatever script and replace the gcj bin with. The script would log whenever the program is called and then launch gcj. Too tired to experiment with it right now though. There's probably a better solution somewhere out there.

Anyway I'm hoping distros will start to include Sun's Java now that it's being relicensed (has been relicensed? Not really following the progress) to GPL, hopefully it'll be the default in the future.

---

### Post by tenmillionmilesaway on 2007-10-21
The opensuse 10.2 that I use at work had the sun java jdk installed by default.  I think that gcj can be used to compile java to machine code (as its the same back end as gcc) but i dont see this as a benefit cos one main benefit of java is that its platform independant.

---

### Post by tageiru on 2007-10-21
Sun has GPL:ed Java (barring a few minor components, but that will be fixed) so the problem will simply disappear when Ubuntu installs Suns Java by default.

---

### Post by pmasiar on 2007-10-21
... and I may add that Sun would be less willing to open Java if gcj was not becoming viable competitor. If they waited 3 more years, it might be too late. If Java would be GPL-free, of course there is no reason for gcj anymore, it fulfilled it's role 100%.

---

### Post by jespdj on 2007-10-24
I agree, no Java installed by default would be better than GNU Java, which is very slow, not fully implemented, buggy and old and soon to be completely obsolete when Sun's Java is finally open sourced.

There are however some packages like OpenOffice which are installed by default, which require Java - probably that's the reason that GCJ is installed on Ubuntu by default.

---

