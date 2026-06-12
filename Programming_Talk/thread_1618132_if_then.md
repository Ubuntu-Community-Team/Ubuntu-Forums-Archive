---
title: "if then"
date: 2010-11-10
forum: Programming Talk
---

### Post by Drenriza on 2010-11-10
anyone who can tell me why this does not work

```
##Baseline
if [ /video1/T1/ ] ; then
        ls /video1/ | awk '{ print $1 }' > /video1/T1
else
        echo "Baseline already exists"
fi
```

or

```
##Baseline
if /video1/T1/ ; then
        ls /video1/ | awk '{ print $1 }' > /video1/T1
else
        echo "Baseline already exists"
fi
```

T1 is just a text file. What i want is the if then command to create it if it does not already exist, and if it already exist. Just say that it does exist.

But it has been a while since ive been using if then last, and aparently i cant get it to work correctly. Since if the file already exist it does not say that it already exist. As if the echo command does not get executed.

Thanks on advance.

---

### Post by SeijiSensei on 2010-11-10
First, if T1 is a file, don't append a trailing slash.  Bash will interpret T1 as a directory in that case.  Next, you need to use a conditional expression to test for the file's existence like this:

```

if [ -s /video1/T1 ] 

```

This is true if T1 exists and has non-zero length.  See [http://www.gnu.org/software/bash/manual/bashref.html#Bash-Conditional-Expressions](http://www.gnu.org/software/bash/manual/bashref.html#Bash-Conditional-Expressions).

---

### Post by Drenriza on 2010-11-12
It says
line 24: syntax error near unexpected token `else'

THIS ->  if [ -s /video1/T1 ]
is line 24

this is the whole if command
```
if [ -s /video1/T1 ]
        ls /video1/ | awk '{ print $1 }' > /video1/T1
else
        echo "Baseline already exists"
fi
```

im not sure what
> -s fileTrue if file exists and has a size greater than zero. Means

---

### Post by Arndt on 2010-11-12
> **Drenriza said:**
> It says
line 24: syntax error near unexpected token `else'

THIS ->  if [ -s /video1/T1 ]
is line 24

this is the whole if command
```
if [ -s /video1/T1 ]
        ls /video1/ | awk '{ print $1 }' > /video1/T1
else
        echo "Baseline already exists"
fi
```



You need a semicolon here and there. This ought to be the right syntax, but I haven't run it:

```
if [ -s /video1/T1 ]; then
        ls /video1/ | awk '{ print $1 }' > /video1/T1;
else
        echo "Baseline already exists";
fi
```

Look in the man page for 'sh' or 'bash'.

---

### Post by SeijiSensei on 2010-11-12
> **Drenriza said:**
> It says
line 24: syntax error near unexpected token `else'

As Arndt said, you were missing the "then".

-s returns true when:

a)  the file or directory exists, and
b)  the file or directory is not empty (non-zero size).

You can test this by creating a zero-length file with the touch command:

```

$ touch testfile
$ ls testfile -l
-rw-r--r-- 1 xxx xxx 0 2010-11-12 09:38 testfile

```

This creates an empty file named "testfile".  This file would fail the -s test because it has zero length.

There are many other testing options; see the link to the bash documentation I posted above for the others.

---

### Post by Drenriza on 2010-11-15
Thanks guys.

Works now :)

And i will read the link and try to get wiser.\\:D/

---

### Post by Drenriza on 2010-11-17
Their is something i dont understand.

When using the -s in creating T1 if i do
```
if [ -s /video1/T1 ]
        ls /video1/ | awk '{ print $1 }' > /video1/T1
else
        echo "Baseline already exists"
fi
```Then it says that the Baseline already exist, when it dosent. And do not create it. But if i do
```
if [ /video1/T1 ]
        ls /video1/ | awk '{ print $1 }' > /video1/T1
else
        echo "Baseline already exists"
fi
```It creates T1, when it does not exist. But if it already exist it does not say that it do so.
Whats up with that?

---

### Post by Drenriza on 2010-11-17
Solved.

```
if [ -s /video1/T1 ]
        echo "Baseline already exists"
else
        ls /video1/ | awk '{ print $1 }' > /video1/T1
fi
```
Now it works.

---

### Post by spjackson on 2010-11-17
> **Drenriza said:**
> Solved.

```
if [ -s /video1/T1 ]
        echo "Baseline already exists"
else
        ls /video1/ | awk '{ print $1 }' > /video1/T1
fi
```Now it works.
I don't see how it could possibly work without a "then", but I'm glad that your problem is solved. Maybe you are using a different shell.

---

### Post by Drenriza on 2010-11-17
> **spjackson said:**
> I don't see how it could possibly work without a "then", but I'm glad that your problem is solved. Maybe you are using a different shell.

argh sorry, i just copy plasted here from an old post before the ; then

```
if [ -s /path/Baseline ]; then
    echo "something"
else
    ls /video1/ | awk '{ print $1 }' > /path/Baseline
fi
```
sorry my bad, that is what it looks like.

#11 hey i had a million things going, so instead of being snide, then just say.
Hey, you sure you not made a mistake their?
or
Hey, you sure that that is what you mean?

Anyways edited.

---

### Post by spjackson on 2010-11-17
> **Drenriza said:**
> argh sorry, i just copy plasted here from an old post before the ; then

```
##Baseline
if [ /video1/T1/ ] ; then
        echo "something"
else
        ls /video1/ | awk '{ print $1 }' > /video1/T1
fi
```sorry my bad, that is what it looks like.
So now you've gone back to not using -s. Oh well, if it works then good for you.

---

