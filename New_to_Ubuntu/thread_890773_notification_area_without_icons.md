---
title: "notification area without icons?"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by !ndy on 2008-08-15
hi there,

something strange happened to my notification area.
now it looks just like a wider separator. no icons in it. 
i have only the volume icon on the original place. 
the battery and network manager icons are gone. 

i've tried removing and adding the "notification area". no success.. --> it just removes and adds the thing i call "wide separator".
it looks like a vertical rectangle with some zigzag inside.

maybe i've minimized it? when i right click on it and select "about", it says it IS the notification area.

help... please!

---

### Post by wolfen69 on 2008-08-15
try removing the panel and adding a new one. start over and see what happens.

---

### Post by iaculallad on 2008-08-15
On your terminal:

```
sudo apt-get install --reinstall gnome-applets
```

---

### Post by bmac on 2008-08-15
This also occurred on my system after an update. I rebooted and the problem disappeared... I'm wondering if it was a NVIDIA issue that required rebooting?

---

### Post by !ndy on 2008-08-15
> **wolfen69 said:**
> try removing the panel and adding a new one. start over and see what happens.

thank you for the quick reply.
however... nothing happens. still it is viewed like the verical line with "zigzag".
it's on the screenshot, left to my account name 'monty'

---

### Post by !ndy on 2008-08-15
> **iaculallad said:**
> On your terminal:

```
sudo apt-get install --reinstall gnome-applets
```

thank you, but it did not help either :-(

---

### Post by !ndy on 2008-08-15
> **bmac said:**
> This also occurred on my system after an update. I rebooted and the problem disappeared... I'm wondering if it was a NVIDIA issue that required rebooting?

i will try to reboot now. 
however, i think that i alreasy rebooted once since i saw it for the first time.

a rebooted as a root and voila - it's there :-)
things are easier than it seems sometimes. 
thank you.

BUT - please, how do i put it now to the correct place? i want the two icons (battery = network) to the right of my account name (together with the volume settings)

thank you

---

### Post by cariboo on 2008-08-15
You will see the icons if you log in as root as root as its own desktop. If you can't get the notification area to waork as a regular user, create a new user and see if everything works, if it does then just change your home directory name to something other than your user name and change the new home directory to your user name, transfer your files and delete the old home directory. You will have to change the ownership of the new directory to your user name, to do this in a terminal:

```
sudo chown -R <yourusername>.<yourusername> <yourhomediretory>
```

Where <yourusername> is self explanatory as well as <yourhomedirectory>

Jim

---

