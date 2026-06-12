---
title: "Repairing permissions?"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by dopefish7590 on 2008-06-29
Hey,

Recently I wanted to change the permissions on my home folder, since when I loging in a term I am already in the home folder I wanted to type "chmod <permissions> ./ -R" But unfortunatly I typed "chmod <permissions> /. -R". Since my home folder was large I decided to come back in an hour. After I returned, I found my entire hard drive with new permissions, anyone know how to fix this?

---

### Post by sharks on 2008-06-29
try sudo in front of the command

---

### Post by dopefish7590 on 2008-06-29
No, I mean I want the old permissions back, I know about "su" and "sudo" but that is not what I am looking for...

---

### Post by Malta paul on 2008-06-29
To change the permission of your HOME folder, Press Alt+F2 then type 'gksudo nautilus' (be careful you now have root privileges). Now go to Places>Home> press the up arrow key till you are in root then go to home, right click 'properties' then untick the root boxes and tick the 'Write & execute' 
This should work:)

---

### Post by nowshining on 2008-06-29
um, u shouldn't have the ability to change privs except on ur home folder, and showing what u said u typed - u didn't use sudo, so ummmm u gotta be using a root account? it's not safe to do that.

---

### Post by vanadium on 2008-06-29
If you did not use "sudo", you cannot have changed permissions from files and directories outside of your home folder. Anyway, mass changing permissions in general is a very bad idea unless you exactly know what you do. For now, just leave things as they are, unless something is broken already. If you continue fiddling with permissions, you will make things worse, especially if you would start using sudo.

---

### Post by ChameleonDave on 2008-06-29
> **dopefish7590 said:**
> After I returned, I found my entire hard drive with new permissions, anyone know how to fix this?
I don't believe that any record of permissions is kept, so, no, you can't get back exactly what you had.  All you can do is reset the permissions to something sensible.  In general, stuff outside of the home directories should be readable by all but writable only by the owner (root).  If you changed the executable bit too... hmm.

---

