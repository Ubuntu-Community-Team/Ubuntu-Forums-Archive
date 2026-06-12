---
title: "[SOLVED] Shell Scripting Syntax Question"
date: 2008-03-08
forum: Programming Talk
---

### Post by DGortze380 on 2008-03-08
Hey all,

I'm working on a script for a class and can't seem to fin this syntax anywhere, it seems to be kind of obscure I guess.

I need to reference an array using a variable for the array name.  

# EXAMPLE:

arrayName=exampleArray

for (x=0;x<5;x++) ;do
    $arrayName[$x]=fill
done

# this creates an array:
#
# exampleArray[0]=fill
# exampleArray[1]=fill
# exampleArray[2]=fill
# exampleArray[3]=fill
# exampleArray[[4]=fill
 
#that all works just fine... what I can NOT do is this:

for (x=0;x<5;x++) ;do
    echo ${$arrayName[$x]}
done

# it returns an error saying that "a" is unexpected (it's always says the first
# letter of the variable is unexpected). Normally you would just use the actual 
# name of the array, not a variable, and it works fine. But the way I have this 
# script set up, I need to use a variable for the name of the array.

# If you have any idea what the syntax might be (or if it just can't be done in 
# shell scripting) it would be a huge help.

---

### Post by munkyeetr on 2008-03-08
I think your problem may lay in this snippet of code
```

for (x=0;**x=5**;x++) ;do
echo ${$arrayName[$x]}
done

```

You are reassigning x to equal 5, not to count to 5 (as I believe you are intending)
There is no array index 5, it only counts 0 to 4.

---

### Post by ghostdog74 on 2008-03-08
am not sure is it what you want, but you can go to the advance bash manual link in my sig, look for example Example 34-2.

---

### Post by DGortze380 on 2008-03-08
> **munkyeetr said:**
> I think your problem may lay in this snippet of code
```

for (x=0;**x=5**;x++) ;do
echo ${$arrayName[$x]}
done

```

You are reassigning x to equal 5, not to count to 5 (as I believe you are intending)
There is no array index 5, it only counts 0 to 4.

That would be a problem, thanks for picking it up, but that was a typo just on the forum, it should say:

for (x=5;x<5;x++ )

---

### Post by DGortze380 on 2008-03-08
> **ghostdog74 said:**
> am not sure is it what you want, but you can go to the advance bash manual link in my sig, look for example Example 34-2.

Thanks, but not quite what I'm looking to do. The index works fine, it's the variable for the array name that's that problem.

---

### Post by munkyeetr on 2008-03-08
Initially I didn't even run the code, I just found that syntax error and posted back, but now that I try and run the code I get errors in the first section that say "Bad for loop variable".

You didn't mention which shell you are using to run this script, and also can you post the shell declaration from the top of your script file...

is it **#!/bin/bash** ?

---

### Post by ghostdog74 on 2008-03-09
what is it that you are actually trying to solve?

---

### Post by DGortze380 on 2008-03-09
*** Full Code Removed ***

---

### Post by DGortze380 on 2008-03-09
This section of code is my problem:

for (( k=0;k<($newCount);k++ )) ;do
(( horseSum+=${$saveName[$k]} ))
(( horseAvg=$sum/$newCount ))
echo $saveName " averaged: " $horseAvg
done

It keeps saying that "s" is unexpected ( in line 2 of the above section of code)

.....

for anyone reading through all that code, the original data file looked something like this:

Horse1 1 1.15 3.24 2.31 2.33
Horse2 3 2.34 1.10 2.95 3.44
Horse3 2 1.34 2.11 2.15 2.43
Horse1 2 2.33 3.23 2.44 3.25

The sorted file is obviously identical, except sorted by name A-Z

---

### Post by munkyeetr on 2008-03-09
Remove the bolded $ in line 2

```

for (( k=0;k<($newCount);k++ )) ;do
(( horseSum+=${**$**saveName[$k]} ))
(( horseAvg=$sum/$newCount ))
echo $saveName " averaged: " $horseAvg
done

```
so it is like this:
```

(( horseSum+=${saveName[$k]} ))

```

---

### Post by ghostdog74 on 2008-03-09
i applaud you for what you have done. If you have not already known, *nix have sorting tools available so that you don't have to code sorting algorithms on your own. Also just an example to find the fastest time among your horses using the data file you provided
```

awk '{
 max=0
 for(i=2;i<=NF;i++){
   if ( $i > max) {
    max=$i
   }
 }
 if ( a[$1] < max ) a[$1]=max
}
END{
 for ( j in a ) print "Fastest time for horse " j " is " a[j]
}
' "file"

```

output:
```

# ./test.sh
Fastest time for horse Horse1 is 3.25
Fastest time for horse Horse2 is 3.44
Fastest time for horse Horse3 is 2.43

```

---

### Post by Mr. C. on 2008-03-09
> **ghostdog74 said:**
> ..., *nix have sorting tools available so that you don't have to code sorting algorithms on your own. 

Is the goal sorted output, or learning how to code a sort algorithm?

---

### Post by DGortze380 on 2008-03-09
> **munkyeetr said:**
> Remove the bolded $ in line 2

```

for (( k=0;k<($newCount);k++ )) ;do
(( horseSum+=${**$**saveName[$k]} ))
(( horseAvg=$sum/$newCount ))
echo $saveName " averaged: " $horseAvg
done

```
so it is like this:
```

(( horseSum+=${saveName[$k]} ))

```

