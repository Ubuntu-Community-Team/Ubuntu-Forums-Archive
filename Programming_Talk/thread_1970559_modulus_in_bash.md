---
title: "modulus in bash"
date: 2012-05-01
forum: Programming Talk
---

### Post by abraxas334 on 2012-05-01
After googling many things i really cannot workout, where I am going wrong.

I amtrying to print out a variable if the number is even:
My very basic script looks like this:
```


#!/bin/bash

echo "this will be a T-jump experiment"

for traj in {1..10} #number of cycles loop
do
        modulo = $traj%2
        echo $modulo
        if [ $traj%2==0 ]; then
                echo $traj
                for temp in {1..2} #number of temperatures
                do
                        filename="nd_temp_($temp)_tran_($traj)"
                        echo $filename

                done
        else
                for temp in {2..1} #number of temperatures
                do
                        filename="nd_temp_($temp)_tran_($traj)"
                        echo $filename

                done
        fi

done


```
Modulus does exist in bash but I am apparently using it wrong. I don't really understand what is wrong tho.

Thanks for any help

---

### Post by ofnuts on 2012-05-01
You have to enclose your arithmetic in double parentheses, so:

```

modulo=$(( $traj  % 2 ))

```

---

### Post by LemursDontExist on 2012-05-01
I don't think bash recognizes the modulo operator in that context - the shell needs to know you're doing arithmetic.

```
if [ $(($traj%2)) == 0 ]; then
```

should work.  Alternatively

```
if (( $traj%2 == 0 )); then
```

should also work.  Or, maybe best

```
if [ `expr $traj % 2` == 0 ]; then
```

The first two rely on bash syntax that I'm not positive works across all standard shells, but the last should work in any normal shell.

---

### Post by sisco311 on 2012-05-02
Check out [http://mywiki.wooledge.org/ArithmeticExpression](http://mywiki.wooledge.org/ArithmeticExpression)

As LemursDontExist already mentioned it, the POSIX version is:
```
if test $((traj%2)) = 0; then ... #or
if [ $((traj%2)) = 0 ]; then ...
```

In BASH you can use let or ((
```

if ((traj%2 == 0)); then ...
if let "$traj%2 == 0"; then ...
```

---

### Post by codemaniac on 2012-05-02
> **ofnuts said:**
> You have to enclose your arithmetic in double parentheses, so:

```

modulo=$(( $traj  % 2 ))

```
or the other way . : )

```
((modulo = $traj  % 2 ))
```

---

