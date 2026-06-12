---
title: "Transfering settings"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by sprogmeister on 2008-08-24
I have just put a 500Gb hdd into my machine and have my old Ubuntu hdd as an external usb hdd. I had tried using back up software but none would work. Is there anyway I can import the settings on my (now) external hdd onto the new hdd, so I can use my old settings?

---

### Post by scragar on 2008-08-24
all of your settings should be stored in your home folder, as long as you move them over it should all be fine(you may need to run:```
sudo chown -R $USER ~/
``` after moving the files over to reset ownership).

---

### Post by sprogmeister on 2008-08-24
Thanks Scragar, have done as you said. My home folder seems the same but the desktop is not, nor are the applications I used run. Is there anything I can do about this?

---

### Post by scragar on 2008-08-24
I thought your problem was just settings(and what about your desktop is different? It's in the home folder, so unless you've installed a theme using emerald or something similar it should be the same).

```
dpkg --get-selections > pkg.list
```
will make a list of all aplications you have installed, when that's a complete(should take a couple of seconds max) use ```
sudo apt-get update
sudo dpkg --set-selections < pkg.list
sudo apt-get -u dselect-upgrade
```
to install them on the new HD. I think that's almost everything...

---

### Post by sprogmeister on 2008-08-24
Thanks for that I will try it now.

---

### Post by sprogmeister on 2008-08-24
Tried it but it sadly seemed to do nothing at all. Excusing my lack of experience, have you got any other ideas?

---

### Post by scragar on 2008-08-24
just a quick q, you did move the file right? (it would be called pkg.list and most likely in your home directory(unless you use **cd** to change that)) That's the list of programs, you will need to move it from the first HD to the second(again, to your home directory. I should have explained this better back when actualy )

an output of any errors would be nice as well.

---

### Post by sprogmeister on 2008-08-24
I can't find pkg.list at all ????

---

### Post by sprogmeister on 2008-08-24
The log on screen also gives warnings of 644 permissions and that I need to own the $Home. I understand that this means I need to take ownership but do not understand how to. Please help?

---

### Post by scragar on 2008-08-24
open a terminal, then run
```
sudo chown -R $USER ./
```

---

### Post by sprogmeister on 2008-08-24
Tried it and got the reply:


chown: cannot access `./.gvfs': Permission denied


Any ideas?

---

