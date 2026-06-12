---
title: "shell help"
date: 2009-05-11
forum: Programming Talk
---

### Post by quickshot89 on 2009-05-11
```
#!/bin/sh

ls=`$which ls`

case $1 in
 -l) options=-l  ;
     filename=$2 ;
     shift      ;;
 -L) options=-L  ;
     filename=$2 ;
     shift      ;;
 -*) echo .ls: illegal option . $1  ;
     echo .usgae ls -l or -L filename ;
     exit 1 ;
 *) filename=$1 ;;
 esac

if [ $filename ]
then
  $ls $options $filename
else
  echo No filename given
  echo usage: ls [-l,L] filename
fi

```

getting an error on line 15, not sure whats going on

this shell is to be used in a limited enviroment with limited commands

edit: error is  line 15: syntax error near unexpected token `)'
 line 15: ` *) filename=$1 ;;'

---

### Post by stroyan on 2009-05-11
Your problem is on line 14 where you have "exit 1 ;" instead of "exit 1 ;;".

You should use double quotes around variables to avoid special characters being interpreted as part of a command instead of part of string.  The "if [ $filename ]" and "$ls $options $filename" lines would behave badly if $filename contained brackets or spaces.

---

