---
title: "Need help on Script"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by spidex on 2008-09-24
Hi,
I'm trying to write a script using If-Then statement.
My question is, How to begin writing like asking a user to input a name and age. The script will compare the age and categorised them as "young" , "middle age", "Old" ...
Finally the script should be able to display users name, age and the category they fall into eg: Old, young...
I'm trying to learn step-by-step, any help from you all will be very much appreciated. Thank you.:)

---

### Post by ghostdog74 on 2008-09-24
shell script? check my sig for learning bash

---

### Post by anotherdisciple on 2008-09-24
> **spidex said:**
> Hi,
I'm trying to write a script using If-Then statement.
My question is, How to begin writing like asking a user to input a name and age. The script will compare the age and categorised them as "young" , "middle age", "Old" ...
Finally the script should be able to display users name, age and the category they fall into eg: Old, young...
I'm trying to learn step-by-step, any help from you all will be very much appreciated. Thank you.:)

```
#!/bin/bash

read -p "What is your name? " NAMEOFUSER
read -p "How old are you? " AGEOFUSER


if [[ $AGEOFUSER < 30 ]]; then
STATUS=young
elif [[ $AGEOFUSER > 50 ]]; then
STATUS=old
else
STATUS="middle aged"

fi

echo "Your name: $NAMEOFUSER"
echo "Your age: $AGEOFUSER"
echo "$NAMEOFUSER, you are $STATUS."
```

The first part asks the question "What is your name?" and that name is set to the variable $NAMEOFUSER

The second line asks the question "How old are you?" and that number is assigned to the variable $AGEOFUSER.

The next part is an if/then statement that says if the age of the user is less than 30... they are young... if they are older than 50, they are old, otherwise they are middle aged.

The last part writes on the screen... lets say the name is Bob and he is 56... it would print this:

```
Your name: Bob
Your age: 56
Bob, you are old.
```


EDIT: Updated because I confused languages!
EDIT AGAIN: I noticed that I messed something up... haha!

---

### Post by superprash2003 on 2008-09-24
there are many ways to achieve this.. using various programming languages.. are you interested in learning any particular language?

---

### Post by anotherdisciple on 2008-09-24
> **superprash2003 said:**
> there are many ways to achieve this.. using various programming languages.. are you interested in learning any particular language?

True, by script I assumed the OP meant using a shell scripting language... like BASH... so in case you are wondering... that was written in BASH... in fact... that script needs to start with

```
#!/bin/bash
```

I'll edit it!

---

### Post by spidex on 2008-09-25
> **anotherdisciple said:**
> True, by script I assumed the OP meant using a shell scripting language... like BASH... so in case you are wondering... that was written in BASH... in fact... that script needs to start with

```
#!/bin/bash
```

I'll edit it!

