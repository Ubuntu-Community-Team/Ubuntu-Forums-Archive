---
title: "what is the best way to read numbers from stdin"
date: 2012-11-20
forum: Programming Talk
---

### Post by Mia_tech on 2012-11-20
what is the best way to read a line containing multiples numbers into an array.
I know "read -a numbers" will put all numbers into the numbers array. But I want to read every number and put them into an array.

I was testing the following method, but the script is still waiting for intput after reading the numbers

```
while read line
do
   numbers=(${numbers[@] $line)
done
```

---

### Post by steeldriver on 2012-11-20
Not sure it's the *right *way to do it, but

```
while read line
do 
    numbers=($line)
done

```should work, I think - as long as $line really does expand to a whitespace delimited list of numbers - you should probably put in some kind of validator

---

### Post by Vaphell on 2012-11-20
i'd do it like this
```
while read -ra n; do numbers+=( "${n[@]}" ); done
```
imo it's more elegant than simply using $line and allowing it to split at whitespace. It's also more flexible because you can set IFS and -d for *read* to get the line split however you wish.

```
**$ while read -ra n; do numbers+=( "${n[@]}" ); echo ${#n[@]} elems added; done <<< $'1 2 3\n4 5 6 7 8\n9 10 11 12'**
3 elems added
5 elems added
4 elems added
**$ for n in "${numbers[@]}"; do echo $n; done**
1
2
3
4
5
6
7
8
9
10
11
12
```

---

### Post by Mia_tech on 2012-11-20
> **steeldriver said:**
> Not sure it's the *right *way to do it, but

```
while read line
do 
    numbers=($line)
done

```should work, I think - as long as $line really does expand to a whitespace delimited list of numbers - you should probably put in some kind of validator

with this method, after you enter the numbers and press enter the terminal is still waiting for input.... something is missing

---

### Post by Mia_tech on 2012-11-20
> **Vaphell said:**
> i'd do it like this
```
while read -ra n; do numbers+=( "${n[@]}" ); done
```
imo it's more elegant than simply using $line and allowing it to split at whitespace. It's also more flexible because you can set IFS and -d for *read* to get the line split however you wish.

```
**$ while read -ra n; do numbers+=( "${n[@]}" ); echo ${#n[@]} elems added; done <<< $'1 2 3\n4 5 6 7 8\n9 10 11 12'**
3 elems added
5 elems added
4 elems added
**$ for n in "${numbers[@]}"; do echo $n; done**
1
2
3
4
5
6
7
8
9
10
11
12
```

I tried this method too, after entering numbers I press enter and terminal is waiting for more input...

---

### Post by Vaphell on 2012-11-21
i admit i don't get what exactly you want to achieve. You want single input but use while read for that?
Give some example - i type this, that should happen.

---

### Post by Mia_tech on 2012-11-21
> **Vaphell said:**
> i admit i don't get what exactly you want to achieve. You want single input but use while read for that?
Give some example - i type this, that should happen.

```
Enter a list of numbers: 2 10 34 44 20
```

then iterate through the numbers and add them to an array... doesn't have to be (while read) any other method is fine, but ```
read -a numbers
``` I'm looking for other alternative method of achieving this

Thanks

---

### Post by Vaphell on 2012-11-21
```
read -p "Enter numbers: " -a num
for n in ${num[@]}; do numbers+=( $n ); done

```

---

### Post by Mia_tech on 2012-11-21
> **Vaphell said:**
> ```
read -p "Enter numbers: " -a num
for n in ${num[@]}; do numbers+=( $n ); done

```

what's the point of the for loop... num is already an array

---

### Post by Vaphell on 2012-11-21
you said you wanted to add those numbers one by one. num is a temp array, numbers is the real deal.
While in case of a single *read* both arrays will be equivalent, it would matter if you read multiple lines.

```
$ while :; do read -p "numbers: " -a num; for n in ${num[@]}; do echo "adding $n to (${numbers[@]})"; numbers+=($n); done; done
numbers: 11 22 33 44
adding 11 to ()
adding 22 to (11)
adding 33 to (11 22)
adding 44 to (11 22 33)
numbers: 23 34 56
adding 23 to (11 22 33 44)
adding 34 to (11 22 33 44 23)
adding 56 to (11 22 33 44 23 34)
```

---

### Post by dwhitney67 on 2012-11-21
> **Mia_tech said:**
> ```
read -a numbers
``` I'm looking for other alternative method of achieving this


From what I have read from this thread, it appears you want the ability to read a sequence of numbers into an array, but once the reads are completed, you do not want the script to block on a subsequent read.

I've googled a bit on ways to emulate non-blocking reads; some threads contained more information than I cared to learn about.  However, you might find something of interest.

Anyhow, one possibility would be to employ a timeout period for the read using the -t option.  For example:
```

echo -n "Enter a list of numbers: "
while read -t 10 num; do
    if [ "$num" == "" ]; then
        break
    fi
    numbers+=($num)
done

```
I place the if-conditional statement in the loop in case the user get's "bored" and wants the read process to complete sooner.  The user would have to enter another newline after they have entered all their numbers (and a newline for those).

---

