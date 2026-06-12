---
title: "Shell script: List all files in a directory along with their sizes."
date: 2012-04-15
forum: Programming Talk
---

### Post by Alphamonkey on 2012-04-15
I am just making a shell script for my "Intro to Linux" class that is supposed to have a user input directory and then list all the files in the directory along with their size. this is what i have so far but it only works with absolute pathnames. I tried ~/Downloads/ and it would not work. Thanks for any help.

```
echo -n "Please enter Directory name or enter path: "
read path


for directory in ${path}*
do
    if [ -f "$directory" ] ; then  #test to see if it is a file and then executes the following commands.

         size=`ls -l $directory |cut -d" " -f5`
         echo " The file $directory has size $size"
    fi
done
```

---

### Post by Vaphell on 2012-04-15
shell interprets ~ right off the bat and in reality commands don't see ~ ever, but when you keep it in variable, shell doesn't expand it to its true value.
```
$ echo ~
/home/me
$ read p
~
$ echo $p
~
```
as you can see ~ is not expanded

you need to transform it with sed or with bash builtin substitution to $HOME, eg
```
path='~/Downloads/'; echo "$path -> ${path/\~/$HOME}"
~/Downloads/ -> /home/me/Downloads/

```
there is another problem though, ~someone_else is a legit shorthand for /home/someone_else/
you would need to identify such a case and support it properly, with sed most likely
... but users can have non-standard home dir locations... ;-)
/etc/passwd provides the info

---

### Post by mörgæs on 2012-04-15
Moved to Programming Talk.

---

### Post by Alphamonkey on 2012-04-15
> **Vaphell said:**
> shell interprets ~ right off the bat and in reality commands don't see ~ ever, but when you keep it in variable, shell doesn't expand it to its true value.
```
$ echo ~
/home/me
$ read p
~
$ echo $p
~
```as you can see ~ is not expanded

you need to transform it with sed or with bash builtin substitution to $HOME, eg
```
path='~/Downloads/'; echo "$path -> ${path/\~/$HOME}"
~/Downloads/ -> /home/me/Downloads/

```there is another problem though, ~someone_else is a legit shorthand for /home/someone_else/
you would need to identify such a case and support it properly, with sed most likely
... but users can have non-standard home dir locations... ;-)
/etc/passwd provides the info

Thank you very much its very useful information to know. I didn't even consider the expansion of ~. Thanks again for your help.

---

