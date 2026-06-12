---
title: "[SOLVED] Help with sed"
date: 2008-05-24
forum: Programming Talk
---

### Post by CSEatOSU on 2008-05-24
I am trying to output the processor type and I need help with the sed command.  This is what I have so far:

```
cat /proc/cpuinfo | grep -m1 'model name' | sed -e 's/model name.*: //'

```

In the cpuinfo file, the line looks like this

```
model name	: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz

```

So the command output:

```
% cat /proc/cpuinfo | grep -m1 'model name' | sed -e 's/model name.*: //'
Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
```

but I want it to only output:

```
Intel(R) Core(TM)2 Duo CPU
```

How do I remove the last bit after CPU?

Thanks

---

### Post by LaRoza on 2008-05-24
> **CSEatOSU said:**
> I am trying to output the processor type and I need help with the sed command.  This is what I have so far:

```
cat /proc/cpuinfo | grep -m1 'model name' | sed -e 's/model name.*: //'

```

In the cpuinfo file, the line looks like this

```
model name	: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz

```

So the command output:

```
% cat /proc/cpuinfo | grep -m1 'model name' | sed -e 's/model name.*: //'
Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
```

but I want it to only output:

```
Intel(R) Core(TM)2 Duo CPU
```

How do I remove the last bit after CPU?

Thanks

Add another | and sed? It worked for me.

---

### Post by CSEatOSU on 2008-05-24
> **LaRoza said:**
> Add another | and sed? It worked for me.

So what would I put for the second sed regexp?

HA! I got it

```
cat /proc/cpuinfo | grep -m1 'model name' | sed -e 's/model name.*: //' | sed -e 's/     .*//'

```

---

### Post by LaRoza on 2008-05-24
> **CSEatOSU said:**
> So what would I put for the second sed regexp?


Exactly. I didn't give code because I my output is formatted differently and the re would have been different.

---

### Post by CSEatOSU on 2008-05-25
Ok so I've changed the solution to using awk like this:
```
% awk '/model name/' /proc/cpuinfo | sed -e 's/model name.*: //' | sed -e 's/  .*//'
Intel(R) Core(TM)2 Duo CPU
Intel(R) Core(TM)2 Duo CPU

```

How would I get it to only print out the second occurrence? aka my 2nd CPU
```
& awk ...
Intel(R) Core(TM)2 Duo CPU
```

---

### Post by odyniec on 2008-05-25
You can do it with just awk:

```
awk -F '[ :][ :]+' '/^model name/ { print $2; exit; }' /proc/cpuinfo
```

A quick breakdown of the command:
```
-F '[ :][ :]+'   -- extract fields separated by a sequence of at least two spaces or colons
/^model name/    -- work with lines that begin with "model name"
print $2; exit;  -- display the second field and exit immediately
```

---

### Post by CSEatOSU on 2008-05-25
> **odyniec said:**
> You can do it with just awk:

```
awk -F '[ :][ :]+' '/^model name/ { print $2; exit; }' /proc/cpuinfo
```

A quick breakdown of the command:
```
-F '[ :][ :]+'   -- extract fields separated by a sequence of at least two spaces or colons
/^model name/    -- work with lines that begin with "model name"
print $2; exit;  -- display the second field and exit immediately
```

Ok, I see how that works, great but the /proc/cpuinfo file contains two lines of the form:
```
model name	: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
```
I would like to retrieve both of them separately.  I'm doing this so I can print the info for CPU1 then print the info for CPU2, using separate scripts.

---

### Post by geirha on 2008-05-25
I only have one CPU, so I made a test-file:
```
$ cat test-file
some other field : nah
model name  : Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz first
model name  : Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz second

```
And then, using an array:
```
$ IFS=$'\n' A=( $(awk -F ': ' '/^model name/ { print $2; }' test-file) )
$ echo ${A[0]}
Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz first
$ echo ${A[1]}
Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz second

```
IFS=$'\n' says that: in the following command, use \n as field seperator, instead of any whitespace.

---

### Post by ghostdog74 on 2008-05-25
you can do all in awk
```

awk -F '[ :][ :]+' '/^model name/ { 
  print $2; 
  # do something 
  # if you want to store in array
  arr[++c] = $2
}END {
  # call the array
  for ( i=1 ; i<=c ; i++ ) {
    print arr[i],i
  }

}' /proc/cpuinfo

```

---

### Post by CSEatOSU on 2008-05-26
I know I could do it like that, not hard to figure out since I have a degree in computer science.  But I'm wanting to make it an easy one liner because it's being used in my .conkyrc file as

```
${pre_exec awk '/model name/' /proc/cpuinfo | sed -e 's/model name.*: //' | sed -e 's/  .*//'}
```
So, ideally I'd like to be able to use something I can put in the .conkyrc file to print each processor separate.  For instance...
```
${pre_exec awk <find and print CPU1>} ${more_stuff}
${pre_exec awk <find and print CPU2>} ${more_stuff}
```

---

### Post by geirha on 2008-05-26
Ah, then maybe: 
```

awk -F ': ' '/^model name/ { print $2; }' /proc/cpuinfo | head -1
awk -F ': ' '/^model name/ { print $2; }' /proc/cpuinfo | tail -1

```

---

### Post by CSEatOSU on 2008-05-26
> **geirha said:**
> Ah, then maybe: 
```

awk -F ': ' '/^model name/ { print $2; }' /proc/cpuinfo | head -1
awk -F ': ' '/^model name/ { print $2; }' /proc/cpuinfo | tail -1

```

YES, thank you very much.  This is what I've been looking for!

Slightly modified:
```
awk '/^model name/' /proc/cpuinfo | sed -e 's/model name.*: //' | sed -e 's/  .*//' | head -1
awk '/^model name/' /proc/cpuinfo | sed -e 's/model name.*: //' | sed -e 's/  .*//' | tail -1
```

---

### Post by ghostdog74 on 2008-05-26
if that's the case, you don't even need head or tail
```

awk -F ': ' '/^model name/ { print $2; exit}' /proc/cpuinfo
awk -F ': ' '/^model name/ {l=$2}END{print l}' /proc/cpuinfo

```

---

