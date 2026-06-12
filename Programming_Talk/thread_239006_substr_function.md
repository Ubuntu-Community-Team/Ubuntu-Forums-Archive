---
title: "substr function"
date: 2006-08-18
forum: Programming Talk
---

### Post by Langstracht on 2006-08-18
I am trying to replicate some BASIC functionality in Unix.

I have a loop which looks at all the files in a directory and culls them based on their names.  Their names however vary and can only be "tested" by looking for a string within the file name.

So I want to test whether filename contains *lena* for example.  

something like [ $filename = *lena ]

However the syntax eludes me.

Anyone know?

TIA

---

### Post by waldschm on 2006-08-18
In the syntax of BASIC I used the syntax for a substring was:

IF c$ = b$[1:4] THEN

END IF

but I'm slightly confused as to whether you are trying to write a BASIC interpreter/compiler or simply writing a program in a pre-existing framework?

---

### Post by Langstracht on 2006-08-18
Sorry for anything misleading. 

Since I did/do not know the Unix terminology I referred to BASIC's.  

However I am trying to write a Unix script which will cull files having identified what to do with them from a (sub)string within the file name.

So, as I said, something like

for loop in 'ls -1'
do
if [ $loop = *str* ]; then
cull number1
fi
if [ $loop = *str2* ]; then
cull number2
fi
done

Sorry again

---

### Post by waldschm on 2006-08-18
Ahh this is a shell script ok. The syntax is:

substring=${string_variable_name:starting_position:length}

so for example:
bigstring="this is a test"
substring=${string:4:3}

---

### Post by Langstracht on 2006-08-18
I guess my memory of BASIC is not nearly as good as I thought it was.  And substr is not what I remembered it as.

The sought string fragment is not in a known position so using a position, length statement isn't going to work I'm afraid.

I need to look for "str" somewhere, anywhere in the filename.

Sorry for all this messing about ...

---

### Post by Lunar_Lamp on 2006-08-18
For the if statement, if you just want to identify a filename that contains "foo" at amy point:

```
for loop in 'ls -1'
do
if [ "$loop" = "*str*" ] ; then
 #do some stuff
elif [ "$loop" = "*str2*" ] ; then
 #do some stuff
fi
done 
```

I'm not sure what you mean by cull, do you mean delete?  If so, the unix command is "rm".  The syntax for the if statements is correct (though you will need to remove the #'s of course), but my loop knowledge is not very good (I'm also new to bash), so it may be wrong.

---

### Post by Langstracht on 2006-08-19
Thanks for the response.

I think your code is right (insofar as no error messages result) but, I haven't been able to accomplish what I wanted.  No I didn't want to delete the files, just move 'em around (depending on their name - or at least this "substr" in their name.

The script is:

#!/bin/sh
cd .data/
for loop in "ls -1 *"
do
if [ "$loop" = "*abc*" ] ; then
cp $loop  Desktop/First
fi
done

A filename containing "abc" IS in the directory but no file gets copied. There are also many files that do NOT contain "abc" but changing = to != doesn't result in any files being copied either.

Perhaps my understanding that "loop" takes on the filenames one by one is the thing that's wrong.

Anyone know?

---

