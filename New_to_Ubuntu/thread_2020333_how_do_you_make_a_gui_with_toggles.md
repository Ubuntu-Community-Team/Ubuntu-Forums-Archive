---
title: "how do you make a gui with toggles"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by z3nhakr on 2012-07-08
i was thinking about making a gui for starting and stoping gameservers, smb, ftp, and whatever and then i remembered those nifty switches/toggles that were added to the ubuntu settings app that look like something from ios. can i get those for my gui?

---

### Post by MG&amp;TL on 2012-07-09
> **z3nhakr said:**
> i was thinking about making a gui for starting and stoping gameservers, smb, ftp, and whatever and then i remembered those nifty switches/toggles that were added to the ubuntu settings app that look like something from ios. can i get those for my gui?

They're a Gtk.Switch object. If you decide to use Gtk as your GUI toolkit, you can use those. If not, there are similiar widgets in most toolkits that look like that, or if all else fails, you can use your widget set's backend to make a custom widget.

---

