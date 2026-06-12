---
title: "csh scripting help"
date: 2007-08-23
forum: Programming Talk
---

### Post by DishBreak on 2007-08-23
I realize a lot of ubuntu users use bash, because it's the shell that it's shipped with. however, i'm having a bit of difficulty with c shell scripting and i hope one of you can help me out.

what is the easiest for a script to find out if a directory is empty or not? i'm writing something that copies files to an sd card, and i want the script to abort if the directory i ask it to copy from is empty. 

also, if someone could point me to a good resource for learning c-shell (online or in print), it would help me...a lot.

thanks!

---

### Post by rharriso on 2007-08-23
you could use the ls command and run a foreach loop and set up a counter, test for zero. Thats just a general way of doing it.

I don't know of a quick and easy way to do it.

---

### Post by rharriso on 2007-08-23
also I've found that the different shells aren't too terribly different and shell programming book will tell you basics of shell programming and point out the differences between the shells, I use Linux in a nutshell by oreilly books

---

### Post by ghostdog74 on 2007-08-23
[For your reference...]("http://www.thp.uni-duisburg.de/~michael/csh-harmful.html.")
however, this aside, you can use GNU find.
```

find . -empty -type d -name "somedirname"

```

---

### Post by DishBreak on 2007-08-23
The link you gave me is dead.

right now, i have the script create and erase a dummy file to force it to work...

I'll try figuring out the find command, thanks for the (now obvious) tip. I'll brush up more on my reading skills. =_=

---

### Post by ghostdog74 on 2007-08-23
> **DishBreak said:**
> The link you gave me is dead.

no its not. You just have to remove the last "dot"

---

### Post by Mr. C. on 2007-08-23
Here are two different techniques you can use :

```
if (`ls -1 | wc -l` == 0) then
    echo Empty
else
    echo Not Empty
endif
```

or

```
set nonomatch
if (`echo *` =~ '*') then
    echo Empty
else
    echo Not Empty
endif
unset nonomatch
```

MrC

---

### Post by DishBreak on 2007-08-25
@ghostdog:
My bad. very interesting article...this script is fairly simple, so i'll go with what i have already.

@Mr. C.
Thanks a lot! those make sense. the only question i have is why do you need to set and unset the variable "nonomatch"?

---

### Post by Mr. C. on 2007-08-25
Setting nonomatch prevents csh from complaining :

```
$ mkdir empty && cd empty
$ 'Got a light'?
Got a light?: No match.

$ echo *
echo: No match.

```

Unsetting nonmatch is to go back to the default mode of warning when a wildcard does not match.  No need to unset if your script exits anyway, or you don't care.

MrC

---

