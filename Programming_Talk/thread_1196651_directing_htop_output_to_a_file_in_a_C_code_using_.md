---
title: "directing htop output to a file in a C code using system()"
date: 2009-06-25
forum: Programming Talk
---

### Post by polarbear12345 on 2009-06-25
i m using the command :
system("htop>data.txt")
to direct the htop output to the file data.txt but the program stops after executing it till i press CTRL C.
moreover,on opening data.txt in text editor it shows all garbage

plzz help

---

### Post by kerry_s on 2009-06-25
cause htop is a running process you have to exit, like top.

you should use> **ps aux > data.txt**
instead. "man ps" to learn more

---

### Post by dwhitney67 on 2009-06-25
htop is (more than likely) using ncurses to display its data; it is unlikely that you will be able to make any sense of it once it is redirected to a file... unless you write one hell of a parser.

It would be easier to query the /proc files for the system information you require.

P.S.  A ctrl-c is equivalent to a SIGINT.

---

### Post by prshah on 2009-06-25
> **polarbear12345 said:**
> 
system("htop>data.txt")

Any reason you cannot use ```
top -b -d 1 -n 1
``` instead of htop? You won't need Ctrl+C, and you wont get "garbage" characters.

---

### Post by polarbear12345 on 2009-06-25
actually i want to get overall CPU utilization from htop which is not given directly in top...
is there any way i may derive overall CPU utilization from items in top output..

---

### Post by kerry_s on 2009-06-25
> **polarbear12345 said:**
> actually i want to get overall CPU utilization from htop which is not given directly in top...
is there any way i may derive overall CPU utilization from items in top output..

```
ps aux
```

---

### Post by nvteighen on 2009-06-25
And why not use a shell script? Why does it have to be C?

---

