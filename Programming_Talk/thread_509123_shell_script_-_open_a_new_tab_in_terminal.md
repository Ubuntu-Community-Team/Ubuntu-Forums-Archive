---
title: "shell script - open a new tab in terminal"
date: 2007-07-25
forum: Programming Talk
---

### Post by Tex-Twil on 2007-07-25
Hello,
I have a little shell script which launch some commands and I'd like to know if it's possible to open programmaticaly a new tab or terminal to launch each of the commands in a different window/tab.

Thank you

---

### Post by nichipet on 2007-07-25
You might be able to do it so it opens them each in new instances of Terminal, but almost certainly not in tabs. Shell scripting basically works within the shell and is limited to there, so it cannot manipulate something outside of the shell, such as a GUI.

---

### Post by Tex-Twil on 2007-07-25
ok I think this should work:
> 
#!/bin/sh

gnome-terminal -e "ping www.free.fr" 
gnome-terminal -e "ping www.google.fr"


---

### Post by Note360 on 2007-07-25
I would look into screen if I where you. It should do what you need. Its kinda like tabbing inside the terminal window.

---

### Post by mikec13 on 2007-07-25
> **nichipet said:**
> You might be able to do it so it opens them each in new instances of Terminal, but almost certainly not in tabs. Shell scripting basically works within the shell and is limited to there, so it cannot manipulate something outside of the shell, such as a GUI.

If you want it in two different tabs you could do something like this:

```
gnome-terminal -e "ping www.free.fr" --tab -e "ping www.google.fr"
```

---

### Post by nichipet on 2007-07-25
> **mikec13 said:**
> If you want it in two different tabs you could do something like this:

```
gnome-terminal -e "ping www.free.fr" --tab -e "ping www.google.fr"
```

Thanks for pointing that out. I use konsole mostly, it's good to learn something new about gnome-terminal.

---

### Post by Note360 on 2007-07-25
er every one ignored my suggestion of screen huh...

---

### Post by cwaldbieser on 2007-07-25
> **nichipet said:**
> Thanks for pointing that out. I use konsole mostly, it's good to learn something new about gnome-terminal.

You can probably use the "dcop" command to automate konsole.  Try running "kdcop" and experiment sending messages to an open konsole (try the newSession method).

---

