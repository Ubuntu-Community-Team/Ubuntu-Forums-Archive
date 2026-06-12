---
title: "Dumb question: How to (1) modify PATH variable and (2) how to add to PATH variable"
date: 2015-02-18
forum: Programming Talk
---

### Post by king-oslo on 2015-02-18
Hello there,

I am sorry to ask this question, however I have for days been trying to understand how to 

1) modify my existing PATH variable
2) add stuff to my PATH

I have read all sort of stuff on google, and nothing that I have tried works, and I dont understand any of the terminology which is used. This is my problem:

When i go to the terminal and type

$ pdflatex

terminal execute /usr/bin/pdflatex

istead I would like to

write 

$ pdflatex 

to execute /usr/local/texlive/2014/bin/x86_64-linux/pdflatex


Can someone please provide exact steps of what to write in the terminal such that the modification will work for all users after any number of reboots of the system?




Second:

Can someone tell me what to exactly what to write into the terminal to add "/directory1/directory2/" to the PATH such that when there is a an executable called "script" located at "/directory1/directory2/script", then typing

$ script

will execute "script"?

Thank you so much for your time. Will you kindly explain in simple terms, because I am confused why this should be so difficult that I need to spend days learning how to do it.

Thank you for your time.

Kind regards,
Marius

---

### Post by steeldriver on 2015-02-18
Personally, for cases like your pdflatex example, rather than add random deeply-nested directories to the system-wide PATH, I would take the approach of symlinking the executable to somewhere that's already on the standard PATH (and ahead of locations like /usr/bin) e.g.

```

sudo ln -s /usr/local/texlive/2014/bin/x86_64-linux/pdflatex /usr/local/bin/pdflatex

```

If /usr/local/bin doesn't already exist,  create it first e.g.

```

sudo mkdir -p /usr/local/bin

```


_____________
If you really want to go ahead and modify the system-wide PATH, it should just be a matter of editing the /etc/environment file - but I don't recommend it. You would change

```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"

```
to
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games**:****/dir1/dir2**"

```
or
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin**[B]:**/dir1/dir2[/B]:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games"

```

etc. depending what order you want the directories to be searched in. **See** [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables) **for other options**.

---

### Post by aromo2 on 2015-02-18
Also, remember that to get your script to run as an executable file you need to:
1) The first line must start with crash-bang followed by the full path of the interpreter (without spaces). For instance, the first line of your bash script would be:
```
[FONT=courier new]#!/bin/bash[/FONT]
```
2) The script file must have execution permissions:
```
[FONT=courier new]chmod +x script[/FONT]
```

---

### Post by Bucky Ball on 2015-02-18
*Thread moved to **Programming Talk**.*

---

