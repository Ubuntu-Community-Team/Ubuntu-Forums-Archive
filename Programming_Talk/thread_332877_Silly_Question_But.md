---
title: "Silly Question But"
date: 2007-01-06
forum: Programming Talk
---

### Post by RZero on 2007-01-06
Hello there Ive just installed Ubuntu and I am learning shell scripting, Ive been using VIM to write them, I save them chmod a+x then move them into my bin in my home dir but when I run the script ie $: test1 
it keeps telling me that the command cannot be found, I can run  them in the bin folder using ./test1 but no where else :( Is there some thing I need to do ? I used to use Suse and use freeBSD while at work,  both of which would work once I carried out the chmod and moved it into the bin so I am at a loss to what I'm doing wrong


thanks

Mick

---

### Post by Mirrorball on 2007-01-06
Is it really in ~/bin? Open ~/.bash_profile and check if these lines are there:
```

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

```

---

### Post by RZero on 2007-01-06
Yup its in my home bin, Im using #!/bin/sh on the opening line of the script if that helps

---

### Post by Mirrorball on 2007-01-06
What is the output of:
```
echo $PATH
```

---

### Post by Woodgar on 2007-01-06
I had a similar problem.

However, after a little looking around I discovered that /home/woodgar/bin was not in my default $PATH. After adding it, as suggested by Mirrorball, everything worked just fine.

---

### Post by RZero on 2007-01-06
echo $PATH 

is blank

in the .bash_profile 

# set PATH so it includes user's private bin if it exists
if [ -d ~/bin ] ; then
    PATH=~/bin:"${PATH}"
fi

is in there


take it I have to add my path into it ?

---

### Post by Mirrorball on 2007-01-06
PATH really shouldn't be blank. :-k Log out and log in again?

---

### Post by RZero on 2007-01-06
Ok done that and it shows:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

:confused:

---

### Post by Mirrorball on 2007-01-06
Run this first:
```
PATH=~/bin:"${PATH}"
```
And then your test script.

---

### Post by RZero on 2007-01-07
> **Mirrorball said:**
> Run this first:
```
PATH=~/bin:"${PATH}"
```
And then your test script.


Thank you thats done the trick :D

---

### Post by RZero on 2007-01-07
Spoke to soon :( it runs the scritp but it does not reconise the commands in the scritp,  simple ones like sort and sed, after I try issue simple shell command like ls and it returns command not found I have to quit the shell and start again :(

---

### Post by Mirrorball on 2007-01-07
This really shouldn't have been happenning. Create another user account, logout, login as that user, and test the script.

---

