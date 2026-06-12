---
title: "pidgin problem"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by furoido on 2008-05-22
Earlier Pidgin was working fine, but recently everytime I try to type in more than a couple of characters, the new instant message box pops up asking for the screen name of the person or alias of the person i want to im. even if i enter the name, it makes no difference...as soon as i try to chat, the box simply re-appears...


anyone know of a solution? i tried uninstalling (to see if re-insalling would help) using add/remove but i get a massage saying some other applications depend on pidgin so can't be uninstalled.

---

### Post by ajgreeny on 2008-05-22
Try temporarily renaming the ~/.purple folder in your home as .purple.bak and then try again.  You will need to re-enter you own and your buddies identification info, but it shouldn't be too difficult.  If that doesn't help, try completely uninstalling pidgin, rather than just uninstalling it.

---

### Post by neurostu on 2008-05-22
If you want to uninstall pidgin try using the synaptic package manager or by opening a terminal and typing:
```

sudo apt-get remove pidgin

```
then to re-install type:
```

sudo apt-get install piding

```

---

### Post by furoido on 2008-05-23
Tried uninstalling and then re-installing, but makes no difference...will try the other suggestion of renaming the ~/.purple folder to .purple.bak.

But exactly how do I access the folder to rename it? Sorry, a complete Linux newbie, so not sure how its done!

---

### Post by Steve413z on 2008-05-23
> **furoido said:**
> Tried uninstalling and then re-installing, but makes no difference...will try the other suggestion of renaming the ~/.purple folder to .purple.bak.

But exactly how do I access the folder to rename it? Sorry, a complete Linux newbie, so not sure how its done!

I agree, removing or renaming .purple is probably the solution,

method one, open a terminal to move it and type (note, move and rename essentially do the same thing)
> mv .purple/ .purple-bakor you can just delete the folder (it only contains pidgin settings, and is recreated automatically next time you start pidgin)
> rm -rd .purple/or the GUI method, using the file browser "Nautilus" goto your home directory, and goto your home directory
then in the menu, select View and select Show Hidden Files
(or Ctrl+H)

just for future reference, if you didn't know, in Linux/Unix any file starting with a "." is a hidden file

not to be confused with dot slash "./" which means current directory

---

### Post by furoido on 2008-05-23
Steve,

Just tried both your command suggestions and it seems there is no 'purple' file or directory in my system!

Any other suggestions?!!

Thanks!

---

### Post by furoido on 2008-05-23
Maybe the easiest would be to simply install and use another chat program? If so, any recommendations?

---

### Post by Steve413z on 2008-05-23
when you issue the commands it usually doesn't even say anything, it just does it, so it might have worked without your realizing, just try to start pidgin again, maybe it'll work

---

### Post by furoido on 2008-05-23
Using the synaptic, I added a couple of additional pidgen files that were listed there but not installed...not sure what they were, but seems to be working ok now!

Anyway, thanks ,guys, for your help!

---

### Post by neurostu on 2008-05-23
in the future if you want to see hidden folders you can open nautilus (equivalent to windows explorer) and press CNTL-H and that will show all hidden folder and files.  (Anything with a . in front of it is considered hidden)

---

