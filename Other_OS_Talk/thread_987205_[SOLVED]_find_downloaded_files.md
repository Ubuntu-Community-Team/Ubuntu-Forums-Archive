---
title: "[SOLVED] find downloaded files?"
date: 2008-11-19
forum: Other OS Talk
---

### Post by Rita G. on 2008-11-19
trying out an operating system based on ubuntu 8.04 (w/no support forum). 

i've downloaded files & don't know where they go.

and there is no option or gui to search for file(s).

anybody know the terminal command to do this?

---

### Post by wolfen69 on 2008-11-19
```
locate name_of_file
```

---

### Post by Rita G. on 2008-11-19
thank you sweetie pie!

---

### Post by wolfen69 on 2008-11-19
oh, btw, if your file does not show up, do ```
sudo updatedb
``` then do locate command.

---

### Post by prshah on 2008-11-19
> **Rita G. said:**
> 
and there is no option or gui to search for file(s).
anybody know the terminal command to do this?

Using the locatedb requires that the database of files be updated all the time. Newly downloaded files will usually not appear in this list. Regenerating the list everytime can get time consuming.

Another option you can also use will be```
find / -iname "*partialnameoffile*"
``` but this will also be (usually) timeconsuming.

How are you downloading the files? Via apt-get / aptitude? Then typically they will be in /var/cache/apt/archives/ ; in which case the above command can be modified to ```
find /var/cache/apt/archives/ -iname "*partialnameoffile*"
```

---

### Post by oldos2er on 2008-11-19
> **Rita G. said:**
> trying out an operating system based on ubuntu 8.04 (w/no support forum). 

i've downloaded files & don't know where they go.

and there is no option or gui to search for file(s).

anybody know the terminal command to do this?

 Which OS? What program are you using to download?

---

