---
title: "how to do this"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by sulekha on 2008-06-22
System -> Preferences -> Sound
Sound preferences

General Tab -> Sounds for events (Un-Checked)

given here:-http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_configure_sound_to_work_properly_in_GNOME

via command prompt

---

### Post by RomeReactor on 2008-06-22
Hi. Try it like this:
```
gconftool --type=bool -s /desktop/gnome/sound/event_sounds 0
```

---

### Post by sulekha on 2008-06-23
can you give a brief explanation on the purpose of gconftool & how to use it ?

---

### Post by RequinB4 on 2008-06-23
> **sulekha said:**
> can you give a brief explanation on the purpose of gconftool & how to use it ?

Here's the man page - [http://linux.die.net/man/1/gconftool-2](http://linux.die.net/man/1/gconftool-2) - you can view it by typing 
```

man gconftool

```

Hope you get that annoying sound off :P

---

### Post by forger on 2008-06-23
The gconftool command given above should be run from gnome terminal, menu applications > accessories > terminal

sulekha, are you using ubuntu dapper drake (6.06)? You could try using ubuntu hardy heron (8.04) instead!

---

### Post by sulekha on 2008-07-03
> **forger said:**
> The gconftool command given above should be run from gnome terminal, menu applications > accessories > terminal

sulekha, are you using ubuntu dapper drake (6.06)? You could try using ubuntu hardy heron (8.04) instead!

nope mine is old p4 , 1.7 ghz, 256 mb ram machine, motherboard D845GLLY/D845GLAD

---

