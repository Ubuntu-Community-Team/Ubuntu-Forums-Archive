---
title: "Printing a directory list"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by squrl on 2012-02-04
x

---

### Post by llamabr on 2012-02-04
Depends on what you mean by "print" and "listing of files for a directory".

Try:

```
ls
```

---

### Post by squrl on 2012-02-04
x

---

### Post by sisco311 on 2012-02-04
I'm still unsure what do you mean by _*Printing a directory list*_

You have to elaborate your question. Specify the output device: screen (monitor) or printer. And the user interface you want to use: GUI or CLI...

---

### Post by wojox on 2012-02-04
```
ls -al > dir.txt
```

```
cat dir.txt
```

^That should work

---

### Post by llamabr on 2012-02-04
> **wojox said:**
> ```
ls -al > dir.txt
```

```
cat dir.txt
```

^That should work

That does in two steps what you could do in only one:

```
ls -aL | more
```

In any case, this will not print anything, assuming by "print" the OP means print.  Also depending on what you mean by printing a directory list.  Do you just mean show the contents of a directory?

---

### Post by wojox on 2012-02-04
Ahh I see. I thought OP meant print to file to send to printer.

---

### Post by llamabr on 2012-02-04
> **wojox said:**
> Ahh I see. I thought OP meant print to file to send to printer.

In that case, what you did was too many steps, too.  Instead of sending to file to send to printer, you could just send to printer:

```
ls -aL | lp
```

Note that the 'L' flag is caps.  Using the big L captures dereferenced symbolic links, too.

---

### Post by sisco311 on 2012-02-04
> **llamabr said:**
> 
```
ls -aL | more
```


This pipeline (sequence of commands) screams for a cliché: *sometimes less is more*. :evil:

```
ls -aL | less
```

---

### Post by squrl on 2012-02-04
sorry. I didn't realize how complicated the word print can get. 

A pencil, paper and twenty minutes and I got what I needed.

Thanks

---

