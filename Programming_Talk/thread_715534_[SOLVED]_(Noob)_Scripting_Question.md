---
title: "[SOLVED] (Noob) Scripting Question"
date: 2008-03-04
forum: Programming Talk
---

### Post by Nerdriot on 2008-03-04
Hello,

I'm trying to do a fairly simple task in this script. I'm basically asking the user for what type of settings they'd like to use for a DPG converter. The script that it's executing uses command line args to specify certain settings.

So, I set it up to ask them a series of questions, then take their answers, and write the args to a text file, in order, so at the end of the questions, it will execute the script with those arguments attached.

But here's my problem: I created one file, and when they select the first option, it simply uses "echo" to copy that to the file. The next option, when they select it, all I really want to do is keep the file the way it is, and use "sed" to attach the new option to the end of the first line. However, it doesn't seem like I'm able to do that, without doing this:

```
cat file | sed '1s\$\ -arg2\' > file2 | cat file2 > file
```

Surely there's a way to do this, without having to create 2 files. I know one of you smart folks has a way, too. :)

Thanks in advance ;)

---

### Post by PaulFr on 2008-03-05
Does this help?```
echo " $arg2\c" >> $file
``` or ```
echo -n " $arg2" >> $file
```

---

### Post by Nerdriot on 2008-03-05
Thaaaaaaaaaaaaaaaaaank you!

You've just saved me from typing at least half of this script, lol.

---

### Post by Nerdriot on 2008-03-05
Ahh, spoke too soon. Seems to do this:

```
ben@ub3ntu:~$ touch file1 | echo "test" > file1 | echo -n " -ing" >> file1
ben@ub3ntu:~$ cat file1
test
 -ingben@ub3nt
```

Or:

```
ben@ub3ntu:~$ touch file1 | echo "test" > file1 | echo " -ing\c" >> file1
ben@ub3ntu:~$ cat file1
test
 -ing\c

```

Something I'm doing wrong? (I should know all of this by now...)

---

### Post by PaulFr on 2008-03-05
Sorry, I misspoke. Here is what you can use ```
echo -n " $arg2" >> $file
``` or ```
echo -e " ${arg2}\c" >> $file
```I forgot the **-e**.

Also you have to use it for every argument. In your example, you are running **echo "test" > file1**. That has to be **echo -n "test" > file1**.

---

### Post by Nerdriot on 2008-03-05
Ah, THAT did it. Thank you very much! Marking thread as "Solved". :)

---

