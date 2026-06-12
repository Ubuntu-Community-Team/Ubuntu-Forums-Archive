---
title: "Doomed : Gnome panels gone and alt+F1/F2 doesn't work!"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by kauboy on 2008-05-13
I was trying to install Avant Window Manager and promptly removed my Gnome panels as was instructed. Now, I'm unable to run the AWM due to some compiz-fusion issue and my alt+F1/F2 doesn't bring up the Terminal or the Run Application window either. I'm on Ubuntu 8.04 Hardy Heron. Having lost my panels as well as my keyboard shortcut for the Terminal, I'm afraid I've doomed myself! Any workarounds? I just want to have my old Desktop back. I'll deal with the AVM later. Please help! :(

---

### Post by ironwolfe on 2008-05-13
hit control-T to get a terminal

then type in the following:

```
gnome-panel
```

should do it.

---

### Post by Caram on 2008-05-13
> **ironwolfe said:**
> hit control-T to get a terminal

then type in the following:

```
gnome-panel
```

should do it.
Ninja Shortcuts
:)

---

### Post by kauboy on 2008-05-13
sorry ... din't work! Ctrl+T did nothing. :(

---

### Post by ironwolfe on 2008-05-14
Really wow!

I have a feeling your keyboard is hatched as well.

right click on the desktop - this will bring up a pop-up menu - select "open terminal"

then type

```
gnome-panel
```

if that doesn't work you may need to kill some processes, specifically compiz and any gnome-panel apps that are running.

let me know if this is the case before I confuse you.

you may want to restart x by hitting control-alt-backspace which may jog things loose.

---

### Post by PinkFloyd102489 on 2008-05-14
Drop to a console by hitting Ctrl+Alt+F1, log in, then enter "gnome-panel" to start it up. Hit Ctrl+Alt+F7 to get back to the GUI.

---

### Post by ironwolfe on 2008-05-14
> **PinkFloyd102489 said:**
> Drop to a console by hitting Ctrl+Alt+F1, log in, then enter "gnome-panel" to start it up. Hit Ctrl+Alt+F7 to get back to the GUI.

He tried that already - sounds like keyboard is not working - compiz?

---

### Post by Inxsible on 2008-05-14
Why do you keep starting up new threads when people are already trying and helping you on your other threads. !!!

And you don't even listen after asking you not to start up new threads. You still start this one up for the same problem. This is your 3rd thread on the topic.

Jeez !!!

---

### Post by PinkFloyd102489 on 2008-05-14
> **ironwolfe said:**
> He tried that already - sounds like keyboard is not working - compiz?

No, he hasnt tried that already. You guys suggested using a terminal, not the console.

---

