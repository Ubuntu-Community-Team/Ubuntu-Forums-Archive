---
title: "Setting the PATH in kubuntu"
date: 2013-09-04
forum: Programming Talk
---

### Post by raac on 2013-09-04
Hello guys, it has been a while since I don't use linux, and I'm back on it. So far I customized my shell to be tcsh. 
The only problem I'm encountering is in setting up the $PATH. My $PATH currently looks the this...

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/tony/Documents/apps/scripts

I added the last section of it (/home/tony/Documents/apps/scripts). In there I have a script (rar.pl) with the following permissions....

-rwxr-xr-x 1 tony tony 179 Sep  3 21:57 rar.pl

I can't execute the script without specifying the whole path. I can only run it as /home/tony/Documents/apps/scripts/rar.pl.

Also, I added the following inside ~/.tcshrc

set PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/home/tony/Documents/apps/scripts

What am i missing?

Thanks.

---

### Post by TheFu on 2013-09-04
use setenv, not set.

---

### Post by raac on 2013-09-04
Thanks!!! That's what I was missing. I'm curious now the regular 'set' was changing the PATH. I would do an 'echo $PATH' and it will reflect the new directory. Do you know why is that?

---

### Post by TheFu on 2013-09-04
"set" is a current process variable.
"setenv" changes the variable in all current and all subprocesses.

BTW, tsch rocks, but these days it isn't worth the hassle since bash has implemented most of the things that made tcsh so much better than sh, csh and ksh.

In sh/ksh/bash, use set or export in the same manner.
All these things are spelled out inside the man page. **man tcsh** to learn many more secures of that shell. Do not script using tsch - it does strange, unexpected things. Use sh/ksh/bash for scripting.

---

### Post by raac on 2013-09-05
I'll have that in mind. Thanks.

---

