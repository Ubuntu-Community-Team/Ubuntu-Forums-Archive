---
title: "gtk# label.left"
date: 2016-05-15
forum: Programming Talk
---

### Post by roxas2 on 2016-05-15
i get this error when i do
myLabel.Left = 1;

Type 'Gtk.Label' does not contain a definition for 'Left' of type 'Gtk.Label' could be found.
are you missing an assemble reference?

basically i want to set a label's position to (0,0) or (200,200)
i looked for a while, and couldn't get an answer

using:
monodevelope
c# and gtk#2.0

can someone help??

---

### Post by roxas2 on 2016-05-15
ahh, found the method
[FONT=Monospace][COLOR=#333333][/COLOR][COLOR=#333333]myLabel[/COLOR][COLOR=#333333].[/COLOR][COLOR=#333333]SetUposition[/COLOR][COLOR=#333333] [/COLOR][COLOR=#333333]([/COLOR][COLOR=#f57d00]100[/COLOR][COLOR=#333333],[/COLOR][COLOR=#333333] [/COLOR][COLOR=#f57d00]0[/COLOR][COLOR=#333333])[/COLOR][COLOR=#333333];

lol it was a warning, not an error...[/COLOR][/FONT]

---

