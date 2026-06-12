---
title: "simple script to tell if a user is logged in or not bash - need comments"
date: 2012-10-24
forum: Programming Talk
---

### Post by lundgren_o on 2012-10-24
I'm taking a a Linux class, I need to check if a user is logged in or not. If no argument is entered, it should ask for username...
Program should exit 0 if user is logged on, and exit 1 if not.
This is what I wrote and it is obviously working, but I also need to comment it out, and I am not sure I understand the function I wrote. I am new to programming...
```
#!/bin/bash

#define my function
function checkuser
{
# for each variable in this command it will do
        for u in `who | cut -f1 -d" " | sort | uniq`
        do
# this is where I thought $u will always be $1 since it is sent from input from user?
        if [ $u = $1 ] ; then
                exit 0
        fi
        done
}
# if no argument was given ask for username.
if [ -z $1 ] ; then
        echo "Enter username: "
        read u
# sends input to function 
        checkuser $u
        exit 1
fi
checkuser $1
exit 1
```

---

### Post by Vaphell on 2012-10-24
you should do something like this:
```
if [ -z $1 ]
then
  read u
else
  u=$1
fi
```
this way you can have only a single test (checkuser $u)

in your function change u to something else for clarity so you don't confuse outer and inner $u. Also you don't need to loop over the list of users and check them one by one in the first place. You can use grep in that pipe chain
```
who | cut -f1 -d" " | grep -qw $u
```
and use its exit status as the exit status of your script

```
$ echo me | grep -q me
$ echo $?
0
$ echo you | grep -q me
$ echo $?
1
```

---

### Post by funicorn on 2012-10-24
```

who | awk '{print $1}' |while read user; do [ "$1" = "$user" ] && exit 0; done

```
And this one runs even faster
```

who |while read user; do [ "$1" = "${user%% *}" ] && exit 0; done

```

The comment is bash is a low-efficient script language so all is to make it as neat as possible. 
a. Running the above way it's unnecessary to use 'uniq' since simply  'read' repeating mismatches is more efficient than 'uniq' handling all duplicate names, not to mention the possibility that first match on certain name completes the whole process. And 'sort' is useless due to similar reason.

b. 'sed', 'awk' and 'grep' are commonly used to handle strings, use them as possible as you can. Specially 'awk' is more efficient than 'cut' in most cases.

c. Pipes, redirections and logic operations are useful to make a script run faster. For example, in the above script, bash doesn't need to print all user names to finish the process due to the second pipe which injects one single user name into the cycling process and one successful match would have finished the process, even though there are left user names spawn in the 'awk print' queue.

Suppose there are 1000 users login into the system, the above script will exit once certain username is matched, without actually dealing with all the 1000 ones. In this way it runs faster and uses less memory.

---

### Post by lundgren_o on 2012-10-25
```
#!/bin/bash

function checkuser
{
        for u in `who | cut -f1 -d" " | sort | uniq`
        do
        if [ $u = $1 ] ; then
                exit 0
        fi
        done
}

if [ -z $1 ] ; then
        echo "Enter username: "
        read u
else
        u=$1
fi

checkuser $u
exit 1
```
So I remade the code a little bit. I still need a bit more explanation on when I call checkuser and send $u with it...? What I don't understand is my for inside the function? I thought my for loop changes $u to the users in "who" command?
Also, when putting the if-else part where I define $u before the function, my script doesnt work.
Ive looked up some guides on functions in programming. But I really got a hard time to understand :). Would be nice for more explanation. Thanks!

---

### Post by Vaphell on 2012-10-25
while your script works, it does so only by accident

Your script badly reuses the same variable in 2 different contexts.
when you pass the parameter from the outside, don't reach to the same variable to modify it ( pass $u which is $1 inside the function but at the same time destroy original value of $u by throwing loop values into it).
In other words local temporary $1 inside the function holds the true value from user input, while at the same time the for loop mangles the u variable that is supposed to hold that true value. You pretty much reversed them.

i slightly modified your script (added few echos to print values and to disable exits)
```
function checkuser
{
**    echo "*** checkuser( $@ ) ***"**

    for u in `who | cut -f1 -d" " | sort | uniq`
    do
        if [ **"**$u**"** = **"**$1**"** ] ; then
           ** echo **exit 0
        fi
  done
}

...

**echo u: $u**
checkuser $u
**echo u: $u**
**checkuser $u**

**echo **exit 1
```
output:
```
Enter username: 
me
u: me
*** checkuser( me ) ***
u: [COLOR="Red"]vaphell[/COLOR]
*** checkuser( [COLOR="Red"]vaphell[/COLOR] ) ***
```
where did this come from? it came from the previous function call where u was used. It's the last value the loop has seen. Letting local trash out is bad mmmkey?
Never perform inner calculations that have no business go outside ever using global variables nor use global scope variables for temporary values.
when you create a function it's interaction with the outside world should be minimal. Running the same thing twice and getting different results should not happen.

change u inside the function to something else, like temp_u and while inside function, forget that $u exists at all. All you should use is $1 and local temp variable.

---

### Post by funicorn on 2012-10-27
[LIST]
[*]a. '*for var in "str1 str2 str3"*' simply goes through *str1*, *str2* and *str3* and replaces *"$var"* with anyone of them.
[/LIST]

[LIST]
[*] b. '*who | cut -f1 -d " " | sort | uniq *' outputs user names.
[/LIST]

[LIST]
[*] c In Bash `` is to obtain the the result of some command, hence *`who | cut -f1 -d " " | sort | uniq`* is actually a list of strings consisting of user names.
[/LIST]

[LIST]
[*] d. So '*for u in `who | cut -f1 -d " " | sort | uniq`*' means going through all user names and replacing *"$u"* with anyone of them.
[/LIST]

[LIST]
[*]e. In each instance of replacement Bash runs the codes inside the loop, then runs into the next one til finishing all the replacements.
[/LIST]

[LIST]
[*]You can compare the '*for var in "str1 str 2 str3"* ' form with the above '*...| while read*' form. The intrinsic difference is the latter uses a **pipe** to transfer variables.
[/LIST]
 
> **lundgren_o said:**
> ```
#!/bin/bash

function checkuser
{
        for u in `who | cut -f1 -d" " | sort | uniq`
        do
        if [ $u = $1 ] ; then
                exit 0
        fi
        done
}

if [ -z $1 ] ; then
        echo "Enter username: "
        read u
else
        u=$1
fi

checkuser $u
exit 1
```So I remade the code a little bit. I still need a bit more explanation on when I call checkuser and send $u with it...? What I don't understand is my for inside the function? I thought my for loop changes $u to the users in "who" command?
Also, when putting the if-else part where I define $u before the function, my script doesnt work.
Ive looked up some guides on functions in programming. But I really got a hard time to understand :). Would be nice for more explanation. Thanks!

---

