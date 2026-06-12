---
title: "super easy BASH null if command line args question"
date: 2011-03-01
forum: Programming Talk
---

### Post by highspider on 2011-03-01
grrr i get error while checking for null in $1 command line arg[] number 1

```

#!/bin/bash
# just search my movie dir for a movie, use grep list all so i only have to have
# a part or 1 whole word of title to show the movie
# why: I forget what's in there  

dir1="/storage/Movies"
dir2="/storage/Movies/NewMovies"

#make sure search is not empty - null
if [ $1 !=  0 ]; then
 # bash check if dir1 exists
 if [ -d $dir1 ]; then
   echo ... $dir1 ...
   #list dir and grep searchname
   ls  $dir1 | grep $1
 fi
 #in line no while just two dir  
 if [ -d $dir2 ]; then
   echo ... $dir2 ...
   ls $dir2 | grep $1
 fi
else
 echo usage: $0 moviename
 echo note moviename can be any part of the whole title   
fi 
   
```i get 
line 10: [: !=: unary operator expected
if arg1 is left null

i don't know what to change line to 
```
#make sure search is not empty - null
if [ $1 !=  0 ]; then
```

---

### Post by SeijiSensei on 2011-03-01
Try 

```

if [ "$1" != "" ]

```

---

### Post by highspider on 2011-03-01
> **SeijiSensei said:**
> Try 

```

if [ "$1" != "" ]

```

thanks works perfect. 

I use the cheesier thru .bash_aliases all time before downloading stuff. fast, easy and kinda cheesy.
I tried 
if [ $1 != "" ] with out string quotes on the var cmd arg and got the same i didn't think of making the arg in string quotes.  

you rock 
:guitar:SeijiSensei:guitar:

---

### Post by jason.m on 2011-05-03
Not sure why I was told this long ago, but I have been following their advice ever since.

if [ "$1" != "" ]; then

should be:

if [ "x$1" != "x" ]; then


There was a reason for this. Something about if $1 happens to be non-present, and not necessarily just null. Previous case usually works though! the x adds just one more level of redundancy.


Just my little FYI on the matter,

cheers!

---

### Post by Vaphell on 2011-05-03
another way to skin the cat
if [ -z "$1" ]; then

---

### Post by kaibob on 2011-05-03
> **jason.m said:**
> Not sure why I was told this long ago, but I have been following their advice ever since.

if [ "$1" != "" ]; then

should be:

if [ "x$1" != "x" ]; then

[SNIP]

This whole issue is discussed under item 4 on the following page:

[http://mywiki.wooledge.org/BashPitfalls?highlight=%28\bCategoryShell\b%29](http://mywiki.wooledge.org/BashPitfalls?highlight=%28\bCategoryShell\b%29)

It generally recommends that the x$var solution be avoided. 

> You may have seen code like this:

      [ x"$foo" = xbar ] # Also right!

The x"$foo" hack is required for code that must run on ancient shells which lack [[, and have a more primitive [, which gets confused if $foo begins with a -. But you'll get really tired of having to explain that to everyone else. 

---

