---
title: "A Strange Shell scripting Problem"
date: 2008-07-29
forum: Programming Talk
---

### Post by Meghnaad on 2008-07-29
I'm facing a strange problem in shell scripting (i'm using bash)
the script goes like this

[I]#!/bin/bash
# $1 will contain name of user
count=0 #Init count to zero
w | grep "^$1" | while read line   #get only the lines which match user name 
do
        name_what=(`echo "$line" | cut -d ' ' -f 1,8- `)
        if [ ${name_what[0]} == $1 ]
        then
                echo "${name_what[*]}"  #Display user and what he's doing
                let count++ 
        fi
done

echo "$1 is logged in $count times"[/I]

The strange thing is $count is always 0 :(
If I store the out put of *w | grep "^$1"*  in a file and then process it it works fine.

I want to know why count is 0 :confused:

Thanks in advance

---

### Post by ghostdog74 on 2008-07-30
are you sure it even works. Show what you pass to the script (ie $1)
also, describe what you want to do more clearly.

---

### Post by mssever on 2008-07-30
> **Meghnaad said:**
> name_what=(`echo "$1" | cut -d ' ' -f 1,8-`)
This is preferable: ```
name_what="$(echo "$1" | cut -d ' ' -f 1,8-)"
```
        > let count++The easiest way to increment a variable is: ```
(( count+ ))
```Since I never use let, I don't know all its syntax. Perhaps it doesn't support the ++ operator. At any rate, double parentheses are more flexible and easier to use.

---

### Post by Meghnaad on 2008-07-30
**_ghostdog74:_**

Yes you are right shell script was not working properly.
I've made the corrections ( pipe after grep was missing )

I've written this script to find out how many times the user is logged in 
and to print what command is being executed by that user

**_mssever:_**
[I]
name_what=(`echo "$1" | cut -d ' ' -f 1,8-`)[/I] #this will Create name_what as an array

*name_what="$(echo "$1" | cut -d ' ' -f 1,8- )"* #this will Create name_what as string I don't want this

*let count++* #this is bash internal and syntax is correct
I've even tried replacing it with
*count=$(expr $count + 1)* # But still no luck ans is 0

[COLOR="DarkRed"]I've written one awk script which does this very nicely for me.
my question is why count is not getting incremented ?
if i print count in loop (while) it shows increment 
but outside loop it's value is same that i've initlized before while loop[/COLOR]

---

### Post by ghostdog74 on 2008-07-30
> **Meghnaad said:**
> 
I've written this script to find out how many times the user is logged in 
and to print what command is being executed by that user


```

w | awk -v u="$1" 'NR>2 && $1 ~ u{ 
   user[$1]++
   commands[$1]=commands[$1]"|"$NF
}END { 
 for(i in user){
  print i" has " user[i]" logins"
 } 
 for (j in commands) {
  print j" executed these commands: "commands[j]
 }
}'

```

---

### Post by Meghnaad on 2008-07-30
ghostdog:

Thank you,
nice script ( your script is much better and easy to understand than awk script that i wrote)

But I want to know why the count var. is not getting incremented,
when I print count in loop it shows incremented values :)

but when i'm out of the loop it is 0 :confused:

Please help me to understand why ?

---

### Post by ghostdog74 on 2008-07-30
> **Meghnaad said:**
> 
But I want to know why the count var. is not getting incremented,
when I print count in loop it shows incremented values :)

but when i'm out of the loop it is 0 :confused:

which code are you referring to? your first post? If it is, have you tried what msserver has suggested?

---

### Post by Meghnaad on 2008-07-30
0:#!/bin/bash
 1:count=0 
 2:w | grep "^$1" | while read line 
 3:do
 4:[INDENT][/INDENT]name_what=(`echo "$line" | cut -d ' ' -f 1,8- `)
 5:[INDENT][/INDENT]if [ ${name_what[0]} == $1 ]
 6:[INDENT][/INDENT]then
 7:[INDENT][INDENT][/INDENT][/INDENT]echo "${name_what[*]}" 
 8:[INDENT][INDENT][/INDENT][/INDENT]let count++
 9:[INDENT][/INDENT]fi
10:done
11:echo "$1 is logged in $count times"

Hello,
I'll state the problem again,
[COLOR="DarkRed"]MY PROBLEM IS NOT HOW TO WRITE THE SCRIPT BUT IS ABOUT STRANGE BEHAVIOR OF THIS SCRIPT ![/COLOR]

The Script will be called with name of a user as an argument
line "2" will get only lines matching user name ($1) and pass it to input of while.
"read" command will read this input (from w | grep "^$1) one line at a time
and then inside loop users name and command will be displayed
and then count will be incremented
If the user is logged more than once this loop will iterate no. of times the user is logged in.

and once out of loop i'm displaying count which should be equal to no. of times user is logged in.

but it's 0 

if i display count in side loop it shows incremented values 
(Hope I've made myself Clear)

STRANGE !!!

Please Explain me Why ?

---

### Post by ghostdog74 on 2008-07-30
this is how you increment in bash
```

# count=1
# echo $(( count + 1 ))
2

```
to assign the increment back to $count, i leave it to you

---

### Post by Meghnaad on 2008-07-30
Got the solution.

Bourne shell redirected control structures run in a subshell, so the value of x only gets changed in the subshell, and is lost when the loop ends.

[http://cfaj.freeshell.org/shell/cus-faq-2.html#33](http://cfaj.freeshell.org/shell/cus-faq-2.html#33)

---

