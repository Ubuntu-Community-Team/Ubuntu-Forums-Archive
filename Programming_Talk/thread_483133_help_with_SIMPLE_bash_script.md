---
title: "help with SIMPLE bash script"
date: 2007-06-24
forum: Programming Talk
---

### Post by andyrobo60 on 2007-06-24
I am new to bash scripting and am having trouble writing a script that just runs a python script over and over in an infinite loop. So far what I have is 

```

#!=/bin/sh
while[1] do
   $HOME/python/script.py
done

```

This runs my script once when my python script exits I then get "bashscript.sh: 4: Syntax error: "done" unexpected" and the bash script ends.
Can someone please point out the mistake in the script

---

### Post by FuturePast on 2007-06-24
Well, I can see a few mistakes there but try putting the [COLOR="Red"]do[/COLOR] on a separate line.

---

### Post by Mr. C. on 2007-06-24
You can keep the "do" on the same line, but need a semicolon.  You can also replace the [1] test with a : as in :

```
#!=/bin/sh
while : ; do
   $HOME/python/script.py
done
```

MrC

---

### Post by andyrobo60 on 2007-06-24
works now
thanks Mr. C.

---

