---
title: "newlines in shell"
date: 2009-09-03
forum: Programming Talk
---

### Post by king vash on 2009-09-03
I have a shell script which takes a string (with newlines in it) as a parameter. It then sends that to another program.

called like "sh printer.sh "Hello \n World"
when I use it later in the program the \n has been converted to a newline character. I need it to not echo with a newline character but with a "\n"

"echo $1" prints
"Hello 
 World"

were I want "Hello \n Wold".

any ideas?

---

### Post by zarthon on 2009-09-03
#!/bin/bash
echo $1

Bash Works the way you want it to

#!/bin/sh
echo $1

Sh does not.

Someone else may know exactly why this is.

---

### Post by king vash on 2009-09-03
Thank you, that solved the problem!

---

### Post by Gen2ly on 2009-09-03
Instead of switching shells, consider using echo with single quotes to print the output literally:

```
echo 'bin \n my bash'
```

---

### Post by epicoder on 2009-09-24
This might work:

```
echo "Hello \\n World"
```

---

