---
title: "bash: test -f doesn't accept quoted tilde from variable"
date: 2015-10-22
forum: Programming Talk
---

### Post by trigone on 2015-10-22
hi,

i observed the following bash output:
```

>>> a=~/foo; [ -f $a ]; echo $?
0
>>> a="~/foo"; [ -f $a ]; echo $?
1
>>> a=~/foo; [ -f "$a" ]; echo $?
0
>>> a="~/foo"; [ -f "$a" ]; echo $?
1

```
my question is: in the case of files with whitespace in the name, is there a (simple) way to put its path in a variable, using the tilde, and making tests, readlink, etc, accept them as actual paths, and not, apparently, items inside /current/working/dir/~/. of course i suppose that individual escaping of whitespace with counterslash could work, but i wonder if there's an other way.

thanks in advance :)

---

### Post by Lars Noodén on 2015-10-22
The a=~/foo gets expanded by the shell before it is assigned to the variable , a="~/foo" doesn't.  The latter means to take the string literally.  Try adding an *echo $a;* to each line and see.

---

### Post by trigone on 2015-10-22
yes, i thought so; if you want, my question is, how to (easily) keep getting the effects of the interpretation of the shell of ~, even with a file with a name containing whitespace.

---

### Post by Lars Noodén on 2015-10-22
The way you mentioned above should work: use backslashes to escape the spaces.

---

### Post by Vaphell on 2015-10-23
you can also leave the tilde outside the quotes for it to work, but the best solution imo would be to stop depending on shell unrolling the ~ shortcut and use $HOME that always works instead.

---

### Post by trigone on 2015-10-25
ah yes, $HOME is a great idea, much more flexible, thanks!

---

