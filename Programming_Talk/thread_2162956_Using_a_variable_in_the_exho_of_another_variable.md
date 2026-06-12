---
title: "Using a variable in the exho of another variable"
date: 2013-07-16
forum: Programming Talk
---

### Post by cbillson on 2013-07-16
Hi, i know how to do this in DOS, and i'm hoping its possible in linux.


file1=bob
file2=joe
file3=ken

var=1

Output needs to be echo $file1

echo $file$var (unfortunately would give me 1)

var=2

echo $file$var

Apologies if that makes no sense at all!!

---

### Post by sudodus on 2013-07-16
I don't know exactly what you want to do. Maybe you can use a for-loop. If the names are files in the current directory, you can get them into the variable 'name' and get an associated counter 'i' like this. (Try it in a directory with rather few files!)

```
 i=0;for name in *;do i=$((i=$i+1));echo -n "$i: "; echo $name;done
```

You can find the following description of the for command in ```
man bash
```
```

       for name [ in word ] ; do list ; done
              The list of words following in is expanded, generating a list of
              items.  The variable name is set to each element of this list in
              turn,  and  list is executed each time.  If the in word is omit&#8208;
              ted, the for command executes  list  once  for  each  positional
              parameter that is set (see PARAMETERS below).  The return status
              is the exit status of the last command that  executes.   If  the
              expansion of the items following in results in an empty list, no
              commands are executed, and the return status is 0.

       for (( expr1 ; expr2 ; expr3 )) ; do list ; done
              First, the arithmetic expression expr1 is evaluated according to
              the  rules  described  below  under  ARITHMETIC EVALUATION.  The
              arithmetic expression expr2 is then evaluated  repeatedly  until
              it  evaluates  to zero.  Each time expr2 evaluates to a non-zero
              value, list is executed and the arithmetic expression  expr3  is
              evaluated.   If  any  expression is omitted, it behaves as if it
              evaluates to 1.  The return value is the exit status of the last
              command in list that is executed, or false if any of the expres&#8208;
              sions is invalid.

```
Some more examples
```

for i in *.txt;do echo textfiles: $i;done

for (( i=1; i<=20 ; i++ )) ; do echo $i;done

for i in *.TXT;do mv $i ${i/\.TXT/}.txt; done  # "move *.TXT *.txt"

```

---

### Post by ofnuts on 2013-07-16
See you other question... this is a hack when you can't use arrays, but shell scripts can do arrays.. 

And in fact in this specific case, you don't even need an array, a for loop on a list of files will work (and surprisingly, it would also be the right solution in a .BAT... see "HELP FOR")

---

### Post by papibe on 2013-07-16
Hi cbillson.

There are two ways that I can think of:

Using arrays (ofnuts's suggestion):
```
file[1]=bob
file[2]=joe
file[3]=ken

var=1

echo "${file[$var]}"
```
Or using eval:
```
file1=bob
file2=joe
file3=ken

var=1

echo $(eval echo \$"file$var")
```
Let us know how it goes.
Regards.

---

### Post by cbillson on 2013-07-17
> **papibe said:**
> Hi cbillson.

There are two ways that I can think of:

Using arrays (ofnuts's suggestion):
```
file[1]=bob
file[2]=joe
file[3]=ken

var=1

echo "${file[$var]}"
```
Or using eval:
```
file1=bob
file2=joe
file3=ken

var=1

echo $(eval echo \$"file$var")
```
Let us know how it goes.
Regards.

you sir are a star..

thank-you to everyone who advised, much appreciated

---

### Post by Vaphell on 2013-07-17
my advice regarding **eval** is forget you've seen it. If you find yourself using it, in 99.9 percent of cases you are doing it wrong.

just stick to arrays.

---

### Post by ofnuts on 2013-07-17
> **Vaphell said:**
> my advice regarding **eval** is forget you've seen it. If you find yourself using it, in 99.9 percent of cases you are doing it wrong.

just stick to arrays.

+2 :)

---

### Post by papibe on 2013-07-17
> **Vaphell said:**
> If you find yourself using it, in 99.9 percent of cases you are doing it wrong. just stick to arrays.
> **ofnuts said:**
> +2 :)
Oopsy :oops:

---

### Post by cbillson on 2013-07-19
ok, another question.. using the array with a for loop.

