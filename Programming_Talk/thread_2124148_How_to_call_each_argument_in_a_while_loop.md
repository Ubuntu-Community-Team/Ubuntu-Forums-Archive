---
title: "How to call each argument in a while loop"
date: 2013-03-10
forum: Programming Talk
---

### Post by toad3000 on 2013-03-10
I want to access each argument so I tried doing ${$counter2}} because that was my first intuition but I keep getting bad substitution error. Does anyone know how to do this? 

```
typeset -i counter=1typeset -i counter2=1
while [ $counter2 -le $# ] 
do
cat ${$counter2} | while read line 
do
echo "$counter. $line"
counter=counter+1
done
counter2=counter2+1
done



```

---

### Post by r-senior on 2013-03-10
Are you just trying to access command line arguments? Can we assume you want to write this in Bash shell script?

*test.sh*
```
#!/bin/bash

for arg in "$@"
do
    echo $arg
done

```

```

$ ./test.sh a b c
a
b
c

```

---

### Post by ofnuts on 2013-03-10
You don't really need this. If you want to iterate on your arguments, you can use:

```

for arg in "$@"
do
    echo "Some arg: $arg"
done

```

The quotes around "$@" are important...

---

### Post by sisco311 on 2013-03-10
If the 'in words...' part is ommited then in "$@" is assumed. So you can simply run: ```
for arg
do
    ...
done
```

---

### Post by toad3000 on 2013-03-10
is it possible to accomplish this using a while loop?

---

### Post by ofnuts on 2013-03-10
> **sisco311 said:**
> If the 'in words...' part is ommited then in "$@" is assumed. So you can simply run: ```
for arg
do
    ...
done
```

nice_bash_tricks_I_know++;

---

### Post by sisco311 on 2013-03-10
> **ofnuts said:**
> nice_bash_tricks_I_know++;

It's standard. Here are the POSIX specs: [http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html)

---

### Post by sisco311 on 2013-03-10
> **toad3000 said:**
> is it possible to accomplish this using a while loop?

Yes. But why?

---

### Post by toad3000 on 2013-03-10
because I tried many ways to accomplish this using a while loop and It wasn't working. I made a counter and I tried ${$counter} but I get bad substitutional error.

---

### Post by ofnuts on 2013-03-10
> **sisco311 said:**
> It's standard. Here are the POSIX specs: [http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/contents.html)
But I assume so of course...  a "trick" is standard. A "hack" is not.

---

### Post by Vaphell on 2013-03-10
```
 i=1; while (( i<=$# )); do echo "\$$i: ${!i}"; ((i++)); done
```

```
$ ./arg a bb ccc dddd
$1: a
$2: bb
$3: ccc
$4: dddd
```

or
```
while (( $# )); do echo "$1"; shift; done;
```
this one is destructive (consumes params)

---

### Post by sisco311 on 2013-03-11
> **toad3000 said:**
> because I tried many ways to accomplish this using a while loop and It wasn't working. I made a counter and I tried ${$counter} but I get bad substitutional error.

Oh, I see. You are trying to use indirect expansion.  As you can see from the example posted by Vaphell, the format of indirect expansion is, ${!name}:
```

name=1
echo "\$$name is: ${!name}"

```

For more details please check out BashFAQ 006 (link in my signature) and the `Parameter Expansion' section from the man page of bash:
```
man bash | less '+/^ +Parameter Expansion'
```

---

