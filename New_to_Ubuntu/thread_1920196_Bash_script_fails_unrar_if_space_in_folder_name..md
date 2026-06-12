---
title: "Bash script fails unrar if space in folder name."
date: 2012-02-04
forum: New to Ubuntu
---

### Post by mafi127 on 2012-02-04
Can some1 help me to fix this litle script. This script will unrar all the files in directory and all sub directorys.
The problem is when the directory name contains space, then script dont work. it will give me this error

[PHP]
masin@mafia:~$ cd /media/-Arhiiv-/Filmid/Seebid/The\ Wire/Season\ 02/
masin@mafia:/media/-Arhiiv-/Filmid/Seebid/The Wire/Season 02$ bash unrar.sh
find: ‘/media/-Arhiiv-/Filmid/Seebid/The’: No such file or directory
find: ‘Wire/Season’: No such file or directory
find: ‘02’: No such file or directory
[/PHP]

The unrar.sh script what I use

[PHP]#!/bin/bash
for i in $(find $(pwd) -name '*.r00')
do
cd $(dirname $i)
unrar e $i &&  rm *.r??
done[/PHP]

I think its not realy hard to fix this.

---

### Post by nothingspecial on 2012-02-04
Always quote you variables.

See here

[http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target](http://mywiki.wooledge.org/BashPitfalls#cp_.24file_.24target)

---

### Post by mafi127 on 2012-02-04
Still get this same error. I changed the line to this

[PHP]cd "$(dirname "$i")"[/PHP]

---

### Post by Lars Noodén on 2012-02-04
Close.  Take a look at your quotes again, they're cancelling each other out.

---

### Post by Vaphell on 2012-02-04
```
find -iname '*.r??' -execdir unrar e "{}" \;
``` wouldn't do the trick?

Your *for* loop is critically broken and will not work
```
for i in $(<command>)
``` will delimit stuff from *$(<command>)* on every single space possible so any space-containing name will go in pieces
example:
```
$ echo $'a b\nc d' #print 2 lines a b, c d
a b
c d
$ for i in $( echo $'a b\nc d'); do echo =$i=; done  # capture echo to feed the loop
=a=
=b=
=c=
=d=
$ for i in "$( echo $'a b\nc d')"; do echo =$i=; done  # quoting $() doesn't help
=a b c d=

```
structure is not preserved.



use *find -exec/-execdir* to perform operation on every matching item, without worrying about its name
or go with
```
find ... -print0 | while read -d $'\0' f; do <stuff with "$f">; done
```
*find* pipes \0-delimited names to *while read* loop which uses \0 as a delimiter, receiving all names in perfect shape

---

