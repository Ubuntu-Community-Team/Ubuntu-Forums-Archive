---
title: "Definitively remove the size request of a widget (Python, Gtk3)"
date: 2012-05-28
forum: Programming Talk
---

### Post by davidedepau1996 on 2012-05-28
I want to fit some text in a label. I almost managed to do it: when I enlarge the window, I add some "<big>" tags to the label and the text enlarges with the window. But if I try to shrink the window, the size-request of the label doesn't let me do it. The label is updated many times a second, so if I try to set a custom size request every time I apply a new label, the window will shrink and enlarge if i try to shrink it.
What I want to do is removing the size request, without word wrapping and other things like this: I just want let the label go out of the window.

Sorry for my English...

Thanks ;)

---

