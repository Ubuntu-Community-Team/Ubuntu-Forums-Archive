---
title: "Help Me With this script."
date: 2012-09-17
forum: Programming Talk
---

### Post by huangyingw on 2012-09-17
Hi,
  The command output:
```

root@laptop:/home/huangyingw/myproject/git/java/algorithm# fw . public
-iname *.java -o -iname *.h -o -iname *.sh
find . \( -iname *.java -o -iname *.h -o -iname *.sh \) -exec fgrep -wnH public {} ;
find: invalid expression; you have used a binary operator '-o' with nothing before it.
root@laptop:/home/huangyingw/myproject/git/java/algorithm# 

```
file fw.sh
```

huangyingw@laptop:~/bashrc$ cat fw.sh 
#!/bin/bash
FILE_POSTFIX=$HOME/bashrc/postfix.bak
find_params=(); or="";
while read suf
do
  find_params+=( $or "-iname" "*.$suf" )
  or="-o"
done < "$FILE_POSTFIX"
echo "${find_params[@]}"
echo find "$1" "\( ${find_params[@]} \)" -exec fgrep -wnH  "$2" {} \;
find "$1" "\( ${find_params[@]} \)" -exec fgrep -wnH  "$2" {} \;

```
file postfix.bak:
```

huangyingw@laptop:~/bashrc$ cat postfix.bak 
java
h
sh
huangyingw@laptop:~/bashrc$

```

---

### Post by Vaphell on 2012-09-17
Find (and any other command) needs to see all its params as distinct words.
let's see what find gets from your expansion
```
find_params=( -iname "*.java" -o -iname "*.h" -iname "*.sh" )
$ i=0; for x in [COLOR="Red"]"\( ${find_params[@]} \)"[/COLOR]; do echo $((++i)) \'"$x"\'; done
1 [COLOR="Red"]'\( -iname'[/COLOR]
2 '*.java'
3 '-o'
4 '-iname'
5 '*.h'
6 '-iname'
7 [COLOR="Red"]'*.sh \)'[/COLOR]
$ i=0; for x in "(" "${find_params[@]}" ")"; do echo $((++i)) \'"$x"\'; done
1 '('
2 '-iname'
3 '*.java'
4 '-o'
5 '-iname'
6 '*.h'
7 '-iname'
8 '*.sh'
9 ')'

```
as you can see you shouldn't glue quoted params array with anything else otherwise you will merge things together.

that **\(** you often see in examples of find is equivalent to **"("** or **'('**. It's escaped because by default bash recognizes ( and ) as syntax related and you need to make it ignore them.
You pick one of these forms and you need to make sure it's a standalone parameter.

you can write all commands in this form
```
some_command '(' 'param1' '-o' 'param2' ')'
```
but since bash can figure out what is a word we don't have to do all that quoting, unless it has some char(s) that can break things like space,tab,;,*,?,(,) etc.

---

### Post by huangyingw on 2012-09-17
> **Vaphell said:**
> Find (and any other command) needs to see all its params as distinct words.
let's see what find gets from your expansion
```
find_params=( -iname "*.java" -o -iname "*.h" -iname "*.sh" )
$ i=0; for x in [COLOR="Red"]"\( ${find_params[@]} \)"[/COLOR]; do echo $((++i)) \'"$x"\'; done
1 [COLOR="Red"]'\( -iname'[/COLOR]
2 '*.java'
3 '-o'
4 '-iname'
5 '*.h'
6 '-iname'
7 [COLOR="Red"]'*.sh \)'[/COLOR]
$ i=0; for x in "(" "${find_params[@]}" ")"; do echo $((++i)) \'"$x"\'; done
1 '('
2 '-iname'
3 '*.java'
4 '-o'
5 '-iname'
6 '*.h'
7 '-iname'
8 '*.sh'
9 ')'

```
as you can see you shouldn't glue quoted params array with anything else otherwise you will merge things together.

that **\(** you often see in examples of find is equivalent to **"("** or **'('**. It's escaped because by default bash recognizes ( and ) as syntax related and you need to make it ignore them.
You pick one of these forms and you need to make sure it's a standalone parameter.

you can write all commands in this form
```
some_command '(' 'param1' '-o' 'param2' ')'
```
but since bash can figure out what is a word we don't have to do all that quoting, unless it has some char(s) that can break things like space,tab,;,*,?,(,) etc.
Great.. Great thanks for your detail instructions. I have updated my script to following, and it works well and optimized now:)
```

huangyingw@laptop:~/bashrc$ cat fw.sh 
#!/bin/bash
FILE_POSTFIX=$HOME/bashrc/postfix
PRUNE_POSTFIX=$HOME/bashrc/prunefix
find_params=();
prune_params=();
or="";
grep_params="";
if [ -n "$3" ]
then grep_params=" -A"$3" -B"$3;
fi
while read suf
do
  find_params+=( $or "-iname" "*.$suf" )
  or="-o"
done < "$FILE_POSTFIX"
or="";
while read suf
do
  prune_params+=( $or "-iname" "*.$suf" )
  or="-o"
done < "$PRUNE_POSTFIX"
find "$1" "(" "${prune_params[@]}" "-o" "-iname" "find.cc" ")" -prune -o "(" "${find_params[@]}" ")" -exec fgrep -wnH  $grep_params "$2" {} \;
huangyingw@laptop:~/bashrc$ 

```

---

### Post by huangyingw on 2012-09-17
Finally, my script update to be:
```

huangyingw@laptop:~/bashrc$ cat fw.sh 
#!/bin/bash
FILE_POSTFIX=$HOME/bashrc/postfix
PRUNE_POSTFIX=$HOME/bashrc/prunefix
find_params=();
prune_params=();
or="";
grep_params="";
if [ -n "$3" ]
then grep_params=" -A"$3" -B"$3;
fi
while read suf
do
  find_params+=( $or "-iname" "*.$suf" )
  or="-o"
done < "$FILE_POSTFIX"
or="";
while read suf
do
  prune_params+=( $or "-iname" "*.$suf" )
  or="-o"
done < "$PRUNE_POSTFIX"
find "$1" "(" "${prune_params[@]}" "-o" "-iname" "find.cc" ")" -prune -o "(" "${find_params[@]}" "-o" "-iname" "makefile" ")" -exec fgrep -wnH  $grep_params "$2" {} \;
huangyingw@laptop:~/bashrc$ 

```

---

