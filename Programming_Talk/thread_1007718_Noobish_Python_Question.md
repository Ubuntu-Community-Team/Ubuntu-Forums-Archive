---
title: "Noobish Python Question"
date: 2008-12-10
forum: Programming Talk
---

### Post by abeisgreat on 2008-12-10
So you know when your downloading a .deb from a repo, and it has the bar in the terminal that keeps updating with the percent downloaded? Yes well I want to do something like that. So i was thinking, I either need a) a way to keep updating that bottom bar, or b) a way to delete the previous line and replace it, making the effect that the one line is changing, this is a bit hard to explain but, does anyone know how to do this in a py script?

---

### Post by pieoncar on 2008-12-10
I searched for python curses progress bar in google, and this was the first result: [http://code.activestate.com/recipes/168639/](http://code.activestate.com/recipes/168639/) - You'll probably want to check the first few comments there too.

Curses or ncurses is the interface used in terminals to "draw" fancy things beyond simply printing text to new lines.

---

### Post by snova on 2008-12-10
The '\r' character may be of use. It returns the cursor to the beginning of the line so you can overwrite it again when updating.

ncurses might be overly complicated for a simple progress bar...

---

### Post by abeisgreat on 2008-12-11
> **snova said:**
> The '\r' character may be of use. It returns the cursor to the beginning of the line so you can overwrite it again when updating.

ncurses might be overly complicated for a simple progress bar...

I tried using \r in several ways but I couldnt get it to function properly

EDIT: nevermind, you have to call it like

print 'hello world', '\r'

not just 

print 'hello world\r'

like I was trying

---