I'm using Ubuntu 7.10 After running the script I get this warning errors.
What is your name?jeff
How old are you?28
1.sh: 9: cannot open 30: No such file
1.sh: 9: [[: not found
1.sh: 9: [[: not found
Warning: unknown mime-type for "Your name: jeff" -- using "application/*"
Error: no such file "Your name: jeff"
Warning: unknown mime-type for "Your age: 28" -- using "application/*"
Error: no such file "Your age: 28"
1.sh: 12: Print: not found

---

### Post by spidex on 2008-09-25
> **superprash2003 said:**
> there are many ways to achieve this.. using various programming languages.. are you interested in learning any particular language?

Rite now, my studies requires me to use Ubuntu 7.10
Thanks

---

### Post by ghostdog74 on 2008-09-25
don't use < and [[. use the more "portable" way
```

if [ "${AGEOFUSER}" -lt 30 ]; then
...

```

---

### Post by anotherdisciple on 2008-09-25
> **ghostdog74 said:**
> don't use < and [[. use the more "portable" way
```

if [ "${AGEOFUSER}" -lt 30 ]; then
...

```

Good point... I will fix it....

```
#!/bin/bash

read -p "What is your name? " NAMEOFUSER
read -p "How old are you? " AGEOFUSER


if [ "${AGEOFUSER}" -lt 30 ]; then
STATUS="young"
elif [[ "${AGEOFUSER}" -gt 50 ]]; then
STATUS="old"
else
STATUS="middle aged"
fi

echo "Your name: $NAMEOFUSER"
echo "Your age: $AGEOFUSER"
echo "$NAMEOFUSER, you are $STATUS."
```


About the errors.... did you run it back when I was using print instead of echo? I was confusing 2 languages... whoops! Also, are you running this in the terminal?

I believe that I tested it yesterday and it worked.

---

### Post by anotherdisciple on 2008-09-25
> **ghostdog74 said:**
> don't use < and [[. use the more "portable" way
```

if [ "${AGEOFUSER}" -lt 30 ]; then
...

```

Also, what do you mean by "portable"? This may be a learning experience for me... I'm still a newbie when it comes to shell scripts and programming.

---

### Post by anotherdisciple on 2008-09-25
> **spidex said:**
> Rite now, my studies requires me to use Ubuntu 7.10
Thanks

Well, Ubuntu is the operating system you are running... or better yet... it is the distribution of GNU/Linux that you are running.

Linux can use many different languages. Ubuntu, by default, can use BASH, Python, and I think it can use Korn and the old Bourne shell. Maybe others, but that's the limit of my knowledge.

There is a whole slew of other languages that you can use also. I was just listing the shells that are built-in.

---

### Post by ghostdog74 on 2008-09-25
> **anotherdisciple said:**
> Also, what do you mean by "portable"? This may be a learning experience for me... I'm still a newbie when it comes to shell scripts and programming.

it means this syntax can work even in old bourne shell.

---

### Post by Tux.Ice on 2008-09-25
by portable i believe he means that it is more likely to work on different computer/ubuntu configurations. And the script should work....

---

### Post by spidex on 2008-09-29
Ok great. now i understand how to use -lt and -gt
How about more then and equal or less then and equal ? symbol >= =<

if a student gets 80 marks and above then PASSED
if a student gets 20 marks and below then FAILED

Thanks a lot for helping me.



> **anotherdisciple said:**
> Good point... I will fix it....

```
#!/bin/bash

read -p "What is your name? " NAMEOFUSER
read -p "How old are you? " AGEOFUSER


if [ "${AGEOFUSER}" -lt 30 ]; then
STATUS="young"
elif [[ "${AGEOFUSER}" -gt 50 ]]; then
STATUS="old"
else
STATUS="middle aged"
fi

echo "Your name: $NAMEOFUSER"
echo "Your age: $AGEOFUSER"
echo "$NAMEOFUSER, you are $STATUS."
```


About the errors.... did you run it back when I was using print instead of echo? I was confusing 2 languages... whoops! Also, are you running this in the terminal?

I believe that I tested it yesterday and it worked.

---

### Post by spidex on 2008-09-29
how do i use the draw_box function ? I tried your example but failed.
i get "draw_box not found" message

This is the example : 
clear    # Clear the terminal.
R=2      # Row
C=3      # Column
H=10     # Height
W=45     # Width
col=1    # Color (red)
draw_box $R $C $H $W $col # Draw the box.
exit 0

---

### Post by anotherdisciple on 2008-09-29
> **spidex said:**
> Ok great. now i understand how to use -lt and -gt
How about more then and equal or less then and equal ? symbol >= =<

if a student gets 80 marks and above then PASSED
if a student gets 20 marks and below then FAILED

Thanks a lot for helping me.

Greater than or equal to is -ge
Less than or equal to is -le

Here are some reference cards on the subject >>> [http://tldp.org/LDP/abs/html/refcards.html]("http://tldp.org/LDP/abs/html/refcards.html")


About the draw box... I'm not exactly sure what you mean... Maybe it's a feature I've never used. I'll look into it.

---

### Post by spidex on 2008-10-11
Hi,
I manage to run my script but how do I make this script runs continuosly until user press Q (to quit)..by making use of the command DO..WHILE command

Where do I insert DO..WHILE in the script 

Thanks


> **anotherdisciple said:**
> Good point... I will fix it....

```
#!/bin/bash

read -p "What is your name? " NAMEOFUSER
read -p "How old are you? " AGEOFUSER


if [ "${AGEOFUSER}" -lt 30 ]; then
STATUS="young"
elif [[ "${AGEOFUSER}" -gt 50 ]]; then
STATUS="old"
else
STATUS="middle aged"
fi

echo "Your name: $NAMEOFUSER"
echo "Your age: $AGEOFUSER"
echo "$NAMEOFUSER, you are $STATUS."
```


About the errors.... did you run it back when I was using print instead of echo? I was confusing 2 languages... whoops! Also, are you running this in the terminal?

I believe that I tested it yesterday and it worked.

---

