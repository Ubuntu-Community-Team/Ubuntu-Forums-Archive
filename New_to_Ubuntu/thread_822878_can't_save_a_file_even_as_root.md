---
title: "can't save a file even as root"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by cartisdm on 2008-06-08
I keep hitting a wall.  I'm trying to use this code to create/open a text file

```
sudo gedit /etc/modrobe.d/iwl3945
```

It opens a text editor.  I enter in what I want, click save and I get "could not save file. file does not exit"

So I tried using GUI to open a text editor, enter what I need, then "save as" and navigate where I need to go and save the file as "iwl3945" then of course it says permission denied.  What the heck, shouldn't sudo gedit create the file?

---

### Post by sam_delta on 2008-06-08
try alt-f2 and type ```
gksudo gedit
``` then make your file and click 'save as'

tell us how it goes
sam

---

### Post by cartisdm on 2008-06-08
Weird, that worked.  I mean I can see why, I don't know why I didn't think of that.  But still, why wouldn't it create the file before?

---

### Post by ibuclaw on 2008-06-08
From what you've posted, you've spelt a name of a folder wrong.

It should be
```
sudo gedit /etc/modprobe.d/iwl3945
```
Although, just incase, create the file beforehand:
```
sudo touch /etc/modprobe.d/iwl3945
```

Regards
Iain

---

### Post by sam_delta on 2008-06-08
yeah, its 'modprobe.d', not 'modrobe.d'

sam

---

### Post by cartisdm on 2008-06-08
crap....brain fart.  Thanks guys for the quick responses

---

