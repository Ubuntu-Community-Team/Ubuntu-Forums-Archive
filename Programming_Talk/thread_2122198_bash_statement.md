---
title: "bash statement"
date: 2013-03-04
forum: Programming Talk
---

### Post by Drenriza on 2013-03-04
The below example has some fancy name in the programming community, but i cant remember what it is :(
But how do you enter one statement if a number is a even number and another if it isint? Do bash have a function which you can feed the number and it then says if a number is even or not.

```

i="1"

##The loop is endless
while [ ! $i -eq 1 ]
do[INDENT]if $i -eq 1,3,5,7,9,11 and so on
then do something
elif $i -eq 2,4,6,8,10,12 and so on
then do something else
[/INDENT]
done

```

Thanks on advance.

---

### Post by r-senior on 2013-03-04
Testing for odd/even is usually done by dividing by 2 and looking at the remainder, i.e. the modulus (%) of 2

```
$ echo $(( 5 % 2 ))
1
$ echo $(( 4 % 2 ))
0
```

When the remainder is zero, it's even (divisible by 2), otherwise it's odd.

---

### Post by rnerwein on 2013-03-04
hi
are you looking for something like this (modul 2)
echo -n "give me a number: "
read x
case $((x % 2)) in
0) echo "$x ist eine gerade zahl";;
1) echo "$x ist nicht gerade";;
*) echo "nix is $x"
esac

ciao

---

### Post by Drenriza on 2013-03-04
Thanks for the suggestions guys.
r-senior that was exactly what i was looking for ,)

---

