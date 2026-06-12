---
title: "'find' command question"
date: 2008-09-04
forum: Programming Talk
---

### Post by Rany Albeg on 2008-09-04
Hi,

I use 'find' in a part of a script im writing , to search for some files.
The output of the command contains the full path name of the files - which i dont need - i want only the name of a specific file.
Its problematic to use 'cut' command to cut a part of the path name cuz 
deeper files makes the path name longer and longer which means i cant cut till i reach a specific place.

likewise, the 'grep' prints only the name of the file -  but i cant reach sub folders with it. Even if i use the -r switch i cant search recursively.

any ideas?

Have a nice day;)

---

### Post by sisco311 on 2008-09-04
try:
```
find /path/to/dir/ -type f *<other-options>* **-printf %f'\n'**
```

---

### Post by kaibob on 2008-09-04
> **Rany Albeg said:**
> The output of the command contains the full path name of the files - which i dont need - i want only the name of a specific file....

I don't totally understand what you want to do, but you may want to look at basename, which can be used to extract only the name of the file.

[http://www.manpagez.com/man/1/basename/](http://www.manpagez.com/man/1/basename/)

---

### Post by Rany Albeg on 2008-09-04
Thanks guys,
i'll try that and let you know if it worked for me ( if you are interested:)).

---

### Post by ghostdog74 on 2008-09-04
> **kaibob said:**
> I don't totally understand what you want to do, but you may want to look at basename, which can be used to extract only the name of the file.

[http://www.manpagez.com/man/1/basename/](http://www.manpagez.com/man/1/basename/)

basename can do the job, for few files. but slow for many files since its external command. you can use find's printf to print the file name.

---

### Post by kaibob on 2008-09-04
> **Rany Albeg said:**
> Thanks guys,
i'll try that and let you know if it worked for me ( if you are interested:)).
I'm just learning shell scripting and would be interested in what works best. I can see how printf would be preferred if a large number of files is involved.

---

### Post by Rany Albeg on 2008-09-05
Your code works fine sisco311.

%f is an option inside -printf allows you to print only the file name?

---

### Post by unutbu on 2008-09-05
The short answer is yes, %f is an option that find understands when put after -printf to print the filename.

The long answer is to type
```
man find
```
Then type
```
/-printf
```
to search for the string "-printf"

Press / a couple of times to find the next occurrence of "-printf"

Stop when you see "-printf format". Starting from there you will see all the special format characters you can use.

---

### Post by Rany Albeg on 2008-09-05
Thanks ;)

---

