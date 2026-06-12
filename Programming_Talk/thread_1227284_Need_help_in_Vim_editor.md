---
title: "Need help in Vim editor"
date: 2009-07-30
forum: Programming Talk
---

### Post by oakdeveloper on 2009-07-30
Hi,

I have a text file which has 20 lines. In all the lines, the beginning of the line has a 3 digit number followed by a space. I tried to do a search and replace in Vim to remove those 3 digits but it doesn't seem to work. Please help me..

```
:%s/\d{3}//gc
```This is the command I gave. But it says "Pattern not found"

Thanks,
Babu

---

### Post by arvevans on 2009-07-30
Pattern matching can be difficult until one has lots of experience in doing it.

As an alternative, and simpler solution...why not save the file and then use the "cut" command to mask off those first 3 character positions:
    
    echo filename | cut -c 4- > newfilename

This might be faster and is based on positional parameters rather than pattern matching.

Arv
_._

---

### Post by Dill on 2009-07-30
I believe you need to precede the *number* of matches with another backslash:

```
:%s/\d\{3}//gc
```

Try that and see if it works.

Cheers,
Dill

---

### Post by oakdeveloper on 2009-07-30
Thanks a lot! It works.

---

### Post by dandaman0061 on 2009-07-30
Yet another suggestion...
Don't get me wrong, regexes definitely have their place, and depending on the size/number of lines in the file, it may be the way to go.  Anyway here is how I would do it (and not have to worry about regex syntax)

- Move cursor to very beginning of file (keystroke: gg)
- Go into visual mode (keystroke: Ctrl+v) notice lowercase 'v'
- Move cursor to bottom of file (keystroke: G)
The whole first column should be highlighted now
- Move cursor to the right 2 places, highlighting the 3 columns (keystroke: ll)
- Now delete them (keystroke: x)

Yay vim.

---

### Post by oakdeveloper on 2009-07-30
Wow! Works like a charm!!! Thanks [dandaman0061]("http://ubuntuforums.org/member.php?u=126481")

---

### Post by Greyed on 2009-08-02
Also when trying to define the pattern try turning on incsearch and then constructing the pattern with a plain / first.  This way you get some sort of feedback as to how far the pattern is matching and when it stops matching.  In this case you'd type in /\d and it would match the first digit but as soon as you typed the non-escaped { the incsearch would fail to match.  You'd know  that's your problem spot.  ;)

---

### Post by veda87 on 2009-08-02
try this too... to remove first 3 chars from all the lines
```
:1,$s/^...//
```
number of dots indicates number of character to be removed.....

---

### Post by Keith_Beef on 2009-08-31
> **oakdeveloper said:**
> Hi,

I have a text file which has 20 lines. In all the lines, the beginning of the line has a 3 digit number followed by a space. I tried to do a search and replace in Vim to remove those 3 digits but it doesn't seem to work. Please help me..

```
:%s/\d{3}//gc
```This is the command I gave. But it says "Pattern not found"

Thanks,
Babu

Here's yet another way to delete three digit numbers at the start of lines:
```
:1,$s/^[0-9]\{3\}//
```

K.

---

### Post by petrus4 on 2009-08-31
> **oakdeveloper said:**
> Hi,

I have a text file which has 20 lines. In all the lines, the beginning of the line has a 3 digit number followed by a space. I tried to do a search and replace in Vim to remove those 3 digits but it doesn't seem to work. Please help me..

```
:%s/\d{3}//gc
```This is the command I gave. But it says "Pattern not found"

I don't know how to do that as a vim command, but I'd quit vim momentarily and write a shell script, like so:-
```

#!/bin/sh

for i in `cat file` # whatever the file is called
do
newstring=`echo $i | sed s"@^[0-9][0-9][0-9] @@"g`
echo ${newstring} >> file.bak
done

mv file.bak file
```

Make sure you use two > signs in the above, as well; that will tell echo to add the next string to the file, rather than replacing everything else in the file with the new string.

---

### Post by DaithiF on 2009-08-31
just for fun, a few more ways in vim
```
:%normal 3x

```similar to some earlier suggestions except that %s is easier than 1,$s
```
:%s/^[0-9]\{3\}//
:%!cut -c4-
:%!sed 's/^[0-9]\{3\}//'

```

---

### Post by Gen2ly on 2009-08-31
> **DaithiF said:**
> ...

similar to some earlier suggestions except that %s is easier than 1,$s

```
:%s/^[0-9]\{3\}//
:%!cut -c4-
:%!sed 's/^[0-9]\{3\}//'

```

Good tips.  Vim's freakin' cool.  Forgot all about executing a command.  I've tried \d before with sed and it doesn't look like it supports it.  What does the 1,$s do?  I've seen this before but usually only on older vim/sed(?) examples.  Obviously 's' is for substitute but what do the other characters mean and why would one use it?

---

### Post by DaithiF on 2009-08-31
1,$ means apply the action that follows ('s' = substitute), on the range of the file from line 1 to $, where $ means the end of the file.
%s means apply the command 's' globally, ie, to every line, and so its equivalent (but shorter) than 1,$s

---

### Post by Gen2ly on 2009-08-31
Ah cool (only known global to this point).  Haven't needed to to ranges yet.  Suppose that's next. :)

---

