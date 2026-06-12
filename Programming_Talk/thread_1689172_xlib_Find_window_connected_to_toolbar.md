---
title: "xlib Find window connected to toolbar"
date: 2011-02-16
forum: Programming Talk
---

### Post by RocketRanger on 2011-02-16
Hi

I have problem. I am trying to move a window using xlib. If the pointer is hovering over the window the XMoveWindow works fine, however if the pointer is hovering over the toolbar, XMoveWindow does nothing.

I can tell from XQueryTree that the window IDs for the main window and its toolbar are different, however traversing the tree isn't of much help as there is no direct parent-child relationship between them.

Any thoughts?

---

