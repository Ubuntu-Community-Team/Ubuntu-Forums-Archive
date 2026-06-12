---
title: "Unable to delete file."
date: 2008-11-30
forum: New to Ubuntu
---

### Post by jason6g on 2008-11-30
So i have this file i wish to remove from my computer.

i try doing so through nautilus and nautilus locks up requiring a hard restart (keyboard and mouse freeze for at least 5 minutes till i lost patience and powered it off)

tried doing so through sudo nautlius and same thing.

so i try doing so through the terminal and this is what i get:

jason@jason-laptop:~/Downloads/Incomplete$ ls
[COLOR="DarkOrchid"]FILE I WANT TO REMOVE.avi[/COLOR]
[COLOR="RoyalBlue"]FILE A.avi
FILE B.avi
FILE C.avi[/COLOR]
jason@jason-laptop:~/Downloads/Incomplete$ sudo rm FILE I WANT TO REMOVE.avi
[sudo] password for jason: 
rm: cannot remove `FILE I WANT TO REMOVE.avi': No such file or directory
jason@jason-laptop:~/Downloads/Incomplete$ 

now, i have never seen a purple output like that from the terminal, and why is this file showing up in nautilus if it does not exist?

any ideas?

---

### Post by drs305 on 2008-11-30
Try opening nautilus with 'gksudo'. Graphical apps can be a bit picky sometimes:
```
gksudo nautilus $HOME/Downloads/Incomplete
```

If it doesn't like the path, just open it with "gksudo nautilus" and navigate to the folder you wish to inspect.

---

### Post by binbash on 2008-11-30
you will use \ before space

example : 

rm Man\ Of\ The\ Year.avi

---

### Post by Mud.Knee.Havoc on 2008-11-30
> **jason6g said:**
> 
rm: cannot remove `FILE I WANT TO REMOVE.avi': No such file or directory
jason@jason-laptop:~/Downloads/Incomplete$ 


Do you actually have spaces in the filename?

rm "FILE I WANT TO REMOVE.avi"

or if there may be permissions issues:

sudo rm "FILE I WANT TO REMOVE.avi"

should work.

---

### Post by binbash on 2008-11-30
above post also will do the trick ;)

---

### Post by bruce89 on 2008-11-30
Tab completion is your friend.

---

### Post by binbash on 2008-11-30
> **bruce89 said:**
> Tab completion is your friend.

You can't use tab completion with those filenames : 

FILE I WANT TO REMOVE.avi
FILE A.avi
FILE B.avi
FILE C.avi

unless you start tabbing after FILE\ A(BC or I)

---

### Post by jason6g on 2008-11-30
thank you for al the replies, i did use escape characters with the code.

problem did get resolved, but i dont know how/why or how/why it happened in the first place :/

pretty much after i posted this i rebooted(shut down, went home, turned back on) and when i looked it wasnt there.

yet i rebooted a few times previously and it still stuck.

maybe it just needed command promt errors to tell itself that the file really wasnt there or something.

---

