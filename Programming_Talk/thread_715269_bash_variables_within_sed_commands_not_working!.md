---
title: "bash variables within sed commands not working!"
date: 2008-03-04
forum: Programming Talk
---

### Post by Mlehliw on 2008-03-04
I'm trying to do a replacement with sed inside a bash script. My sed command looks something like the following

sed "s/TEXT/$VAR/" input_file

But sed keeps complaining at me about the $ character. Is it possible to put a variable inside sed in this manner?

---

### Post by kaens on 2008-03-04
```

$ cat >> test << EOF
this is a test
Ctrl-D
$ VAR=test
$ sed s/$VAR/toast/ test
this is a toast

```

Works with $VAR in replacement or searching position. What are you trying to expand $VAR to? What happens when you do the small example above?

---

### Post by ghostdog74 on 2008-03-04
show your code

---

### Post by Ramses de Norre on 2008-03-05
> **Mlehliw said:**
> 
sed "s/TEXT/$VAR/" input_file


```
sed -e s/TEXT/$VAR/ input_file
```

---

### Post by Mlehliw on 2008-03-15
I came up with a solution and completely forgot about this thread, anyway if anyone's having the same problems. I changed

sed "s/TEXT/$VAR/" input_file

to

sed "s|TEXT|$VAR|" input_file

---

