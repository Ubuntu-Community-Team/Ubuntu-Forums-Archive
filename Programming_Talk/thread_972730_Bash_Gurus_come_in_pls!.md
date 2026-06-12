---
title: "Bash Gurus come in pls!"
date: 2008-11-06
forum: Programming Talk
---

### Post by firdooze on 2008-11-06
I need help on changing my environment values in my bashrc. 

I am installing different versions of a program (Network sim 2) and the environment values will also be different. 

for example, if I run .. 

$ ns1 abc.tcl (it will run version 2.32)

and 

$ ns2 abc.tcl (it will run version 2.33)

how configure my bashrc to choose which environment values to use?

---

### Post by jpkotta on 2008-11-06
Your question is vague.  I will guess that you want either an alias or a function.

Aliases:
```
alias short='big_long_command -with -lots -of -options'
short data.dat
```

Functions:
```
function short()
{
    export ENV_VAR="blah"
    big_long_command "$@"
}
short data.dat
```

---

