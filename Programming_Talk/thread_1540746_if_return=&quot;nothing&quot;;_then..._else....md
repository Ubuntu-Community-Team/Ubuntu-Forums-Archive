---
title: "if return=&quot;nothing&quot;; then... else..."
date: 2010-07-28
forum: Programming Talk
---

### Post by Intrepid Ibex on 2010-07-28
Hey!

So, my 'task' is to create a Bash script that reports when the previous command returns nothing (say ls) and when it does return something.

e.g.
```
**if [** -quiet-return ls **]; then**
   There's no output!
**else**
   There's the following output!**;** print from memory
**fi**

```

---

### Post by Bachstelze on 2010-07-28
```
ls_output=`ls 2> /dev/null`
if [ "x$ls_output" = "x" ]; then
    echo "No output."
else
    echo $ls_output
fi
```

---

### Post by Intrepid Ibex on 2010-07-28
Thanks :)!!

---

### Post by Intrepid Ibex on 2010-07-30
Except of course you wouldn't need the extra "x"s there:

```
ls_output=`ls 2> /dev/null`
if [ "$ls_output" = "" ]; then
    echo "No output."
else
    echo $ls_output
fi
```

---

### Post by Bachstelze on 2010-07-30
> **Intrepid Ibex said:**
> Except of course you wouldn't need the extra "x"s there

I put them for a reason.  Some shells do funky things when you use the empty string like that.

---

### Post by Intrepid Ibex on 2010-08-01
Oh okay. Figured you knew better but had to be sure =).

---

### Post by Bachstelze on 2010-08-01
> **Intrepid Ibex said:**
> Oh okay. Figured you knew better but had to be sure =).

To be honest, you are very unlikely to encounter such a shell today.  It is stil a good idea to do it, though.  As Henry Spencer wrote in his annotation to the Ninth Commandment of C:

> 
Though some hasty zealots cry ``not so; the Millenium is come, and this saying is obsolete and no longer need be supported'', verily there be many, many ancient systems in the world, and it is the decree of the dreaded god Murphy that thy next employment just might be on one.


[http://www.lysator.liu.se/c/ten-commandments.html](http://www.lysator.liu.se/c/ten-commandments.html)

---

### Post by geirha on 2010-08-01
> **Bachstelze said:**
> To be honest, you are very unlikely to encounter such a shell today.  It is stil a good idea to do it, though.  As Henry Spencer wrote in his annotation to the Ninth Commandment of C:



[http://www.lysator.liu.se/c/ten-commandments.html](http://www.lysator.liu.se/c/ten-commandments.html)

I can guarantee you though, that it is not needed in Bash (which the OP stated he/she was using) nor in POSIX sh. It's just ancient shells like the bourne shell that may get confused if the LHS of = starts with a -.

In bash, though, you shouldn't use the [ command, instead use [[ for testing strings and files, and (( for arithmetics.
```
#bash
output=$(some command)
if [[ $output ]]; then
  echo "output"
else
  echo "no output"
fi

```

If you actually want to check if a directory is empty or not, do not use ls. In fact, never use ls in a script ever, it's not designed for it. See [http://mywiki.wooledge.org/BashFAQ/004](http://mywiki.wooledge.org/BashFAQ/004) on how to do that check properly.

---

### Post by Intrepid Ibex on 2010-08-01
> **geirha said:**
> Bash (which the OP stated he/she was using)
Actually I'm _using_ Zsh.

> **geirha said:**
> do not use ls. In fact, never use ls in a script ever, it's not designed for it.
Sure? Lots of things aren't (designed for lots of things) but thanks for the heads up.

---

