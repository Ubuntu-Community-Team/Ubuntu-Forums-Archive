---
title: "awk : why do these two give a different o/p for the first line ?"
date: 2014-05-16
forum: Programming Talk
---

### Post by IAMTubby on 2014-05-16
Hello,
This question is regarding using the FS (Field separator) option in awk

Why is the output different for the below commands,
**1.** IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ **[COLOR=#800000]head -n 2 /etc/passwd | [/COLOR][COLOR=#800000]awk 'BEGIN{FS=":"}{OFS="--";print $1, $2}'[/COLOR]**
[COLOR=#800000][B]0--0--root
1--1--daemon[/B][/COLOR]


**2.**IAMTubby@IAMTubby-Inspiron-1545:~/Desktop$ **[COLOR=#800000]head -n 2 /etc/passwd | awk '{FS=":";OFS="--"; print $3, $4, $5}'[/COLOR]**
[B][COLOR=#800000]----
1--1--daemon[/COLOR][/B]

According to me, the first output is what I'm looking for and the second output is incorrect.
My question is, why isn't the FS=":" taken into account for the first line of /etc/passwd in [COLOR=#800000]**2**[/COLOR] above ?
Doesn't everything inside the action block {} run for EVERY line ?

Thanks.

---

### Post by spjackson on 2014-05-16
In the 2nd case, on line 1 of input, the line has been parsed and $3, $4, $5 assigned before you enter the action block, i.e. before you assign FS. You need to do the assignment in a BEGIN block, e.g.
```

head -n 2 /etc/passwd | awk 'BEGIN {FS=":";OFS="--";} {print $3, $4, $5}'

```

---

### Post by IAMTubby on 2014-05-17
> **spjackson said:**
> In the 2nd case, on line 1 of input, the line has been parsed and $3, $4, $5 assigned before you enter the action block, i.e. before you assign FS. You need to do the assignment in a BEGIN block, e.g.
Thanks spjackson. Shall follow assignment inside the BEGIN block.

---

