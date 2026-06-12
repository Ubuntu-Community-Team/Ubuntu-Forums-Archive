---
title: "bash: parameter expansion + passing arguments with spaces = fail"
date: 2010-08-16
forum: Programming Talk
---

### Post by Zorgoth on 2010-08-16
I am trying (mostly for fun - I just want to make it work) to make a command that will simulate another command with the exact same arguments, plus some more.

An example would be a command 

emacs-ro

where 

emacs-ro arg1 arg2 arg3

is equivalent to

emacs arg1 arg2 arg3 --funcall toggle-read-only

Here is a script that intended to do this:

```

#!/bin/bash
argnumber=$BASH_ARGC
arglist=''
while [[ $argnumber > 0 ]] 
do
    argnumber=$(( argnumber - 1 ))
    arglist=$arglist\ `echo ${BASH_ARGV[argnumber]} | sed 's/ /\\ /g'`
done
arglist="$arglist --funcall toggle-read-only"
emacs$arglist

```

This works fine if you want to, for example, run 'emacs-ro -nw ~/test'.

But if you want to run 'emacs-ro "~/.wine/Program Files/World of Warcraft/WTF/Config.wtf"', the spaces will not be handled correctly - it will not pass the quoted expression to 'emacs' as one argument.  

Another approach that I tried and failed with was to put quotes around each argument and escape any literal quotes contained within the arguments.

Is there any way to use parameter expansion or command substitution or anything where there is a clear way to choose exactly which spaces we do and do not wish to separate arguments?

---

### Post by DaithiF on 2010-08-16
Hi,
```

#!/bin/bash
emacs "$@" --funcall toggle-read-only

```

for an explanation of $@ see man bash and search for the section "Special Parameters"

---

### Post by tbastian on 2010-08-16
you could also put an alias in your ~/.bashrc file.
eg
```
alias emacs-ro='emacs --funcall toggle-read-only'
```

---

### Post by geirha on 2010-08-16
[http://mywiki.wooledge.org/Arguments](http://mywiki.wooledge.org/Arguments) explains in more detail why your initial approach failed.

---

### Post by Zorgoth on 2010-08-16
> **geirha said:**
> [http://mywiki.wooledge.org/Arguments](http://mywiki.wooledge.org/Arguments) explains in more detail why your initial approach failed.

Thanks.  This was really what I was looking for.  What I really wanted to know about was how to use a bash script to pass an arbitrary number of arguments which could potentially include spaces.  I couldn't figure out how to do it with arrays because I didn't know about "${myarray[@]}" to pass all of the elements of an array as arguments.

The first post was very helpful too of course :D

---

