---
title: "command-line mathematics"
date: 2007-05-05
forum: Programming Talk
---

### Post by munkyeetr on 2007-05-05
I am curious if there is anything standard in the bash shell or the terminal that allows you to perform simple mathematics from the command line.

I am currently writing some c programs that will allow me to evaluate equations using syntax like:

```

add 10 12.34
22.34

sub 30.20 16 4 
10.20

```

I am also creating modules for  division, multiplication and percent finding.

I guess I have a couple questions:

Is there anything like this already available?
Would there be interest in having this available?

I have already compiled and am running the addition module, but I am pretty new to C programming, so if anyone is interested in looking at the source and giving some input, I can make it available.

Thanx

---

### Post by aanderse on 2007-05-05
> **munkyeetr said:**
> I am curious if there is anything standard in the bash shell or the terminal that allows you to perform simple mathematics from the command line.

I am currently writing some c programs that will allow me to evaluate equations using syntax like:

```

add 10 12.34
22.34

sub 30.20 16 4 
10.20

```

I am also creating modules for  division, multiplication and percent finding.

I guess I have a couple questions:

Is there anything like this already available?
Would there be interest in having this available?

I have already compiled and am running the addition module, but I am pretty new to C programming, so if anyone is interested in looking at the source and giving some input, I can make it available.

Thanx

if you're doing this for a learning exercise in c then good stuff, that's a neat idea.
if you actually just want to be able to do simple arithmetic in bash though, the syntax is like so:
echo $(( 5+4 ))

good luck

---

### Post by allyn on 2007-05-05
i use the dc command for quick arithmetic.  uses reverse polish notation.  there's also a command bc.

---

### Post by munkyeetr on 2007-05-05
Nice. thank for that;  echo works well.

I like to screw around, so I'll probably keep writing the c modules, and may even write a wrapper script for echo to do math.

Cheers.

---

### Post by chriscando on 2007-05-05
Yea a little wrapper script would be nice, then you can just put it in your PATH and use 'add'  and 'sub' commands like you mentioned above.

something like this (for add or sub)
```
#!/bin/bash

if [ $# -lt 1 ]; then
        echo "usage: $0 <value1> <value2> [<valueN>]"
        exit 0
fi

sum=0
for arg in $@
do
        sum=$(($sum+$arg))
done

echo $sum
```

but this wont do decimals.. hmmm

---

### Post by jfinkels on 2007-05-05
The interactive python interpreter does math pretty well.

---

### Post by sdide on 2007-05-05
~$ echo  10 + 12.34 | bc 
22.34

Im not sure how to understand 
"sub 30.20 16 4 
10.20" 

does that mean "sub" takes arg1 and then subtracts all futher arguments (eg, arg2, arg3, etc.. ) 

anyways

~$ echo 30.20 - 16 - 4 | bc 
10.20 

if you like to introduce: 
sum = arg1 + arg2 + arg3 + ... + argN 
and
sub = arg1 - (arg2 + arg3 +  ...  + argN) 


then making with your favorite editor (vi of course)

~# vi /usr/local/bin/sum
echo $@ | sed 's/ / + /g' | bc

and 

~# vi /usr/local/bin/sub
echo $@ | sed 's/ / - /g' | bc

---

### Post by bapoumba on 2007-05-05
Thread moved to "Programming Talk".

---

### Post by Nikron on 2007-05-05
> **jfinkels said:**
> The interactive python interpreter does math pretty well.

seconded.  It's great for some quick calculations

---

### Post by Tomosaur on 2007-05-05
You could use the 'let' command:

```

let i=5+7 && echo $i

```

---

### Post by amo-ej1 on 2007-05-07
Even octave works from the command line which offers you functionality up to matrix calculations ... and I also second bc. Advantage is that these offer better support (arbitrary precision etc) over a bash echo

---

