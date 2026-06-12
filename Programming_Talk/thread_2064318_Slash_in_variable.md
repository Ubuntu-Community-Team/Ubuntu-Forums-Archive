---
title: "Slash in variable"
date: 2012-09-29
forum: Programming Talk
---

### Post by huangyingw on 2012-09-29
Hi,
  I am writing following script:
  ```
huangyingw@laptop:~/bashrc$ cat fr.sh
#! /bin/sh
file=/home/huangyingw/myproject/git/test_fr/makefile
sed -i "s/"$1"/"$2"/gi" $file
huangyingw@laptop:~/bashrc$ 
```
  And passing following parameter to it, then I got the error. ```
huangyingw@laptop:~/myproject/git/test_fr$ fr ~/myproject/git/makefile/GNU_makefile_template ~/myproject/git/GNU_makefile_template
sed: -e expression #1, char 9: unknown option to `s'
huangyingw@laptop:~/myproject/git/test_fr$ 

```
   I think it is caused by the special character "Slash" in the parameter. 
   How could I work around this?

---

### Post by Lars Noodén on 2012-09-29
Quotes don't nest and it looks like you had them nested.  Try different quotes instead.

```

[s]sed -i 's/"$1"/"$2"/gi' $file[/s]

```

---

### Post by spjackson on 2012-09-29
I'm not sure what those inner quotes are meant to be doing. Are they intentionally part of the pattern? If so, for this particular case, this should get around your slash problem.
```

sed -i "s#\"$1\"#\"$2\"#gi" $file
```However, if $1 or $2 contains a # then you will get the same problem.

You would have to update your variables to escape whatever character you use as the separator.

@       Lars Noodén If a single quote is used for the outer quote, then $1 and $2 are not subsituted by the shell.

---

### Post by huangyingw on 2012-09-29
> **spjackson said:**
> I'm not sure what those inner quotes are meant to be doing. Are they intentionally part of the pattern? If so, for this particular case, this should get around your slash problem.
```

sed -i "s#\"$1\"#\"$2\"#gi" $file
```However, if $1 or $2 contains a # then you will get the same problem.

You would have to update your variables to escape whatever character you use as the separator.

@       Lars Noodén If a single quote is used for the outer quote, then $1 and $2 are not subsituted by the shell.
I have tried both of above solution, neither of them works:(
```
huangyingw@laptop:~/bashrc$ cat fr.sh
#! /bin/sh
file=/home/huangyingw/myproject/git/test_fr/makefile
#sed -i "s/"$1"/"$2"/gi" $file
#sed -i 's/"$1"/"$2"/gi' $file
sed -i "s#\"$1\"#\"$2\"#gi" $file

```
....

---

### Post by Vaphell on 2012-09-29
spjackson asked if the quotes are a part of the string (s/"something"/"something else"/). that would require escaping literal quotes and he he showed how to obtain it (\")

in case there are no quotes to worry about, the whole thing is straightforward

```
sed -i "s#$1#$2#gi" "$file"
```

# will solve slash issue, but you can use any character as a delimiter. It's best to use one that can't possibly exist in patterns and replacements.

---

### Post by huangyingw on 2012-09-29
> **Vaphell said:**
> spjackson asked if the quotes are a part of the string (s/"something"/"something else"/). that would require escaping literal quotes and he he showed how to obtain it (\")

in case there are no quotes to worry about, the whole thing is straightforward

```
sed -i "s#$1#$2#gi" "$file"
```

# will solve slash issue, but you can use any character as a delimiter. It's best to use one that can't possibly exist in patterns and replacements.

I have tried this:```
huangyingw@laptop:~/bashrc$ cat fr.sh
#! /bin/sh
file=/home/huangyingw/myproject/git/test_fr/makefile
#sed -i "s/"$1"/"$2"/gi" $file
#sed -i 's/"$1"/"$2"/gi' $file
#sed -i "s#\"$1\"#\"$2\"#gi" $file
sed -i "s#$1#$2#gi" "$file"

