---
title: "[SOLVED] Can't change directory!"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-07-17
Hi,

Using Hardy Heron.

Just tried to install Adobe Flash player. Was following instructions and in terminal I typed
```
cd /Desktop
```
reponse -

bash: cd: /Desktop: No such file or directory

Uh? Why? Never had this problem before. What have I done wrong now?

---

### Post by benfindlay on 2008-07-17
It's ```
cd Desktop
```

Putting a / before implies it is in the root folder, whereas your Desktop folder is likely located in /home/yourusername/Desktop

Hope this helps!

---

### Post by appi2012 on 2008-07-17
your current directory is /home/user/, so cd /Desktop is trying to go to [root]/Desktop, which doesn't exist. Try:
```
cd Desktop
```

whoops - too late:)

---

### Post by Stunts on 2008-07-17
the "/" means an absolute path.

type cd Desktop

or if that fails type cd ~/Desktop.

The  "~/" represents your home folder.

Good luck!

---

### Post by Tim Silver on 2008-07-17
What can I say? ..Bloody fool! Thanks chaps.

---

