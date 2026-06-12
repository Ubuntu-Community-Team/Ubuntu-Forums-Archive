---
title: "Unix Sort Question"
date: 2010-05-18
forum: Programming Talk
---

### Post by SNYP40A1 on 2010-05-18
I have a long text file that I would like to sort using Unix sort utility.  The data is simply comma-separated with one entry per line.  The format is:

<Numeric-Date-1>,<Numeric-Date-2>,<Attribute-1>,<Attribute-2>,<Attribute-3>

I want to sort by numeric date 1 and 2.  Numeric-Date-1 is a long (integer) which represents a date in Java.  Numeric-Date-2 a shorter integer which more precisely encodes the time.  So I want to sort by field 1 and only consider field 2 when there are two entries with the same field 1.  If there are two entries with the same Numeric-Date fields, I don't care which order they come in the sorted file.  I tried using the command:

sort -n -t ',' but this did not work.  From the output, it looks like it just lumped the first two fields together.  Does anyone know a command for the above sort?  I could code this in Java / C++, but I'd rather not re-invent the wheel.

---

### Post by amauk on 2010-05-18
the -k switch allows you to specify multiple columns to sort by

```
sort -n -t ',' -k 1,2
```
will sort by column 1, then by column 2

---

### Post by SNYP40A1 on 2010-05-18
> **amauk said:**
> the -k switch allows you to specify multiple columns to sort by

```
sort -n -t ',' -k 1,2
```
will sort by column 1, then by column 2

amauk, thanks for your reply, but that's not quite right.

If I try sorting this:

[PHP]
3,742,DOG
3,79,CAT
[/PHP]  

The output is the same as the input.  However, the last line should come before the first because 79 < 742.  So sort should compare the first column and only look at the second when the data in the first column is the same.

---

### Post by r-senior on 2010-05-18
It worked for me ... ;)

```

$ cat temp.txt 
3,742,DOG
3,79,CAT  
$ cat temp.txt | sort -n -t ',' -k 1,2
3,79,CAT  
3,742,DOG

```

---

### Post by amauk on 2010-05-19
> **r-senior said:**
> It worked for me ... ;)as it should

not sure why SNYP40A1 is getting different results
there's got to be something else going on here

*edit*
confirmed non-working if there's spaces after the commas
could this be the issue?

Working
3,742,DOG
3,79,CAT

not working
3, 742, DOG
3, 79, CAT

---

### Post by rnerwein on 2010-05-19
> **amauk said:**
> as it should

not sure why SNYP40A1 is getting different results
there's got to be something else going on here

*edit*
confirmed non-working if there's spaces after the commas
could this be the issue?

Working
3,742,DOG
3,79,CAT

not working
3, 742, DOG
3, 79, CAT
hi
it's not the spaces -->
it's the [COLOR=Blue]different language[/COLOR] we speak: you know --> decimal point is comma ( . --> , )   :-)
that means: 3,742 is smaller than 3,79  and there for the sort is ok
ciao

---

### Post by SNYP40A1 on 2010-05-20
No, for me it's:
[PHP]
$ cat temp.txt | sort -n -t ',' -k 1,2
3,742,DOG
3,79,CAT[/PHP]

And there are no spaces anywhere.

Although I am using sort function on Cygwin.  I will try on Ubuntu once my brother is done using the computer.  Although...should be the same:

[PHP]
$ sort --version
sort (GNU coreutils) 6.10
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Mike Haertel and Paul Eggert.[/PHP]

---

### Post by rnerwein on 2010-05-21
> **SNYP40A1 said:**
> No, for me it's:
[PHP]
$ cat temp.txt | sort -n -t ',' -k 1,2
3,742,DOG
3,79,CAT[/PHP]And there are no spaces anywhere.

Although I am using sort function on Cygwin.  I will try on Ubuntu once my brother is done using the computer.  Although...should be the same:

[PHP]
$ sort --version
sort (GNU coreutils) 6.10
Copyright (C) 2008 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.

Written by Mike Haertel and Paul Eggert.[/PHP]

hi
again: sort is working -k 1,2 --> this means: highest priority has field 1 and in your example 
field 1 are: 3,742 and 3,79. because the sort priority is first field 1 and 3,742 is smaller than 3,79 field 2
plays no role.
try following to bring sort to look at the second field ( field 2 ).
contens of the file s will be:
3,742,DOG
3,79,CAT
3,742,CAT
cat s | sort -n -t ',' -k 1,2
will give you:
3,742,CAT
3,742,DOG
3,79,CAT
you can see here the sort was going to the second field ( CAT/DOG ) and the result is OK
have fun
ciao

---

