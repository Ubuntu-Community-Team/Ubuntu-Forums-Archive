---
title: "sh - Command not found when invoking script"
date: 2010-10-19
forum: Programming Talk
---

### Post by ndefontenay on 2010-10-19
Hi.

Before I get the usual "Check your user rights", I got the following:

```
chmod 755 dwexport.sh
chmod 755 genparam.sh
```

I got a script called dwexport.sh that looks like this:
```
##################################################
#Description: Call mysql sql file dwgetactivity.sql along with parameters from param.sql
#Called by dwexport.sh
##################################################

rm -f /home/dw/data/*.txt

cd /home/dw/scripts
./genparam.sh
cat param.sql dwgetactivity.sql | mysql -u[user] -p[password] [database]

exit

```

When called separately directly in the shell, it all works nicely but inside the script it fails.

What I got is:
```
ns:/home/dw/scripts# ./dwexport.sh
: command not found 7:
: command not found 9:
: Aucun fichier ou répertoire de ce typeipts
: Aucun fichier ou répertoire de ce type
'RROR 1102 (42000): Incorrect database name 'mydb_name
: command not found 13:
: command not found 14: exit

```

I've tried with user dw then root, to no avail.

" Aucun fichier ou répertoire de ce type" -> No files or folder of this type

Some help finding out what's going on would be welcome.

---

### Post by ndefontenay on 2010-10-19
I think it could be due to extra characters at the end of each line but inside vim I see nothing.

I've ssh'ed the files to my desktop and opened them with notepad++, all I got is CRLF.

Not sure what's going on still :/

---

### Post by Some Penguin on 2010-10-19
Are we supposed to guess the contents of genparam.sh ?

---

### Post by spjackson on 2010-10-19
> **ndefontenay said:**
> I think it could be due to extra characters at the end of each line but inside vim I see nothing.

I've ssh'ed the files to my desktop and opened them with notepad++, all I got is CRLF.

Not sure what's going on still :/
1. If you dont't indicate what interpreter to use for your script, then this has to be inferred and that process can produce incorrect results.
2. CRLF as line terminators can certainly cause this type of problem.

So, first ensure that you have LF only not CRLF. There are many ways to do this, but one is in vim:
```

:set ff=unix
:w

```And second, use a shebang as the first line of the script, i.e. a line like
```

#!/bin/bash

```(or #!/bin/sh if you prefer).

---

