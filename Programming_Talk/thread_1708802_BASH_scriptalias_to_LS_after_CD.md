---
title: "BASH script/alias to LS after CD"
date: 2011-03-17
forum: Programming Talk
---

### Post by esmurdo on 2011-03-17
How do I program my BASH shell to automatically 'ls' after I've 'cd'?

```
cd $*;ls
```
doesn't work. I want to simply type:
```
cd dir
```
and have it automatically list contents after changing directory.

Any help?

---

### Post by DaithiF on 2011-03-17
put this function in your .bashrc:
```
function cd()
{
 builtin cd "$*" && ls
}
```

---

### Post by pl@yer on 2011-03-17
[edit]Oops noticed that DaithiF has already answered.

Only the last command in the alias gets the passed argument.
```

alias cd="echo changing to $1;cd $1;echo changing $1"

steve@steve-HP-Compaq-dc7100-CMT-PJ075UA:~$ cd Downloads/
changing to
changing Downloads/

steve@steve-HP-Compaq-dc7100-CMT-PJ075UA:~$ pwd
/home/steve

```

---

### Post by DaithiF on 2011-03-17
> **pl@yer said:**
> 
Only the last command in the alias gets the passed argument.

Hi, thats not strictly true.  when bash encounters an alias it just expands that alias, it doesn't pass it any arguments.

so in your example:
```
alias cd="echo changing to $1;cd $1;echo changing $1"
cd Downloads/
```

your cd Downloads command gets expanded to:
```
echo changing to $1;cd $1; echo changing $1 Downloads/

```$1 is empty, so it ends up as:
```
echo changing to ;cd; echo changing Downloads/
```
which i guess is why it looked to you like the last command was getting passed the argument.

---

### Post by pl@yer on 2011-03-17
Hey,
Thanks for the explanation. :)

---

