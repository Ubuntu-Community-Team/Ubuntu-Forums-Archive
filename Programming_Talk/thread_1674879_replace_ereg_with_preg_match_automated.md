---
title: "replace ereg with preg_match automated"
date: 2011-01-24
forum: Programming Talk
---

### Post by Humphreybas on 2011-01-24
Hey I try to fix the ereg errors (> **Deprecated**:  Function ereg() is deprecated in) in a php tool which is no longer maintained (phlogger).

On the php.net page of ereg someone suggested:
> FIND

ereg\((['"])(.*)(['"])([,\)])

REPLACE WITH

preg_match(\1/\2/\3\4I tried to do this with sed but got an error:
```
sed 's/ereg\((['"])(.*)(['"])([,\)])/preg_match(\1/\2/\3\4/g' old.php > new.php 
  
```-bash: syntax error near unexpected token `)'

I'm not that familiar with regexp and sed to see what's wrong with the brackets..What am I doing wrong?

And how should I use this for eregi ?

---

