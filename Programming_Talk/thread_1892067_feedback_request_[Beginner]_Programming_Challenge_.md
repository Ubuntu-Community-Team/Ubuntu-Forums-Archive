---
title: "feedback request [Beginner] Programming Challenge: 1]"
date: 2011-12-07
forum: Programming Talk
---

### Post by unifid on 2011-12-07
*Well im new here, so please be kind ;)*
Found that awesome competition, know its old just want some feedback or other alternative bash solutions.

This is my first attempt after reading a couple of pages in the excellent  []("http://tldp.org/LDP/abs/html/")
Any other advices on documentation would be appreciated

```
#!/bin/bash
##
# 99 Bottles of beer song-generator  
##
NOMOREBOTTLES=0
BOTTLES=99

eval BottleAry=({$NOMOREBOTTLES..$BOTTLES})
BottleAry[$NOMOREBOTTLES]="no"
for N in $(eval echo {$BOTTLES..$NOMOREBOTTLES}); do
case $N in 
[3-99]*) echo ${BottleAry[$N]} "bottles of beer on the wall," ${BottleAry[$N]} "bottles of beer "
	  echo "Take on down and pass it around," ${BottleAry[($N-1)]} "bottles of beer on the wall" 
	  ;;
[2]) 	  echo ${BottleAry[$N]} "bottles of beer on the wall," ${BottleAry[$N]} "bottles of beer "
	  echo "Take on down and pass it around," ${BottleAry[($N-1)]} "bottle of beer on the wall" 
	  ;;
[1]) 	  echo ${BottleAry[$N]} "bottle of beer on the wall," ${BottleAry[$N]} "bottle of beer."
	  echo "Take one down and pass it around," ${BottleAry[($N-1)]} "more bottles of beer on the wall."
	  ;;
[0])	  echo ${BottleAry[$N]} "more bottles of beer on the wall," ${BottleAry[$N]} "more bottles of beer."
          echo "Go to the store and buy some more," $BOTTLES "bottles of beer on the wall."
	  ;;
esac
done

```

---

### Post by sisco311 on 2011-12-07
Hi and welcome to the forums!

By convention, we capitalize environment variables (PAGER, EDITOR, SHELL, ...) and internal shell variables (BASH_VERSION, RANDOM, ...). All other variable names should contain at least one lowercase letter. Remember that variable names are case-sensitive; this convention avoids accidentally overriding environmental and internal variables.

'eval' is a common misspelling of 'evil'. :evil:
See BashFAQ 048 and BashFAQ 006 (link in my signature).

[**3-9**9] is equivalent to [**3456789**9]. See  [http://tiswww.case.edu/php/chet/bash/bashref.html#SEC36](http://tiswww.case.edu/php/chet/bash/bashref.html#SEC36)


HTH

---

### Post by unifid on 2011-12-12
First of all many thanks to sisco311
Using the env | sort gave some interesting insight of what errors that could occur. 

From my previous post i must clarify that the guide that was refered to was
[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

And also the brace expansion, the method is refered as pitfall. Is there any solution since i want to avoid using values later in the code. 

[http://wiki.bash-hackers.org/syntax/expansion/brace]("http://wiki.bash-hackers.org/syntax/expansion/brace")

```
#!/bin/bash
##
# 99 Bottles of beer song-generator  
##
lastBottle=0
bottleCount=99

eval BottleAry=({$lastBottle..$bottleCount})

BottleAry[$lastBottle]="no"
for N in $(eval echo {$bottleCount..$lastBottle});do
case $N in 
[3-"99"]*) echo ${BottleAry[$N]} "bottles of beer on the wall," ${BottleAry[$N]} "bottles of beer "
	  echo "Take on down and pass it around," ${BottleAry[($N-1)]} "bottles of beer on the wall" 
	  ;;
[2]) 	  echo ${BottleAry[$N]} "bottles of beer on the wall," ${BottleAry[$N]} "bottles of beer "
	  echo "Take on down and pass it around," ${BottleAry[($N-1)]} "bottle of beer on the wall" 
	  ;;
[1]) 	  echo ${BottleAry[$N]} "bottle of beer on the wall," ${BottleAry[$N]} "bottle of beer."
	  echo "Take one down and pass it around," ${BottleAry[($N-1)]} "more bottles of beer on the wall."
	  ;;
[0])	  echo ${BottleAry[$N]} "more bottles of beer on the wall," ${BottleAry[$N]} "more bottles of beer."
          echo "Go to the store and buy some more," $BOTTLES "bottles of beer on the wall."
	  ;;
esac
done


```

---

### Post by sisco311 on 2011-12-12
The infamous "Advanced" Bash Scripting Guide should be avoided unless you know how to filter out the junk. It will teach you to write bugs, not scripts. In that light, the BashGuide was written: [http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

You could use a loop.

```

#POSIX

lb=0
bc=99

while test "$bc" -gt "$lb"
do
    n=$((n-1))
    do something
done

```

```


#Bash. C-style for loop:
lb=0
bc=99

for ((i=lb; i<=bc; i++))
do
    do something
done

```

And here is my solution:
```
#!/bin/bash

print ()
{
    local i
    string="$@"
    for ((i=0; i<${#string}; i++))
    do
        printf '%s' "${string:i:1}"
        sleep 0.02
    done
    printf '\n'
}

bottles ()
{
    case "$n" in
        0) bottle="no more bottles of beer";;
        1) bottle="one bottle of beer";;
        *) bottle="$n bottles of beers";;
    esac
}

printn ()
{
     n="$1"
     bottles "$n"
     print "$bottle on the wall, $bottle."
     ((n--))
     bottles "$n"
     print "Take one down and pass it around, $bottle on the wall."
     printf '\n'

}

number=3

for ((i=number;i>0;i--))
do
    printn "$i"
done


```

---

