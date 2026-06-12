---
title: "expr wont work?"
date: 2009-03-05
forum: Programming Talk
---

### Post by Somiac on 2009-03-05
I'm learning bash script, and I've tried everything on this script

```
#!/bin/bash
echo "Number of Arguments are $#"
argAmount=$#
n=0
echo "File name is $#"
argz=1
while [ -n "$*" ]
do
echo "Parameter $argz $1"
shift
argz=expr[ $argz + 1 ]
done
```

On the argz=expr[ $argz + 1 ]

I've tried having no brackets, single quotes etc.
Each time I try something different on that line I either get output of

Number of Arguments are 2
File name is 2
Parameter 1 par1
Parameter expr $argz + 1 par2

Or

./argu: line 11: [: too many arguments
./argu: line 11: [: too many arguments

...

Now heres what I want to know.

When I do

```
#!/bin/bash
echo "Number of Arguments are $#"
argAmount=$#
n=0
echo "File name is $#"
argz=1
while [ -n "$*" ]
do
echo "Parameter $argz $1"
shift
argz=expr[ $argz + 1 ]
done
```

and type like
./bash argu par1 par2 > results.txt

it puts the correct results into the .txt file, but in the shell it shows those two errors I just gave..the 

./argu: line 11: [: too many arguments
./argu: line 11: [: too many arguments

Any help, and please explain why you do what you do so I can learn it also..thanks.

---

### Post by sujoy on 2009-03-05
try this:

```
 argz=`expr $argz + 1`
```

those are backquotes (the one with the tilde '~' key)

---

### Post by ghostdog74 on 2009-03-05
i suggest you take a look at the bash guide in my sig, Chapter 15 for some examples of expr usage.

---

### Post by Somiac on 2009-03-05
Thank you! All the documentation I read makes it look like a single quote!!

it works now!

and thanks for that bash link ghostdog, definitely bookmarking it.

---

