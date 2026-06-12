---
title: "Starting X Window programming"
date: 2012-10-24
forum: Programming Talk
---

### Post by NeoStark on 2012-10-24
Hi everyone!

I am wondering if there is any good FULL tutorial to programming the X window system?
I don't wish to use a Tookkit such as gtk or Qt.

I have done work in Qt before but am looking for a more cross platform method and X is universal to most unix, linux and mac systems.

Thank-you!!!

---

### Post by MG&amp;TL on 2012-10-24
> **NeoStark said:**
> Hi everyone!

I am wondering if there is any good FULL tutorial to programming the X window system?
I don't wish to use a Tookkit such as gtk or Qt.

I have done work in Qt before but am looking for a more cross platform method and X is universal to most unix, linux and mac systems.

Thank-you!!!

Not really in my experience, sorry, although the API reference is okay. 

What do you actually want to do? IMO your approach is all wrong.

For starters, why do you not want to use a toolkit? They're there to stop you making the same mistakes they did. It's not going to bog your code down that much. :)

Both Qt and GTK+ (and many others) are cross-platform. They'll run on *nix, mac, and windows systems. Whereas X windows stuff will not run on windows.

Thirdly, X windows is (hopefully) on the way out for desktop linux: there is a replacement afoot to deal with the (frankly ancient) technology X uses. [http://wayland.freedesktop.org](http://wayland.freedesktop.org)  ...so it's likely that your code may be deprecated fairly quickly if Wayland takes off.
[]("http://wayland.freedesktop.org")

---

### Post by trent.josephsen on 2012-10-24
MG&TL is on the mark, I think.

If you want to avoid using a toolkit for the UI because you want more direct control over what's displayed, perhaps you should be looking at a library like SDL or Allegro instead.

---

### Post by satsujinka on 2012-10-24
Here's as good a place to start as any:
[http://tronche.com/gui/x/](http://tronche.com/gui/x/)

It's really not that hard to find more resources if that doesn't work for you.

As has already been noted, QT, GTK+, or even SDL are much more portable than using XLib or XCB.

---

