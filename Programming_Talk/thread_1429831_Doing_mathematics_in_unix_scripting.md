---
title: "Doing mathematics in unix scripting"
date: 2010-03-14
forum: Programming Talk
---

### Post by hakermania on 2010-03-14
Is there a more accurate way to do mathematics in unix scripting?
I am using "expr" but for example if you tell lol=`expr 10 / 3`
lol will be 3 and no 3,33 and if you tell lol=`expr 10 / 60` 
lol will be 0 (!!!)
Is there any other command which is more accurate?;)

---

### Post by lykeion on 2010-03-14
you can use bc for floating point maths:

[http://hacktux.com/bash/math]("http://hacktux.com/bash/math")

---

### Post by kaibob on 2010-03-14
In addition to the bc utility, you can use awk for math calculations.

> $ awk 'BEGIN { print 20/3 }'
6.66667
$ 
$ awk 'BEGIN { printf "%.2f\n", 20/3 }'
6.67

One advantage of awk is that it half rounds. The bc utility appears not to:

> $ bc <<< 'scale=3 ; 20/3'
6.666

---

### Post by hakermania on 2010-03-14
Hmmm I think I need little help here:
```

alex@lol-pc:~/Desktop$ lol=5
alex@lol-pc:~/Desktop$ lil=2
alex@lol-pc:~/Desktop$ echo 'scale=2; $lol - $lil ' | bc > /home/alex/Desktop/qwe
(standard_in) 1: illegal character: $
(standard_in) 1: illegal character: $
alex@lol-pc:~/Desktop$ 

```

---

### Post by kaibob on 2010-03-14
Use double instead of single quotes:

> $ lol=5 ; lil=2 ; echo 'scale=2; $lol - $lil' | bc
(standard_in) 1: illegal character: $
(standard_in) 1: illegal character: $
$
$ lol=5 ; lil=2 ; echo "scale=2; $lol - $lil" | bc
3

The single quotes prevent variable expansion.

---

### Post by hakermania on 2010-03-14
> **kaibob said:**
> In addition to the bc utility, you can use awk for math calculations.



One advantage of awk is that it half rounds. The bc utility appears not to:

Similar problem:
```
alex@lol-pc:~/Desktop$ lol=5
alex@lol-pc:~/Desktop$ lil=2
alex@lol-pc:~/Desktop$ awk 'BEGIN { print $lol - $lil }'
0
alex@lol-pc:~/Desktop$
```

---

### Post by hakermania on 2010-03-14
> **kaibob said:**
> Use double instead of single quotes:



The single quotes prevent variable expansion.

Oh, nice ty

---

### Post by hakermania on 2010-03-14
Hmmmm...The program I need to make is like this:
```
read lol
read lil
echo "scale=2; $lol - $lil" | bc
```
so
```
lol=5 ; lil=2 ; echo "scale=2; $lol - $lil" | bc
```
cannot be used.Any other ideas?

---

### Post by kaibob on 2010-03-14
> **hakermania said:**
> Similar problem:
```
alex@lol-pc:~/Desktop$ lol=5
alex@lol-pc:~/Desktop$ lil=2
alex@lol-pc:~/Desktop$ awk 'BEGIN { print $lol - $lil }'
0
alex@lol-pc:~/Desktop$
```

Try this:

> lol=5 ; lil=2 ; awk 'BEGIN { print '"$lol"' - '"$lil"' }'
3

---

### Post by kaibob on 2010-03-14
> **hakermania said:**
> Hmmmm...The program I need to make is like this:
```
read lol
read lil
echo "scale=2; $lol - $lil" | bc
```

I tried this, and it worked fine for me.

---

### Post by falconindy on 2010-03-14
> **hakermania said:**
> ```
lol=5 ; lil=2 ; echo "scale=2; $lol - $lil" | bc
```
cannot be used.Any other ideas?
Because you're declaring the variables in the current shell **only**.

```
lol=5 lil=2 echo "scale=2; $lol - $lil" | bc
```
This still doesn't work because of a parsing error. However, this does work:
```
export lol=5 lil=2; echo "scale=2; $lol - $lil" | bc
```

edit: not sure what version of Bash allows this, but....
```
$ echo $(( 5.0 / 2.0 ))
2.5
```
/shrug

---

### Post by hakermania on 2010-03-15
> **falconindy said:**
> Because you're declaring the variables in the current shell **only**.

```
lol=5 lil=2 echo "scale=2; $lol - $lil" | bc
```
This still doesn't work because of a parsing error. However, this does work:
```
export lol=5 lil=2; echo "scale=2; $lol - $lil" | bc
```

edit: not sure what version of Bash allows this, but....
```
$ echo $(( 5.0 / 2.0 ))
2.5
```
/shrug

Could this be
```
read lol
read lil
echo $(( $lol / $lil ))
```
?????

---

### Post by ssam on 2010-03-15
if your script is complex enough to need floating point math it might be time to look at using a more advanced language.

---

### Post by falconindy on 2010-03-15
> **hakermania said:**
> Could this be
```
read lol
read lil
echo $(( $lol / $lil ))
```
?????

Sure, if the variables as entered as floating point. Also, I'm an idiot. This works in ZSH, not Bash. How often I forget what shell I'm using...

Use the bc solution.

---

