---
title: "add new character to the beginning of some lines"
date: 2013-10-22
forum: Programming Talk
---

### Post by peter_brickles on 2013-10-22
Hi guys 

I have a large list of uk phone numbers all of which should be 11 characters long. 

They should begin with a 0 some how ever have the 0 missing is there any way to iterate though the file and add a 0 as the first character if it does not laready exist.

thanks pete

---

### Post by vasa1 on 2013-10-22
You should include a few lines to illustrate what you want. The experts here will then be better placed to help you.

---

### Post by peter_brickles on 2013-10-22
list is as below 

07887123456
7878345343
07070712345
799999999

the numbers that do not start with a 0 should have a 0 added to them so all file is in a standard format ! 

thanks

---

### Post by Lars Noodén on 2013-10-22
You can use printf in many scripting languages.  Here is one example from awk.

```

[s]awk '{ printf("%011d\n", $1)}' < list1.txt > list2.txt[/s]

```

Edit: better double check to make sure that does what you want.

---

### Post by peter_brickles on 2013-10-22
e sort of works but double zeros records already starting with zero

---

### Post by Lars Noodén on 2013-10-22
Here's a second approach.

```

awk '/^0/ { print $1; } ! /^0/ { print "0" $1 }' < file1.txt > file2.txt

```

It won't check the number length, just prepend a zero if it is missing from the start of the number.

---

### Post by ICanHasNick on 2013-10-22
if you want to examine before the change is made what the change will be like:

$> vim yourfile
[COLOR=#222222][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]:%s/^\([1-9]\)/0\1/
# if it has done what you have intended
:wq[/FONT][/COLOR]
#if not
u
:q!

---

### Post by ofnuts on 2013-10-22
The sed-based solution:
```

sed -re 's/^([0-9]{10})$/0\1/' <phonenums.txt

```

---

### Post by drmrgd on 2013-10-22
Perl solution (assuming text file with one phone number per line):

```

$ perl -pne 's/(.*)/0$1/ if ( ! /^0/ )' numbers.txt 
07887123456
07878345343
07070712345
0799999999

```

---

