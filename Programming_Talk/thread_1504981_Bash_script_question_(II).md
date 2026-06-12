---
title: "Bash script question (II)"
date: 2010-06-08
forum: Programming Talk
---

### Post by j_arquimbau on 2010-06-08
How can I do to set a determined number of leading zeros to rise a defined number of characters. Let me explain myself:

I have numbers from 1 to 1000, but I need them to count 9 characters, so it would be like:

000000001
...
000000013
...
000000104

(the number of leading zeros change).

And another question is: Is it possible to change the order of the numbers to an the order I want them to be? How?

i.e. 12345 to 53241
     62130 to 01236

Thank you!

---

### Post by blchinezu on 2010-06-08
i'm sure there is a much better method but here's my basic 'dumb' method:
```

fc () { for (( c=${#1}; c<**9**; c++ )); do return="${return}0"; done; echo ${return}$1; }
```You just call the function like this: **fc 2351** and the output will be **000002351**
if you want another number of leading zeros just change the *c<9* condition to another number

as for the second question: [wikipedia]("http://en.wikipedia.org/wiki/Permutation#Algorithms_to_generate_permutations")

---

### Post by j_arquimbau on 2010-06-08
Going to try. Thank you!

---

### Post by johnl on 2010-06-08
```

printf "%09d\n" 142

```

---

### Post by geirha on 2010-06-08
```
printf "%09d\n" 104
000000104
help printf

```

For the second question, I don't see any pattern to the ordering you want, though you can use substring expansion to separate each character of the string.
```
string=62130
echo "${string:0:1}" # first char
echo "${string:2:1}" # third char

```
[http://mywiki.wooledge.org/BashFAQ/073](http://mywiki.wooledge.org/BashFAQ/073)

---

### Post by DaithiF on 2010-06-08
Hi,
for the first requirement, a variation on the printf solutions, which generates the list in one go:
```
seq -f "%09g" 1 1000
```

for the second requirement, I think this does what you want:
```
$ for number in 12345 62130 
> do
> echo $number | sed -r 's/(.)(.)(.)(.)(.)/\5\3\2\4\1/'
> done
53241
01236

```

---

### Post by blchinezu on 2010-06-08
as i said.. there has to be an easier way to do it... there always is :)

---

### Post by geirha on 2010-06-08
> **DaithiF said:**
> Hi,
for the first requirement, a variation on the printf solutions, which generates the list in one go:
```
seq -f "%09g" 1 1000
```

I'd still use printf; it's defined by POSIX and is a built-in in bash. seq is non-standard.

```
printf "%09d\n" {1..1000}
```
In bash4 you can even generate that list with brace expansion
```
for i in {000000001..000001000}; do ...
```
[http://mywiki.wooledge.org/BashFAQ/018](http://mywiki.wooledge.org/BashFAQ/018)

---

### Post by apmcd47 on 2010-06-08
If you install ksh93 and check the man page it is possible to use ```
set -i var
``` with an option to make var an integer with a set number of leading zeroes. Zsh may also have this functionality.

As for the reversing of digits, the sed option looks good to me, but for an arbitrary number of characters or digits:
[PHP]a=12345
b=
c=
while -n "$a"
do
   b="${a#.}" # first char of $a
   c="$c$b"   # append to $c 
   a="${a/$b/} # remove $b from $a
done[/PHP]
Untested.

Andrew

---

### Post by kaibob on 2010-06-08
Here's another approach that will do what you want. The number and number order are input as command-line parameters. 

```
#!/bin/bash

printf $2 | while read -n 1 char ; do
  printf ${1:((--char)):1}
done

echo
```

For example,

> $ testscript 62130 53241
01236

---

