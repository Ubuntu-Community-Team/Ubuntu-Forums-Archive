---
title: "ubuntu keyboard (re)map"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by newway on 2008-09-02
the "Esc" key and some other keys on my laptop are somehow broken
(I can tell is it a hardware problem)
since I use vi alot this is unbearable! 

does anyone know how to change the key mappings, for example,
to use "F9" key as a "ESC" so everytime I press "F9" it is actually a "ESC"? 

P.S. if this can happen with "WinKey" would be even better!
Thanks!

---

### Post by Elfy on 2008-09-02
I have added a line to my etc/gdm/PostLogin/Default which adds £ for shift 3 - it looks like

xmodmap -e 'keycode 12 = 3 sterling'

You could try that changing 3 sterling to ESC, use xev from a terminal to get keycodes, if they are standard then the keycodes are

keycode 115 - Left Win key
keycode 117 - Right Win key
keycode 75 - F9

so to my understanding this would map esc to the left win key, of course it might be Escape though.

xmodmap -e 'keycode 115 = ESC'

---

### Post by newway on 2008-09-02
thank you, I am trying to see if this works.
do you know if your method only works on xwindow mode?

---

### Post by Elfy on 2008-09-02
It works in gnome.

---

