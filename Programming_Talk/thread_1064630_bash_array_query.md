---
title: "bash array query"
date: 2009-02-09
forum: Programming Talk
---

### Post by matteojg on 2009-02-09
Hello, I am trying to find a way to "automate" the creation of arrays.
I thought I could do this with command substitution...but I keep getting errors.

My first idea was this :
```
**[COLOR="Navy"]#! /bin/bash[/COLOR]**
      
     [COLOR="Blue"]MASTERARRAY[/COLOR]=**[COLOR="DarkRed"]([/COLOR]**[COLOR="Magenta"] 'a b c' 'd e f' 'g h i' **[COLOR="DarkRed"])[/COLOR][/COLOR]**
     [COLOR="Blue"]CMASTER[/COLOR]=[COLOR="Blue"]$[/COLOR]{#MASTERARRAY[@]**[COLOR=DarkRed]}[/COLOR]**

    **[COLOR="DarkRed"]for[/COLOR]** (( i = 0 ; i < $CMASTER ; i++ ))
     **[COLOR="DarkRed"]do[/COLOR]**
      [COLOR="DarkOrchid"]`echo [/COLOR][COLOR="Magenta"]"SUBARRAY[/COLOR][COLOR="Blue"]$i[/COLOR][COLOR="Magenta"]=([/COLOR][COLOR="Blue"]${MASTERARRAY[/COLOR][COLOR="Magenta"][[/COLOR][COLOR="Blue"]$i[/COLOR][COLOR="Magenta"]]} )"[/COLOR][COLOR="DarkOrchid"]`[/COLOR]
     **[COLOR="DarkRed"]done[/COLOR]**

```

