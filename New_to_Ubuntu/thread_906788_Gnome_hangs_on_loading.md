---
title: "Gnome hangs on loading"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Elwas on 2008-08-31
I recently upgraded from Feisty to Hardy, and after rebooting I've had trouble every time I've logged into Gnome.  Usually, I'll be able to click on an icon or on the menu, but then the application window won't appear (or will appear, but blank) and the menu will hang.  Sometimes, it never completes loading and a gray box appears in the upper left corner on top of the brown loading background.  Oddly, I can still move the mouse throughout all of this.

I've done a number of searches and some people have similar problems, but they seem to be caused by nvidia drivers or issues with compiz.  I don't run compiz, and I have an Intel graphics card.  I've tried both the new intel driver and the older i810 (w/ 915resolution), to no avail.

Does anybody have any clue what might be causing this?  Is there any diagnostic info that might be helpful?  Thank you!

---

### Post by cwsnyder on 2008-08-31
Question:  Is your Intel graphics on the motherboard or a separate card?

If it is a separate card, I would check Intel's site for updated drivers for Debian/Ubuntu GNU/Linux.

If it is on the motherboard, I would suggest either getting a separate graphics card (desktop machine) or reversing the upgrade and go back to Feisty (laptop).  It is probably a kernel driver problem from your description.

cwsnyder

---

