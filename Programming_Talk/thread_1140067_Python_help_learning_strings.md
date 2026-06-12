---
title: "Python help learning strings"
date: 2009-04-27
forum: Programming Talk
---

### Post by burntresistor on 2009-04-27
Well I'm teaching myself python I got a book and I just need help this part of the book really sucks. I'm trying to complete the problems at the end of the chapter like every chapter. What it wants me to do is create a decoder that uses a list instead of a loop. numbers2text I'm using raw_input and im getting the first letter done but not any decoded letters after it.

import string

def main():
   print"this program converts a sequence of ascii into "
   print"the string of text that it repressents"
   print

   instring= raw_input ("please enter ascii encoded message: ")

   
   list2= string.join(instring,"")
   print "list2"
   asciinum= eval(list2)
   print "asciinum"
   value = chr(asciinum)
   print "final message is ",value

main()

the objective was to have to raw_input go into a string list and be able to decode the list

---

### Post by Arndt on 2009-04-27
> **burntresistor said:**
> Well I'm teaching myself python I got a book and I just need help this part of the book really sucks. I'm trying to complete the problems at the end of the chapter like every chapter. What it wants me to do is create a decoder that uses a list instead of a loop. numbers2text I'm using raw_input and im getting the first letter done but not any decoded letters after it.

import string

def main():
   print"this program converts a sequence of ascii into "
   print"the string of text that it repressents"
   print

   instring= raw_input ("please enter ascii encoded message: ")

   
   list2= string.join(instring,"")
   print "list2"
   asciinum= eval(list2)
   print "asciinum"
   value = chr(asciinum)
   print "final message is ",value

main()

What's the name of the book?

What list functions has that chapter been talking about? What format is the input string supposed to have?

By the way, you can make your inserted code easier to read if you enclose it in code tags (mark the code part and press the # symbol in the tool bar above).

---

### Post by burntresistor on 2009-04-27
> **Arndt said:**
> What's the name of the book?

What list functions has that chapter been talking about? What format is the input string supposed to have?

By the way, you can make your inserted code easier to read if you enclose it in code tags (mark the code part and press the # symbol in the tool bar above).

Python programing by John zelle. The encoder is very simple it just uses ord to convert to text. The only suggestions in the problem were the use string.join and make a program that does the same thing but uses list format instead of a loop, which the book does. The criticism on the book was kinda harsh I just don't think they explained what they wanted me to program very well, in problems. yes I know about the # but I'm just getting lazy and want to get it functional for the learning process.

---

### Post by imdano on 2009-04-27
Can you copy the exact wording of the question from the book?  I don't quite follow what you're trying to do.

---

### Post by burntresistor on 2009-04-27
> **imdano said:**
> Can you copy the exact wording of the question from the book?  I don't quite follow what you're trying to do.

this is what it says.


the decoder program numbers2text uses string variable as an accumulator of output. Because strings are immutable  this is somewhat insufficient 
message= message +chr(asciinum)

essentially this creates a complete copy of the message so far and tacks more characters at the end of it.
one way to avoid recopying the message over and over again is to use a list. the message can be accumulated as a list of characters where each new character is appended to the end of the existing list,using  an empty string between the characters.

string.join(msglist,"")
use this approach to redo a decoder program.

---

### Post by imdano on 2009-04-27
Ok, so basically all it's saying is to replace the ```
message= message +chr(asciinum)
```line with a line that appends the result of the chr(asciinum) operation to a list.  Then, once you've put all the characters in the list, call ```
"".join(msglist)
```to turn it into a string.  (I know the question says to use string.join(msglist, ""), but that usage is deprecated afaik).  You're using a for loop to iterate over the input string either way.

---

### Post by wmcbrine on 2009-04-27
The quote from the book seems clear enough to me, but there are a number of other issues you need to take into account to make your program work.

You're off to a good start with raw_input(). That should give you a string something like this:

'72 101 108 108 111'

The next thing you need to do is to split that string into a list of strings -- one for each number. In other words:

['72', '101', '108', '108', '111']

Now, you have to turn each of those strings into an int:

[72, 101, 108, 108, 111]

Then turn each of those into a character:

['H', 'e', 'l', 'l', 'o']

And finally, join the characters into a longer string:

'Hello'

This last step is really the only one covered by that passage in the book, although it also mentions chr().

You don't necessarily need to go through all of the structures shown above; you can combine some of the steps.

A correct solution is unlikely to involve eval().

---

### Post by burntresistor on 2009-04-28
import string

def main():
   print"this program converts a sequence of ascii into "
   print"the string of text that it represents"
   print

str2= raw_input ("please enter ascii encoded message: ")
for numstring in string.split(str2):
  str3 =int(numstring)
list3="".join(str3)
print "final message is ",list3

main()

---

### Post by burntresistor on 2009-04-28
I'm still having trouble getting it to work it was working with chr but only with the first letter if I entered more than 1 letter to decode it wouldn't work, Now I dnnno if im on the right track im getting a error

invalid literal for int() with base 10: "'72"
 


import string

def main():
   print"this program converts a sequence of ascii into "
   print"the string of text that it repressents"
   print

str2= raw_input ("please enter ascii encoded message: ")
for numstring in string.split(str2):
  str3 =int(numstring)
list3="".join(str3)
print "final message is ",list3

main()

---

### Post by Can+~ on 2009-04-28
the [FONT="Courier New"]string[/FONT] library was deprecated in favour of string methods.

[PHP]for numstring in string.split(str2):[/PHP]

[PHP]for numstring in str2.split():[/PHP]

Also, I suggest using [CODE][*/CODE] tags


(It wouldn't be complete without the python one-liner)

[PHP]"".join(chr(int(numword)) for numword in "72 101 108 108 111".split())[/PHP]

---

