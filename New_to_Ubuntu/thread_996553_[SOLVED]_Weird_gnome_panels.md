---
title: "[SOLVED] Weird gnome panels"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Linuturk on 2008-11-28
Please see the attached image. I've increased my resolution via the preference menu, and my top and bottom gnome panels aren't filling the screen as they should. I was able to fix the bottom one by dragging it around some, but the top one is still failing to conform. I've also noticed that my login window isn't the correct resolution either. How do I fix this?

---

### Post by linuxguymarshall on 2008-11-29
Try :

[LIST]
[*]Restarting 'X'
[*]Relocating the bar to the left or right then putting it back at the top
[*]Deleting the bar and making another
[/LIST]

---

### Post by Linuturk on 2008-11-29
No change using all of your suggestions.

---

### Post by anonymous_user on 2008-11-29
Check the panel properties and make sure its set to be full width.

---

### Post by drs305 on 2008-11-29
*Added: Anonymous_user's method is the easiest. Right cick the panel, Properties, tick 'expand'. Here is where the changes are stored:*

There is a section in gconf that determines whether a panel expands across the entire page. Check this setting:
```

gconf-editor /apps/panel/toplevels/panel_0/expand

```

You can also check panel_1, etc.

---

### Post by Linuturk on 2008-11-29
yes, it is set to full width. I think there is a problem with the max resolution that gnome is seeing. 

For example, when the Authorization for Administrative Password box pops up, the grayed out area doesn't cover my full resolution. In fact, it covers the exact area my panels are limited to. Programs, like firefox, aren't affected by this limit.

---

### Post by Linuturk on 2008-11-29
Do you think I should change something in my xorg.conf? There isn't anything specific configured in there right now.

---

### Post by Linuturk on 2008-11-30
I realized that the external display was on, so I disabled that via the config applet. That fixed the problem :)

---

