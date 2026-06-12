---
title: "[SOLVED] Question about grep command."
date: 2008-09-01
forum: Programming Talk
---

### Post by Rany Albeg on 2008-09-01
Hi,

I want to make a wide search over the folder Music.
Inside Music folder there are several sub folders and inside these folders there are few mp3 files.
I want , using the command grep , to search for all the songs that their names starts with the letter 'f'.
Since the Music folder contains folders and I want to use the grep command , I need to use the r (recurse) parameter in case that if the current sub folder starts with the letter 'f' , the command will search inside it for files which starts with the same character, and so on.

I do have some folders which their names starts with the letter 'f',
though , when i use the grep command with the parameter r , ( combined with ls and a pipe ) the output contains only the names of the folders which starts with the letter 'f', which means grep didn't search inside these folders.

the output is stored inside a text file named 'list' , and the command looks like this:

cd ~/Music;(ls|grep -r "^f" )>list

I'll be happy for some help.

Have a nice day ;)

---

### Post by sisco311 on 2008-09-01
you can use the *find *command:
```
find /path/to/dir/ -type f -name f*
```

---

### Post by Rany Albeg on 2008-09-01
Thanks :D 

well, how do i mark the thread as SOLVED ? ;)

---

### Post by sisco311 on 2008-09-01
To mark your thread solved, go to **Thread Tools** and select [B]Mark this thread as solved.

[/B](more info in my signature :) ---------V)

---

### Post by Rany Albeg on 2008-09-01
:d Thanks

---

