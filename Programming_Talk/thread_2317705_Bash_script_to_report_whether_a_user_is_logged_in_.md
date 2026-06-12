---
title: "Bash script to report whether a user is logged in or not"
date: 2016-03-18
forum: Programming Talk
---

### Post by henrik-schewenius on 2016-03-18
Hi,
I'm taking a Linux course. 
One task is creating a script to check whether a user is logged in or  not. 
The script run with username for argument. If there is none, it is to be prompted for.
The script is to exit 0 if user is logged in, and exit 1 if not.

```

#!/bin/bash

function checkUser
{
    for u in $(who | awk '{print $1}' | sort | uniq)
    do 
        if [ "$u"="$user" ]; then
            echo "User $u is logged in."
            echo "Exit status: $?"
            exit $?
        else
            "User $u is not logged in."
            echo "Exit status: $?"
            exit $?
        fi
    done
}

if [ -z $1 ]; then
    echo "User to check:"
    read user
else
    "$user"="$1"
fi
checkUser $1

```

There are issues however.
Executing the script with argument, there is error message:
```

$ ./checkuser henrix
.checkuser: line23: =henrix: command not found
User adam is logged in.
Exit status 0.

```

Running the script without argument, it doesn't even consider entered name:
```

$ ./checkuser
User to check: henrix
User adam is logged in.
Exit status 0.

```

For this script, I keep two users logged in:
```

$ who | awk '{print $1}' | sort | uniq
adam
henrix

```

I was only recently introduced to Bash, and this is my first forum post.
I've done my best to provide information. I hope someone can shed light on this.
Thanks.

