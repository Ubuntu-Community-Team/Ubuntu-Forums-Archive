---
title: "[SOLVED] Fonts with linux"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-08-19
I have a bunch of fonts that I have copied over on to a stick drive. I am wondering if I can put these microsoft fonts on linux. Also if I get these fonts on to linux, will GIMP recognize that they are there, like with windows

---

### Post by Separ on 2008-08-19
Have you tried installing msttcorefonts?

[apt://msttcorefonts]("apt://msttcorefonts")

---

### Post by halitech on 2008-08-19
> **deadlySniper said:**
> I have a bunch of fonts that I have copied over on to a stick drive. I am wondering if I can put these microsoft fonts on linux. Also if I get these fonts on to linux, will GIMP recognize that they are there, like with windows

if they are .ttf then yes,  you can use them easily with linux.

Open Nautilus, go to View - show hidden files (or press Ctrl - H) and create a folder called .fonts (the . is important) and copy the fonts in there. GIMP will look at that location and allow you to use them.

---

### Post by deadlySniper on 2008-08-19
Ya, have installed it

---

### Post by deadlySniper on 2008-08-19
Ya I made the folder .fonts and well none of the ttf are getting recognized by gimp or any other program and I did restart my comp

---

### Post by halitech on 2008-08-19
in GIMP, go to File - Preferences - Folders - Fonts and check if the /home/(username)/.fonts is listed there. If not, add it.

---

### Post by deadlySniper on 2008-08-19
ya, it wont let me for some reason

---

### Post by halitech on 2008-08-19
when you click on the add button, what happens?

---

### Post by deadlySniper on 2008-08-19
wants me to add a file path and when I do the green dot turns red

---

### Post by halitech on 2008-08-19
type in ```
~/.fonts
``` and then click okay. you should then see your fonts in GIMP without needing to restart (don't think you even need to close GIMP)

---

### Post by deadlySniper on 2008-08-19
nope nothing is happening

---

### Post by deadlySniper on 2008-08-19
oops, nvm, I didnt put a foward slash in it.

---

### Post by halitech on 2008-08-19
okay, try it with /home/(username)/.fonts then

replace (username) with your username

---

### Post by JillSwift on 2008-08-19
Have you re-cached the fonts?
```
fc-cache -fv
```

---

### Post by halitech on 2008-08-19
> **deadlySniper said:**
> oops, nvm, I didnt put a foward slash in it.

so you got it working?

---

