---
title: "Color picker in python?"
date: 2008-08-30
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-08-30
I want a color picker that I can use with my python app.

---

### Post by snova on 2008-08-30
There's probably one built into whatever GUI toolkit you're using. I can't say anything for Tk or GTK, as I don't know a thing about them, but Qt has QColorDialog.

Tell us what toolkit you use, and somebody experienced with it (probably not me) will help. Or just look in the reference docs... assuming they exist.

Unless, of course, you haven't chosen a toolkit. Well, somebody else will have to compare them.

PS. Wow, very succint. (Your question, that is.)

---

### Post by nvteighen on 2008-08-30
GTK+ has the GtkColorSelection, which you can add to any window you like as a GtkWidget. But, if you instead want a popup dialog, you can use GtkColorSelectionDialog.

---

### Post by crazyfuturamanoob on 2008-08-31
I use pygame.

---

### Post by fifth on 2008-08-31
I've never used PyGame, but a quick google gives [http://www.pygame.org/project/687/]("http://www.pygame.org/project/687/").

---

