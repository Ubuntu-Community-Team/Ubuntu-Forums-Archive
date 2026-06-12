---
title: "question"
date: 2010-10-29
forum: Programming Talk
---

### Post by Reddoug on 2010-10-29
HI All

How can I tell what shells I can use on my computer. I am using Ubuntu 10.10. If I try to run a script that I created using #!/bin/sh that I wrote in my class and works on the server that I log into for class but will not run on this computer. Very simple script.
#!/bin/sh

if [ $# = 0 ]
then
   echo "Doug Oct 2010"
   exit
fi

Just trying to figure out what shells, not how to write scripts
Thanks, Doug

---

### Post by TSJason on 2010-10-29
Hey Reddoug,

Perhaps this will shed some light on it:

```

cat /etc/shells

```

---

### Post by Reddoug on 2010-10-30
Hi and Thanks. Shows I have 15 shells. 

Doug

---

### Post by Vox754 on 2010-10-30
> **Reddoug said:**
> HI All

How can I tell what shells I can use on my computer. I am using Ubuntu 10.10. If I try to run a script that I created using #!/bin/sh that I wrote in my class and works on the server that I log into for class but will not run on this computer. Very simple script.
#!/bin/sh

if [ $# = 0 ]
then
   echo "Doug Oct 2010"
   exit
fi

Just trying to figure out what shells, not how to write scripts
Thanks, Doug
How are you calling your script? That particular simple script should work.

Forget about the "/etc/shells" advice. That's useless.

Ubuntu comes installed with "/bin/dash" and "/bin/bash".

Bash is a major, widely used shell. It is normally considered the "default" shell. It is used when you open any terminal emulator, xterm, gnome-terminal, etc. Examples from most books and the Internet should work.

Dash is a minimal shell used to run basic system scripts in Ubuntu.

By default, "/bin/sh" is a symbolic link to "/bin/dash". So, if you use the shebang "#!/bin/sh" you are actually using "/bin/dash". This has caused some confusion among learners because their books or professors assume that the shell is the widely used "bash".

I advice you to use the shebang "#!/bin/bash" to avoid most problems.

However, this doesn't explain why your code doesn't work. It should.

---

### Post by spjackson on 2010-10-30
> **Reddoug said:**
> Shows I have 15 shells. 

Well, not necessarily. On my system there are 14 shells listed in /etc/shells, but only 6 are actually installed. Maybe try this:
```

for f in `cat /etc/shells`
do
    if [ -f "$f" ] ; then
        echo "$f"
    fi
done

```

---

### Post by MadCow108 on 2010-10-30
> **Vox754 said:**
> 
However, this doesn't explain why your code doesn't work. It should.

the problem is the = this is for string comparison.

To compare numbers you need to use -eq (or -ne -lt -gt -ge -le) or convert the number to a string with quotes
see: man test

---

### Post by Reddoug on 2010-10-30
doug@doug-laptop:~$ for f in `cat /etc/shells`
Hi 

This is what I have. TRhe script runs ok on the server I log into at school with =  I will give eq a try on my Linux computer. 

Thanks, Doug

> do 
>    if [ -f "$f" ] ; then 
>       echo "$f"
> fi
> done
/bin/csh
/bin/sh
/usr/bin/ksh
/bin/ksh
/bin/dash
/bin/bash
/bin/rbash
/usr/bin/screen
/bin/pdksh
/bin/ksh93
doug@doug-laptop:~$

---

