---
title: "update manadger wont update"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by wargodsown on 2008-09-15
i get into the update manadger and origonally it kinda worked sometimes it would work it would ask me for the admin password to install everything and it worked fine now it wont ask for the password and it just sits and spins forever   any ideas???? any help would be much apreciated

---

### Post by iaculallad on 2008-09-15
> **wargodsown said:**
> i get into the update manadger and origonally it kinda worked sometimes it would work it would ask me for the admin password to install everything and it worked fine now it wont ask for the password and it just sits and spins forever   any ideas???? any help would be much apreciated

What about doing it in the terminal:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by northern lights on 2008-09-15
Theoretically, you could set the sudo timeout to infinity, such that you'd only have to enter your password once per session.

For reasons of security, I wouldn't recommend such modification, however.

---

### Post by wargodsown on 2008-09-19
ok i pressed esc and went thru the menu and took it thru recovery mode and it fixed a bunch of stuff now my problem is that after it fixed it all now i have no sounf i mean wtf it says my gstreamer codecs are either not installed or my sound card is'nt installed ether or some crap like that so now i'm trying to figure out how to fix that lol dam i swear its like its laughing at me lol

---

