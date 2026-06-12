---
title: "Shell script: problem with IF"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by daniel3ub on 2008-11-08
Hi, folks.

I need to do this:

```

var1=`cat lista_dirs.tmp | wc -l`
if [[ "$var1" > "$2" ]]

```

But if $var1 or $2 is greater than 9 I cannot get the IF to be true. I need to compare values, but aparently the script interprets just the first character from the number.

For example, this is what I get:
```
$var1=3 and $2=7
3>7 : FALSE

$var1=7 and $2=5
7>5 : TRUE

$var1=3 and $2=12
3>12 : TRUE

$var1=10 and $2=5
10>5 : FALSE
```

I know it's just a problem with quotation marks or other way to tell the script we are dealing with numbers. Could someone help, please??

Thanks a lot!

---

