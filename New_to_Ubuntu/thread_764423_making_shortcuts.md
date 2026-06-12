---
title: "making shortcuts?"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by Zopiac on 2008-04-23
i got version 0.99.01 linux of a 3d mesh installer, Wings3D, from wings3d.com. I opened the .run file, (i think it was a run, maybe after extracting a .bz or something) and it installed to /home/zopiac. all looks good. the thing is, it did not add a shortcut anywhere, and im still a n00b at linux extensions. could someone help?

by the way, i have 0.98.x installed from the add/remove app, but i wanted to get this new(er) version.

thx in advance!

---

### Post by spiderbatdad on 2008-04-23
Not familiar with the program you've installed. If you can launch it from the terminal with a ./filename command, you can usually create a panel launcher by right clicking on the panel and adding an application launcher. The command is the path to the run file.

---

### Post by Zopiac on 2008-04-28
uhm what?

---

### Post by damis648 on 2008-04-28
If you already know the command to run it, IE /home/user/program/program.run just right click the desktop and select "Create Launcher" and then as the command put the path to the run file.

---

### Post by Zopiac on 2008-04-28
> **damis648 said:**
> If you already know the command to run it, IE /home/user/program/program.run just right click the desktop and select "Create Launcher" and then as the command put the path to the run file.

the thing is, i dont. all i know 9is that in /home/zopiac/wings-0.99.01 there are the following files: AUTHORS, license.terms, README, vsnn, and wings. i believe the first three are just text files, nothing else. the last two, i dont know. there are two folders: bin and lib. bin has a few files in it, nothing that can be opened, that i know of, and lib has a bunch more, without knowledge of open-ability.

---

### Post by spiderbatdad on 2008-04-28
Hmm, sorry. I was trying to give an example of how to create a launcher for a program that has a binary run file. Let's say the program is in a folder in your home directory, or any directory for that matter. In that folder is a big blue diamond thingy with a program name under it. If you click it, it should offer you the opportunity to run the program, unless it has not been made executable. But that's another issue. So, let's say the name of the program is RunMe...it's in the folder runme2 in your home directory.

I was thinking...you right click on a panel (top or bottom of desktop) you select 'add to panel.' Then choose, 'custom application launcher.' Click 'Add.'  Give the thing a name. What goes in the command area is the path to the binart. In the case of this example: /home/your_user_name/runme2/RunMe
Et, voila! A launcher should appear in the panel and it should start the program when clicked. If you want to change the icon you can...but that comes after the thing works.

---

### Post by damis648 on 2008-04-28
ok try this, open terminal (Applications>Accessories>Terminal) and type in 
```
cd /home/zopiac/wings-0.99.01/
```

then type

```
chmod a+x vssn
```

and ```
chmod a+x wings
```

then type ```
./vsnn
``` and ```
./wings
```
and tell me what each one does

---

### Post by Zopiac on 2008-04-28
> **damis648 said:**
> ok try this, open terminal (Applications>Accessories>Terminal) and type in 
```
cd /home/zopiac/wings-0.99.01/
```

then type

```
chmod a+x vssn
```

and ```
chmod a+x wings
```

then type ```
./vsnn
``` and ```
./wings
```
and tell me what each one does

zopiac@zopiac:~/wings-0.99.01$ chmod a+x vssn
chmod: cannot access `vssn': No such file or directory

---

### Post by Zopiac on 2008-04-28
hello?

---

### Post by Dr Small on 2008-04-28
What are the file's name?
```
ls -l ~/wings-0.99.01
```

---

### Post by elmer_42 on 2008-04-28
For chmod, you usually have to append sudo to the beginning. E.g.:
```
sudo chmod a+x vssn
```

---

### Post by Dr Small on 2008-04-28
> **elmer_42 said:**
> For chmod, you usually have to append sudo to the beginning. E.g.:
```
sudo chmod a+x vssn
```
No, that is incorrect.
Sudo is only needed when the file that you are attempting to chmod is owned by root.

---

### Post by Zopiac on 2008-04-28
i see:

zopiac@zopiac:~/wings-0.99.01$ ls -l ~/wings-0.99.01
total 28
-rw-r--r-- 1 zopiac zopiac 3269 2008-01-16 01:45 AUTHORS
drwxr-xr-x 2 zopiac zopiac 4096 2008-01-16 01:45 bin
drwxr-xr-x 6 zopiac zopiac 4096 2008-01-16 01:45 lib
-rw-r--r-- 1 zopiac zopiac 2158 2008-01-16 01:45 license.terms
-rw-r--r-- 1 zopiac zopiac  618 2008-01-16 01:45 README
-rw-r--r-- 1 zopiac zopiac   18 2008-01-16 01:45 vsn.mk
-rwxr-xr-x 1 zopiac zopiac  398 2008-04-19 12:15 wings
zopiac@zopiac:~/wings-0.99.01$

---

### Post by Zopiac on 2008-04-29
bump, i still need to know how to get wings to work :(

---

