---
title: "Cairo, double buffering, blurred rendering"
date: 2010-02-26
forum: Programming Talk
---

### Post by kahumba on 2010-02-26
Hi,
Pretty sure no one's gonna look into it, but I got nothing to lose for I've lost the whole day trying to figure out what's the matter.

So here's the deal.
While learning Gtkmm I decided to create a file browser my way - that is by drawing the table myself, not using the Gtk::TreeView for a slew of reasons.

Now, anything is drawn fine. But, when scrolling (my table is inside a ScrolledWindow obviously) - the thing was flickering. So I implemented my own double-buffering to fix the flickering. Done, but now for some reason when scrolling the rendered stuff is sometimes blurred. See second screenshot.

The drawing code is in DetailedTable.cpp
Hope someone's got time and ideas about why it's blurred are highly welcome!

Edit: somehow I managed to fix it, sorcery, I don't know why it works now.

---

