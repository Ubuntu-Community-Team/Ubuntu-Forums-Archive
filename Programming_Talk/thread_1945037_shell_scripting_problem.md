---
title: "shell scripting problem"
date: 2012-03-22
forum: Programming Talk
---

### Post by DirkRenegade on 2012-03-22
Before I start, I am new to shell scripting (hence the dumb script below!) so I may be making a basic error. Anyhoo, here's the prob:

I put this in:

[B]#!/bin/sh
n=1
until test "$n" -gt "10"
do
    echo "hello $n"
    n=$[n+1]
done[/B]

I expected a print out of "hello 1-10" but instead I got this:

[B]hello $[n+1]
test: 7: Illegal number: $[n+1]
[/B]
this looped until i killed it with ctrl+c. what's going on? It should work shouldn't it:confused:? I have experience in c/c++ and I just thought this would be a simple increment operator. Please help as I really want to get into the nuts and bolts of linux.

---

### Post by DirkRenegade on 2012-03-22
Before I start, I am new to shell scripting (hence the dumb script below!) so I may be making a basic error. Anyhoo, here's the prob:

I put this in:

[B]#!/bin/sh
n=1
until test "$n" -gt "10"
do
echo "hello $n"
n=$[n+1][/B][B]
done
[/B]
I expected a print out of "hello 1-10" but instead I got this:

[B]hello $[n+1]
test: 7: Illegal number: $[n+1]
[/B]
this looped until i killed it with ctrl+c. what's going on? It should work shouldn't it? I have experience in c/c++ and I just thought this would be a simple increment operator. Please help as I really want to get into the nuts and bolts of linux.

sorry if you read the identical post below. I thought I'd re-post with a more specific title.

---

### Post by cortman on 2012-03-22
> **DirkRenegade said:**
> Before I start, I am new to shell scripting (hence the dumb script below!) so I may be making a basic error. Anyhoo, here's the prob:

I put this in:

[B]#!/bin/sh
n=1
until test "$n" -gt "10"
do
    echo "hello $n"
    n=$[n+1]
done[/B]

I expected a print out of "hello 1-10" but instead I got this:

[B]hello $[n+1]
test: 7: Illegal number: $[n+1]
[/B]
this looped until i killed it with ctrl+c. what's going on? It should work shouldn't it:confused:? I have experience in c/c++ and I just thought this would be a simple increment operator. Please help as I really want to get into the nuts and bolts of linux.

Change

```
#!/bin/sh
```

to

```
#!/bin/bash
```

Bourne shell doesn't have an until command.

---

### Post by DirkRenegade on 2012-03-22
many thanks...sorry for the ridiculous question!

---

### Post by DirkRenegade on 2012-03-22
solved!

---

### Post by codemaniac on 2012-03-22
hello DirkRenegade 
try something like below .

```
#!/bin/sh
n=1
until test "$n" -gt "10"
do
echo "hello $n"
n=`expr $n + 1`
done
```

---

### Post by DirkRenegade on 2012-03-22
many thanks..that solved it.

---

### Post by codemaniac on 2012-03-22
I see you are C/C++ guy , definately then you would love the C style syntaxes of bash.unfortunately you are using the bourne shell(#!/bin/sh) as your interpreter .
Bourne shell does not support C style increment operators like .
```
((n++))
```
try using bash (#!/bin/bash), it is rich and you would find many programming constructs that are missing in legacy bourne shell .Here is a bash shell script equivalent to your bourne one .
```

#!/bin/bash
n=1
until test "$n" -gt "10"
do
echo "hello $n"
((n++))
done
```

---

### Post by asmoore82 on 2012-03-22
Your logic makes perfect sense for programming; but shell scripting becomes a whole different beast :D.

A much more "shell-ish" way to accomplish the same thing would be this:
```
for n in {1..10}
do
    echo "hello $n"
done
```

Technically there is no counting involved in this loop, the variable n is stepping through a list of **text** values "1" through "10"

These "countless" text loops have countless uses:
```
for name in Steve Billy John
do
    echo "hello $name"
done
```

```
for n in 1st 2nd 3rd {4..10}th
do
    echo "$n hello"
done
```

:KS

---

### Post by codemaniac on 2012-03-22
> **cortman said:**
> Change

```
#!/bin/sh
```

to

```
#!/bin/bash
```

Bourne shell doesn't have an until command.

Are you sure mate , bourne shell doesnot have the until loop .
Bourne shell was just able to interpret an until loop on my shell.
 Have a try .
```
#!/bin/sh
n=1
until test "$n" -gt "10"
do
echo "hello $n"
n=`expr $n + 1`
done
```

---

### Post by cortman on 2012-03-22
> **DirkRenegade said:**
> many thanks...sorry for the ridiculous question!

Not ridiculous at all! Always feel free to ask. You can mark this thread [SOLVED] by using the thread tools in the upper right.

> **codemaniac said:**
> Are you sure mate , bourne shell doesnot have the until loop .
Bourne shell was just able to interpret an until loop on my shell.
 Have a try .
```
#!/bin/sh
n=1
until test "$n" -gt "10"
do
echo "hello $n"
n=`expr $n + 1`
done
```

Now that's odd. I am sure that Bourne doesn't interpret until loops- from "[Shell scripting in 24 hours]("http://www2.el.vgtu.lt/~mantas.paulinas/knyga.pdf")"-

> The while loop is perfect for a situation where you need to execute a set of commands while some
condition is true. Sometimes you need to execute a set of commands until a condition is true.
A variation on the while loop **available only in ksh and bash**, the until loop provides this functionality.

I'll look into this further... good catch!

---

### Post by sisco311 on 2012-03-22
In Ubuntu, /bin/sh is a symlink to DASH. [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

The until loop should work in any POSIX shell. [http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_09_04_11](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_09_04_11)

@OP
Check out:
[http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

EDIT:

BTW, threads merged.

---

### Post by cortman on 2012-03-22
> **sisco311 said:**
> In Ubuntu, /bin/sh is a symlink to DASH. [https://wiki.ubuntu.com/DashAsBinSh](https://wiki.ubuntu.com/DashAsBinSh)

The until loop should work in any POSIX shell. [http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_09_04_11](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/V3_chap02.html#tag_18_09_04_11)

@OP
Check out:
[http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

EDIT:

BTW, threads merged.

Thanks for the info, I must have been reading dated material.
But then how does changing #!/bin/sh to #!/bin/bash make the OP's script work?

---

### Post by sisco311 on 2012-03-22
In BASH, $[ EXPRESSION ] is a non-standard and obsolete form of arithmetic expansion. It still works in BASH, but the standardized form $(( EXPRESSION )) is preferred!

---

