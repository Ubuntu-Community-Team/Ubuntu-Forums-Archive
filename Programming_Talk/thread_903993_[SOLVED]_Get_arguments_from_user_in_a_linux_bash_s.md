---
title: "[SOLVED] Get arguments from user in a linux bash script"
date: 2008-08-28
forum: Programming Talk
---

### Post by niccholaspage on 2008-08-28
I am writing some scripts and I need to get an argument from the user.Like if someone wants to use the mv command,you would type mv <old file> <new file> and I don't know how to do something like that.Can anyone tell me how?

---

### Post by monkeyking on 2008-08-28
The name of your program is denoted by

$0
first argument is $1 on so forth

so 

prog.bash arg1

$0=prog.bash
$1=arg1


if you want to check for existance use -z in af if cond

if [ -z $1 ]; then
   echo "no args given"
fi

---

### Post by ghostdog74 on 2008-08-28
> **niccholaspage said:**
> I am writing some scripts and I need to get an argument from the user.Like if someone wants to use the mv command,you would type mv <old file> <new file> and I don't know how to do something like that.Can anyone tell me how?

see [here](http://tldp.org/LDP/abs/html/internal.html) and go to getopts.

---

### Post by niccholaspage on 2008-08-28
Thanks monkeyking.And thanks ghostdog74 for the guide:P

---

