---
title: "edting .bashrc file"
date: 2013-12-29
forum: New to Ubuntu
---

### Post by gulatiakshay2 on 2013-12-29
I am new to linux so need help with editing .bashrc file

this is what i am trying to do.
when i type echo $PATH i get
/home/software/share/madagascar/etc/env.sh
because i have 
export PATH=/home/software/share/madagascar/etc/env.sh

but software only work when i put in terminal window..

source software/share/madagascar/etc/env.sh
I am not sure if its in path how come i have to put sourece every time
cn some one tell me what wrong i am doin

---

### Post by deadflowr on 2013-12-29
Do you want to launch the file every time you open a terminal?

Then simply put the file in the .bashrc like
/home/stuff/stuff/stuff/filename.sh
don't export or path or anything.

But again, don't really know what the endgame is.

---

### Post by Bashing-om on 2013-12-29
gulatiakshay2; Hi !

I am a bit confused by your reference:
My output:
```

sysop@1310mini:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
sysop@1310mini:~$

```

Your output is not similar ?

[INDENT][INDENT]My bit to try and help too
[/INDENT][/INDENT]

---

### Post by damage3025 on 2013-12-30
> **gulatiakshay2 said:**
> 
this is what i am trying to do.
when i type echo $PATH i get
/home/software/share/madagascar/etc/env.sh
because i have 
export PATH=/home/software/share/madagascar/etc/env.sh


You do not understand PATH variable correctly.
This line is wrong by every sense; please remove it.
You may learn about PATH variable through:
[http://superuser.com/questions/517894/what-is-the-unix-path-variable-and-how-do-i-add-to-it](http://superuser.com/questions/517894/what-is-the-unix-path-variable-and-how-do-i-add-to-it)

> **gulatiakshay2 said:**
> 
 but software only work when i put in terminal window..

source software/share/madagascar/etc/env.sh
I am not sure if its in path how come i have to put sourece every time
cn some one tell me what wrong i am doin

This is the line you probably want to add to your .bashrc

---

