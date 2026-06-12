---
title: "Lightning and Thunderbird not working for me in 8.04"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by SamNSane on 2008-10-24
I have a fairly recent Hardy Heron installation. The only non-standard part of the configuration is the use of restricted drivers for the nVidia video subsystem.

I've been using Thunderbird 2.0.0.17 and wanted to add calendar functionality to it. I downloaded Lightning 0.9 from Mozilla and installed it from the Add On menu selection in Thunderbird.

Installation went the way extension installations normally go. Restarted Thunderbird. What I have now is a calendar and tasks view in Thunderbird, but they aren't usable. The calendar is stuck in single day mode. I am unable to add events or tasks. And the calendar import selection is grayed out in the menu.

Does anyone have an idea what I might try to get this to work?

---

### Post by OldGrey on 2008-10-24
Are you using 64bit? If so the lightening add on will not work. I had a similar problem recently when I "upgraded" from 32bit.

---

### Post by Thelasko on 2008-10-24
> **OldGrey said:**
> Are you using 64bit? If so the lightening add on will not work. I had a similar problem recently when I "upgraded" from 32bit.
It works for me.  It's in the repositories.

---

### Post by OldGrey on 2008-10-24
> It works for me. It's in the repositories.


Is it - I'll check that out, when I tried the add on from the Thunderbird site I was told - will not work with 64bit tell the developer - or words to that effect.

---

### Post by Thelasko on 2008-10-24
> **OldGrey said:**
> Is it - I'll check that out, when I tried the add on from the Thunderbird site I was told - will not work with 64bit tell the developer - or words to that effect.
Lightning is open source, so it can always be compiled for 64-bit.  If you can't find it in the repositories, a forum member [compiled version 0.8]("http://ubuntuforums.org/showpost.php?p=4675948&postcount=6") a while back.

---

### Post by Udibuntu on 2008-10-24
I installed Hardy a couple of days ago.

One of the first things I did was to delete Evolution and install TB and Lightning from "add/remove" in "applications" menu. It worked like a charm for me.

I would recommend you remove TB and Lightning and install again from either "add/remove" or Synaptic Manager. You can check both for simultaneous installation.

Downloading from Mozilla is good only if you know how to keep links and dependencies between components from Ubuntu and components from Mozilla or other sources, for that matter. 

Good luck,

Udi

---

