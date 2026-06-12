---
title: "how to navigate to subdirectories in a shell script"
date: 2010-11-23
forum: Programming Talk
---

### Post by jamesbon on 2010-11-23
I am having a directory.This directory has a lot of subdirectories which contain html pages and some c source code files,Makefiles etc etc.The script I am trying to write would be executed from one directory which has all these subdirectories.
Following is the set of directories and files you can see
```
ls
delete.sh  lddbus   Makefile      misc-progs  sbull  scullc  scullp  short       simple  snull  usb
include    LICENSE  misc-modules  pci         scull  sculld  scullv  shortprint  skull   tty

```
Some of them are directories and some are files in the subdirectories above there are further subdirectories and html pages also which I want to eliminate.
The manual way would be do go to each directory and remove the pages via following command 
```
rm *.html* 

```
Since the html page has name ending with ```
?=/something 
``` sort of names.
So I decided to write a shell script.
But what I am not clear is how will I take directory names as arguments in my shell script.If I decided to use a for loop or some thing similar.
In this case what should I be doing?

---

### Post by Arndt on 2010-11-23
> **jamesbon said:**
> I am having a directory.This directory has a lot of subdirectories which contain html pages and some c source code files,Makefiles etc etc.The script I am trying to write would be executed from one directory which has all these subdirectories.
Following is the set of directories and files you can see
```
ls
delete.sh  lddbus   Makefile      misc-progs  sbull  scullc  scullp  short       simple  snull  usb
include    LICENSE  misc-modules  pci         scull  sculld  scullv  shortprint  skull   tty

```
Some of them are directories and some are files in the subdirectories above there are further subdirectories and html pages also which I want to eliminate.
The manual way would be do go to each directory and remove the pages via following command 
```
rm *.html* 

```
Since the html page has name ending with ```
?=/something 
``` sort of names.
So I decided to write a shell script.
But what I am not clear is how will I take directory names as arguments in my shell script.If I decided to use a for loop or some thing similar.
In this case what should I be doing?

```
find . -name '*.html*' | xargs rm
```

maybe?

---

### Post by DaithiF on 2010-11-23
or using just the find command:
```
find . -name '*.html*' -exec rm -f {} \;

```

---

### Post by dwhitney67 on 2010-11-23
another variant using find:
```

find . -name '*.html*' -delete

```

---

### Post by jamesbon on 2010-11-24
No none of these.I want to have a shell script which should navigate to each subdirectory and delete.This is for learning purpose.
So I want to know if I write some thing like
```

#!/bin/bash
somevariable=`ls -l`
for (if somevariable has a directory)
rm *.html*

```In the above sort of shell script I am storing the output of ls -l in *somevariable*.
I want to use this *somevariable* in for loop in my shell script.

---

### Post by dwhitney67 on 2010-11-24
:confused:

```

#!/bin/bash

echo
echo -n "Top-level directory for deleting HTML files? "
read dir

find $dir -name '*.html*' -delete

echo
echo "Done!"

```
Yeah, very complicated script.  No wonder you had trouble writing it yourself.

---

### Post by jamesbon on 2010-11-24
> **dwhitney67 said:**
> :confused:

find $dir -name '*.html*' -delete


I do not want to use find in my script.

---

### Post by Arndt on 2010-11-24
> **jamesbon said:**
> No none of these.I want to have a shell script which should navigate to each subdirectory and delete.This is for learning purpose.
So I want to know if I write some thing like
```

#!/bin/bash
somevariable=`ls -l`
for (if somevariable has a directory)
rm *.html*

```In the above sort of shell script I am storing the output of ls -l in *somevariable*.
I want to use this *somevariable* in for loop in my shell script.

You can use the program 'stat' to find out the type of a file, for example if it is a directory.

---

### Post by dwhitney67 on 2010-11-24
> **jamesbon said:**
> I do not want to use find in my script.

Ahh... you are working on a **homework** problem with very specific requirements handed out by your teacher, probably with one that stipulates that you cannot use "find".

Consider using "ls -R" and "stat" (as Arndt suggested).

---

### Post by jamesbon on 2010-11-25
> **dwhitney67 said:**
> Ahh... you are working on a **homework** problem with very specific requirements handed out by your teacher, probably with one that stipulates that you cannot use "find".

Consider using "ls -R" and "stat" (as Arndt suggested).
This is the most non sensical reply you have ever given me in my questions.This is not a homework problem if you do not know how to do so do not reply.

---

### Post by ziekfiguur on 2010-11-25
use for to loop through all the files in a folder, use if to test if the file is a folder, cd to go to that folder and cd .. to go back when you are done in that folder.
If you want to use recursion, you will have to define functions, you can't use a linear script.

---

### Post by dwhitney67 on 2010-11-25
> **jamesbon said:**
> This is the most non sensical reply you have ever given me in my questions.This is not a homework problem if you do not know how to do so do not reply.

I no longer am willing to hold your hand at every little problem you have.  Figure out the problem on your own, given the suggestions offered, or go back to nursery school and whine/complain there.

If you are not working on a homework problem, then there is absolutely no reason on earth why you should not be able to use the "find" command.

Don't bark at someone who tries to help you.  Continue it up, and you might face a situation where no one will help you.

As for myself, I will NEVER help you again.  You are a fool who doesn't appreciate anything offered.

---

### Post by jamesbon on 2010-11-26
> **dwhitney67 said:**
> 
If you are not working on a homework problem, then there is absolutely  no reason on earth why you should not be able to use the "find" command.

Don't bark at someone who tries to help you.  Continue it up, and you might face a situation where no one will help you.

As for myself, I will NEVER help you again.  You are a fool who doesn't appreciate anything offered.
Sorry for that **dwhitney67.**
The reason I posted such that was I was frustrated with people telling me that I am discussing home work problems here.(Since you also said the same so I got upset) I do not ask for any home work problems here.Since some one reading this thread  might understand from your reply that the question I asked is  homework problem and they might not reply hence I was frustrated at this.By your message (this being a home work problem) some one who might have replied would not reply.I apologize for being rude but I do not discuss any home work problem here.I just get an idea to do some thing and then while doing I post if any thing comes to mind here.This problem of deleting I do understand that your find logic is good and works very well.But for learning sake(as an experiment) I did not wanted to use find.

Following is what I am aiming at.

```
for d in * .[!.]* ..?*; do
    test -d "${d}" && ls "${d}"
done

```and then ```

function f {
    cd "$1"
    # do something in this dir
    for d in * .[!.]* ..?*; do
        cd "$1"
        test -d "$1/$d" && f "$1/$d"
    done
}

f "`pwd`"
```> **dwhitney67 said:**
> 
As for myself, I will NEVER help you again.  You are a fool who doesn't appreciate anything offered
You are a mature member of community and you should not react to such pithy things by newbies.Your messages give a lot of encouragement to people like me to
keep doing the research.
I totally appreciate your help in various other threads which you gave to me.Specially the thread where I asked AF_INET and a socket file being created inside the directory where I had locally created the socket.I remember all your messages and they have given a  lot of insight to my understanding.
Please accept this as a sincere apology and do not quit.I do not mean to offend I was frustrated that I did not expected from you at least.

---

