---
title: "Restore default terminal instead of qterminal?"
date: 2021-09-24
forum: New to Ubuntu
---

### Post by NotQuiteSU on 2021-09-24
I installed lubuntu on an old system, but I'm not a fan of qterminal. Is there a way to restore the default terminal?

---

### Post by guiverc on 2021-09-24
`qterminal` is the default terminal for a Lubuntu/LXQt system.

You've provided no release details; but on a Qt5 desktop, a Qt5 terminal will be most efficient (ie. will use libraries/toolkits that are already in RAM as they are used by the desktop itself), thus the default `qterminal` is all Lubuntu have provided since using the LXQt desktop.

[https://manual.lubuntu.me/stable/3/3.1/3.1.3/qterminal.html](https://manual.lubuntu.me/stable/3/3.1/3.1.3/qterminal.html)

(you didn't provide release details; so if you're not using the latest *stable* release you can adjust the URL to view the *lts* release)

---

### Post by NotQuiteSU on 2021-09-24
Sorry, I was hoping to use the terminal which is standard on ubuntu, most like Putty.

---

### Post by sudodus on 2021-09-24
In standard Ubuntu Desktop **[FONT=Courier New]gnome-terminal[/FONT]** is the default terminal. The name of the program is the same as the name of the package for installation, so you can install it with the following command

```

sudo apt update
sudo apt install gnome-terminal

```

It works well but will bring some gnome program packages into Lubuntu.

There are many alternative terminal emulator programs, that are more or less independent, for example **[FONT=Courier New]sakura[/FONT]**.

---

