---
title: "translate this simple ruby while loop to bash?"
date: 2010-04-22
forum: Programming Talk
---

### Post by Søren on 2010-04-22
hey all, i'm trying to learm bash and get the hang of control structures.
i want to do a while loop and decrement a variable so it counts down ...
basically i wanna do what this ruby code does in bash: 

```
a = 10
b = 0
while a > b
a -= 1
puts a
end


```so im trying to do the same thing in bash. i think bash uses -gt for >
 so far i've got

```
a=10; 
b=0; 
while [a -gt b]
do
$a = $a - 1
echo $a
done
```but this doesnt work. i think i the prob is to do with the decrement command?

---

### Post by RTrev on 2010-04-22
```

a=10
b=0
while [ $a -gt $b ]
do
  (( a-- ))
  echo $a
done

```

Just learning this stuff myself, so can't really explain why the syntax is so fussy. <g>

---

### Post by nikhilbhardwaj on 2010-04-22
> 
```
a=10; 
b=0; 
while [a -gt b]
do
$a = $a - 1
echo $a
done
```but this doesnt work. i think i the prob is to do with the decrement command?

few mistakes
try
```

a=10; 
b=0; 
while [ $a -gt $b ]
do
a=$((a - 1))
echo $a
done

```
you need to understand how to use variables
and howto do arithmetic in bash

if you know ruby/python/perl
i see little point in learning bash

---

### Post by RTrev on 2010-04-22
> **nikhilbhardwaj said:**
> 
if you know ruby/python/perl
i see little point in learning bash

Could you elaborate a bit on this?  I'm learning bash at the moment, and wonder if I should abort and go with Python which is already installed on my machine.  Thoughts would be appreciated.  TIA.

---

### Post by Søren on 2010-04-22
Thanks, nikhilbhardwaj. Guess I better get my head around this double parentheses concept.

Rtrev, after using Ruby bash certainly does seem quite awkward and ugly (doing loops and stuff anyway). I just figured I would learn bash cause it's the default on Ubuntu (and I think all unix machines?)

---

### Post by nikhilbhardwaj on 2010-04-22
> **RTrev said:**
> Could you elaborate a bit on this?  I'm learning bash at the moment, and wonder if I should abort and go with Python which is already installed on my machine.  Thoughts would be appreciated.  TIA.
IMHO you'll be better off learning python as a scripting language
it has a simpler syntax and is very easy to pick up
bash is quite primitive python supports more advanced concepts like object oriented programming
also python is platform independent it runs on all unixes windows etc 

having said that knowing the basic commands for bash can be a lifesaver in situations but for any complex script you should go with python/perl

in the end its your choice to learn any language you wish
best of luck

---

### Post by RTrev on 2010-04-22
Thanks nikhilbhardwaj.  I'll take a closer look at Python.  Appreciate the pointer.

---

