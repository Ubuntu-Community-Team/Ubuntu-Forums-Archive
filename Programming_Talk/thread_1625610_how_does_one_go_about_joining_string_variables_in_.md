---
title: "how does one go about joining string variables in Bash?"
date: 2010-11-19
forum: Programming Talk
---

### Post by argedion on 2010-11-19
I am new to Bash programming and I would like to be able to concatenate two variables together for output for a backup bash script I'm currently working on.


An example is :
Mydir="/home/argedion"
file1="/afile.7z
file2="/bfile.7z

In vb I would
Mydir & file1

Is this simular in bash?

---

### Post by ziekfiguur on 2010-11-19
Bash is even easier, since variables will automatically be expanded in a string.
So you can just use

fullname="${Mydir}${file1}"

the {} aren't even necessary, although i think it makes it more readable.

---

### Post by argedion on 2010-11-19
Thanks a bunch I have a few files I'm saving to the same directory and I want to be able to make it easier :D

---

### Post by Vox754 on 2010-11-19
> **argedion said:**
> I am new to Bash programming and I would like to be able to concatenate two variables together for output for a backup bash script I'm currently working on.


An example is :
Mydir="/home/argedion"
file1="/afile.7z
file2="/bfile.7z

In vb I would
Mydir & file1

Is this simular in bash?

I do not recommend including the slash ( / ) as part of the string; I would put it explicitly as part of the string concatenation. This makes it evident that it is a path you are building and not other random string.

For example:
```

full="${HOME}/${var_1}/${var_2}"

```

If you skim through this, you can't tell if it's a path or some other variable you are building:
```

full="${var_3}${var_4}"

```

The braces { } help define the variable when it contains characters that also appear in directories. You can include them everytime, or you may leave them out when there is no confusion.
```

blah="$HOME/${var}_one_two"  # The variable is 'var'
blah="$HOME/${var_one}_two"  # The variable is 'var_one'
blah="$HOME/${var_one_two}"  # The variable is 'var_one_two'

```

Notice the use of $HOME. There are several other variables that are set by bash, including $USER, $SHELL, and others.

---

### Post by argedion on 2010-11-19
Thanks Vox

---

