---
title: "Piping stderr while re-directing stdout in bash - can it be done?"
date: 2006-08-03
forum: Programming Talk
---

### Post by gazurtoids on 2006-08-03
ey up

So, I've got this program which writes progress information to stderr and, upon finishing or being interrupted, writes it's actual output to stdout. I'd like to redirect stdout into a file while piping stderr through tee so that I've got a record how things progressed while also being able to see the right moment to interrupt. 

So, essentially, I want to do:

myprogram stdout>somefile stderr| tee someotherfile

but a fair bit of googling has not yielded a workable solution. Does anyone know how I might accomplish this in bash?

(Incidentally, I've tried redirecting both to a file while "tail -f"ing the stderr file in another terminal but this seems a very fudgey way of doing things)

---

### Post by cwaldbieser on 2006-08-05
> **gazurtoids said:**
> ey up

So, I've got this program which writes progress information to stderr and, upon finishing or being interrupted, writes it's actual output to stdout. I'd like to redirect stdout into a file while piping stderr through tee so that I've got a record how things progressed while also being able to see the right moment to interrupt. 

So, essentially, I want to do:

myprogram stdout>somefile stderr| tee someotherfile

but a fair bit of googling has not yielded a workable solution. Does anyone know how I might accomplish this in bash?

(Incidentally, I've tried redirecting both to a file while "tail -f"ing the stderr file in another terminal but this seems a very fudgey way of doing things)


Try:
```

$ myprogram 2>&1 1>somefile | tee someotherfile

```

This points fd 2 to stdout.  Then it points fd 1 to somefile.  The pipe sends stdout to the tee program.  (fd == file descriptor; I hope I have the terminology correct).

---

### Post by ernstp on 2010-02-25
Here's something fun you can play with:
make 2> >(tee error.log) 1> out.log
for example!

---

### Post by dribeas on 2010-02-26
This might not seem intuitive, but the order of redirects do affect the outcome. What you need is:

```

./command 2>&1 > out | tee -o err

```

If you instead do:

```

./command > out 2>&1 | tee -o empty

```

both streams will go to the file and 'tee' will get no input. 

The way I remember it is that whenever '2>&1' is found, it will redirect the output to the file descriptor that stdout is pointing at this time. Any later change to the stdout file descriptor will not affect stderr

---

