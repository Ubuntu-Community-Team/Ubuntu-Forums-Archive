---
title: "help with grep"
date: 2010-08-17
forum: Programming Talk
---

### Post by dunryc on 2010-08-17
HI guys 

Hopefully some one more informed than me will no ? 

is there any way to use grep ( or any other command ) to give me lines starting with in a  text file so 

display all commands starting with a I have searched the net but seem unable to find any pertinent results  !! 

Here's hoping cheers guys

---

### Post by DaithiF on 2010-08-17
Hi, you want to search a file for lines which begin with a certain pattern? (not completely clear from your post).

lets say you want to find lines starting with 'a'.  some examples:

```
grep "^a" somefile            # match lines where 1st character is a
grep "^\s*a" somefile       # match lines where 1st non-whitespace character is a
grep -i "^\s*a" somefile    # match lines where 1st non-whitespace character is a or A

```

---

### Post by dunryc on 2010-08-17
that great erally appreciate it 

thanks :D

---

### Post by libssd on 2010-08-17
Not quite what you asked for, but this lists all lines that contain a specific string (in this example, the word **source** ):

```
$ cat *.txt | grep source
4. Re-add remastersys and medibuntu to Synaptic sources.
   sudo gedit /etc/apt/sources.list
# Source: https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560464
Various sources, including: https://help.ubuntu.com/community/AA1/Using
```

Terminal screenshot attached, showing color mapping.

---

### Post by libssd on 2010-08-17
Even easier: use look 

This finds lines beginning with **Source** (but not beginning with source):

```
$ look Source *.txt
Source: https://bugs.launchpad.net/ubuntu/+source/linux/+bug/560464
Source: http://www.webupd8.org/2010/04/install-nautilus-elementary-230-via-ppa.html

```


```

LOOK(1)                   BSD General Commands Manual                  LOOK(1)

NAME
     look &#8212; display lines beginning with a given string

SYNOPSIS
     look [-bdf] [-t termchar] string [file ...]

```

---

### Post by DaithiF on 2010-08-17
> **libssd said:**
> Even easier: use look 


no, read the next part of the manpage:

> DESCRIPTION
     The look utility displays any lines in file which contain string as a
     prefix.  [B]As look performs a binary search, the lines in file must be
     sorted[/B] 

look is intended for looking up words in dictionaries (where the words are sorted), its not a general purpose grep-replacement.

---

### Post by libssd on 2010-08-17
> **DaithiF said:**
> look is intended for looking up words in dictionaries (where the words are sorted), its not a general purpose grep-replacement.
I understand that's what **look** is intended for, but in fact, **look** appears to work as I described. Before posting, I used it against a text file to check.

---

### Post by DaithiF on 2010-08-17
no it doesn't.  for unsorted files it will occasionally match what you are looking up, when its binary search mechanism happens to chance upon a matching line.  but mostly it won't.

to illustrate -- the following uses look to first try to match each line of an unsorted file, then does the same for a sorted version.  
```
$ cat testfile
this
is
a
file
with
various
lines
of
text

$ while read line; do echo "testing '$line'"; look "$line" testfile; done < testfile
testing 'this'
testing 'is'
testing 'a'
testing 'file'
file
testing 'with'
testing 'various'
testing 'lines'
testing 'of'
of
testing 'text'
text

$ sort testfile > testfile.sorted

$ while read line; do echo "testing '$line'"; look "$line" testfile.sorted; done < testfile.sorted
testing 'a'
a
testing 'file'
file
testing 'is'
is
testing 'lines'
lines
testing 'of'
of
testing 'text'
text
testing 'this'
this
testing 'various'
various
testing 'with'
with

```

---

### Post by libssd on 2010-08-17
Thanks for taking the time for the explanation and examples, which describe the correct way to get the desired result using grep.

---

