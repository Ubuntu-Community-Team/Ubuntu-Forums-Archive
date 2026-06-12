---
title: "bash decrement not working"
date: 2007-02-02
forum: Programming Talk
---

### Post by gaillard on 2007-02-02
run this script and you'll see what i mean ```
 
#!/bin/bash
echo 5 > testing
echo $(cat testing)
declare -i n=$(cat testing)
echo $n
n-=2; echo -n "$n" > testing
echo $(cat testing)
n+=2; echo -n "$n" > testing
echo $(cat testing) But this works..

```

Anyone??
Sorry this script is just copied, thats why it is writing to a file, I was using it for something else so I chopped it down. My apologeeeees.

---

### Post by gaillard on 2007-02-02
nm

I forgot to put in "let x-=2"  but its strange because x+=2 WORKS while the decrement doesn't.

Sorry guys just learning this stuff.

---

### Post by yabbadabbadont on 2007-02-02
Try using "expr" instead.  "man expr" for details.  :)

---

### Post by gaillard on 2007-02-02
is it faster? computational wise?

---

### Post by yabbadabbadont on 2007-02-02
> **gaillard said:**
> is it faster? computational wise?

Does it matter as long as it works?  Especially since your current method doesn't.  ;)

---

### Post by WW on 2007-02-02
Instead of ```
n-=2
```  use ```
let n-=2
```

Edit: Ooops, I just reread your second post;  you already knew about "let".

---

### Post by yabbadabbadont on 2007-02-02
> **WW said:**
> Instead of ```
n-=2
```  use ```
let n-=2
```

Edit: Ooops, I just reread your second post;  you already knew about "let".

You could try doing it the oldschool way.  (I haven't tested this... because I don't feel like it.  :p)

```
let n=n-2
```

You kids and your fancy shortcut operators...  :D

EDIT: I was bored, so I tested it for you.
```
/home/bubba/temp $ cat go.sh
let n=10

while test $n -gt 0
do
echo $n
let n=n-2
done
/home/bubba/temp $ . ./go.sh
10
8
6
4
2

```

---

### Post by Wybiral on 2007-02-02
Well, I don't know how important it is in a BASH script.

But inc/dec are actually important in some areas of programming.

Generally, they are faster...

x=x+2
=
add x, 2
push x
pop x


x+=2
=
add x, 2

A good compiler will optimize that, but I'm not sure how the expression optimization in BASH works. If it isn't optimized, x=x+2 will basically be treated the same as "y=x+2; x=y" because without optimization, it has no idea that x is x.

If you need your script to be as fast as possible, it may be better to increment...

But, how often do you need a BASH script to be lightning fast? Unless it's inside some incredibly tight loop... But then I might consider thinking outside of BASH.

---

### Post by yabbadabbadont on 2007-02-02
> **Wybiral said:**
> Well, I don't know how important it is in a BASH script.

But inc/dec are actually important in some areas of programming.

Generally, they are faster...

x=x+2
=
add x, 2
push x
pop x


x+=2
=
add x, 2

A good compiler will optimize that, but I'm not sure how the expression optimization in BASH works. If it isn't optimized, x=x+2 will basically be treated the same as "y=x+2; x=y" because without optimization, it has no idea that x is x.

If you need your script to be as fast as possible, it may be better to increment...

But, how often do you need a BASH script to be lightning fast? Unless it's inside some incredibly tight loop... But then I might consider thinking outside of BASH.

Bash is an interpreter, not a compiler.  :)
The whole reason this thread exists is because "-=" does not work in Bash.  :p :D

---

### Post by Wybiral on 2007-02-02
I know what bash is. I'm just explaining how they are usually processed and why it's faster. Even if it's not compiled, it has to be processed somehow.

Does "x+=-2" work?

---

### Post by gaillard on 2007-02-18
I believe that works, so now I am just wondering why the increment works without let yet the decrement doesn't... perhaps its very technical.  Unfortunately it was in a very tight loop because I kind of programmed a music player that uses some features I couldn't find outa bash, not optimal I know but I am not very experienced in c++ (although I am getting there...)

---

