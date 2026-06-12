---
title: "ctrl + a"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by GediminasB on 2011-10-22
Hello,

I use Ubuntu 11.10. Somehow Ctrl+A started to move cursor to beginning of line instead of selecting all text. Anyone can help me to fix it? :confused:

---

### Post by MG&amp;TL on 2011-10-22
Using a text editor or a browser?

In web browsers and some text editors, triple-clicking selects all text an a line.

---

### Post by cgroza on 2011-10-22
If you this happens in a terminal, you must know that this is the default behaviour in bash.
The way to select all the text in it is already terminal dependent.

---

### Post by GediminasB on 2011-10-22
It happens in gedit, chrome, firefox, banshee... But only in text fields e.g. I can select whole text in page with ctrl + a. In nautilus it works on both location field and files list. Moreover ctrl+f moves cursor forward, ctrl+e moves it to the end.

---

### Post by GediminasB on 2011-10-23
Figured it out :) Keybinding theme was set to "Emacs" in gnome-tweak-tool. Switched it to "Default" and everything works as it should :popcorn:

---

