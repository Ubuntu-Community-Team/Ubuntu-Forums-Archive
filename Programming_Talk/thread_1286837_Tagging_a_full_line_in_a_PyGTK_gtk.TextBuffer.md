---
title: "Tagging a full line in a PyGTK gtk.TextBuffer"
date: 2009-10-09
forum: Programming Talk
---

### Post by Twiggy794 on 2009-10-09
So I'm building out a diff viewer and would like to highlight lines in the diff (contained within a gtk.TextBuffer) based on adds/removes etc.  However, I want to do a background highlight across the entire physical line, not just terminating at the '\n' character.  Is this doable?  Can anybody offer some insight?

Thanks!

---

### Post by giuspen on 2009-10-09
Do you know about [meld]("http://meld.sourceforge.net/")?
That's a masterpiece, no reason to implement another diff viewer...
anyway if you want to take a look to its source code, meld is
in PyGTK.

---

### Post by Twiggy794 on 2009-10-09
> **giuspen said:**
> Do you know about [meld]("http://meld.sourceforge.net/")?
That's a masterpiece, no reason to implement another diff viewer...
anyway if you want to take a look to its source code, meld is
in PyGTK.

Yeah, I'm developing something more specific to what I do day-to-day.  It's more like an all-encompassing git tool, that includes a diff viewer.  I actually use DiffMerge for my day-to-day diffing :)

Thanks for reminding me though.  meld's source should give me a good reference!

---

