---
title: "Can't Empty Trash"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by szaqlon on 2008-06-08
I have 2 folders in my trash that will not go away. I have tried to force empty and nothing. The strange thing is that anything I delete goes into the trash and empties fine. The 2 folders that won't delete look like something I deleted about a week ago.
Any ideas on how to clear this out?
Oh and when I open the trash the window at the top has the path as trash:/// I don't know if that's how it should be or not.

---

### Post by UnWarierMage224 on 2008-06-08
fire up a root filebrowser and empty your trash that way. 

```

gksudo nautilus

```

Then navigate to the .Trash folder (it's hidden - IIRC) and delete the files. 

A quick explanation of privileges:
root user, for all intents and purposes, is God of your computer - root can do whatever: create anything, delete anything etc. 
what you log in under is the NOT root user, meaning you have restricted privileges. In this case, you cannot delete or modify anything created by root. the gksudo command will let you be root temporarily. 

And no, you do NOT want to log in as root on a daily basis. VERY VERY BAD! Use gksudo or sudo from a terminal to work as root when need be.


EDIT 2: On second thought, maybe just open up your trash (as non root) and right click on the folders and say "delete from trash"? 

Best, 

-'Mage

---

### Post by drs305 on 2008-06-08
There are several Trash folders on your system. You can do a universal search using the command below and then browse to and delete the files within using 'gksudo nautilus' as UnWarierMage224 suggested.

```
sudo find / -type d -iname Trash
```

---

### Post by szaqlon on 2008-06-08
well, I did the search and found exactly where they were and open a window as root and deleted them. Thanks, very helpful.

---

