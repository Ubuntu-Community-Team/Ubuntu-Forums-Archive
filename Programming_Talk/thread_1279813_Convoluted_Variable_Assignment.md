---
title: "Convoluted Variable Assignment"
date: 2009-10-01
forum: Programming Talk
---

### Post by Matuku on 2009-10-01
I'm relatively new at Bash programming so I'm probably just violating a very simple rule which makes this unable to work. What I'm trying to do is generate a list of the form:

```

Adam 1
Adam 2
Adam 3
...

Brent 23
Brent 24
...
Coby 31
Coby 32

```

The script I made for this is (at the moment it's still a work in progress so should only output "Adam 6 Brent 40 Coby 35":
```

#!/bin/bash

name1="Adam"
name2="Brent"
name3="Coby"
${name1}Number=6
${name2}Number=40
${name3}Number=35

for name in $name1 $name2 $name3
do
  for number in $"${name}"Number
    do
      echo "$name $number"
    done
  echo
done


```

But I keep getting this output (Test1 is the filename):
```

./Test1: line 27: AdamNumber=6: command not found
./Test1: line 28: BrentNumber=40: command not found
./Test1: line 29: CobyNumber=35: command not found
Adam AdamNumber

Brent BrentNumber

Coby CobyNumber

```

Why does it think the NameNumber variables are commands? What am I doing wrong?

---

### Post by Arndt on 2009-10-01
> **Matuku said:**
> I'm relatively new at Bash programming so I'm probably just violating a very simple rule which makes this unable to work. What I'm trying to do is generate a list of the form:

```

Adam 1
Adam 2
Adam 3
...

Brent 23
Brent 24
...
Coby 31
Coby 32

```

The script I made for this is (at the moment it's still a work in progress so should only output "Adam 6 Brent 40 Coby 35":
```

#!/bin/bash

name1="Adam"
name2="Brent"
name3="Coby"
${name1}Number=6
${name2}Number=40
${name3}Number=35

for name in $name1 $name2 $name3
do
  for number in $"${name}"Number
    do
      echo "$name $number"
    done
  echo
done


```

But I keep getting this output (Test1 is the filename):
```

./Test1: line 27: AdamNumber=6: command not found
./Test1: line 28: BrentNumber=40: command not found
./Test1: line 29: CobyNumber=35: command not found
Adam AdamNumber

Brent BrentNumber

Coby CobyNumber

```

Why does it think the NameNumber variables are commands? What am I doing wrong?

It only recognizes literal names followed by an equal sign as variable assignments. What you are doing is convoluted, but not nonsensical. You can use 'eval' to do an extra expansion. It turns this is needed in other places too. Here is what I came up with:

```
#! /bin/bash

name1="Adam"
name2="Brent"
name3="Coby"
eval "${name1}Number=6"
eval "${name2}Number=40"
eval "${name3}Number=35"

for name in $name1 $name2 $name3
do
  name=${name}Number
  eval "n=\$$name"
  for number in `seq 1 $n`
    do
      echo "$name $number"
    done
  echo
done

```

---

### Post by kaibob on 2009-10-01
I've been working to learn bash arrays and decided to use the question raised by the OP as practice. I came up with the following. 

```
#!/bin/bash

name[0]="Adam"
name[1]="Brent"
name[2]="Coby"

number[0]=2
number[1]=4
number[2]=6

for i in ${!name[@]} ; do
   for j in $(seq ${number[i]}) ; do
      echo "${name[i]}${j}"
   done
done
```

---

