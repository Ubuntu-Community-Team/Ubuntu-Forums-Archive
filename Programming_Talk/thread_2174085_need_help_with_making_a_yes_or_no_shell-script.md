---
title: "need help with making a yes or no shell-script"
date: 2013-09-12
forum: Programming Talk
---

### Post by vonvic on 2013-09-12
Hi! I'm really new to Linux and I'm trying to make a yes or no shell script.
Here's what I got:

echo "yes or no"
read answer

if ( $answer == yes ); then
echo you chose yes
exit

if ( $answer == no ); then
echo you chose no
exit

if ( $answer == * ); then
echo please pick yes or no
exit

but after that I get in the terminal:

vonvic23@VVMC123:~$ ./yn.sh
yes or no
yes
./yn.sh: line 15: syntax error: unexpected end of file
vonvic23@VVMC123:~$

---

### Post by vonvic on 2013-09-12
Hi! I'm really new to Linux and I'm trying to make a yes or no shell script.
Here's what I got:

echo "yes or no"
read answer

if ( $answer == yes ); then
echo you chose yes
exit

if ( $answer == no ); then
echo you chose no
exit

if ( $answer == * ); then
echo please pick yes or no
exit

but after that I get in the terminal:

vonvic23@VVMC123:~$ ./yn.sh
yes or no
yes
./yn.sh: line 15: syntax error: unexpected end of file
vonvic23@VVMC123:~$

Any help?

---

### Post by Vaphell on 2013-09-12
*if *block should always end with *fi *and conditions use [ ] or [[ ]], not ( )
also why use multiple *if*s if you can use one with *elif *and *else*
```
if ...; then
  ...
elif ...; then
  ...
else
  ...
fi
```
another option to test the answer against possibilities would be to use *case*

---

### Post by vonvic on 2013-09-12
thank you! that help

---

### Post by steeldriver on 2013-09-12
You could also consider using a *case ... esac* statement

```

#!/bin/bash

read -p "yes or no: " ans

case "$ans" in
    yes) echo "you chose yes"
    ;;
    no) echo "you chose no"
    ;;
    *)  echo "please pick yes or no"
    ;;
esac

```

---

### Post by vonvic on 2013-09-12
what would the -p do?

---

### Post by HiImTye on 2013-09-12
exit tells your script to terminate, what you want to use is fi, which tells the script you're at the end of your if statement, such as

```
# example if statement
a="ten"
if [ "$a" = "ten" ]; then
 echo "yes"
else
 echo "$a"
fi
```

---

### Post by steeldriver on 2013-09-12
It's a neater way of doing an echo and then a read - type

```
help read
```

for more info

---

### Post by oldfred on 2013-09-12
Please do not create duplicate threads.

Merged & moved to programming.

---

