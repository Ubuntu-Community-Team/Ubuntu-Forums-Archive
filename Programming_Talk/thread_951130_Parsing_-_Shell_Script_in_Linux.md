---
title: "Parsing - Shell Script in Linux"
date: 2008-10-17
forum: Programming Talk
---

### Post by cation007 on 2008-10-17
Hi,
I am breaking my head to find out how to parse a file using shell script in linux.

I have seen people using awk, sed etc...

But the problem is...

I have to read a file...

Say a file with contents like this...

---------
$objects= obj1 obj2 ... objn

abc: con1 con2 con3 ... conN

---------


How to do I parse/ split the lines one by one?

For Eg: I want to split the first like w.r.t "=" and store "objects" in a variable and "obj1 obj2 ... objn" in another variable.

I again want to split "obj1 obj2 obj3 ... objn" with space as delimiter and store all of them "obj1", "obj2", "obj3" ... "objn" in an array.

I do not know what n is so I do not the size of array.

Can anybody help please ?

Thanks,

---

### Post by yabbadabbadont on 2008-10-17
Since this looks suspiciously like a homework problem...  ;)  I'll just give you the basic framework for reading a text file one line at a time in bash.

```
while read NextLine
do
put your commands to work with the line stored in NextLine here
done < NameOfInputFile

```

---

### Post by cation007 on 2008-10-17
Hi,
Thanks.
I am sorry. I should have been very specific.

My problem is with parsing.

What is the command used to parse strings or lines ?

if I use awk, can I store the parsed values in a array?


p.s. Its not a homework problem.
I am trying to parse a sequence file for a bioinformatics problem ...

I know I can do it with PERL, but shell scripting would be faster I believe ...

---

### Post by ghostdog74 on 2008-10-18
> **cation007 said:**
> Hi,
What is the command used to parse strings or lines ?

in the shell, the best tool to parse files and do things to it is awk.
To check it out, do a google search on "effective awk".  or you can look at one of the link in my sig.

> 
if I use awk, can I store the parsed values in a array?

yes you can. awk provides you with basic programming facilities like loops and arrays etc. like i said , check it out in the manual.


> 
I know I can do it with PERL, but shell scripting would be faster I believe ... 
not really, it depends on the complexity and how you solve your problem. Since you know Perl and its for your work (i guess), then use Perl.

---

### Post by WW on 2008-10-18
Personally, I prefer python:

**parse_test.py**
```

# Parse the file and put the two forms in different dictionaries.
# (This code does not check for errors in the file!)
x = {}
y = {}
for line in open("file.txt"):
    line = line.strip()
    if line[0] == '$':
        words = line[1:].split()
        x[words[0][:-1]] = words[1:]
    else:
        words = line.split()
        y[words[0][:-1]] = words[1:]

print "Lines of the first form:"
for key,value in x.items():
    print key,'=',value

print "Lines of the second form:"
for key,value in y.items():
    print key,':',value

```
**file.txt**
```

$one= a bb ccc
two: alpha beta gamma delta
$three= four score and seven years ago

```
Run:
```

$ python parse_test.py
Lines of the first form:
three = ['four', 'score', 'and', 'seven', 'years', 'ago']
one = ['a', 'bb', 'ccc']
Lines of the second form:
two : ['alpha', 'beta', 'gamma', 'delta']
$ 

```

...but you could just as easily use perl.

---

### Post by ghostdog74 on 2008-10-18
```

for line in open("file.txt").readlines(): 
  line=line.strip()

```
is equal to 
```

for line in open("file.txt"):
  line=line.strip()

```

---

### Post by stroyan on 2008-10-18
You can do this kind of parsing with bash.
The 'case' keyword can match line patterns.
The ${variable/pattern} expansion can be used to remove unwanted parts.
Here is an example.
```

#!/bin/bash
# turn on extended pattern matching
shopt -s extglob
while read
do
    echo read "'$REPLY'"
    case "$REPLY" in
        \$+([[:alnum:]])=\ *)
        echo matching = pattern
        name="${REPLY/[$]/}"
        name="${name/=\ */}"
        values=( ${REPLY/\$+([[:alnum:]])=\ } )
        echo name = "$name"
        echo there are ${#values[*]} values in the array
        echo values = "${values[*]}"
        ;;
        +([[:alnum:]]):\ *)
        echo matching : pattern
        name="${REPLY/:\ */}"
        values=( ${REPLY/+([[:alnum:]]):\ } )
        echo name = "$name"
        echo there are ${#values[*]} values in the array
        echo values = "${values[*]}"
        ;;
        *)
        echo did not match
        ;;
    esac
done

```

---

### Post by ghostdog74 on 2008-10-18
> **cation007 said:**
> 
I have seen people using awk, sed etc...

awk:
```

awk '/^\$/{
 object=$1;$1=""
 m=split($0,_," ")
 for(i in _){  print i, _[i] } 
}' file

```

if you want to know more, google "effective awk"

---

### Post by cation007 on 2008-10-20
Hi all,
Thanks for your replies.

awk seems to work good.


:)

---

