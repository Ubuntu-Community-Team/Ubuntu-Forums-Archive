---
title: "cd in script"
date: 2007-01-13
forum: Programming Talk
---

### Post by YourFriendlyGopher on 2007-01-13
Hi everyone,

I'm new to bash scripting and I'm trying to make a simple script that'll move to my programming folder and any of its subfolders if given as arguments.

e.g. Typing 'code C++' would be equivalent to 'cd ~/programming/C++/' (yeah, I'm lazy :P)

The script:

```
#!/bin/bash

cd ~/programming/ # cd to programming folder

if [ $1 ] # If subfolder is specified, cd to the folder
then
    cd $1 2> /dev/null
    if [ $? -ne 0 ]
    then
        echo -e "Could not find directory:" $1
    fi
fi
```

The problem is that when run, the cd command only 'cds' in a forked(?) bash process, instead of the one it's executed from. So basically what I'm asking is how to make the current shell execute a script rather than a newly created one. Any help with this would be appreciated, thanks.

---

### Post by jblebrun on 2007-01-13
You have to call the script file using *source*.

I.e., if it's called prog.sh

```

source prog.sh

```

Have you tried using aliases?

---

### Post by YourFriendlyGopher on 2007-01-13
Ah brilliant - it works, thanks! Yeah I used to have an alias to just my programming folder but I wanted to make something more flexible, and something easy to practice scripting with.

Now where is that damn [resolved] tag option? :-k

---

### Post by jblebrun on 2007-01-13
> **YourFriendlyGopher said:**
> Ah brilliant - it works, thanks! Yeah I used to have an alias to just my programming folder but I wanted to make something more flexible, and something easy to practice scripting with.

Now where is that damn [resolved] tag option? :-k

Well, aliases can still help you here... alias prog="source prog.sh" then you don't have to type source every time :-)

---

### Post by jblebrun on 2007-01-13
> **YourFriendlyGopher said:**
> Hi everyone,

I'm new to bash scripting and I'm trying to make a simple script that'll move to my programming folder and any of its subfolders if given as arguments.

e.g. Typing 'code C++' would be equivalent to 'cd ~/programming/C++/' (yeah, I'm lazy :P)

The script:

```
#!/bin/bash

cd ~/programming/ # cd to programming folder

if [ $1 ] # If subfolder is specified, cd to the folder
then
    cd $1 2> /dev/null
    if [ $? -ne 0 ]
    then
        echo -e "Could not find directory:" $1
    fi
fi
```

The problem is that when run, the cd command only 'cds' in a forked(?) bash process, instead of the one it's executed from. So basically what I'm asking is how to make the current shell execute a script rather than a newly created one. Any help with this would be appreciated, thanks.

I just realized another thing you can do... define a function in your .bashrc file.

like:

```

function prog {
cd ~/programming/ # cd to programming folder

if [ $1 ] # If subfolder is specified, cd to the folder
then
    cd $1 2> /dev/null
    if [ $? -ne 0 ]
    then
        echo -e "Could not find directory:" $1
    fi
fi
}

```

Then all of your login shells will have a command called prog that you can use.

it's too bad that aliases can't have arguments!

---

### Post by YourFriendlyGopher on 2007-01-13
> Well, aliases can still help you here... alias prog="source prog.sh" then you don't have to type source every time 

Ha yeah I already did that, neglected to mention it. :p

> I just realized another thing you can do... define a function in your .bashrc file.

Ooh nice, thanks for the tip! That's gunna come in handy :)

---