This is exactly my problem.  saveName is not the name of the array, if it was then removing the $ would work.  saveName is a variable, which holds a string, that string is the name of the array.  The problem is, the name will change as the loop reads through the sorted data.  I can use a variable to assign a value into the array (random example: $saveName[0]=1.32), but I don't know how to reference it that way (random example: echo ${$saveName[0]} )

---

### Post by DGortze380 on 2008-03-09
> **ghostdog74 said:**
> i applaud you for what you have done. If you have not already known, *nix have sorting tools available so that you don't have to code sorting algorithms on your own. Also just an example to find the fastest time among your horses using the data file you provided
```

awk '{
 max=0
 for(i=2;i<=NF;i++){
   if ( $i > max) {
    max=$i
   }
 }
 if ( a[$1] < max ) a[$1]=max
}
END{
 for ( j in a ) print "Fastest time for horse " j " is " a[j]
}
' "file"

```

output:
```

# ./test.sh
Fastest time for horse Horse1 is 3.25
Fastest time for horse Horse2 is 3.44
Fastest time for horse Horse3 is 2.43

```

Thanks for the information. I was not aware.  I'm just a few weeks into a basic shell scripting class, so I coded it the way I knew how.  Either way, the sort works, I just need to figure how to reference an array using a variable for the array name.

---

### Post by ghostdog74 on 2008-03-09
small example
```

# a=b
# b[0]=1
# echo ${b[0]}
1
# echo ${a} #this is not what you want
b
# eval echo \${${a}} #is this what you want??
1
# b[2]=1000
# eval echo \${${a}[2]}
1000



```

---

### Post by Mr. C. on 2008-03-09
The only way to do this prior to bash's indirect variables was via eval.

With bash, you can use the ${!$var} syntax:

```
$ a=1
$ b=a
$ echo ${a}
1
$ echo ${b}
a
$ echo ${!b}
1
```

---

### Post by ghostdog74 on 2008-03-09
> **Mr. C. said:**
> The only way to do this prior to bash's indirect variables was via eval.

With bash, you can use the ${!$var} syntax:

```
$ a=1
$ b=a
$ echo ${a}
1
$ echo ${b}
a
$ echo ${!b}
1
```

the strange thing is , this method is shown in example 34-2  (from the bash manual ) which i directed the OP to in post #3 and OP replied that its not what he's looking for in post #5.

---

### Post by DGortze380 on 2008-03-09
> **Mr. C. said:**
> The only way to do this prior to bash's indirect variables was via eval.

With bash, you can use the ${!$var} syntax:

```
$ a=1
$ b=a
$ echo ${a}
1
$ echo ${b}
a
$ echo ${!b}
1
```

Ok, I think I get it.
Does ksh support indirect variables as well?

---

### Post by Mr. C. on 2008-03-09
Use the echo eval method if you need portability.

---

### Post by Mr. C. on 2008-03-09
> **ghostdog74 said:**
> the strange thing is , this method is shown in example 34-2  (from the bash manual ) which i directed the OP to in post #3 and OP replied that its not what he's looking for in post #5.

Perhaps the OP went to section 34-2 ?

---

### Post by DGortze380 on 2008-03-09
> **Mr. C. said:**
> Use the echo eval method if you need portability.

Sorry, it's 3:30AM here, maybe I'm just a little dense, haha..  That work great to echo the values, but how would a use that in another expression...

	for (( k=0;k<($index);k++ )) ;do
				echo "this is slot " $k ":"
				eval echo \${${saveName}[$k]}

#				(( horseSum+=\${${saveName}[$k]} ))
#				echo "this is horseSum" $horseSum
#				(( horseAvg=$sum/$newCount ))
#				echo $saveName " averaged: " $horseAvg

		done		

what I need is to add each of the values in the array to horseSum using horseSum+=

obviously this syntax is wrong, but something like:

(( horseSum+=eval \${${saveName}[$k]} ))
echo $horseSum

---

### Post by ghostdog74 on 2008-03-09
> **DGortze380 said:**
> Ok, I think I get it.
Does ksh support indirect variables as well?

you can use nameref in ksh. See [here]("http://www.informit.com/articles/article.aspx?p=99035")

---

### Post by DGortze380 on 2008-03-09
nameref doesn't seem to work in referencing an array, and I can't find the syntax to use eval like I stated above. Calling it quits for tonight. any syntax advice would be awesome.

---

### Post by ghostdog74 on 2008-03-09
you can save it to a variable first?
```

result=$(eval echo \${${saveName}[$k]})

```

---

### Post by DGortze380 on 2008-03-09
Thanks a bunch! Everything is working.

---

### Post by provisional_idiot on 2008-03-09
so in summary??:


```

#!/bin/bash
arrayName=exampleArray
for x in 0 1 2 3 4 5 
do
eval $arrayName[$x]=$x
done
temp=
sum=0
for x in 1 2 3 4 5 
do
eval temp=\${$arrayName[$x]}
sum=`expr $sum + $temp` 
done
echo $sum
```

---

### Post by DGortze380 on 2008-03-09
> **provisional_idiot said:**
> so in summary??:


My code ended up looking something like this:

```


for (( k=0;k<($index);k++ )) ;do
echo "this is slot " $k ":"
eval echo \${${saveName}[$k]}
(( sum+=$(eval echo \${${saveName}[$k]}) ))
(( avg=$sum/$index ))
echo $avg
done


```

It's obviously only a small chunk of the script, but I used it to reference the name of array which is not yet know during a while read loop.

PM with any future questions I can send you more of the code.

---

