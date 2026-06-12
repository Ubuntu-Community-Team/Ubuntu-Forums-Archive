---
title: "Changed Panel Text Color - Now other colors are weird!"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by Preturbed on 2008-10-02
I changed panel color with the code at the end of the post (as described in another place on this forum), and my window decoration went from orange to blue. Some other colors have changed, too. How can I get them back to normal?

```
gedit .gtkrc-2.0
```

```
style "panel"
{
    bg[NORMAL]               = "#842525"
    fg[NORMAL]               = "#FFFFFF"
}
widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"
```

---

### Post by rybaxs on 2008-10-02
```

metacity --replace

```

---

### Post by Preturbed on 2008-10-02
Well that didn't do it. It *did* change my window decoration color back to blue, but the problem is that the decoration color is set to Human which, at least on this computer, was orange before the mess above.

EDIT: Colors are back to normal after I fiddled around in Appearance Prefs > Theme for a while. Changed back seemingly at random.

EDIT EDIT: Maybe something to do with Emerald?

---

### Post by Preturbed on 2008-10-02
annnd it's back, with no excuse this time.

---

