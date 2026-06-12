---
title: "Ignoring warning for shell &quot;ls&quot; command..."
date: 2007-01-11
forum: Programming Talk
---

### Post by Wybiral on 2007-01-11
Hey, I need to list a few different file types in one directory and I was doing it with the "ls" command.

It works great when all of the files I'm looking for exist, but when one type doesn't it sends an error which messes up my whole script.

Is there a flag for something I can use to disable the warning message when "ls" doesn't find any files?

Examples...

```

ls *aaa
ls *bbb
ls *ccc

```

When there is an aaa, bbb, and ccc files, it's ok... But if one doesn't exist it reports it... How do I stop that?

Thanks.

---

### Post by po0f on 2007-01-11
Wybiral,

```
[FONT="Courier New"]$ ls something_you_wont_find 2>/dev/null[/FONT]
```

[EDIT]

You can compare stdin, stdout, and stderr from C++ with 0, 1, and 2 on the command line.  What the above does is redirect stderr (2) to /dev/null, getting rid of any error messages.

---

### Post by Wybiral on 2007-01-12
I'm not sure I follow... I also need to use the response of the ls in C++... Well, I'm writing it to a file, like this...

```

system("ls *aaa *bbb>myFile")

```

But I would rather it not say "ls: *aaa: No such file or directory" even when there is a *bbb

---

### Post by po0f on 2007-01-12
Wybiral,

You can do multiple redirections of the std streams; something like the following should work:
```
[FONT="Courier New"]system("ls *aaa *bbb *ccc >my_file 2>/dev/null");[/FONT]
```

[quote=Wybiral]... script. ...[/quote]

Liar.  ;)

---

### Post by ghostdog74 on 2007-01-12
> **Wybiral said:**
> I'm not sure I follow... I also need to use the response of the ls in C++... Well, I'm writing it to a file, like this...

```

system("ls *aaa *bbb>myFile")

```

But I would rather it not say "ls: *aaa: No such file or directory" even when there is a *bbb

hi
does C/C++ has a library to perform opening of directories and listing files ? just like opendir() in Perl, or os.listdir() in Python. i think you would have better control over what you want to do, without the need to use "ls"...I vaguely remember there is a library called <dirent.h>...but i don't know whether it can do the job.

---

### Post by Wybiral on 2007-01-12
> Liar.
LOL, It is a script... Inside a C++ program... :)
Thanks po0f, your way worked.

Anyway, yeah there are C++ libraries for handling files, but since the system command is built in, and I need to write the results to a file anyway, it's easier to just use "system"

EDIT:

BTW, is there any way to run a case insensitive command? Or is that blasphemy to linux?
(In case you haven't noticed, I've been using C++ much longer than linux or BASH... I'm a windows refugee)

---

