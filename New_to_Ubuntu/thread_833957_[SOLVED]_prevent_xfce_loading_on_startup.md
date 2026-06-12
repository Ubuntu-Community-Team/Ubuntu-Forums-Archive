---
title: "[SOLVED] prevent xfce loading on startup"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by batfastad on 2008-06-19
Hi everyone
I'm trying to build a sort of test-server using Xubuntu to mess around and get used to Linux.

How can I stop the window manager (xfce in Xubuntu) loading on startup?
I just want Linux to start with the user/pass prompt. Then to manually type the command to start up the Xubuntu GUI.
I'm guessing there's a startup script I need to edit somewhere, but where can I find it in Xubuntu?

Thanks, B

---

### Post by hyper_ch on 2008-06-19
try:
```

sudo update-rc.d -f gdm remove

```
that should remove the graphical login manager from all runlevels and hence boot into shell login.

---

### Post by barbedsaber on 2008-06-19
> **hyper_ch said:**
> try:
```

sudo update-rc.d -f gdm remove

```
that should remove the graphical login manager from all runlevels and hence boot into shell login.

thats cool, I might do that just to make me feel geeky

---

### Post by hyper_ch on 2008-06-19
or is it "xdm" on Xfce? I think Xfce uses also gdm....

---

### Post by batfastad on 2008-06-19
Wow ok, I'll give that a go!

Then when I login at the shelll, what command do I need to start up xfce as normal?

Thanks :D

---

### Post by hyper_ch on 2008-06-19
```

startx

```

---

### Post by batfastad on 2008-06-19
Ok that all works perfectly in Xubuntu!

Final question on this... is there a button/icon/command anywhere in xfce where I can basically quit X and return to the prompt from where I typed startx?

Thanks, B

EDIT: SOLVED!
I've got this worked out... I just use the quit icons in xfce and that dumps me down to the shell prompt again. Because we removed the graphical login manager above

Thanks for all the help guys :D

---

