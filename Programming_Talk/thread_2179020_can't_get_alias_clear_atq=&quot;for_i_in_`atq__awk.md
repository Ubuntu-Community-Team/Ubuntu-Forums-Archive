---
title: "can't get alias clear_atq=&quot;for i in `atq | awk '{print $1}'`;do atrm $i;done&quot; to work"
date: 2013-10-06
forum: Programming Talk
---

### Post by sam_baker2 on 2013-10-06
hi,
I am trying to make an alias that will clear out all of the queue of the "at" commands.
This works just fine when I post it into a terminal:
```
for i in `atq | awk '{print $1}'`;do atrm $i;done
```

but when I try to make an alias out of it:
```
alias clear_atq="for i in `atq | awk '{print $1}'`;do atrm $i;done"
```

I get this error when I type "clear_atq" in the terminal: 
```
bash: syntax error near unexpected token `460'
```
"460" being one of the "at" queue numbers.

I think it has something to do with the number of  > "   '   `
 that are in the alias, but don't know.

Thanks

---

### Post by Lars Noodén on 2013-10-06
Here's what I got from the above:

```

alias clear_atq='for i in $(atq | awk "{print \$1}");do atrm $i;done'

```

This is complicated because it is intepreted in two parts.  First as it is made an alias.  Then again as the alias is run.

---

### Post by Vaphell on 2013-10-06
don't bother with alias and write a function or a script instead. Aliases are for really simple stuff and you are trying to fit a square peg into a round hole.
function:
```
clear_atq() { for i in $( atq | awk '{ print $1 }' ); do atrm $i; done; }
```

---

### Post by sam_baker2 on 2013-10-06
Thanks guys,
The alias works and I am going to look into making a script too.

---

