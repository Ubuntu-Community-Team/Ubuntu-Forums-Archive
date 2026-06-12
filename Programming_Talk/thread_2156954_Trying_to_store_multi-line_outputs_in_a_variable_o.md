---
title: "Trying to store multi-line outputs in a variable or array"
date: 2013-06-23
forum: Programming Talk
---

### Post by s3a on 2013-06-23
I've found several links but, none of them worked.

_Here is the one that seems to be the best to me (but, it is still not good enough)._:
```
#!/bin/bash

i=1
ls -la /tmp | while read line
do
    array[ $i ]="$line"
    (( i++ ))
done
```

_I'm trying to do this for two reasons._:
(1) To learn more about Linux shell scripting.
(2) To, ultimately, create a script which allows me to remove absolutely everything containing a certain string in it (or to move it to a directory to confirm that there is nothing being removed that I need prior to removing the bunch of files).

What I am trying to figure out, using this thread, is how to store each individual line of the multi-line input of ```
ls -la /tmp
``` into its respective array element.

Running the syntax I gave above prints out a new line character (by which I mean it just jumps a line).

Any input in figuring out how to get the syntax above working as I intend it to would be greatly appreciated!

---

### Post by trent.josephsen on 2013-06-23
I'm not a bash expert, but I bet if you're seeing double-spaced output it's because of the printing logic, not how you're reading it in. What you have looks fine to me.

---

### Post by steeldriver on 2013-06-23
I'm not a bash expert either, but you could also consider using the *readarray* builtin in place of your for loop - something like

```
$ readarray -t array < <(ls -la /tmp)
```

might work for you - e.g.

```
$ readarray -t array < <(ls -la test)
$ 
$ for f in "${array[@]}"; do echo "$f"; done
total 12
drwxr-xr-x  3 steeldriver steeldriver 4096 Jun 23 19:31 .
drwxr-xr-x 40 steeldriver steeldriver 4096 Jun 22 19:30 ..
drwxr-xr-x  2 steeldriver steeldriver 4096 Jun 14 21:27 dir
-rw-r--r--  1 steeldriver steeldriver    0 Jun 23 19:31 file with space
$
$ echo ${array[3]}
drwxr-xr-x  2 steeldriver steeldriver 4096 Jun 14 21:27 dir

```

---

### Post by Vaphell on 2013-06-23
readarray would be the way to go...
... but using ls output for anything is considered harmful as it doesn't guarantee the true representation of the filename in case of nasty characters (newline, unprintable). Kosher way would utilize native globs or null delimited find command

btw, bash has += operator that allows to add element to array without managing indices by hand
```
$ array=( "abc" "def" )
$ array+=( "ghi" ) #array is now "abc" "def" "ghi"
```

---

### Post by s3a on 2013-06-23
**trent.josephsen:**
Oh my god! I forgot to print it out! Lol!

Looking at this link ( [http://www.thegeekstuff.com/2010/06/bash-array-tutorial/](http://www.thegeekstuff.com/2010/06/bash-array-tutorial/) ), I added ```
echo ${array[ $i ]}
``` between the setting-each-array-element and the element variable incrementation steps and, it works! Thanks! :D

**steeldriver:**
Thanks for this as well! :)

**Vaphell:**
Thank you for yet another useful thing! :)

---

