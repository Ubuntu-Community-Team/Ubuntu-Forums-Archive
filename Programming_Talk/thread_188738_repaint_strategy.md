---
title: "repaint strategy"
date: 2006-06-04
forum: Programming Talk
---

### Post by earthvisitor on 2006-06-04
Hi,
When I move or resize widgets from GTK+ toolkit, even on GTK based dektops, screen update is quite delayed (background is filled with a greyish color, and content of the window is drawn a while later) compared to qt widgets and Windows(TM). I checked the examples in GTK+ tutorial both on Linux and Windows, and I concluded that this shouldn't have anything to do with Linux, as Windows version is even more annoying. This also doen't happen when I checked in IceWM, as far as Desktop effects are concerned, but when two GTK widgets overlap, this happens again. It's definitely a GTK thing. Not that painting is slow, but it's rather very delayed!

Question: How can I correct this and get smooth screen painting (as in MacOSX and Windows) in GTk (its API is really cool, and used so widely)? Or is it possible with GTK?
I need some programming tips, not flames, bashing or flames please.

Thanks for any tip.

---

### Post by pacofvf on 2008-05-26
its an old post but I'm in the same problem i tried to destroy and rebuild a window when resizing but it can't destroy a window when a resize is pending, any help would be appreciated .
thanks

---

