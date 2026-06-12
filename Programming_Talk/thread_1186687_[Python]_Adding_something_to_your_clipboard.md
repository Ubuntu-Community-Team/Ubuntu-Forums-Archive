---
title: "[Python] Adding something to your clipboard"
date: 2009-06-13
forum: Programming Talk
---

### Post by Bodsda on 2009-06-13
I was wondering, how can you add say a string to a users clipboard for pasting?

Any references, links, examples would be greatly appreciated :)

Regards,

Bodsda

---

### Post by expelledboy on 2009-06-14
hmm.. I guess there would be something in the (py)gtk module. If not there definetly in the wx.. or even, what was it called again.. tkinter?

---

### Post by unutbu on 2009-06-14
There are two clipboards in Ubuntu -- the GTK clipboard and the X clipboard. The GTK clipboard is understood by GTK programs like gnome-terminal. (When you press Shift-Ctrl-v in the gnome-terminal, you get the GTK clipboard's contents.)
When you middle-click, you get the X clipboard's contents.

Here is an easy way to get and set the GTK clipboard:
[http://www.answermysearches.com/python-how-to-copy-and-paste-to-the-clipboard-in-linux/286/](http://www.answermysearches.com/python-how-to-copy-and-paste-to-the-clipboard-in-linux/286/)

It also mentions using xsel to set the X clipboard. (xsel is a package in the repository).

---

### Post by Bodsda on 2009-07-23
> **unutbu said:**
> There are two clipboards in Ubuntu -- the GTK clipboard and the X clipboard. The GTK clipboard is understood by GTK programs like gnome-terminal. (When you press Shift-Ctrl-v in the gnome-terminal, you get the GTK clipboard's contents.)
When you middle-click, you get the X clipboard's contents.

Here is an easy way to get and set the GTK clipboard:
[http://www.answermysearches.com/python-how-to-copy-and-paste-to-the-clipboard-in-linux/286/](http://www.answermysearches.com/python-how-to-copy-and-paste-to-the-clipboard-in-linux/286/)

It also mentions using xsel to set the X clipboard. (xsel is a package in the repository).
Sweet, that looks like what I want, thanks dude.

---

