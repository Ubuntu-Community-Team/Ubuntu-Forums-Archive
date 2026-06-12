---
title: "Bash - is anything wrong with this shorthand if statement"
date: 2013-05-07
forum: Programming Talk
---

### Post by CaptainMark on 2013-05-07
I've been messing around with bash scripts for a while (nothing too heavy, just casual) and I never knew of this shorter way of writing a simple if statement, obviously it's only for really simple ones, defining a single variable or something like that.
I was surprised I've never seen it before because it looks so simple and that made me wonder if there's something wrong with it, perhaps it has some more sinister potential problem that I don't know about, so I'll ask you guys.
Basically, is```
if [ -d $HOME ]; then
    echo "Well done"
else
    echo "You are homeless"
fi
```the same as```
[ -d $HOME ] && echo "Well Done" || echo "You are homeless"
```

---

### Post by schragge on 2013-05-07
Yes, they are essentially equivalent. See [http://tldp.org/LDP/abs/html/list-cons.html](http://tldp.org/LDP/abs/html/list-cons.html)

Just don't forget to quote the variable being tested
```
test -d "$HOME" && echo Well done || echo You are homeless
``` or use double-brackets
```
[[ -d $HOME ]] && echo Well done || echo You are homeless
```

---

### Post by apmcd47 on 2013-05-07
> **schragge said:**
> Yes, they are essentially equivalent. See [http://tldp.org/LDP/abs/html/list-cons.html](http://tldp.org/LDP/abs/html/list-cons.html)

Essentially equivalent, but not the same. Consider:
```
[ -d "{HOME}" ] && echo "Well done" && false || echo "You are homeless"
Well done
You are homeless
```
Because there is a "false" command there the last echo is executed regardless of the outcome of the condition. As the above link says this construct is useful for constructing a chain of commands where you want to stop after a non-zero value is returned, ie a failure occurs. Quite often I use one or the other as in
```
 test $# -lt 2 && { echo "$USAGE" 1>&2; exit 1; }

```
in my scripts, or for testing the outcome of some condition:
```
alias yes="echo Yay!"
alias no="echo BOO!"
some-condition && yes || no
```
Andrew

---

### Post by CaptainMark on 2013-05-07
Thanks, good to know. I'll certainly use this for some simple statements, it looks nice and tidy

---

### Post by Vaphell on 2013-05-07
&& (AND) and || (OR) operators simply follow rules of boolean logic, where success is considered TRUE and failure is considered FALSE
in case you are not familiar with them, they are somewhat similar to arithmetic * and + operators, where 0 = FALSE and positive non-0 number = TRUE
```
OR ||:
non-0 + non-0 = non-0         TRUE || TRUE = TRUE
non-0 + 0 = non-0             TRUE || FALSE = TRUE
0 + 0 = 0                     FALSE || FALSE = FALSE
AND &&:
non-0 * non-0 = non-0         TRUE && TRUE = TRUE
non-0 * 0 = 0                 TRUE && FALSE = FALSE
0 * 0 = 0                     FALSE && FALSE = FALSE
```

**a && b || c** skips parts of the expression because
**FALSE && whatever** = FALSE -> you can skip *whatever*
**TRUE || whatever** = TRUE -> you can skip *whatever*

a && b || c  is done left from right, so the order of operations will be like this: (a && b ) || c
1. if a** is FALSE, *b* is skipped (*FALSE && whatever* will be false either way), so you get **FALSE || c** and need *c* because the expression can go either way
2. if *a* is TRUE, you need to calculate *a&&b* because it can go either way depending on value of *b*. Once you have that *a&&b* value you look at *value||c* and see if you need to run c to evaluate the whole (note that if *b* returns FALSE, you will run *c* part, because a&&b will yield FALSE and *FALSE || c* can go either way depending on value of *c*)
```
$ true && true || echo fail
$ true && false || echo fail
fail
```

---

