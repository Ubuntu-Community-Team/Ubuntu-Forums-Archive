---
title: "Map &quot;Fn&quot; key on laptop to Super?"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by linkmaster03 on 2008-08-25
How can I map the "Fn" (function) key on my laptop to Super permanently?

---

### Post by jrothwell97 on 2008-08-25
Hmm... the Super key is another name for the Logo key (usually labelled with the Windows logo or a 'home' icon. Fn, on the other hand, performs hardware funcions, so I'm not sure it's possible.

---

### Post by linkmaster03 on 2008-08-25
I'm pretty sure it acts like a Num Lock key. My keyboard is like this:

[img]http://www.notebookreview.com/assets/2013.jpg[/img]

The Win key in the top right corner doesn't act as Super either. :(

---

### Post by damis648 on 2008-08-25
The Fn key is not directed to the OS when pressed, by directed to the BIOS. The Fn key is never seen by the OS, meaning that the BIOS decides what happens when you press the function key, so, for example, if I say Fn+U, my BIOS simply sends the OS the keypress "4" and that is all. So, unless your BIOS has this option, no.

---

### Post by linkmaster03 on 2008-08-25
Ohh... what do you think about that windows key in the corner? Or maybe the pause key?

---

### Post by damis648 on 2008-08-25
> **linkmaster03 said:**
> Ohh... what do you think about that windows key in the corner? Or maybe the pause key?

Well try to change to change a combination in System>Preferences>Keyboard Shortcuts and see what happens when you press that corner super key and some other key.

---

### Post by linkmaster03 on 2008-08-25
It says Super L. But it doesn't work with Compiz shortcuts containing Super. :(

---

### Post by drs305 on 2008-08-25
Some commands that might be helpful in your quest:

You can see what code a key returns by running:
```
xev
```
or:
```

sudo apt-get install xkeycaps
xkeycaps
```

You can also see what all the key assignments are with:
```

xmodmap -pke
```

---

