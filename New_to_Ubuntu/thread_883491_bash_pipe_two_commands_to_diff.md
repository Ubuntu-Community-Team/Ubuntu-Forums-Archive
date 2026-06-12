---
title: "bash pipe two commands to diff"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by PGScooter on 2008-08-08
Hi, here is the code that I am trying to condense into one command:

```

du -ab | sort > file1.txt
du -ab directory2 | sort > file2.txt
diff file1.txt file2.txt

```

How can I do this with one command (and multiple pipes)?

Thanks

---

### Post by eightmillion on 2008-08-08
```
du -ab | sort > file1.txt && du -ab directory2 | sort > file2.txt && diff file1.txt file2.txt 
```

Would that not work?

---

### Post by PGScooter on 2008-08-08
thanks eightmillion. yes that does work. I was trying to get confortable doing pipes (that is, avoiding the use of files), but I guess you can't use pipes for commands that need two inputs (like diff) ?

---

### Post by eightmillion on 2008-08-08
As far as I know, there's no easy way to pipe multiple inputs to one command. You can pipe one output to multiple inputs.

---

### Post by PGScooter on 2008-08-08
> **eightmillion said:**
> As far as I know, there's no easy way to pipe multiple inputs to one command. You can pipe one output to multiple inputs.

How do you pipe one output to multiple inputs?

---

### Post by eightmillion on 2008-08-08
You use the **tee** command.

> ls *.txt | tee /dev/tty txtlist.txt

The above command displays the output of **ls *.txt** to the terminal and ouputs it to the text file **txtlist.txt**.

---

### Post by PGScooter on 2008-08-08
cool, thanks

---

### Post by addps4cat on 2008-08-18
You can get away with just making one file if you want:

```
du -ab | sort > file1.txt && du -ab directory2 | sort | diff file1.txt - && rm file1.txt
```

---

### Post by PGScooter on 2008-08-19
> **addps4cat said:**
> You can get away with just making one file if you want:

```
du -ab | sort > file1.txt && du -ab directory2 | sort | diff file1.txt - && rm file1.txt
```

thanks addps4cat, I am just starting to see the advantage of using - for piping STDIN. This helps a bit more.

---

### Post by foolishchild on 2008-09-19
or how about diff <(du -ab | sort) <(du -ab directory2 | sort)

---

### Post by adbot asdakjsfhs on 2008-10-02
> **foolishchild said:**
> or how about diff <(du -ab | sort) <(du -ab directory2 | sort)

IMHO that's the most elegant way possible. Though keep in mind it is available only in bash. At least I don't know of others that implement it.

---

### Post by -bug- on 2011-11-01
I know it's a very old thread, and the OP might have forgot about it, but maybe someone else finds this useful. You can do:

diff <(du -ab | sort) <(du -ab directory2 | sort)



Edit: Sorry, I overlooked that there was already a reply with that solution, it wasn't displayed by default. Can I delete the whole entry somehow?

---

### Post by oldos2er on 2011-11-01
Closed, please don't bump old threads.

---

