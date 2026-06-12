---
title: "Accessing array of integer"
date: 2009-08-16
forum: Programming Talk
---

### Post by colau on 2009-08-16
```

ar="6 4 6 1 5"
for (( i = 0; i <= 4; i++ ))
do
    echo ar[$i]
done  

```
How can i print:
```

6
4
6
1
5

```

---

### Post by kaibob on 2009-08-16
I'm new to arrays, so this may be a dumb question, but have you actually created an array? From what I've learned so far, it should be:

```
array=( 6 4 6 1 5 ) ; for item in ${array[@]} ; do echo $item ; done
```

or

```
array=( 6 4 6 1 5 ) ; for (( i = 0; i <= 4; i++ )) ; do echo ${array[$i]} ; done
```

---

### Post by colau on 2009-08-16
> **kaibob said:**
> I'm new to arrays, so this may be a dumb question, but have you actually created an array? From what I've learned so far, it should be:

```
array=( 6 4 6 1 5 ) ; for item in ${array[@]} ; do echo $item ; done
```

Then, getting say the first element of the array would be:

```
array=( 6 4 6 1 5 ) ; for item in ${array[0]} ; do echo $item ; done
```
Thank you.
Trying to solve with this pattern:
[php]
for (( i = 0; i <= 4; i++ ))
[/php]

---

### Post by kaibob on 2009-08-16
> **colau said:**
> Thank you.
Trying to solve with this pattern:
[php]
for (( i = 0; i <= 4; i++ ))
[/php]

Sorry, like I said, I'm new to all this. I'm sure geirha, stroyan, ghostdog74 or one of the other very knowledgeable forum members will have an answer to your question.

---

### Post by soltanis on 2009-08-16
I am not familiar with this syntax. What language is this being done with?

---

### Post by MadCow108 on 2009-08-16
looks like bash (at least the for loop)
in that case you can to do it like that:
```

ar=(6 4 6 1 5);
for (( i = 0; i <= 4; i++ ));
do
    echo ${ar[$i]}
done

```

---

### Post by nvteighen on 2009-08-16
> **soltanis said:**
> I am not familiar with this syntax. What language is this being done with?

Aj... Again, people have to please put the language they're asking about in the thread title... Heck, specially in shell scripting languages, which are very close to eachother in syntax but very different in semantics.

---

### Post by colau on 2009-08-16
> **MadCow108 said:**
> looks like bash (at least the for loop)
in that case you can to do it like that:
```

ar=(6 4 6 1 5);
for (( i = 0; i <= 4; i++ ));
do
    echo ${ar[$i]}
done

```
Thank you.
Can you tell in ***echo ${ar[$i]}***, why is the color of first brace different from the second in gedit?

---

### Post by MadCow108 on 2009-08-16
this just seems to be a bug in syntax highlighting of gedit
it probably "thinks" the first brace is part of the variable name so it colours it wrong

---

### Post by colau on 2009-08-16
> **MadCow108 said:**
> this just seems to be a bug in syntax highlighting of gedit
it probably "thinks" the first brace is part of the variable name so it colours it wrong
Which version of gedit are you using?

---

### Post by colau on 2009-08-17
> **kaibob said:**
> 
```
array=( 6 4 6 1 5 ) ; for item in ${array[@]} ; do echo $item ; done

```
Is there any other option except [COLOR="Red"]**${array[@]}**[/COLOR]?
What does it mean by **[COLOR="Red"]@[/COLOR]**?
It starts to print from array[0].
I do not want to use **for ((i=1;i<=5;i++))** pattern to print the element of array.
Is it possible to print from arr[1] using this pattern **for vv in**  


```
#!/bin/bash

arr="0"
cnt=1
for i in $(seq 1 5)
do
	m=`expr $i % 2`
	if [ $m -ne 0 ];then
		arr[$cnt]=$i
		cnt=`expr $cnt + 1`
	fi
done

for vv in ${arr[@]}
do
	echo $vv
done

```

---

### Post by geirha on 2009-08-18
```
#!/bin/bash

arr=(0)
for i in {1..5}; do
  (( i%2 == 0)) && arr+=($i)
  # You can also do ((i%2)) || arr+=($1)
done

for vv in "${arr[@]}"; do
  echo "$vv"
done

```

Make sure to quote the expansion "${arr[@]}". See also [http://mywiki.wooledge.org/BashFAQ/005](http://mywiki.wooledge.org/BashFAQ/005)

EDIT: Oh and to skip element 0 (i.e. start from element 1), you can use "${arr[@]:1}"

---

### Post by colau on 2009-08-18
> **geirha said:**
> ```
#!/bin/bash

arr=(0)
for i in {1..5}; do
  (( i%2 == 0)) && arr+=($i)
  # You can also do ((i%2)) || arr+=($1)
done

for vv in "${arr[@]}"; do
  echo "$vv"
done

```

Make sure to quote the expansion "${arr[@]}". See also [http://mywiki.wooledge.org/BashFAQ/005](http://mywiki.wooledge.org/BashFAQ/005)

EDIT: Oh and to skip element 0 (i.e. start from element 1), you can use "${arr[@]:1}"

Thank you.

---

### Post by colau on 2009-08-18
> **geirha said:**
> 
Make sure to quote the expansion "${arr[@]}".

If I remove double quote from **"${arr[@]}"** it works too.

---

### Post by geirha on 2009-08-18
> **colau said:**
> If I remove double quote from **"${arr[@]}"** it works too.

In your case when it only contains integers, it will work without quotes, however, if any of the elements contained spaces or glob characters, you'd get undesired results. You might as well make it a good habit right away.

---