This is a follow-up to [http://ubuntuforums.org/showthread.php?t=2075873](http://ubuntuforums.org/showthread.php?t=2075873) (closed).

---

### Post by papibe on 2016-03-18
Hi 
This
```
    "$user"="$1"
```
should be
```
    user="$1"
```
In other words, when assigning a variable you should just use the bare name.

Another observation: I believe you want to make sure the variable 'user' holds the correct value before calling checkUser, so I would call the function like this:
```
checkUser "$user"
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by henrik-schewenius on 2016-03-19
Thanks for the quick response!

I've done the proposed changes, and since the error message is gone.
However, the script exits as soon as the first logged on user (adam) is found.

I have also tried adding another equal sign. Still, the result is the same:
```

if [ "$su"=="$user" ]; then ...

$ ./checkUser asdf
User adam is logged in.
Exit status 0.


$ ./checkUser
User to check: asdf
User adam is logged in.
Exit status 0.

```

I should add, these are the file properties:
```

$ ls -lh ./checkUser
-rwxrwxr-x 1 henrix henrix 381 mar 19 11:14 ./checkUser
 
```

---

### Post by spjackson on 2016-03-20
> **henrik-schewenius said:**
> 
I've done the proposed changes, and since the error message is gone.
However, the script exits as soon as the first logged on user (adam) is found.

I have also tried adding another equal sign. Still, the result is the same:
```

if [ "$su"=="$user" ]; then ...

```

I would always write that with a space either side of the ==, because otherwise I'd expect the expression to expand to a single token. I could be mistaken.

However, the fundamental issue is the algorithm in the for loop. In both the if and the else branch, you do something then exit. Therefore you will never look at more than one item.

---

### Post by henrik-schewenius on 2016-03-20
Good point, not to exit both if and else.

As for the brackets, I did try [ "$u" == "$user" ] (space before and after equal signs), but that results in "command not found".
Double brackets made no difference.

I've added a check of $user for each case:
```

$ cat ./checkuser
#!/bin/bash

function checkUser 
{
    for u in $(who | awk '{print $1}' | sort | uniq)
    do 
        if [ "$u"=="$user" ]; then
            echo "\$u $u is logged in."
            echo "\$user = $user"
        else
            "\$u $u is not logged in."
            echo "\$user = $user"
        fi
    done
}

if [ -z $1 ]; then
        echo "User to check for login status:"
        read user
else
        user="$1"
fi

checkUser "$user"
exit $?

```

Output:
```

$ ./checkuser asdf
$u adam is logged in.
$user = asdf
$u henrix is logged in.
$user = asdf

```

Conclusion: Despite $u not being equal to $user, that statement is still run!

---

### Post by papibe on 2016-03-20
There are several things.

**Syntax**
You should use spaces to separate the equal symbol and the variables:
```
if [ "$u" = "$user" ]; then
```

Line 13 is just a string. I think you are missing an 'echo'.

**Logic**
Using proper parameter on a function: inside the function checkUser, you should access the parameters as $1, $2, etc. Right now, you're using a global variable, which kind of defeat the use of the function.

Error message is printing "$u" which is index variable of the 'for'. It would be more consistent with your current logic to print "$user is logged in". Going one step forward, and considering the previous point, you should be printing "$1 is logged in"

The structure of the function is not accomplishing what you want. You are trying to looping for each logged user, that's good. However, the if-else is comparing the first one, and exiting the program. That is why it never gets to  'asdf'.

There a couple of approaches to solve this:

[LIST]
[*]If you match the user inside the 'for' then exit, but do nothing otherwise. Once you complete the 'for', you are in the position to print "not logged", or
[*]Use a flag, initially false, to indicate if the user is matched. If you match it, set the flag to true. After the loop is finish, you can use a similar if-then as you have now to to print whether the user was found.
[/LIST]
Does that help? Let us know how that goes, and if you have more questions.
Regards.

---

### Post by henrik-schewenius on 2016-03-22
Thanks for input. 
I've seen to your suggestions, and have made progress.
There is an odd behaviour though.

Current code:
```

#!/bin/bash

function checkUser 
{
    for u in $(who | awk '{print $1}' | sort | uniq)
    do 
        if [ "$u" = "$user" ]; then
            status=1
        else
            status=0
        fi
    done

    if [ "$status" = "1" ]; then
        echo "status: $status: $user is logged in."
    else
        echo "status: $status: $user is not logged in."
    fi

    echo "Exit status $?"
    exit $?
}

if [ -z "$1" ]; then
        echo "User to check for login status:"
        read user
else
        user="$1"
fi

checkUser "$1"

```

Somehow, only one user is reported logged in, not the first one in order which would have been expected:
```

$ who | awk '{print $1}' | sort | uniq
adam
henrix

$ ./checkuser henrix
status: 1: henrix is logged in. 
Exit status 0

$ ./checkuser adam
status: 0: adam is not logged in.
Exit status 0

```

---

### Post by papibe on 2016-03-22
Right now the variable 'status' changes value on every iteration, so if the user is found the first time, the second time is forgotten. I'd recommend setting a default value before the loop, and only changing it if the user matches.

Something like this (note that you need to compare $u with $1, not $user):
```

function checkUser 
{
    status=0
    for u in $(who | awk '{print $1}' | sort | uniq)
    do 
        if [ "$u" = "**[COLOR="#B22222"]$1[/COLOR]**" ]; then
            status=1
        fi
    done

    if [ "$status" = "1" ]; then
        echo "status: $status: $1 is logged in."
    else
        echo "status: $status: $1 is not logged in."
    fi
}

```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by henrik-schewenius on 2016-03-28
I believe it's working now! 
Replacing $user for $1 the script would not work when run without argument:
```

#!/bin/bash

function checkUser 
{
    status=0

    for u in $(who | awk '{print $1}' | sort | uniq) 
    do 
        if [ "$u" = "$user" ]; then
            status=1
        fi
    done

    if [ "$status" = "1" ]; then
        echo "$user is logged in."
        exit 0
    else
        echo "$user is not logged in."
        exit 1
    fi
}
if [ -z $1 ]; then
    echo "User to check:"
    read user 
else
    user=$1
fi

checkUser $1

```

Confirmation:
```

$ ./checkuser asdf
asdf is not logged in.
$ echo $?
1

$ ./checkuser adam
adam is logged in.
$ echo $?
0

$ ./checkuser
User to check: asdf
asdf is not logged in.
$ echo $?
1

$ ./checkuser
User to check: henrix
henrix is logged in.
$ echo $?
0

```

---

### Post by papibe on 2016-03-28
I' glad you are making progress :D

Note that the script is working because the function checkUser is receiving its parameters via a global variable: user. This may work, but it is not how a function should work. As it is right now you may call the function without parameters and it would work:
```
...

if [ -z $1 ]; then
    echo "User to check:"
    read user 
else
    user=$1
fi
checkUser

...
```
Take a look at this example:
```
#!/bin/bash

function checkUser 
{
    echo "parameter: $1"
}

if [ -z $1 ]; then
    echo -n "Enter word: "
    read word 
fi

checkUser "$1"
checkUser "$word"
checkUser "bye"

```
Then:
```
$ ./script.sh 
Enter word: hello
parameter: 
parameter: hello
parameter: bye


$ ./script.sh hola
parameter: hola
parameter: 
parameter: bye
```
I hope that points you in the right direction. Let us know if you need more help with that.
Regards.

---

### Post by henrik-schewenius on 2016-04-03
Aplogies for late response.

Being able to call the function without parameters, does that mean ending the script with "checkUser" and not "checkUser $1"?
I've been unable to find another way than a global variable (user), "read $1" for instance. As expected, it doesn't work.
STDIN has been considered, but I can't find such a folder (/dev/stdin or similiar).

```

#!/bin/bash

function checkUser 
{
    status=0

    for u in $(who | awk '{print $1}' | sort | uniq) 
    do 
        if [ "$u" = "$1" ]; then
            status=1
        fi
    done

    if [ "$status" = "1" ]; then
        echo "$1 is logged in."
        exit 0
    else
        echo "$1 is not logged in."
        exit 1
    fi
}

if [ -z $1 ]; then
        echo -n "User to check: "
        read $1 #Does not work!
fi

checkUser "$1"

```

---

### Post by henrik-schewenius on 2016-04-20
Latest edit:

```

#!/bin/bash

function checkUser 
{
    status=0

    for u in $(who | awk '{print $1}' | sort | uniq) 
    do 
        if [ "$u" = "$1" ]; then
            status=1
        fi
    done

    if [ "$status" = "1" ]; then
        echo "$1 is logged in."
        exit 0
    else
        echo "$1 is not logged in."
        exit 1
    fi
}

if [ -z "$1" ]; then
        echo -n "User to check: "
        read user
else    
    user=$1
fi
checkUser $user

```

Anything up for discussion?

Cheers.

---

### Post by papibe on 2016-04-21
It looks good :D

---

