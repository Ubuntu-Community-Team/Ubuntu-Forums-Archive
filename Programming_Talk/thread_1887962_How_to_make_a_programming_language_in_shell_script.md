---
title: "How to make a programming language in shell script"
date: 2011-11-28
forum: Programming Talk
---

### Post by /bin/sh on 2011-11-28
Have you ever wanted to make your own programming language?
First you need to decide which programming language to build your programming language with. I will show how to do it in shell script. Follow the steps to a new programming language:
1. Chooce which programming language to build your programming language with.
2. Go to the core of the programming language you choose.
3. Make your own shell:
Lets say you chose shell script. DON'T just copy the text, read it thoroughly and make sure you understand every line of the code, read it so thoroughly that someone could come up to you and ask "what does that line mean" and you should be able to anwser that:
```

 #!/bin/sh

while :
do
  echo "__MYSHELL|>>>>> \c"; read line
  case $line in
    exit) exit ;;
    help) echo 'Commands: exit, cls, os' ;;
    cls) clear ;;
    os) uname ;;
    *) continue ;;
  esac
done

```
Save it as myshell.sh
Make it executable (the executable permission in the properties of the file).
Run it in bash:
root@ubuntu:~$ /path/to/myshell.sh
When it runs it will look like this:
__MYSHELL|>>>>> 
There are only 4 commands in this shell: exit, cls, help and os. You can expand the commands and if you need to you can make a command that loads an other file with the nessesary functions you need.

---

### Post by Habitual on 2011-11-28
> **/bin/sh said:**
> Have you ever wanted to make your own programming language?
No interpreter?

> **/bin/sh said:**
> ...if you need to you can make a command that loads an other file with the necessary functions you need.

a la "source /path/to/myshellfunctions.ext" ?

> **/bin/sh said:**
> ...make sure you understand every line of the code...

There's LOTS of code I don't understand. I have a basic idea of the *flow* of the logic, however the details of that process may not be familiar to me. I don't consider it necessary to ***understand*** every line of code. YMMV

> **/bin/sh said:**
> ...Go to the core of the programming language you choose

No distinction in your post between "programming language" and "shell scripting"?

Nice thought-provoking read.
I mean no offense.

---

### Post by Bodsda on 2011-11-28
....

---

