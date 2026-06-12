---
title: "python-indicate server"
date: 2009-11-06
forum: Programming Talk
---

### Post by ukblacknight on 2009-11-06
I'm developing a plugin for emesene, that utilises the indicator-applet, just like pidgin, empathy etc do.

It's very nearly completed, however there is one problem that's preventing me from releasing:

Because this is a plugin and not part of the actual application, I need to be able to remove the "server" (remove the "Emesene" text from the indicator).  I can disconnect the server, and call hide() on it, however it still remains in the indicator.

If I turn the plugin back on again, I get two indicators, such as "Joe is online." messages and so on.

My question is, how do I go about removing the emesene instance from the indicator when the plugin is stopped?

I've **not** got an emesene.desktop entry in /usr/share/applications/, nor does it show it in there by default like it does in Karmic.  Any help would be much appreciated :)

---

