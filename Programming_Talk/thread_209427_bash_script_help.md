---
title: "bash script help"
date: 2006-07-05
forum: Programming Talk
---

### Post by udha on 2006-07-05
Here's some psudocode of what I'm after:
to run the script:
./addthis.sh something

the script will do something like:
get input $1
if $1 exists in file: sorry, that is taken
else add $1 to file

do if a string exists somewhere in a file, I need to catch that out, any tips, I'm sure this is easy to do but it's got me stumped:?

---

### Post by kabus on 2006-07-05
A rough idea :

```
if grep -q "$1"' file; then
    echo "sorry, that is taken"
else
    echo "$1" >> file
fi
```

---

### Post by udha on 2006-07-05
[QUOTE=kabus]A rough idea :

```
if grep -q "$1" file; then
    echo "sorry, that is taken"
else
    echo "$1" >> file
fi
```[/QUOTE]

Thanks that works, one further tweak is that some lines might have more text, so if there was:

yoyo

and you try to insert 'yo' it will fail, any ideas?

---

### Post by udha on 2006-07-05
I've gotten around it by putting values in double-quotes:

grep -q "\"$1\"" file; ....

echo "\"$1\"" >> file
...

---

