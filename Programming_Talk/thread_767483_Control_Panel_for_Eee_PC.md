---
title: "Control Panel for Eee PC"
date: 2008-04-25
forum: Programming Talk
---

### Post by jfbilodeau on 2008-04-25
For anyone who is interested, I created a little control panel for an Eee PC running [eee][X|K]ubuntu that takes advantage of the [eee kernel module]("http://code.google.com/p/eeepc-linux/").

This is actually my first time using Gtk, Glade and creating a .deb package.

It's functional, but the code is not very clean (lack of constants and duplicate code). However, being new to Gtk, and not having a working Internet connection during most of the development work, I know there's plenty of room for improvement in the way I'm using Gtk.

Screenshots:
[IMG]http://chronogears.com/eeectl/eeectl-tooltip.png[/IMG]
[IMG]http://chronogears.com/eeectl/eeectl-control.png[/IMG]

Debian package:
[http://chronogears.com/eeectl/eeectl_0.1-1_i386.deb]("http://chronogears.com/eeectl/eeectl_0.1-1_i386.deb")
Source Tarball:
[http://chronogears.com/eeectl/eeectl-0.1.tar.bz2]("http://chronogears.com/eeectl/eeectl-0.1.tar.bz2")

Hope you enjoy!

J-F

---

### Post by mike_g on 2008-04-26
Nice :) I was thinking of making the same sort of thing, but it never got past being an idea. Been busy with other stuff lately. Anyway I'll have a play around with it later when I'm on my eee.

---

### Post by Can+~ on 2008-04-26
> It's functional, but the code is not very clean (**lack of constants** and duplicate code).

I suggest you to use a configuration file for constants, something easy like, instead of the hard coded way.

```
constant1=value
constant2=value
```

Also, have you tried the latest Glade? It doesn't produce C any more, it just generates a .glade (which is on XML). It could tidy up all that mess of gtk library there. I recommend it, because I use glade+python.

Wish I had an EeePeeCee to try it :(.

---

### Post by jfbilodeau on 2008-04-26
> **Can+~ said:**
> Also, have you tried the latest Glade? It doesn't produce C any more, it just generates a .glade (which is on XML). It could tidy up all that mess of gtk library there. I recommend it, because I use glade+python.

Thanks for the suggestions. I used Glade 3.4, which generated an XML file. The rest of the GTK code was to create a GtkStatusIcon which, as far as I can tell, cannot be defined in Glade. Also, correct me if I'm wrong, but the only way I could see to control the content of the Glade file is through the Gtk APIs.

As for the constants, I agree 100%. I would also want to look at gettext to ensure that it can easily be localized.

Thanks, and have a great day,

J-F

---

