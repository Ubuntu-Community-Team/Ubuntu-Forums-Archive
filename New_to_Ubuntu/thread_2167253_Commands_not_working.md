---
title: "Commands not working"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by radha2 on 2013-08-13
Hello Friends

Whenever I am trying to use command on terminal, it just display following message

radha@radha-desktop:~$ cat tecmint.txtcat: tecmint.txt: No such file or directory

radha@radha-desktop:~$ cat tecmint.txt
cat: tecmint.txt: No such file or directory


for that what i have to do ???

---

### Post by deadflowr on 2013-08-13
Where is the tecmint.txt file located?
run 
locate tecmint.txt

---

### Post by DuckHook on 2013-08-13
The command you are attempting will only work for a file in your current directory. If the file is in another directory (even a subdirectory of your current one) then *cat* will not find it and will return the error message that you see.

<edit>
Beaten to the punch by *deadflower*
</edit>

---

### Post by radha2 on 2013-08-13
]If the file is in another directory (even a subdirectory of your current one) then how to work or set any permanent path to display contents by WC command.

---

### Post by DuckHook on 2013-08-13
I don't understand your question. *wc* displays word/line/byte count; not content.

If you want the system to check all the files in any specific directory every time you issue a command, then you can include that specific directory in your path variable. But to include all directories is extremely unwise and likely not even possible. You cannot include every possible directory on your path without ballooning the variable into a resource hog of gargantuan proportions. I also believe that there is a very real upper limit to the size of the path variable, so it's an impossibility anyway. Or perhaps I am misunderstanding your question.

Linux is designed to segregate files into a directory tree that can grow as big and complex as you like. This has many benefits including allowing you to give two files the same name under different directories. Example: "Tax Return" under /2012 and "Tax Return" under /2013. However, this requires you to define the full path in order to act upon that specific file. There is no getting around this requirement and, if I may be so bold, that's the way it should be.

If you want to *cat* the contents of tecmint.txt, then type in:```
cat /the/full/path/to/tecmint.txt
```

---

