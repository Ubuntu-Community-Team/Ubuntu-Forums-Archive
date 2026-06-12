---
title: "GTK3 veto window destroy"
date: 2012-03-05
forum: Programming Talk
---

### Post by r-senior on 2012-03-05
Does anyone know how this is done with GTK3? Or even GTK2?

For example, an application has a document open. It's modified and the user hits the window close button. I show a Save/Don't Save/Cancel dialog. If the user hits Cancel, the window should stay open.

But the window has already gone. :(

I've done this in wx and it has CanVeto() and Veto() methods but I can't see anything similar in GTK.

Am I perhaps using the wrong event (destroy)?

---

### Post by r-senior on 2012-03-05
> **r-senior said:**
> Am I perhaps using the wrong event (destroy)?
Yes, I was. 

I needed "delete-event" rather than "destroy". Return true to prevent propagation of the event, thereby keeping the window open.

---

