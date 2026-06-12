---
title: "How in ls command show relative path of any file ?"
date: 2022-02-10
forum: New to Ubuntu
---

### Post by petrogromovo on 2022-02-10
Hello,
I know in Kubuntu 20 a way to show all files under subdirectires :

```
ls -Rl |sort -k5 -hr|more
```

But I see only short names of files, but I also need to show relative path(to the current directory) of this file ? 

How can I get it ?

Thanks in advance!

---

### Post by Holger_Gehrke on 2022-02-10
I'd use 'find' with a '-printf' action that mimics the output of 'ls -l'.
```

find . -type f -printf "%M\t%n\t%u\t%g\t%s\t%T+\t%P\n"|sort -k5 -hr|less

```

See 'man find' for details. You can fine tune the output to only have the fields you actually want in the order you want them.

Holger

---

### Post by schragge on 2022-02-10
GNU find even has the [[FONT=monospace]-ls[/FONT]](https://www.gnu.org/software/findutils/manual/html_node/find_html/Print-File-Information.html) action.

---

### Post by TheFu on 2022-02-10
find is crazy powerful ... and while the manpage is complete, I think it is one command (find) that learning by seeing 50 examples really makes sense.  After seeing and playing with the examples, then delve into the manpage and things will start to make sense.

My solution to the question wouldn't be to provide relative paths, since I use symbolic links and different shells will convert those to canonical results on access ... er ... sometimes, but not always.

The typical problem when I expect parent and sibling directories to be used is with a single application, so I just force the application startup script to set an "APP_HOME" environment variable. Everything else is below that point, by definition for a self-contained application.  For installed applications, there is the package manager which keeps all the locations of the installed files along with their names.  Not very elegant.  But looking from $CWD/../  and $CWD/../../ with **find** isn't too hard.  So this is the command and the returned results
```
$ find ../ -type f -print
../bin/hdhr-tuner-scan
../bin/tv-convert.pl
../cache/TV-signals
../etc/Channels.txt
../etc/scheduling.conf
```

Heck, even using the $0 argument, which contains the current program being run, getting that to provide the actual, complete, path to itself is non-trivial.  There are simple, likely, "good-enough" solutions to that problem, but it could easily be broken.  

Under bash, 
```
$!/bin/bash

SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" >/dev/null 2>&1 && pwd )"
echo "Running from: $SCRIPT_DIR"

```
But it is easy to break that result. So we add
```
#!/bin/bash

SCRIPT_DIR="$( cd "$( dirname "${BASH_SOURCE[0]}" )" >/dev/null 2>&1 && pwd )"
if [ -h "${BASH_SOURCE[0]}" ] ; then
   SCRIPT_DIR=$(stat "${BASH_SOURCE[0]}" |grep File: | sed -e 's#^.*-> ##go')
fi
echo "Running from: $SCRIPT_DIR"
```

BTW, I've seen scripts refuse to run if there wasn't a blank line after the #! line.  "Text File is busy" is the error.

And the more complex solution nearly works 90% of the time. There are still some ways to break it.

---

### Post by Tadaen_Sylvermane on 2022-02-12
Once I discovered the find command it has taken a central place in many of my scripts. I keep finding new ways to use it. It's amazing.

---

