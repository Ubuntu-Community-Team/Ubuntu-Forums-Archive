---
title: "Move-to-Trash Command ( rm removes permanently but MTT moves-to-trash :D )"
date: 2010-10-28
forum: Programming Talk
---

### Post by hakermania on 2010-10-28
That's the script (designed for Ubuntu 10.10 trash system):
```
#!/bin/sh
if [ -d /home/`logname`/.local/share/Trash/ ]; then false; else mkdir /home/`logname`/.local/share/Trash/; mkdir /home/`logname`/.local/share/Trash/files; mkdir /home/`logname`/.local/share/Trash/info; fi
if [ X"$1" = X"" ]; then
echo "`logname`, You have to mention a file or folder to move to Trash!"
else
mv $1 /home/`logname`/.local/share/Trash/files/
realname=`basename $1`
echo "[Trash Info]
Path=`readlink -m $1`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$2" != X"" ]; then
mv $2 /home/`logname`/.local/share/Trash/files/
realname=`basename $2`
echo "[Trash Info]
Path=`readlink -m $2`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$3" != X"" ]; then
mv $3 /home/`logname`/.local/share/Trash/files/
realname=`basename $3`
echo "[Trash Info]
Path=`readlink -m $3`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$4" != X"" ]; then
mv $4 /home/`logname`/.local/share/Trash/files/
realname=`basename $4`
echo "[Trash Info]
Path=`readlink -m $4`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$5" != X"" ]; then
mv $5 /home/`logname`/.local/share/Trash/files/
realname=`basename $5`
echo "[Trash Info]
Path=`readlink -m $5`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$6" != X"" ]; then
mv $6 /home/`logname`/.local/share/Trash/files/
realname=`basename $6`
echo "[Trash Info]
Path=`readlink -m $6`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$7" != X"" ]; then
mv $7 /home/`logname`/.local/share/Trash/files/
realname=`basename $7`
echo "[Trash Info]
Path=`readlink -m $7`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$8" != X"" ]; then
mv $8 /home/`logname`/.local/share/Trash/files/
realname=`basename $8`
echo "[Trash Info]
Path=`readlink -m $8`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$9" != X"" ]; then
mv $9 /home/`logname`/.local/share/Trash/files/
realname=`basename $9`
echo "[Trash Info]
Path=`readlink -m $9`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
```It can become better though.. :)

---

### Post by hakermania on 2010-10-29
Added an option to empty the trash and a help screen.
```

#!/bin/sh
if [ -d /home/`logname`/.local/share/Trash/ ]; then false; else mkdir /home/`logname`/.local/share/Trash/; mkdir /home/`logname`/.local/share/Trash/files; mkdir /home/`logname`/.local/share/Trash/info; fi
if [ X"$1" = X"" ]; then
echo "`logname`, You have to mention a file or folder to move to Trash!"
elif [ X"$1" = X"-empty" ]; then if [ -s /home/`logname`/.local/share/Trash/files/* ]; then rm -r /home/`logname`/.local/share/Trash/files/* /home/`logname`/.local/share/Trash/info/*; exit; fi
elif [ X"$1" = X"-help" ]; then echo "mtt is a program to move files to trash.\nType -help to navigate to this page or -empty to empty the trash."; exit;
else
mv $1 /home/`logname`/.local/share/Trash/files/
realname=`basename $1`
echo "[Trash Info]
Path=`readlink -m $1`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$2" != X"" ]; then
mv $2 /home/`logname`/.local/share/Trash/files/
realname=`basename $2`
echo "[Trash Info]
Path=`readlink -m $2`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$3" != X"" ]; then
mv $3 /home/`logname`/.local/share/Trash/files/
realname=`basename $3`
echo "[Trash Info]
Path=`readlink -m $3`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$4" != X"" ]; then
mv $4 /home/`logname`/.local/share/Trash/files/
realname=`basename $4`
echo "[Trash Info]
Path=`readlink -m $4`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$5" != X"" ]; then
mv $5 /home/`logname`/.local/share/Trash/files/
realname=`basename $5`
echo "[Trash Info]
Path=`readlink -m $5`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$6" != X"" ]; then
mv $6 /home/`logname`/.local/share/Trash/files/
realname=`basename $6`
echo "[Trash Info]
Path=`readlink -m $6`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$7" != X"" ]; then
mv $7 /home/`logname`/.local/share/Trash/files/
realname=`basename $7`
echo "[Trash Info]
Path=`readlink -m $7`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$8" != X"" ]; then
mv $8 /home/`logname`/.local/share/Trash/files/
realname=`basename $8`
echo "[Trash Info]
Path=`readlink -m $8`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
if [ X"$9" != X"" ]; then
mv $9 /home/`logname`/.local/share/Trash/files/
realname=`basename $9`
echo "[Trash Info]
Path=`readlink -m $9`
DeletionDate=`date +'%Y'`-`date +'%m'`-`date +'%d'`T`date +'%T'`" > /home/`logname`/.local/share/Trash/info/$realname.trashinfo
fi
```

