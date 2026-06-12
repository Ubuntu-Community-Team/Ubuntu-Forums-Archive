---
title: "Variable Substitution"
date: 2008-05-14
forum: Programming Talk
---

### Post by rj175 on 2008-05-14
I'm trying to find out about variable substitution and dont exactly know where to look for information. I've tryed google but to not much success. Any ideas? Or even how to setup/use variable substitution's.

Thanks

---

### Post by pmasiar on 2008-05-14
is it in any language known to man? :-)

---

### Post by ghostdog74 on 2008-05-14
i will assume you meant the shell(bash)
See [here]("http://tldp.org/LDP/abs/html/varsubn.html")

---

### Post by natirips on 2008-05-14
If you want to swap two variables ("a" and "b" for example), the simpelest principle is the following:

temp=a
a=b
b=temp

Where temp only _saves_ "a" as it is overwritten in the second line, and can be deleted/ignored/recycled(re-used) after the swapping is done.

---

