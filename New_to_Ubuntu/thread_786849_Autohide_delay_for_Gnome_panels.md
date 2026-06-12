---
title: "Autohide delay for Gnome panels"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by wrgb2 on 2008-05-08
Anyone know how to set the auto-hide delay for Gnome panels - mine takes too long to hide and unhide.
thanks,

---

### Post by wrgb2 on 2008-05-08
Ok, I found the setting in the Gnome configuration editor, but I have it set to zero and there is still a short delay (maybe a quarter second or so) before the panel hides and unhides.  I'm used to this happening immediately in Windows (sorry) - is this just the way it is in Gnome?

---

### Post by glennric on 2008-05-08
Find the key /apps/panel/toplevels/ and select the panel you want to change the settings for (top_panel_screen0, bottom_panel_screen0, etc).

Make sure the keys hide_delay and unhide_delay are set to 0, and enable_animations is not checked.  This makes for an almost instantaneous hide and show of the panel.

Edit:  With enable_animations not checked you won't get the sliding in and out of the panel, it just kind of pops up and down.  It may be that you were setting the hide and unhide keys in the wrong place before.  There are also such settings in the general options, but you have to set the options for specific panels.

---

### Post by wrgb2 on 2008-05-08
thanks, glennric - unchecking enable_animations did it.

---

### Post by rolfen on 2009-08-16
Add a new string key, named **animation_speed** and with the value **fast**. When it is not set then it defaults to **medium**.

---

