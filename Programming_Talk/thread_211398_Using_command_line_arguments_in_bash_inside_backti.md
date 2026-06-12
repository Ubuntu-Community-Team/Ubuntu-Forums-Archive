---
title: "Using command line arguments in bash inside backticks"
date: 2006-07-08
forum: Programming Talk
---

### Post by Guest1234 on 2006-07-08
I'm trying to create the following alias:
cd.n <number of directories to go back>

For example, if I'm in the directory:
~/programming/java/workspace

and I'll type "cd.n 2"
I'll get to ~/programming

What I tried to do is:
alias cd.n='for i in `seq 1 $1`; do cd .. done'

the problem is that somehow the bash ignores the $1, probably because it is inside backticks.

If I run from the command line:
for i in `seq 1 2`; do cd .. done

Then it works but when I try to use the command line argument it doesn't.

I tried to escape the dollar sign with '\' but it didn't
work, how can I use a command line argument inside backticks?

---

### Post by hegenious on 2006-07-08
> What I tried to do is:
alias cd.n='for i in `seq 1 $1`; do cd .. done'

you missed out a ; (semicolon) between .. and done

I did it like this and it worked fine:
alias cd.n='for i in `seq 1 $1`; do cd .. ;  done'

hth

---

### Post by Ragazzo on 2006-07-08
As far as I know you can't pass arguments to aliases in Bash shell. You could use a function:

cd.n () { for i in `seq 1 $1`; do cd .. ; done }

---

### Post by Guest1234 on 2006-07-14
Thanks Ragazoo it worked! :)

---

