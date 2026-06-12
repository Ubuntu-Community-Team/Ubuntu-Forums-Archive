---
title: "Help with panels in Java"
date: 2007-08-31
forum: Programming Talk
---

### Post by Fireblend on 2007-08-31
I'm having some issues trying to create an interface for a Java assignment. I want to have 2 panels, on an horizontal arrangement. One of them is just a menu, so I want it to be not as big as the first one.

However, I have no idea how to set sizes. I know panels have flow layout by default also, which won't let me add buttons in the menu panel vertically. Also, component-less panels look like 3 x 3 boxes, and I want them to stretch as much as they can inside my window.

I'm guessing this is probably a layout issue, and I'm using wrong methods for resizing or something.

Thanks in advance!.

---

### Post by jnorthr on 2007-08-31
Look into the boxlayout manager. I think you can set to to Y_AXIS (?). so when you add several buttons then the box layout mgr will stack them vertically. You will not be able to dictate the actual size of your jcomponents as the layout mgr does that according to available screen size.

---

### Post by Fireblend on 2007-08-31
> **jnorthr said:**
> Look into the boxlayout manager. I think you can set to to Y_AXIS (?). so when you add several buttons then the box layout mgr will stack them vertically. You will not be able to dictate the actual size of your jcomponents as the layout mgr does that according to available screen size.

Thanks. I looked into BoxLayout, and it does seem to be what I'm looking for. However, now it seems I'm not able to say how much space there is between components and they're now all stacked one after the other. I'd like to them be a little pixels apart. Anyway, thanks a lot, it's definitely been of help.

---

