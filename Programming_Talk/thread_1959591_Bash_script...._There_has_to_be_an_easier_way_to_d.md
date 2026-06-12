---
title: "Bash script.... There has to be an easier way to do this"
date: 2012-04-16
forum: Programming Talk
---

### Post by Alphamonkey on 2012-04-16
Well it seems to me like this could be a lot better written and less complex. The point of it was to test to see if the user input "username" exists and if so to figure out if that person is logged on or not using who. This is for my linux class and it just seems to me like this is very poorly written. Please advise on how to make it better. Thanks.

```
1    #!/bin/bash
     2    # script8.2
     3    # A script accept input of a username test to see if that is a valid username. 
     4    # if it is a valid username then it will test to see if that user is logged in
     5    # and output a statement of either logged in or not logged in.
     6    # 
     7    if [ $# -eq 0 ]   #Test to see if there is an argument entered
     8    then
     9        echo "please provide and argument in the form of a valid username:"  #Output if no argument
    10        read usr_input_name # accept a user name
    11        cat /etc/passwd | grep -w $usr_input_name > /dev/null #checks to see if a                 user exists and avoids output
    12        do_i_exist=`echo $?`    #Sets a variable to the exit value or return status
    13        if [ $do_i_exist = 0 ] ; then #if the user exists run the following
    14            who | grep -w $usr_input_name > /dev/null #check to see if the user                 #islogged in and then throw the output                             #into the bit bucket.
    15    
    16            logged_in=`echo $?` #set variable to exit status of previous command
    17            if [ $logged_in -eq 0 ] ; then #check the exit status of previous                 command
    18                echo "user is logged in" #if it returns exit 0
    19            else 
    20                echo "user is not logged in" #if it returns exit 1 or other
    21            fi
    22        else    #if user does not exist run the following
    23            echo "that username was not found. Exiting now"
    24            exit 1
    25        fi
    26    else
    27        cat /etc/passwd | grep -w $1 > /dev/null #checks to see if a                         user exists and avoids output
    28        do_i_exist=`echo $?`    #Sets a variable to the exit value or return status
    29        if [ $do_i_exist = 0 ] ; then #if the user exists run the following
    30    
    31            who | grep -w $1 > /dev/null #bit bucket again
    32            logged_in=`echo $?` #again set variable to exit status
    33            if [ $logged_in -eq 0 ] ; then #check exit status
    34                echo "user is logged in" #if 0
    35            else 
    36                echo "user is not logged in" # if other
    37            fi
    38        else
    39            echo "That user does not exist. Exiting now."
    40        fi
    41    fi
    42    


```

---

### Post by slavik on 2012-04-16
that's pretty much it. check /etc/passwd if the user is there and who/finger if they are logged in. I would not do the echo $? type stuff you do, but compare it directly against 0.

the other problem you are running into is, what if the user exists but never logged in and the user exists in ldap or some such, so their home dir does not exist .. and they are not in /etc/passwd

---

### Post by DrBuzz on 2012-04-16
I'm new to bash, but otherwise an old hand at programming.  I offer this as an untested improvement:
Can someone tell me how to retain all the carefully inserted white space that was lost on submission?

     1    #!/bin/bash
     2    # script8.2
     3    # A script accept input of a username test to see if that is a valid username. 
     4    # if it is a valid username then it will test to see if that user is logged in
     5    # and output a statement of either logged in or not logged in.
     6    # 
     7    if [ $# -eq 0 ]                                        # Test to see if there is an argument entered
     8    then
     9        echo "please provide and argument in the form of a valid username:"  # Output if no argument
    10        read usr_input_name                                # accept a user name
    11    else
    12        usr_input_name=$1
    13    fi
    14
    15    cat /etc/passwd | grep -w $usr_input_name > /dev/null  # see if a user exists and avoids output
    16    do_i_exist=`echo $?`                                   # Sets a variable to the exit value or return status
    17    if [ $do_i_exist = 0 ] ; then                           # if the user exists run the following
    18        who | grep -w $usr_input_name > /dev/null          # see if the user is logged in and then throw
    19                                                           # the output into the bit bucket.
    20        logged_in=`echo $?`                                # Set variable to exit status of previous command
    21        if [ $logged_in -eq 0 ] ; then                     # check the exit status of previous command
    22            echo "user is logged in"                       # if it returns exit 0
    23        else 
    24            echo "user is not logged in"                 # if it returns exit 1 or other
    25        fi
    26    else                                                              # if user does not exist run the following
    27        echo "that username was not found. Exiting now"
    28    fi

---

### Post by r-senior on 2012-04-16
> **DrBuzz said:**
> Can someone tell me how to retain all the carefully inserted white space that was lost on submission?
Wrap it in code tags. Easiest way is to edit the post, select the code and hit the # button in the little toolbar that appears just above the posting window.

If you want to type them instead, the closing tag is [/code], the opening tag is [code].

---

### Post by sisco311 on 2012-04-16
The syntax of the if statement is:
```
if COMMAND; then
    COMMANDS
else
    COMMANDS
fi
```

[ is a shell built-in command; it's NOT part of the syntax. You can do something like:
```
if grep -q ^"$uname": /etc/passwd 
then
    printf '%s\n' "user $uname exists"
fi
```

Instead of **cat foo | grep bar** you should use **grep bar foo**; unless you want to win the [Useless Use of cat award]("http://partmaps.org/era/unix/award.html"). :)

Always use "double quotes" around expansions: "$foo", "$(awk ..)"
 

Errors and warnings shall be redirected to STDERR:
```
printf '%s\n' "$0: WARNING $uname invalid user" >&2
```

For reference, here is how I'd do this in Bash:
```

#!/bin/bash

err ()
{
    printf '%s\n' "USAGE: $0 USER..."
    exit 1
} >&2


if [[ -z "$1" ]] # or: if (( "$#" == 0 ))
then
    err
fi

for uname
do
    if grep -q ^"$uname": /etc/passwd
    then
        printf '%s\n' "$uname is in the passwd file"
        if who | grep -q ^"$uname "
        then
            printf '%s\n' "$uname is logged in"
        else
            printf '%s\n' "$uname is not logged it"
        fi
    else
        printf '%s\n' "$0: WARNING: $uname invalid user" >&2
    fi
done

```

---

### Post by DrBuzz on 2012-04-17
Thanks, will do it that way from now on!

---

