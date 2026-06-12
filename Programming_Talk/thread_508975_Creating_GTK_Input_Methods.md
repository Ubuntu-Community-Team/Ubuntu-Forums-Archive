---
title: "Creating GTK Input Methods"
date: 2007-07-24
forum: Programming Talk
---

### Post by KyleCardoza on 2007-07-24
I've written a small suite of input methods for Eastern and Western Ojibwe, using Canadian Aboriginal Syllabics, as a SCIM table module. It works, but I'd much rather any potential users not have to play around with SCIM and such just to use it. I'd prefer to make it a GTK input method, similar to the built-in Inuktitut method. (User right-clicks, chooses "Input Methods", chooses "Eastern Ojibwe (A-finals)", and goes on with his typing)

Does anyone here know any good resources on where I should begin converting my SCIM table into a GTK IM module?

Thanks.

---

### Post by KyleCardoza on 2007-07-28
Well, taking the GTK+ Inuktitut IM as a base, I've managed to knock together some source code that *should* do the job. Now how do I compile it into a working IM module? This is... quite frustrating.

---

### Post by civetta on 2007-08-31
This topic is way out of my range in terms of helping you out, but I support all your effort! I know of a couple of young people in a NW Ont community I've been working with who are in to linux, and I'm sure they could put this to good use. So good luck and happy to bump your thread if you're still working on it!  :)

---

### Post by neskie on 2008-01-14
I don't know the answer to your question, but I'm interested in meeting other people that are working in the Free/Open Source Software and Indigenous Languages area.

I'm working on a localizing Ubuntu into Secwepemctsin[1].  I'm using the fonts from languagegeek.com and creating a keyboard in

```
/etx/X11/xkb/symbols/
```

You then have to edit a few files so that you can choose that keyboard in GNOME.  I don't know how to add a new keyboard layout in KDE yet.   It works pretty good for me.

[1] - [https://launchpad.net/~ubuntu-l10n-shs](https://launchpad.net/~ubuntu-l10n-shs)

---

