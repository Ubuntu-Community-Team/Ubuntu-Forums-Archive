---
title: "Zenity: Using login dialog to set variables"
date: 2014-03-04
forum: Programming Talk
---

### Post by aFoxNamedMorris on 2014-03-04
Hi. I am trying to write a shellscript that will use Zenity to create a login dialog, and pass the user input to variables... but it keeps crashing the script. I am fairly good with shellscript itself, but I am just starting out in Zenity...

This is the part that is messing with me:

```

#!/bin/sh

USER="USERNAME"
PASSWD="PASSWORD"

`zenity --password --username "$USER" "$PASSWD"`

case $? in
         0)
         echo "User Name: `echo $USER | cut -d'|' -f1`"
         echo "Password : `echo $PASSWD | cut -d'|' -f2`"
        ;;
         1)
                echo "Stop login.";;
        -1)
                echo "An unexpected error has occurred.";;

echo $USER
echo $PASSWD
esac
```

Any help would be greatly appreciated.

EDIT>>: It's not actually crashing, but rather on reading the output from the terminal, Zenity is not setting the variables. Please help.

---

### Post by Vaphell on 2014-03-05
you need to capture the output and cut the string on '|' which you didn't do. You run zenity but don't do anything with it other than checking its exit code.
btw, you really shouldn't use a variable name like $USER. It's taken, you are overriding env variable of the shell. By convention they are all caps and variables user scripts should have at least 1 lowercase char to avoid collision.

switch to more convenient bash and go with something like this
```
IFS='|' read user pw < <( zenity --password --username )
echo $?
echo $user $pw

```


also backticks `` are deprecated and $( ) should be used instead

---

### Post by aFoxNamedMorris on 2014-03-05
> **Vaphell said:**
> you need to capture the output and cut the string on '|' which you didn't do. You run zenity but don't do anything with it other than checking its exit code.
btw, you really shouldn't use a variable name like $USER. It's taken, you are overriding env variable of the shell. By convention they are all caps and variables user scripts should have at least 1 lowercase char to avoid collision.

switch to more convenient bash and go with something like this
```
IFS='|' read user pw < <( zenity --password --username )
echo $?
echo $user $pw

```


also backticks `` are deprecated and $( ) should be used instead

Thank you! This worked perfectly!

---

