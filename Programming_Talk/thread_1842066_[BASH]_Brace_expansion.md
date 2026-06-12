---
title: "[BASH] Brace expansion"
date: 2011-09-10
forum: Programming Talk
---

### Post by ofnuts on 2011-09-10
If I do:
```
echo {a,b}
```I get ```
*a b*
```If I do:
```
x={a,b}
echo $x
```I get ```
*{a,b}*
```Besides the not-so-pretty```
x=$(echo {a,b})
```Is there a more elegant way to set a variable from a brace expansion?

---

### Post by dave01945 on 2011-09-10
if you do 

```
x={a,b}
echo $x
```

your output will be

```
{a,b}
```

as you already know

if you do

```
x={a,b}
eval echo $x
```

your output will be

```
a b
```

is this what you was looking for

---

### Post by ofnuts on 2011-09-10
> **dave01945 said:**
> if you do 

```
x={a,b}
echo $x
```your output will be

```
{a,b}
```as you already know

if you do

```
x={a,b}
eval echo $x
```your output will be

```
a b
```is this what you was looking for
I was looking for an eval-less solution... (and possibly, the rationale behind this restriction)

---

### Post by dave01945 on 2011-09-10
these pages should explain why eval is required


[why use eval with variable expansion](http://fvue.nl/wiki/Bash:_Why_use_eval_with_variable_expansion%3F)

[Bash shell brace expansion](semicrazy.wordpress.com/2009/09/09/fun-with-bash-shell-brace-expansion/)

---

### Post by ofnuts on 2011-09-10
> **dave01945 said:**
> these pages should explain why eval is required


[why use eval with variable expansion]("http://fvue.nl/wiki/Bash:_Why_use_eval_with_variable_expansion%3F")

[Bash shell brace expansion]("http://semicrazy.wordpress.com/2009/09/09/fun-with-bash-shell-brace-expansion/")
I don't get it... the first page says that brace expansion occurs before about everything else.

so x={1..3} should initialize x to "1 2 3"

As to the other page it says:

```
echo values_{$one,$two}values_1 values_2
```
but ```
[FONT=monospace]x=1
y=5
echo {$x..$y}
{1..5}
[/FONT]
```so this example must be working for the wrong reason.

---

### Post by dave01945 on 2011-09-11
> **ofnuts said:**
> 

```
echo values_{$one,$two}values_1 values_2
```
but ```
[FONT=monospace]x=1
y=5
echo {$x..$y}
{1..5}
[/FONT]
```

i think it is because the braces are expanded before the variables and because the braces contain variables there is nothing to expand the range until the variables have been expanded if we do

```
echo {1..5}
```

gives us 
[
```
1 2 3 4 5
```

also if we use a for loop

```
for x in {a,b}
do
     echo value$x
done
```

this gives the output

```
valuea
valueb
```

---

### Post by ofnuts on 2011-09-11
> **dave01945 said:**
> i think it is because the braces are expanded before the variables and because the braces contain variables there is nothing to expand the range until the variables have been expandedWhat I don't get is the difference of behavior betwen the list syntax (comma) and the sequence one (two dots):
```

=>echo a{1,3}
[I]a1 a3
[/I]=>echo a{1..3}
*a1 a2 a3*
```and
```

=>x=1
=>y=3
=>echo a{$x,$y}
[I]a1 a3
[/I]=>echo a{$x..$y}
*a{1..3}*
```I would expect either full expansion for both
```

=>x=1
=>y=3
=>echo a{$x,$y}
[I]a1 a3
[/I]=>echo a{$x..$y}
*a1 a2 a3*
``` or no expansion for either:
```

=>x=1
=>y=3
=>echo a{$x,$y}
[I]a{1,3}
[/I]=>echo a{$x..$y}
*a{1..3}*
```

---

### Post by dave01945 on 2011-09-11
the way i see it is that with the example

```
a=1
b=5
echo {$a,$b}

1 5
```

there is no expansion because they are separate values but with

```
a=1
b=5
echo {$a..$b}

{1..5}
```

the braces need expanding to fill in the number **2  3  5 ** and because the braces expanded before the variables are expanded then it gives the output as above

---

### Post by sisco311 on 2011-09-11
[http://wiki.bash-hackers.org/syntax/expansion/brace](http://wiki.bash-hackers.org/syntax/expansion/brace)

^^ explains brace expansion very well

---

### Post by ofnuts on 2011-09-11
> **sisco311 said:**
> [http://wiki.bash-hackers.org/syntax/expansion/brace](http://wiki.bash-hackers.org/syntax/expansion/brace)

^^ explains brace expansion very well

OK, got it. "{$x,$y}" is seen by brace expansion as a list of two strings, "$x" and "$y", so it's expanded to "$x $y" and the variable substitution that occurs later replaces $x and $y by their values, yielding "1 3". OTOH "{$x..$y}" is not seen as a range since $x and $y are just "$x" and "$y" so there is no expansion and it remains as "{$x..$y}" and when variable substitution occurs this yields "{1..3}".

Fun conclusion:
```

=>v1=value1
=>v2=value2
=>v3=value3
=>echo $v{1..3}
[B][I]value1 value2 value3
[/I][/B]
```

---

