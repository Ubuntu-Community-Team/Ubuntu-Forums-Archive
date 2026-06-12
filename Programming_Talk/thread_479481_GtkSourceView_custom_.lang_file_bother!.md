---
title: "GtkSourceView custom .lang file bother!"
date: 2007-06-20
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2007-06-20
Following some documentation (the only documentation) I found, I have created a .lang file for a little programming language I use. (I'm taking bets, by the way: Could gtksourceview's web site be *any worse*?)

However, it turns out that I followed the wrong documentation! I seem have created a "new" 2.0 language format, which is apparently not supported by the version currently available in Feisty.
Instead, I get this error: > (scribes:6843): GtkSourceView-WARNING **: Usupported language spec version '2.0' in file '/home/dmccall/.gnome2/gtksourceview-1.0/language-specs/blitzmax.lang'

(scribes:6843): GtkSourceView-WARNING **: Error reading language specification file '/home/dmccall/.gnome2/gtksourceview-1.0/language-specs/blitzmax.lang'


Looks like the version in SVN uses the 2.0 language format, but I'm hoping that there is something else, stable and released, that will.
...Is there?

---

