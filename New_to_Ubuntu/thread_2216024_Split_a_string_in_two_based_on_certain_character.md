---
title: "Split a string in two based on certain character"
date: 2014-04-09
forum: New to Ubuntu
---

### Post by sujitrjadhav on 2014-04-09
Hi friends,

below here is sample data.

12345678,A N KARMARKAR
87645321,D M SUDHAKAR
23456781,D S GANESH
34567812,S B VARHADE

I am writing a bash script which need above given data be split in two separate variables for further processing. For example var1=12345678 and var2=A N KARMARKAR. So I want to read a line and split it in two variables on the basis of character ','. 

How do I do that in a bash script?

Thanks in advance

---

### Post by sujitrjadhav on 2014-04-09
Ok. Got solution

var1=$(echo $line | cut -f1 -d,)
var2=$(echo $line | cut -f2 -d,)

---

### Post by sudodus on 2014-04-09
You can do it 'semi-graphically' in a spreadsheet program, e.g. LibreOffice Calc or gnumeric.

You can use the ***cut*** command in bash, and assign variables to the various parts of the line.

But maybe the easiest way you can do it is with the ***read*** command in ***bash***. 

```
    Reads a single line from the standard input, or from file descriptor FD
    if the -u option is supplied.  The line is split into fields as with word
    splitting, and the first word is assigned to the first NAME, the second
    word to the second NAME, and so on, with any leftover words assigned to
    the last NAME.  Only the characters found in $IFS are recognized as word
    delimiters.

```


Get more details with ```
help read
```

---

