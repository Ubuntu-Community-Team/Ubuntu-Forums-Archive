---
title: "Horizontal Scroll"
date: 2011-12-15
forum: Programming Talk
---

### Post by jesuisbenjamin on 2011-12-15
Hi,

I'm working on an interface as part of a DE, using Python and Qt.
This interface shows and hides on scrolling over the bit that's always visible. What surprises me is that the application reacts to vertical scroll on my touch-pad as well as it reacts to horizontal scroll.

I expected it to distinguish the two and not respond to horizontal scroll. Also I wanted to be able to browse the content of a list within this application using horizontal scroll, and hide the application again with vertical scroll.

Is this something universal? Is it a GUI kit problem or is proper to X environment or touchpad behaviour? I suppose touch-screens make the difference between the two, but it probably works differently altogether?

Do you have some clues for me here?

Thanks.
B.

---

### Post by jesuisbenjamin on 2011-12-15
Ah, it must be a Qt thing, because when scrolling over a scroll area or list, it makes the difference between horizontal and vertical scroll. So there's something I missed out in capturing the scroll event.

Cheers anyway for the 42 views so far :D

---

