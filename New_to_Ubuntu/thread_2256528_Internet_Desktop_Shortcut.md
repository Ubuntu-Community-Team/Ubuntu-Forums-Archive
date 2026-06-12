---
title: "Internet Desktop Shortcut"
date: 2014-12-13
forum: New to Ubuntu
---

### Post by Tyler_Posey on 2014-12-13
Is there a simple way to create an Internet Desktop Shortcut on Ubuntu 14.04?

---

### Post by mikewhatever on 2014-12-13
You mean a shortcut to [The Internet]("http://en.wikipedia.org/wiki/Internet")? Isn't that what web browsers are for?

---

### Post by coffeecat on 2014-12-13
Support thread, not chat.

*Thread moved to **New to Ubuntu**.*

---

### Post by pfeiffep on 2014-12-13
> **Tyler_Posey said:**
> Is there a simple way to create an Internet Desktop Shortcut on Ubuntu 14.04?Perhaps I didn't understand your question, but .... If you are using unity an internet short cut is easily made by pinning or locking the icon created on the left hand side of the screen (assuming that you have the default configuration). After pinning the icon you should be able to set the home page to any site you desire.

---

### Post by Dennis N on 2014-12-13
This works in Xubuntu - you will have to try and see if Ubuntu offers this feature:

**Right Click on Desktop > Create URL Link**

A dialog pops up to put in the Description and URL. When done, an icon shows up on the Desktop. Double click launches the web browser  and opens the URL (in a new tab if browser already open). Note: First use, it will ask you to mark the shortcut as executable. Choose yes.

---

### Post by CRYy0OKmKpJgc on 2014-12-13
[SIZE=2][FONT=arial]Install this software to create desktop icons:
```
sudo apt-get install --no-install-recommends gnome-panel
```

Run this to open the program and create the icon:
```
[/FONT][/SIZE][FONT=Ubuntu Mono]gnome-desktop-item-edit ~/Desktop/ --create-new[/FONT][FONT=arial]
```[/FONT]

---

