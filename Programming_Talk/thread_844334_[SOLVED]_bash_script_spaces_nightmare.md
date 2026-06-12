---
title: "[SOLVED] bash script spaces nightmare"
date: 2008-06-29
forum: Programming Talk
---

### Post by kung fu buntu on 2008-06-29
The script is more complex but the problem lies here:
```

$ FOO="/vault/kaizoku/home/system/wine/drive_c/Program Files/foobar2000"
$ wine $FOO
wine: cannot find '/vault/kaizoku/home/system/wine/drive_c/Program'

$ FOO="/vault/kaizoku/home/system/wine/drive_c/Program\ Files/foobar2000"
$ wine $FOO
wine: cannot find '/vault/kaizoku/home/system/wine/drive_c/Program\'


### works fine like this:
$ wine /vault/kaizoku/home/system/wine/drive_c/Program\ Files/foobar2000/foobar2000.exe

```

---

### Post by Martin Witte on 2008-06-29
put the directory name in single quotes, bash doesn't interpret all between single quotes```
martin@sony:~$ z='a string with spaces'
martin@sony:~$ echo "$z"
a string with spaces
martin@sony:~$ 

```

---

### Post by Alasdair on 2008-06-29
You can also use backslash characters to escape the space like so: ...drive_c/Program\ Files/...

Edit: Except it looks like you tried that and it didn't work, maybe if you remove the double quotes from your second example it would. I'm not using Linux right now so I can't check.

---

### Post by kung fu buntu on 2008-06-29
@ all
**[COLOR="Red"]PLEASE try your solutions before replying! It's very likely that they won't work.[/COLOR]** :roll: :p


@ Martin Witte, Alasdair
That didn't worked.

---

### Post by vanadium on 2008-06-29
echo $foo | xargs wine

There is a pecularity in how wine handles its command line arguments.

---

### Post by geirha on 2008-06-29
> **kung fu buntu said:**
> 
@ Martin Witte, Alasdair
That didn't worked.

Marin Witte's suggestion should work ...
```

$ FOO="/vault/kaizoku/home/system/wine/drive_c/Program Files/foobar2000"
$ wine "$FOO"
$ #    ^    ^ important

```

---

### Post by kung fu buntu on 2008-06-29
@ vanadium
That didn't work for me.
But this does (notice the slash space):
FOO="/home/kaizoku/home/system/wine/drive_c/Program**\ **Files/foobar2000/foobar2000.exe"
echo $FOO | xargs wine




@ Martin Witte, geirha
You are correct.
The problem was me being distracted in the first place.
I tried a couple more things besides what I posted in my first message, but if you notice, I'm trying to wine (ie, run) a directory -_-'
And I probably made that same mistake when trying Martin's suggestion.

And the reason for that (me screwing up) was because the issue was a bit more complicated in the first place...

Anyway I fixed my problem in another way.

---