normally a for loop will repeat until it runs out of things to repeat on, like if you're using a file (lines) or a directory (files).

how does it work with an array, will it just stop when there is nothing more to increment?

---

### Post by Vaphell on 2013-07-19
it's works the same because you provide the for loop with a finite set of elements, once they are processed the loop exits.

there are few ways you can iterate arrays

```
$ array=( a b c )  # standard integer indexed array, starting from 0
$ declare -A asoc_arr # associative array indexed with strings
$ asoc_arr=( [abc]=lol [def]=wut )

$ for elem in "${array[@]}"; do echo "$elem"; done
a
b
c

$ for elem in "${asoc_arr[@]}"; do echo "$elem"; done
wut
lol

```
works both with integer indexed and associative arrays, note that associative arrays don't guarantee order

```
$ echo "${!array[@]}"
0 1 2
$ for [COLOR="#0000FF"]idx[/COLOR] in "${!array[@]}"; do echo "array[[COLOR="#0000FF"]$idx[/COLOR]]: ${array[[COLOR="#0000FF"]$idx[/COLOR]]}"; done 
array[[COLOR="#0000FF"]0[/COLOR]]: a
array[[COLOR="#0000FF"]1[/COLOR]]: b
array[[COLOR="#0000FF"]2[/COLOR]]: c

$ echo "${!asoc_arr[@]}"
def abc
$ for [COLOR="#0000FF"]idx[/COLOR] in "${!asoc_arr[@]}"; do echo "asoc_arr[[COLOR="#0000FF"]$idx[/COLOR]]: ${asoc_arr[[COLOR="#0000FF"]$idx[/COLOR]]}"; done 
asoc_arr[[COLOR="#0000FF"]def[/COLOR]]: wut
asoc_arr[[COLOR="#0000FF"]abc[/COLOR]]: lol

```
works both integer indexed and associative arrays,** ${!array[@]}** generates set of indices/keys found in the array

```
$ for (( i=0; i<${#array[@]}; i++ )); do echo "array[[COLOR="#0000FF"]$i[/COLOR]]: ${array[[COLOR="#0000FF"]$i[/COLOR]]}"; done
array[[COLOR="#0000FF"]0[/COLOR]]: a
array[[COLOR="#0000FF"]1[/COLOR]]: b
array[[COLOR="#0000FF"]2[/COLOR]]: c
```
C-like for loop, works only with integer indexed arrays, **${#array[@]}** returns array size so the loop spans range of 0..ARRAY_SIZE-1

---

### Post by cbillson on 2013-07-19
Thanks.. having a play now

for (( i=1; i<${#array[@]}; i++ )); do echo "array[$i]: ${array[$i]}"; done

i get that i = start of array, as mine was specified as array[1] array[2] array[3] and it returned 0=(blank)

however as i=0 or i=1 the following returns:

[INDENT]array[1]=bob
array[2]=joe
array[3]=ken

for (( i=1; i<${#array[@]}; i++ )); do echo "array[$i]: ${array[$i]}"; done[/INDENT]

array[0]:
array[1]: bob
array[2]: joe




or

array[1]: bob
array[2]: joe


Why does it always stop at 2?

---

### Post by Vaphell on 2013-07-19
C-like loops work well only when they start from 0 and they are continuous (don't have holes). Holes outright prevent this approach from working and what you have is a wrong condition due to the offset you introduced (starting from 1 not from 0). Array size says 3 so its a range of integers 1+ but (less than 3) => 1, 2.

why don't you use **array=( "bob" "joe" "ken" )** with autoassigned indices, which would make the for loop work properly? You don't have to be a control freak ;-)

if you still want to manage index by hand you should go the **${!array[@]}** route. This lists all indices that can be found inside the array
```
$ irregular[2]=a; irregular[5]=b
$ echo "${!irregular[@]}"
2 5
$ for idx in "${!irregular[@]}"; do echo "irregular[$idx]: ${irregular[$idx]}"; done
irregular[2]: a
irregular[5]: b
```


and what is wrong with using
```
for elem in "${array[@]}"; do echo "$elem"; done
``` in the first place? It will iterate over all available elements automagically, without any index management at all. Is there any meaning to the index that you hold on to it so much?

---