```
But nothing change after I use in this way:
```
huangyingw@laptop:~/myproject/git/test_fr$ fr ~/myproject/git/makefile/GNU_makefile_template temp
huangyingw@laptop:~/myproject/git/test_fr$ gs
# On branch master
nothing to commit (working directory clean)
```
the git status command tell me that, nothing changed. And I have actually open the target file to check.

---

### Post by Vaphell on 2012-09-29
test it without -i first

or in terminal with
echo "line that should be changed" | sed 's#a#b#g'
i always do that while finetuning sed expressions

edit: wait a minute, won't ~ get expanded to /home/username/ ?
in that case sed won't be able to find literal "~/file/something"
what do you have in file and what do you get if you *echo "$1"*?

do yourself a favor and normalize it, expand everything in file to full paths (sed "s#~/#$HOME/#g")
or do the reverse - leave ~, but explicitly replace /home/whatever/ with ~ in $1 ( sed "s#**${1/$HOME/\~}**#$2#g" )

---

### Post by huangyingw on 2012-09-29
> **Vaphell said:**
> test it without -i first

or in terminal with
echo "line that should be changed" | sed 's#a#b#g'
i always do that while finetuning sed expressions

edit: wait a minute, won't ~ get expanded to /home/username/ ?
in that case sed won't be able to find literal "~/file/something"
what do you have in file and what do you get if you *echo "$1"*?

do yourself a favor and normalize it, expand everything in file to full paths (sed "s#~/#$HOME/#g")
or do the reverse - leave ~, but explicitly replace /home/whatever/ with ~ in $1 ( sed "s#**${1/$HOME/\~}**#$2#g" )
Currently it works when the file content is 
```

huangyingw@laptop:~/myproject/git/test_fr$ cat makefile 
OBJECTS = bitsort.exe
include /home/huangyingw/myproject/git/makefile/GNU_makefile_template
LOCFLAGS = -I../bitsort

```
And the fr.sh is ```

huangyingw@laptop:~/bashrc$ cat fr.sh
#! /bin/sh
file=/home/huangyingw/myproject/git/test_fr/makefile
#sed -i "s/"$1"/"$2"/gi" $file
#sed -i 's/"$1"/"$2"/gi' $file
#sed -i "s#\"$1\"#\"$2\"#gi" $file
sed "s#$1#$2#g" "$file"

```
So, if wrapped in fr.sh, the special character like "~", and "..", could not be recognized by sed?

---

### Post by Vaphell on 2012-09-30
there is no problem with .. but when you type *fr.sh ~/some/stuff* bash automatically replaces ~ with /home/me

```
$ cat params.sh
#!/bin/bash
param=( "$@" )
for(( i=0; i<${#param[@]}; i++ )); do echo $((i+1)) ${param[$i]}; done
$ ./params.sh ~/test/ .. "~"
1 /home/me/test/
2 ..
3 ~
```
as you can see the script never gets to see ~, shell replaces it with /home/me before passing parameters to the script. You have to quote the string so bash ignores the expansion or change $1 back to ~ inside the script with "${1/$HOME/~}" (it will replace $HOME=/home/me with literal ~)

---

### Post by huangyingw on 2012-09-30
> **Vaphell said:**
> there is no problem with .. but when you type *fr.sh ~/some/stuff* bash automatically replaces ~ with /home/me

```
$ cat params.sh
#!/bin/bash
param=( "$@" )
for(( i=0; i<${#param[@]}; i++ )); do echo $((i+1)) ${param[$i]}; done
$ ./params.sh ~/test/ .. "~"
1 /home/me/test/
2 ..
3 ~
```
as you can see the script never gets to see ~, shell replaces it with /home/me before passing parameters to the script. You have to quote the string so bash ignores the expansion or change $1 back to ~ inside the script with "${1/$HOME/~}" (it will replace $HOME=/home/me with literal ~)

Great thanks for your explanation.
Finally, my working fr.sh is as bellow:
```

huangyingw@laptop:~/bashrc$ cat fr.sh
#! /bin/sh
FILE_POSTFIX=$HOME/bashrc/postfix
PRUNE_POSTFIX=$HOME/bashrc/prunefix
PRUNE_FILE=$HOME/bashrc/prunefile
find_params=();
prune_params=();
prune_files=();
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
while read suf
do
  prune_files+=( $or "-iname" "$suf" )
  or="-o"
done < "$PRUNE_FILE"
find "$1" "(" "${prune_params[@]}" "${prune_files[@]}" ")" -prune -o "(" "${find_params[@]}" "-o" "-iname" "makefile" ")" -type f | while read -r file
do
  sed -i "s#$2#$3#g" "$file"
done

```

---

