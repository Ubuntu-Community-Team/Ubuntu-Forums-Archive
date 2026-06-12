---
title: "[SOLVED] Can't Empty Trash Can"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by ExSuSEusr on 2008-08-16
Getting a strange error when I try to delete some huge folders from my trash can.
 
"There was an error deleting BDA.cab"
 
When I empty the trash can it goes through the process, but the items are still showing up.  When I try to delete the individual folders I get the error message above.
 
They are huge folders of windows programs I was using in Wine.
 
Any ideas?

---

### Post by Sycron on 2008-08-16
Type in a terminal:
```
gksudo nautilus
```
go to trash and delete it.

---

### Post by sisco311 on 2008-08-16
In hardy the location of the trash is: ~/.local/share/Trash/files/
```
gksu nautilus ~/.local/share/Trash/files/
```

In earlier releases is: ~/.Trash
```
gksu nautilus ~/.Trash/
```

---

### Post by ExSuSEusr on 2008-08-16
When I try that I get:
 
"Sorry, couldn't display all the contents of "trash" Operation not supported."

---

### Post by Sycron on 2008-08-16
Try with gksudo.

---

### Post by drs305 on 2008-08-16
Perhaps this will work then:
```

sudo chown -R **username** /home/*username*/.local/share/Trash
rm -rf /home/*username*/.local/share/Trash

```

---

### Post by ExSuSEusr on 2008-08-16
Same thing with both gksu and gksudo..
 
Very strange - I've never had a problem emptying the trash can before.

---

### Post by sisco311 on 2008-08-16
> **Sycron said:**
> Try with gksudo.
gksudo and gksu are the same.
gksudo is a symbolic link to gksu.

---

### Post by Vivaldi Gloria on 2008-08-16
Restarting and fsck'ing the disk sometimes helps.

---

### Post by ExSuSEusr on 2008-08-16
> **drs305 said:**
> Perhaps this will work then:
```

sudo chown -R /home/*username*/.local/share/Trash
rm -rf /home/*username*/.local/share/Trash

```
 
Tried that and get "chown: invalid option -- r"

---

### Post by Sealbhach on 2008-08-16
I had that problem too, so I tried these solutions. This one worked on its own:

```
sudo rm -rf /home/username/.local/share/Trash
```

The 
```

sudo chown -R /home/username/.local/share/Trash
```

gave me Permission Denied.:confused:

.

---

### Post by sisco311 on 2008-08-16
It's:
```
sudo chown -R $USERNAME:$USERNAME *~*/.local/share/Trash
```

---

### Post by Too Late on 2008-08-16
> **ExSuSEusr said:**
> Tried that and get "chown: invalid option -- r"
```
r
```
is not
```
R
```

---

### Post by ExSuSEusr on 2008-08-16
> **Sealbhach said:**
> I had that problem too, so I tried these solutions. This one worked on its own:
 
```
sudo rm -rf /home/username/.local/share/Trash
```
 
The 
```

sudo chown -R /home/username/.local/share/Trash
```
 
gave me Permission Denied.:confused:
 
.
 
 
sudo rm -rf /home/username/.local/share/Trash worked!  Thanks everyone!

---

### Post by sisco311 on 2008-08-16
Cool!
If your thread is solved, please mark it solved by selecting 
**Mark this thread as solved** from the **Thead Tools**.

---

### Post by drs305 on 2008-08-16
> **ExSuSEusr said:**
> Tried that and get "chown: invalid option -- r"

Should be:
```

sudo chown -R **username** /home/*username*/.local/share/Trash
rm -rf /home/*username*/.local/share/Trash

```

Corrected original.

---

