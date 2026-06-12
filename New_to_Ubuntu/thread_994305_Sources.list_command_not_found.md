---
title: "Sources.list command not found"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-11-26
Hey recently I went to check my repositories, and when I tried to pull up my sources.list it says command not found?  Not sure I know why it's doing this, and everything else is working fine, any help would be appreciated.

---

### Post by ohzopants on 2008-11-26
Where/how were you trying to check this?

You can do it visually from Synaptic, or from the command line try:
```

cat /etc/apt/sources.list

```

---

### Post by Nazty_Nayt on 2008-11-26
I'm trying to pull it up in the terminal, because just as I thought I had 2 of the same line in there, and was just wanting to edit the other out.  Normally I would just type in the following:

```
sudo /etc/apt/sources.list
```

---

### Post by mvalviar on 2008-11-26
You can also try: System>Admin>Software Sources

---

### Post by taurus on 2008-11-26
You are missing a command after the sudo.

Sudo only gives you a root privilege so if you want to edit /etc/apt/sources.list, you need to also include an editor.

```
sudo nano -Bw /etc/apt/sources.list
```

---

### Post by Nazty_Nayt on 2008-11-26
That's weird, normally I've always done it the other way, and never had a problem, with it.  Oh well, I got it fixed, so I'm not worried about it, thanks guys.

---

### Post by ohzopants on 2008-11-26
Eeeeewwwww! nano?! For real?

But he's right, the command you are entering is trying to run sources.list as a program, which it isn't.

You need to tell it which program you want to use.  There are a number of text editors available: gedit, kate, emacs, vim, vi, nano, pico...

I suggest you pick one, get used to it, and then make fun of other people for using an "inferior" one.  It's a very Linux thing to do.

---

