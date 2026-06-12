---
title: "file in the trash, not in the gksudo nautilus trash, can't delete it!"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by savethewabbit on 2008-05-31
the title is pretty self-explanatory! 
so i have this folder in my trash that i can't delete as it says "permission denied". 
so i thought i'd gksudo nautilus and delete it from there - did so, but when i looked, it's still in the main trash!
now if i open the trash the folder is there and won't be deleted. if i open gksudo nautilus and go to the trash, it says it's empty. 
what's wrong with it? is the file really still on my computer? if so, how can i delete it? and if it isn't, how can i have it *not* show up in my trash? might be silly, but i can't stand the full trash icon :P


thank you!

---

### Post by sisco311 on 2008-05-31
The Trash folder is a hidden folder(the folders name begins with a period) in your home directory.
You can press Ctrl+H in nautilus or select Show Hidden Folder from the View menu to list the hidden folders.

To open nautilus (as super-user) in the .Trash folder
press Alt+F2 and type:
```
gksu nautilus ~/.Trash
```

In Hardy Heron(8.04) the Trash is in ~/.local/share/Trash/files/

```
gksu nautilus ~/.local/share/Trash/files/
```

Or delete the content of the folder from the terminal:

```
sudo rm -fr ~/.Trash/*
```

Hardy Heron(8.04):
```
sudo rm -fr ~/.local/share/Trash/files/*
```

---

### Post by savethewabbit on 2008-05-31
the first code did the trick, thanks a lot. 
only i don't really understand what was going on: was the file hidden when i looked at the trash as a super user?

---

### Post by sisco311 on 2008-05-31
> **savethewabbit said:**
> the first code did the trick, thanks a lot. 
only i don't really understand what was going on: was the file hidden when i looked at the trash as a super user?

The root user(super user) has a different trash folder in the /root directory.

---

### Post by syxbit on 2008-06-15
> **sisco311 said:**
> 
Hardy Heron(8.04):
```
sudo rm -fr ~/.local/share/Trash/files/*
```
surely you want to do this
```
sudo rm -fr ~/.local/share/Trash/*
```
as the 'info' DIR should also get deleted

---

### Post by grunge09 on 2008-06-20
I had a couple directories from /var/backup from using simple backup config.

When I use "gksudo nautilus /root/.local/share/trash/files"

If I select them and delete them, they pop right back there like 1 second later.  Kinda annoying, that you can not delete them.  

What I had to do was right click on the files and changed permissions to the user acccount (I am logged in as) with read/write and delete access, and move the files to the users home directory and them close that gksudo nautilus window.

Then Goto that directory as the user and move to trash.  Then empty trash and it is gone.

in 7.10 Gutsy I just used "gksudo nautilus /root/.Trash" and deleted them there and they were gone.  Is this a problem in 8.04 32 bit???

---

### Post by Tomàs M. on 2008-08-12
[http://ubuntuforums.org/showthread.php?t=824635](http://ubuntuforums.org/showthread.php?t=824635) :-)

---