---

### Post by nvteighen on 2010-10-30
I have any knowledge on sh programming, but I think you could abstract some stuff into functions. Also, have you tried whether KDE also uses the same trash path or not? Anyway, it's nice and simple, congrats! :D

---

### Post by Vox754 on 2010-10-30
> **nvteighen said:**
> I have any knowledge on sh programming, but I think you could abstract some stuff into functions. Also, have you tried whether KDE also uses the same trash path or not? Anyway, it's nice and simple, congrats! :D
Please don't encourage him to write terrible, terrible code. Hint: indentation.

Of all people, you have played with C, C++, C#, python, java, lisp, scheme, clojure, whatever. It's about time you take a few days to learn minimal bash skills. Really, since you post a lot, and are friendly towards beginners, you would help them and us who don't have the patience to deal with this mess.

---

### Post by nvteighen on 2010-10-30
> **Vox754 said:**
> Please don't encourage him to write terrible, terrible code. Hint: indentation.


Honestly, I think it's not that terrible. Sure, it needs more abstraction, as I said in the previous post, but I do believe he's on the right track this time: the idea isn't bad (although it isn't original). 

I remember way much more terrible code from him; that's why I wrote that post and encouraged him this time.

---

### Post by hakermania on 2010-10-30
--_--

---

### Post by hakermania on 2010-10-30
Surely I can make some functions to deal with the 9 only files that can be moved to trash, but here i need more experienced help :) That's why I posted this code here guys, not actually for criticizing it but I though it would be a good idea to make such a command and so I posted it here to see it and make it better. That's the whole philosophy, isn't it?

---

### Post by ibuclaw on 2010-10-30
> **hakermania said:**
> Surely I can make some functions to deal with the 9 only files that can be moved to trash, but here i need more experienced help :) That's why I posted this code here guys, not actually for criticizing it but I though it would be a good idea to make such a command and so I posted it here to see it and make it better. That's the whole philosophy, isn't it?

I wrote something a little more fully fledged two years ago. Back then, of course, there was no way to ***restore*** files from the trash back to their original location, so I wrote a command-line util that could do what Nautilus couldn't at the time. :P
[http://ibuclaw.ubuntuforums.org/showthread.php?t=787535](http://ibuclaw.ubuntuforums.org/showthread.php?t=787535)

As far as I'm aware the standard on the Trash bin hasn't changed, so it should still work OK.
And I consider the code public domain, so do what you want with it. :)

Regards

---

### Post by sisco311 on 2010-10-30
reinventing the wheel?

gvfs-trash and trash, list-trash, restore-trash, empty-trash from the trash-cli package...

---

### Post by ibuclaw on 2010-10-30
> **sisco311 said:**
> reinventing the wheel?

gvfs-trash and trash, list-trash, restore-trash, empty-trash from the trash-cli package...

My script actually predates trash-cli, and oddly enough, I was even asked to join the dev team from trash-cli at the time (see somewhere near the end of the thread you'll see the proposal). I kindly accepted, but nothing came to fruition. Bottom line is it turned out that I just can't do python. ;)

---

