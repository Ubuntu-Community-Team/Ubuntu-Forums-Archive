---
title: "Gnome Fallback - Changing the window buttons"
date: 2011-10-08
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Spr0k3t on 2011-10-08
So I'd like to add or change the location of the buttons for the gnome-fallback session, but I can't figure out how to do this and make it stick.

In Gnome-Shell session, I can change this without problems by doing the following:

[gconf-editor] /desktop.gnome.shell.windows.button_layout

Then edit the configuration to how I want it.  Relog the shell and everything is in place exactly how I want it.  In the Fallback session, this is a different story.  Everything I have tried to change the layout and configuration, it reverts back to the layout found when using Unity.

HALP!

---

### Post by tista on 2011-10-08
> **Spr0k3t said:**
> So I'd like to add or change the location of the buttons for the gnome-fallback session, but I can't figure out how to do this and make it stick.

In Gnome-Shell session, I can change this without problems by doing the following:

[gconf-editor] /desktop.gnome.shell.windows.button_layout

Then edit the configuration to how I want it.  Relog the shell and everything is in place exactly how I want it.  In the Fallback session, this is a different story.  Everything I have tried to change the layout and configuration, it reverts back to the layout found when using Unity.

HALP!

Hi Spr0k3t,

If we change the "/apps/metacity/general/button_layout" value on gconf-editor, happens any success? ;)

cheers.

---

### Post by Spr0k3t on 2011-10-09
Thank you very much, this is exactly what I was looking for.  Placements corrected.

---

