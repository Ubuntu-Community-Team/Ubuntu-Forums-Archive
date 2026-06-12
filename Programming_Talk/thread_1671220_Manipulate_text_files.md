---
title: "Manipulate text files"
date: 2011-01-19
forum: Programming Talk
---

### Post by AVatch on 2011-01-19
Hi, I am trying to make a small program that will alter a specified text file.

For example:

in file test.txt

x     y
10    2
15    3
20    4
25    4
30    5

and so on for several hundred lines. 

I want to write something along the lines of a program that "widens" the range in the x column. By this I mean, all values above 20 will be subtracted by 5 and all values below 20 will be added by 5. The corresponding y values should stay the same though with the original line number, so 10 will always be paired with 2 even after it has 5 subtracted from it. The gap of entries that are left around 20 (like the space for 15, 25) should be just copies of 20 with its associated y value. I am not sure how to do it.

In my head it looks something like this:

widenRange(filename, centralvalue, offsetvalue)
{
code
}


I would really appreciate some help with this since there are a lot of lines to be edited and I would like to learn how to do this to streamline the process. If there are any helpful links with tutorials on how to do this I would appreciate the help or advice.

Thank you so much!!

---

### Post by geirha on 2011-01-19
Well, the answer would depend on what programming language you intend to use ... which you haven't specified.

---

### Post by AVatch on 2011-01-19
Well, which would you think would be the best choice? I have some knowledge of java and python, so it would be preferable to use one of those so I can better understand how it is happening. 

Or i know in Windows you could make a batch file which could possibly do something like this, maybe there is something analogous on Ubuntu.

---

### Post by Vaphell on 2011-01-20
> Or i know in Windows you could make a batch file which could possibly do something like this, maybe there is something analogous on Ubuntu.
lol, maybe? :D Windows batch files have *nothing* on linux command line. Isn't that one of the reasons why people in general think that linux is a system for geeks where everything is done with white characters on a black screen? :-)

eg this one liner
```
awk -v d=5 -v c=20 '!/[a-z]/{ offset=0; if ($1>c) offset=d; if ($1<c) offset=-d; print $1+offset, $2 }' data.txt
```
d - offset, c - center, data.txt - some input file


same thing in a nicer form of bash script
[php]#!/bin/bash

input="test.txt"
offset=5
center=20

if [ "$1" ]; then input="$1"; fi;
if [ "$2" ]; then center="$2"; fi;
if [ "$3" ]; then offset="$3"; fi;  

awk -v d=$offset -v c=$center '!/[a-z]/{ offset=0; if ($1>c) offset=d; if ($1<c) offset=-d; print $1+offset, $2 }' "$input"
[/php]

script is parametrized, first arg - input file, second - center, third - offset, with default values defined
prints to screen by default, to write to file redirect output with >, e.g.
```
./widen.sh file 20 5 > target.file
```

---

### Post by ghostdog74 on 2011-01-20
> **AVatch said:**
> Hi, I am trying to make a small program that will alter a specified text file.

next time, show your expected output as well
```

awk 'NR>1{$1=($1>20)?$1-5:$1+5;print}' file

```

---

### Post by geirha on 2011-01-20
Here's one using pure bash.

```

#!/usr/bin/env bash

if (($# != 2)); then
  printf "Usage: %s center offset\n" "$0" >&2
  exit 1
fi

center=$1 offset=$2

# read and output the header
read -r && printf '%s\n' "$REPLY"

while read -r x y; do
  printf '%d %d\n' "$((x > center ? x - offset : x + offset))" "$y"
done

```

Save the script as ~/bin/widen and make it executable:
```
chmod +x ~/bin/widen
```


If you don't have a directory called bin (all lowercase) in your home directory, create it. After creating it, the next time you log in, that directory will be added to the PATH environment variable, so you can just run
```
widen 20 5 < infile > outfile
```

---

### Post by ghostdog74 on 2011-01-20
> **geirha said:**
> Here's one using pure bash.

provided there's no floating point numbers.

---

### Post by AVatch on 2011-01-20
I wanted to thank you guys! This was very helpful.

---

### Post by AVatch on 2011-01-20
I wanted to thank you guys! This was very helpful.

---

### Post by AVatch on 2011-01-20
This was very helpful, i wanted to thank you guys!

---

