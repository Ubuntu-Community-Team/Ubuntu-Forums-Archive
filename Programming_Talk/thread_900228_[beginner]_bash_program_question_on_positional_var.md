---
title: "[beginner] bash program question on positional var"
date: 2008-08-25
forum: Programming Talk
---

### Post by BLo on 2008-08-25
Hi,
I'm no expert programmer, far from it - especially in bash. I've had a look around and can't figure how to do what I want specified below or if I even can.

for example I want to run my program going something like: 

./myprog.sh one two three

in my program I have:

count=0
myvar="\$$count"


and what I want to be able to do is use myvar to gain access to the positional variable (i.e $0) so that when I echo myvar, it should print:
one


Ive tried a many combinations of quotations and cant get it working, any help is much appreciated

---

### Post by ghostdog74 on 2008-08-25
```

echo "File name: $0"
echo "First parameter: $1"
echo "Second parameter: $2"
echo "All parameters: $@"

```

---

### Post by rogeriopvl on 2008-08-25
```
myvar=$1
echo $myvar
```

this will output: one

---

### Post by amo-ej1 on 2008-08-25
Well in short, don't. From a programming standpoint it's a very bad idea if you need to use those tricks to get to your variables. Typically one will use arrays for this (man bash and scroll down to the Arrays section) or use getopt (man getopt) when talking about command line parsing.

---

### Post by BLo on 2008-08-25
I think ghostdog74 & rogeriopvl are missing my point. 
I'm quite aware that I can go: 

myvar=$1
echo $myvar

Basically depending on a positional variable's value and some algorithm I want to pull out a different positional variable. 

I know I can just put it all into an array and then be able to any manipulation but I was just seeing if its possible without me having to do this

---

### Post by ghostdog74 on 2008-08-25
```


count=1
myvar="\$$count"
eval echo $myvar

```

---

### Post by BLo on 2008-08-25
thank you ... eval is what im after

---

### Post by drubin on 2008-08-26
BLo You miss that from php right?

---

