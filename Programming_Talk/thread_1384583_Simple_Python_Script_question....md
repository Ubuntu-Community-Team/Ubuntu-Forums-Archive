---
title: "Simple Python Script question..."
date: 2010-01-18
forum: Programming Talk
---

### Post by Eremis on 2010-01-18
Hi everybody!

I just started learning python (have a background in java), and I am using a "Learning Python O'REILLY" book. However I tried making a simple script that would convert text to binary, one letter at a time with a for loop...

Here's an example of my logic:

read a file to a string --> convert string to a list (ex. "Hello" --> ['H','e','l','l','o']) --> convert each letter to a int (ex. ord('H')) --> convert each int into bin (ex. bin(num)) --> put all the binary numbers into array --> print them to a diffrent file...

The result:

File1.txt --> Hello
File2.txt --> 0b1001000 0b1100101 0b1101100 0b1101100 0b1101111

Here's my code so far:
```

#!usr/bin/python26

#
# Description:
#   Text to binary converter
#   converts using regular ascii code
#
# Developer:
#   Eremis
#

import sys

if len(sys.argv) != 2:
    print "\n\t          Text to Binary Converter 1.0               "
    print "\t  ---------------------------------------------------\n"
    print "\t       Usage: ./TextToBin.py <inputFile.txt>\n"
    sys.exit(1)

# reading input file...
try:
    text = open(sys.argv[1], "r").readlines()
except(IOError):
    print "[-] Error: Check your text file path\n"
    sys.exit(1)

listText = list(text)
listOutText = []

for c in listText:
    listOutText[c] = bin(ord(listText[c]))

print listOutText

```

Every time I run this I get an error: Why?, and How can I fix it?

```

Traceback (most recent call last):
  File "TextToBin.py", line 31, in <module>
    listOutText[c] = bin(ord(listText[c]))
TypeError: list indices must be integers, not str

```

Thanks for the help1

---

### Post by kostkon on 2010-01-18
You can change it to 
```
listText = list(text)
listOutText = []

for c in listText:
    listOutText.append(bin(ord(c)))
```
or to
```
listText = list(text)
listOutText = []

for c in range(len(listText)):
    listOutText[c] = bin(ord(listText[c]))
```


```
for c in listText
``` just iterates throught the char of listText and thus c is a char and not an int index.

---

### Post by Eremis on 2010-01-18
Oh, ok!

Thank you so much!

---

### Post by Eremis on 2010-01-18
I thought I solved it, but I still keep getting error...

Traceback (most recent call last):
  File "TextToBin.py", line 31, in <module>
    listOutText[c] = bin(ord(listText[c]))
TypeError: ord() expected a character, but string of length 7 found

---

### Post by kostkon on 2010-01-18
although as I can see it now, the second code part
```
for c in range(len(listText)):
    listOutText[c] = bin(ord(listText[c]))
```
will most likely throw an error.

Eh, thus, it should be:
```
for c in range(len(listText)):
    listOutText.append(bin(ord(listText[c])))
```
or even more compactly if you want
```
listOutText = [bin(ord(listText[c])) for c in range(len(listText))]
```
or
```
listOutText = [bin(ord(c)) for c in listText]
```

---

### Post by kostkon on 2010-01-18
> **Eremis said:**
> I thought I solved it, but I still keep getting error...

Traceback (most recent call last):
  File "TextToBin.py", line 31, in <module>
    listOutText[c] = bin(ord(listText[c]))
TypeError: ord() expected a character, but string of length 7 found
Oh ok, you are reading every line of the file and save it to a list, thus every list item contains a line of text.

thus, you could change to something like this:
```
for line in text:
    binline = "" 
    for char in line:
        binline += (bin(ord(char)))
    listOutText.append(binline)
```

This will give you a new list containing the same lines but with the text converted to binary.

---

### Post by Eremis on 2010-01-18
Ok, this last one worked, Thanks!

(I just need to get better in python for loops, still thinking in java...)
I think I understand it now... I was trying to convert the whole line... right?

Well thanks again...

Python should be thought in schools insted of java...

---

### Post by kostkon on 2010-01-18
> **Eremis said:**
> I was trying to convert the whole line... right
In:
```
for c in listText:
    listOutText[c] = bin(ord(listText[c]))
```
you were trying to use *c* as an index but actually the code
```
for c in listText
```
iterates through the list and assigns the value of each of its item to *c* which in this case every item is a line of text.
Secondly, yeah, you were trying to convert the whole line to binary, wheres the *ord()* method accepts only one character and that most likely would have thrown a *TypeError* exception if the loop was working right.

Thus, you have to iterate through the *text* list and get each line and then iterate through each line to get the individual characters.
As you can see, you can iterate through a string as you would iterate through a list, by simply using a *for* loop.

and this line
```
listText = list(text)
```
is not needed, since it just copies the *text* list to a new list.

Hope the above makes some sense. :(

---

