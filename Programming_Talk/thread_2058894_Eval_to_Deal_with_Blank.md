---
title: "Eval to Deal with Blank"
date: 2012-09-16
forum: Programming Talk
---

### Post by huangyingw on 2012-09-16
Hi,
   I have difficulty at disposing blank in eval shell expression.
   See my output bellow
   ```

huangyingw@laptop:~/myproject/git/java/algorithm temp$ find "`pwd`"
/home/huangyingw/myproject/git/java/algorithm temp/GetClosestToZero/.git/refs/heads/master
/home/huangyingw/myproject/git/java/algorithm temp/GetClosestToZero/.git/refs/tags
huangyingw@laptop:~/myproject/git/java/algorithm temp$ eval find "`pwd`"
find: `/home/huangyingw/myproject/git/java/algorithm': No such file or directory
find: `temp': No such file or directory

```
   How could eval to handle with blank?

---

### Post by huangyingw on 2012-09-16
> **huangyingw said:**
> Hi,
   I have difficulty at disposing blank in eval shell expression.
   See my output bellow
   ```

huangyingw@laptop:~/myproject/git/java/algorithm temp$ find "`pwd`"
/home/huangyingw/myproject/git/java/algorithm temp/GetClosestToZero/.git/refs/heads/master
/home/huangyingw/myproject/git/java/algorithm temp/GetClosestToZero/.git/refs/tags
huangyingw@laptop:~/myproject/git/java/algorithm temp$ eval find "`pwd`"
find: `/home/huangyingw/myproject/git/java/algorithm': No such file or directory
find: `temp': No such file or directory

```
   How could eval to handle with blank?
When I run find "`pwd`", it is ok, the " could handle the blank.
But using in eve find "`pwd`", I would get into trouble..

---

### Post by Vaphell on 2012-09-16
why on earth do you want to use 'eval' for anything? it's a dirty hack that has almost no legit use case.

also you don't have to embed $(pwd)/`pwd`, there is $PWD available.

---

### Post by huangyingw on 2012-09-16
> **Vaphell said:**
> why on earth do you want to use 'eval' for anything? it's a dirty hack that has almost no legit use case.

also you don't have to embed $(pwd)/`pwd`, there is $PWD available.
Because my script is written in the following way:
```

#!/bin/bash
TARGET='/export/home1/username/cscope_db/cscope.files'
FILE_POSTFIX=$HOME/bashrc/postfix
command_params=`cat ${FILE_POSTFIX}|{ read suf; echo -n "-name '*.$suf'";while read suf;do echo -n " -o -name '*.$suf'";done; }`
eval find $PWD/ $command_params -o -iname makefile |sed 's/\(["'\''\]\)/\\\1/g;s/^/"/;s/$/"/' > ${TARGET}
#cscope -kqR -i ${TARGET} 

```
And I found that the problem is caused by eval.
If I could walk around without eval, that would be great.

---

### Post by Vaphell on 2012-09-16
what happens when you run that find line without eval at all?
what's in $FILE_POSTFIX that you need to do that magic with command_params? what's the purpose of that?

you don't have to pipe *cat* to *while read*, while read can process files natively.
```
while read -r line; do echo $line; done < input_file
```


edit:
```
find_params=(); or="";
while read suf
do
  find_params+=( $or "-name" "*.$suf" )
  or="-o"
done < "$FILE_POSTFIX"
find "$PWD" "${find_params[@]}" -o -iname makefile

```
btw, if you want to put results in quotes you don't have to do s/^/"/; s/$/"/" substitution, you can use & symbol which holds the matched value, eg s/.*/"&"/

---

### Post by huangyingw on 2012-09-16
> **Vaphell said:**
> what happens when you run that find line without eval at all?
what's in $FILE_POSTFIX that you need to do that magic with command_params? what's the purpose of that?

you don't have to pipe *cat* to *while read*, while read can process files natively.
```
while read -r line; do echo $line; done < input_file
```
Without eval, the variable $command_params will not be expanded/evaluated, the find command will only deal with -o -iname makefile option.
The content of FILE_POSTFIX, are the \*.postfix file, that I want to find. For example, I am only interested in the file name like \*.java, \*.sh, \*.cc, etc.

---

### Post by huangyingw on 2012-09-16
> **huangyingw said:**
> Without eval, the variable $command_params will not be expanded/evaluated, the find command will only deal with -o -iname makefile option.
The content of FILE_POSTFIX, are the \*.postfix file, that I want to find. For example, I am only interested in the file name like \*.java, \*.sh, \*.cc, etc.
The content of the FILE_POSTFIX:
```

huangyingw@laptop:~/bashrc$ cat postfix 
py
xml
jsp
js
c
cc
cpp
hpp
java
h
sh
classpath
project
sql
xml.model
asm
inc
php
huangyingw@laptop:~/bashrc$ 

```

---

### Post by Vaphell on 2012-09-16
i updated my earlier post with possible solution before i saw your recent posts with clarifications

---

### Post by Vaphell on 2012-09-16
> Without eval, the variable $command_params will not be expanded/evaluated

of course it will be expanded, how do you think it's possible to use *find **$PWD** ... > **$TARGET*** at all? Bash sees no difference.
The problem is to make that particular expansion work for you. That variable is supposed to hold many params and many bash related chars which makes it a complete pain in the a$s to work with, because it requires careful escaping of characters that can break things (whitespace, *, etc)
my solution in post #5 opted for array where every single param is a separate 'word'

---

### Post by huangyingw on 2012-09-16
> **Vaphell said:**
> of course it will be expanded, how do you think it's possible to use *find **$PWD** ... > **$TARGET*** at all? Bash sees no difference.
The problem is to make that particular expansion work for you. That variable is supposed to hold many params and many bash related chars which makes it a complete pain in the a$s to work with, because it requires careful escaping of characters that can break things (whitespace, *, etc)
my solution in post #5 opted for array where every single param is a separate 'word'
Yes, great thanks.Your solution is great, I have updated mine to the following:
```

huangyingw@laptop:~/bashrc$ cat vitag.sh 
#!/bin/bash
TARGET='/export/home1/username/cscope_db/cscope.files'
FILE_POSTFIX=$HOME/bashrc/postfix
find_params=(); or="";
while read suf
do
  find_params+=( $or "-name" "*.$suf" )
  or="-o"
done < "$FILE_POSTFIX"
find "$PWD" "${find_params[@]}" -o -iname makefile |sed 's/\(["'\''\]\)/\\\1/g;s/.*/"&"/' > ${TARGET}
cscope -kqR -i ${TARGET} 
huangyingw@laptop:~/bashrc$ 

```
While, upset to say, our solution could handle the blank issue well, while, seems that the cscope could not handle file name with blank...

---