which gives :
./arraytest: line 8: SUBARRAY0=(: command not found
./arraytest: line 8: SUBARRAY1=(: command not found
./arraytest: line 8: SUBARRAY2=(: command not found

So I tried also :
```
**[COLOR="Navy"]#! /bin/bash[/COLOR]**
      
     [COLOR="Blue"]MASTERARRAY[/COLOR]=**[COLOR="DarkRed"]([/COLOR]**[COLOR="Magenta"] 'a b c' 'd e f' 'g h i' **[COLOR="DarkRed"])[/COLOR][/COLOR]**
     [COLOR="Blue"]CMASTER[/COLOR]=[COLOR="Blue"]$[/COLOR]{#MASTERARRAY[@]**[COLOR=DarkRed]}[/COLOR]**

    **[COLOR="DarkRed"]for[/COLOR]** (( i = 0 ; i < $CMASTER ; i++ ))
     **[COLOR="DarkRed"]do[/COLOR]**
      [COLOR="DarkOrchid"]`echo [/COLOR][COLOR="Blue"]\`[/COLOR][COLOR="Magenta"]"SUBARRAY[/COLOR][COLOR="Blue"]$i[/COLOR][COLOR="Magenta"]=([/COLOR][COLOR="Blue"]${MASTERARRAY[/COLOR][COLOR="Magenta"][[/COLOR][COLOR="Blue"]$i[/COLOR][COLOR="Magenta"]]} )"[/COLOR][COLOR="Blue"]\`[/COLOR][COLOR="DarkOrchid"]`[/COLOR]
     **[COLOR="DarkRed"]done[/COLOR]**

```

which gives :

./arraytest: line 8: SUBARRAY0=( a b c ): command not found
./arraytest: line 8: SUBARRAY1=( d e f ): command not found
./arraytest: line 8: SUBARRAY2=( g h i ): command not found

Any ideas are greatly appreciated

---

### Post by cyfur01 on 2009-02-09
You're missing a second square bracket on the echo command:
```

#! /bin/bash
      
     MASTERARRAY=( 'a b c' 'd e f' 'g h i' )
     CMASTER=${#MASTERARRAY[@]}

    for (( i = 0 ; i < $CMASTER ; i++ ))
     do
      echo "SUBARRAY$i=(${MASTERARRAY[$i]} )"
     done

```

---

### Post by ghostdog74 on 2009-02-09
what is the real problem you are trying to solve?

---

### Post by stroyan on 2009-02-09
You can use the eval builtin to accomplish that kind of assignment to an indirect variable name.
```

for (( i = 0 ; i < $CMASTER ; i++ ))
 do
  eval "SUBARRAY$i=(${MASTERARRAY[$i]})"
 done

```
If you want to delay evaluation of a "$var" until during the eval you would quote it with a backslash like
```

eval "echo \$SUBARRAY$i"
eval "echo \${SUBARRAY${i}[*]}"

```
You can also use a ! notation for indirection when using the value of a variable ```
name=SUBARRAY$i; echo ${!name}
```
Only the eval method can do assignment to an indirect variable name or work with array notation based on an indirect name.

---

### Post by matteojg on 2009-02-09
Thanks for the replies.

Good eyes Cyfur01, I have edited the original post to correct the typo. This was not the problem though, as the typo was only in the post not the actual script...so the error outputs are still the same.

Thank you stroyan...the eval command does the trick.

ghostdog74, I suppose the "real problem" would be how to include a variable as part of a variable/array name. The eval command seems to accomplish this for the purposes of assignment. But what if I want to pass each variable/array into a conditional or simply print out its value? e.g. :
```
**[COLOR="Navy"]#! /bin/bash[/COLOR]**

[COLOR="Blue"]MASTERARRAY[/COLOR]=**[COLOR="DarkRed"]([/COLOR]**[COLOR="Magenta"] 'a b c' 'd e f' 'g h i' **[COLOR="DarkRed"])[/COLOR][/COLOR]**
[COLOR="Blue"]CMASTER[/COLOR]=[COLOR="Blue"]$[/COLOR]{#MASTERARRAY[@]**[COLOR=DarkRed]}[/COLOR]**

    **[COLOR="DarkRed"]for[/COLOR]** (( i = 0 ; i < $CMASTER ; i++ ))
     **[COLOR="DarkRed"]do[/COLOR]**
      **[COLOR="DarkRed"]eval [/COLOR]**[COLOR="Magenta"]"SUBARRAY[/COLOR][COLOR="Blue"]$i[/COLOR][COLOR="Magenta"]=([/COLOR][COLOR="Blue"]${MASTERARRAY[/COLOR][COLOR="Magenta"][[/COLOR][COLOR="Blue"]$i[/COLOR][COLOR=Magenta]]})"[/COLOR]
       [COLOR="Blue"]#A line that prints the elements of SUBARRAY$i...
       echo ${SUBARRAY$i[@]} gives, of course, a substitution error[/COLOR]
     **[COLOR="DarkRed"]done[/COLOR]**

```

---

### Post by stroyan on 2009-02-09
> **matteojg said:**
> The eval command seems to accomplish this for the purposes of assignment. But what if I want to pass each variable/array into a conditional or simply print out its value?

#A line that prints the elements of SUBARRAY$i...
echo ${SUBARRAY$i[@]} gives, of course, a substitution error 

You use eval for that as well.

eval "echo \${SUBARRAY${i}[@]}"

The unquoted inner ${i} is evaluated before the 'eval'.
The backslash quoted $ is evaluated during the 'eval'.

---

### Post by geirha on 2009-02-09
Using eval will make your script more and more unreadable, so I recommend you either try doing it a different way, or use a more suitable language. Ever tried python?

---

### Post by matteojg on 2009-02-09
Thank you again stroyan. As you probably have noticed I am very new to BASH and struggling to get a hold of its expansion rules. I most have tried a hundred variations of eval to print the elements, but kept getting "bad substitution" or "command not found" errors. 

geirha, thanks for the suggestion. The only other way I could think of was using command substitution...but even if that would work I am sure it would involve just as much, if not more, use of escapes and expansion brackets as the eval command ( which is what I am assuming you feel makes the script difficult to read ). 

I have heard of python...but as I am new to Linux I thought BASH was the best starting point. I'm really new to programming as a whole...took some classes in college, but that was so long ago they were still teaching PASCAL.

---

### Post by Yuzem on 2009-02-09
> **stroyan said:**
> Only the eval method can do assignment to an indirect variable name

You can also use declare:
```
var=test
declare $var="hello world"
echo $test
```

---

### Post by geirha on 2009-02-09
Well, there's usually a better way of doing things than doing it the eval (read: evil) way. If you explain what you actually want the script to do, we might be able to guide you onto a better track.

---

### Post by matteojg on 2009-02-09
I'm really just trying to learn BASH geirha. As I mentioned earlier, the question was how to use a variable as part of an array's name when either assigning or calling its value...eval seems to work, but if there is a better way I am happy to learn it.

---

### Post by ghostdog74 on 2009-02-09
> **matteojg said:**
> T
ghostdog74, I suppose the "real problem" would be how to include a variable as part of a variable/array name. 
usually you don't do this. the proper way is to use arrays. you can imagine each element of the arrays as "different names".
By the way, that's not a real problem. I am referring to things that you want to do, for example, are you parsing a file and doing some text manipulation, etc.

---

### Post by matteojg on 2009-02-09
I'm really just kicking BASH around to see what it can do ghostdog 74.

I guess in the example I initially gave the question is how given an array BASH can use a loop to create an array for each element in the given array
such that the 1st new array has as its elements the names contained in the first element of the given array, and in general that the nth new array has as its elements the names contained in the nth element of the given array.

e.g.
```

 #! /bin/bash
 MASTERARRAY=( 'alex bob caleb' 'daniel eric fred' 'greg hiedi ian' ) 
 CMASTER=${#MASTERARRAY[@]}
 echo ${MASTERARRAY[@]}
 echo $CMASTER

```

Now, as the script will print, the array MASTERARRAY has three elements, the strings 'alex bob caleb', 'daniel eric fred', and 'greg hiedi ian'.
If I want to create three new arrays SUBARRAY1, SUBARRAY2, and SUBARRAY3 who have as their elements, respectively, the strings 'alex' 'bob' 'caleb', 'daniel' 'eric' 'fred', and 'greg' 'hiedi' 'ian', then I could obviously continue the script so:

```

SUBARRAY1=${MASTERARRAY[0]}
SUBARRAY2=${MASTERARRAY[1]}
SUBARRAY3=${MASTERARRAY[2]}

```

I was just looking to see if there was a way to do this using a loop.

---

### Post by matteojg on 2009-02-09
sorry, accidental duplication of post...and I couldn't figure out how to delete it alltogether

---

### Post by Yuzem on 2009-02-09
Edit: You already know this, sorry.

---

### Post by matteojg on 2009-02-09
You may overstimate my knowledge there Yuzem...besides I didn't get a chance to read your post before you edited it...which makes me curious to know what I already know.

ghostdog, I think I might have tried something like you mentioned with using the array elements :

```

#! /bin/bash

MASTERARRAY=( 'alex bob caleb' 'daniel eric fred' 'greg hank ian' )
CMASTER=${#MASTERARRAY[@]}

for (( i = 0 ; i < $CMASTER ; i++ ))
 do
  for name in ${MASTERARRAY[$i]} 
   do
    SUBARRAY[$i]+=$name
   done
 done

```

But instead of getting, for example, SUBARRAY[0] having the strings 'alex', 'bob', and 'caleb' with ${#SUBARRAY[0]} = 3, calling the value of the element SUBARRAY[0] gives "alexbobcaleb" with ${#SUBARRAY[0]} = 12.

I could of course put double quotes around $name and add a space before the second quote so the printing the value of the element would give "alex bob caleb", but this simply adds the blank spaces to the count of ${#SUBARRAY[0]} so echo ${SUBARRAY[0]:0:1} gives "a" and not "alex"

---

### Post by Yuzem on 2009-02-09
> **matteojg said:**
> You may overstimate my knowledge there Yuzem...besides I didn't get a chance to read your post before you edited it...which makes me curious to know what I already know.
this:
```
#!/bin/bash
MASTERARRAY=( 'alex bob caleb' 'daniel eric fred' 'greg hiedi ian' )
CMASTER=${#MASTERARRAY[@]}

for ((i=0;i<$CMASTER;i+=1)); do
	declare SUBARRAY${i}=(${MASTERARRAY[$i]})
done

```
You did almost the same in a previous post.

> **matteojg said:**
> 
```

#! /bin/bash

MASTERARRAY=( 'alex bob caleb' 'daniel eric fred' 'greg hank ian' )
CMASTER=${#MASTERARRAY[@]}

for (( i = 0 ; i < $CMASTER ; i++ ))
 do
  for name in ${MASTERARRAY[$i]} 
   do
    SUBARRAY[$i]+=$name
   done
 done

```

But instead of getting, for example, SUBARRAY[0] having the strings 'alex', 'bob', and 'caleb' with ${#SUBARRAY[0]} = 3, calling the value of the element SUBARRAY[0] gives "alexbobcaleb" with ${#SUBARRAY[0]} = 12.

I could of course put double quotes around $name and add a space before the second quote so the printing the value of the element would give "alex bob caleb", but this simply adds the blank spaces to the count of ${#SUBARRAY[0]} so echo ${SUBARRAY[0]:0:1} gives "a" and not "alex"[/QUOTE][/QUOTE]

What about this:
```

#! /bin/bash

MASTERARRAY=( 'alex bob caleb' 'daniel eric fred' 'greg hank ian' )
CMASTER=${#MASTERARRAY[@]}

for (( i = 0 ; i < $CMASTER ; i++ )); do
	SUBARRAY[$i]=${MASTERARRAY[$i]}
done

give_me () {
	num=$1
	shift
	eval echo \$$num
}

give_me 2 ${SUBARRAY[0]}

```

---

### Post by matteojg on 2009-02-09
```

#! /bin/bash

MASTERARRAY=( 'alex bob caleb' 'daniel eric fred' 'greg hank ian' )
CMASTER=${#MASTERARRAY[@]}

for (( i = 0 ; i < $CMASTER ; i++ )); do
	SUBARRAY[$i]=${MASTERARRAY[$i]}
done

give_me () {
	num=$1
	shift
	eval echo \$$num
}

give_me 2 ${SUBARRAY[0]}

```

Thanks for the feedback Yuzem...this seems to work in its way, but isn't the creation of the SUBARRAY redundant in this case? 
```

#! /bin/bash

MASTERARRAY=( 'alex bob caleb' 'daniel eric fred' 'greg hank ian' )
CMASTER=${#MASTERARRAY[@]}

give_me () {
	num=$1
	shift
	eval echo \$$num
}

give_me 2 ${MASTERARRAY[0]}

```

Would seem to do the same thing, no?

---

### Post by Yuzem on 2009-02-10
Yes, you are right. :lolflag:

Another:
```
#!/bin/bash
MASTERARRAY=( 'alex bob caleb' 'daniel eric fred' 'greg hiedi ian' )
CMASTER=${#MASTERARRAY[@]}

for ((i=0;i<$CMASTER;i+=1)); do
	array=(${MASTERARRAY[$i]})
	carray=${#array[@]}

	for ((ii=0;ii<$carray;i+=1)); do
		SUBARRAY_$i_$ii=${array[$ii]}
	done
done

query=SUBARRAY_0_2
echo ${!query}
```

---

