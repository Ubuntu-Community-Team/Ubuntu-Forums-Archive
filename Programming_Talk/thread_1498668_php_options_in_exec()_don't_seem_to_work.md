---
title: "php: options in exec() don't seem to work"
date: 2010-06-01
forum: Programming Talk
---

### Post by fairieswearboots on 2010-06-01
hi there,

i'm trying to do exec('ivtv-tune -f 100') in php but it seems like it won't except the '-f 100' part. I've tried escaping it or using quotes around it but i can't get it to work.
 
Does anybody have a solution to this? Thanks for reading.

---

### Post by new_tolinux on 2010-06-01
> **thundercunt said:**
> i'm trying to do exec('ivtv-tune -f 100') in php but it seems like it won't except the '-f 100' part. I've tried escaping it or using quotes around it but i can't get it to work.
I'm assuming you mean "accept" instead of "except"?

Have you tried to use that same command in terminal? What's it saying there?

---

### Post by fairieswearboots on 2010-06-01
> **new_tolinux said:**
> I'm assuming you mean "accept" instead of "except"?

Have you tried to use that same command in terminal? What's it saying there?

oh lol, i mean accept (sorry, i'm on a phone). Yes it works with regular command line. When i use it with php, it returns all the options and arguments i can use (like when you only type the name of a program that requires arguments)

---

### Post by new_tolinux on 2010-06-01
What I read from [here](http://ivtvdriver.org/index.php/Ivtv-tune) is:
>  -fFLOAT    --frequency=FLOAT   set new frequency (MHz)

What I see in your commandline there is a space between -f and 100:
>  -f 100

Probably you'll need to remove that.
I don't know the package, so I only tell what I just read.

---

### Post by fairieswearboots on 2010-06-01
thank you for answering. There is a space there, yes. However, wether i use exec('ivtv-tune -f 100') or exec('ivtv-tune --frequency=100') i get the same result (as if i gave no parameters), but both ways work when i use regular command line interface.

---

### Post by new_tolinux on 2010-06-01
> **thundercunt said:**
> thank you for answering. There is a space there, yes. However, wether i use exec('ivtv-tune -f 100') or exec('ivtv-tune --frequency=100') i get the same result (as if i gave no parameters), but both ways work when i use regular command line interface.
I guess it's not going to change anything, but I never use single quotes with exec.
That's mostly because with MySQL-queries '".$somevar."' is more simple to me than \"".$somevar."\" but as a result of that I always use double quotes (1x ") to define PHP commands.

Another way to try could be:
$somevar="ivtv-tune --frequency=100";
exec($somevar);

---

### Post by fairieswearboots on 2010-06-06
Thanks for your reply, I tried it but it didn't work. I've found a way to make it work though. The answer was to just simply use sudo (or just change the user/rights that php/apache uses of course):

```
system("sudo ivtv-tune -f 100");
```

---

