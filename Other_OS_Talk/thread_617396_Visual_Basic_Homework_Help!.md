---
title: "Visual Basic Homework Help!"
date: 2007-11-19
forum: Other OS Talk
---

### Post by giambrone on 2007-11-19
Hey there, wrong forum to post this in (not signed up to any others!) but its worth a try!!

This is my first term of computing and we've been given the task to write a simple script for a calculator-like display (with the bars that appear and disappear) in Visual Basic. I've not got very far because I have no idea what to do now.

I figure that if I somehow split the integer into one digit each I can then have a sub that runs for each character, but how the hell do I split then store the string/integer!!?!?! lol

I'm using visual studio 2005 for this.

Thanks :-)

---

### Post by jatos on 2007-11-19
You have come to the wrong forum  for this.

I don't much VB (Yuk, Microsoft), but I know element.show and element.hide show and hide things.

---

### Post by ukripper on 2007-11-19
> **giambrone said:**
> Hey there, wrong forum to post this in but its worth a try!!

This is my first term of computing and we've been given the task to write a simple script for a calculator-like display (with the bars that appear and disappear) in Visual Basic. I've not got very far because I have no idea what to do now.

I figure that if I somehow split the integer into one digit each I can then have a sub that runs for each character, but how the hell do I split then store the string/integer!!?!?! lol

I'm using visual studio 2005 for this.

Thanks :-)

It is very hard to tell what you mean by splitting the integer(datatype). Need more info

However, this may help [http://www.osix.net/modules/article/index.php?id=53](http://www.osix.net/modules/article/index.php?id=53)

---

### Post by giambrone on 2007-11-19
Sorry, I haven't really said what I needed to clear enough :)

I would like to script (in effect) an LCD display like the ones you get on calculators. This is so that if you put any number in it would appear like it would on the display. 

I'm thinking that if you turn the input number into a string, then split it into characters, you could run the "convert it into the display" sub more than once. I'm not sure how to split a string into separate characters, nor store them.

Thanks

---

### Post by ukripper on 2007-11-19
> **giambrone said:**
> Sorry, I haven't really said what I needed to clear enough :)

I would like to script (in effect) an LCD display like the ones you get on calculators. This is so that if you put any number in it would appear like it would on the display. 

I'm thinking that if you turn the input number into a string, then split it into characters, you could run the "convert it into the display" sub more than once. I'm not sure how to split a string into separate characters, nor store them.

Thanks

if you want to convert String to char ,this should do it for you
```
 String* str = S"Hello";
char c = (char)str->Chars[0];
```

Then perhaps use For next loop for looping it further or Do while, that is upto you

---

### Post by giambrone on 2007-11-19
Thanks for the help so far... I'll try to use this in my project :)

Just looked on MSDN and found > Visual Basic (Declaration)
Public Function Split ( _
	ParamArray separator As Char() _
) As String()
Visual Basic (Usage)
Dim instance As String
Dim separator As Char()
Dim returnValue As String()

returnValue = instance.Split(separator)


... Not that I know how to use it!

---

### Post by ukripper on 2007-11-19
> **giambrone said:**
> Thanks for the help so far... I'll try to use this in my project :)

Just looked on MSDN and found 

... Not that I know how to use it!

They gave you syntax and i gave you example. Now I guess it should be pretty simple to implement your solution.

---

### Post by giambrone on 2007-11-19
I'm really confused now...

I've tried to fit it into my code but I can't see what I'm doing (or doing wrong). Perhaps i'm going about this the wrong way... Should I split the string into an array? (Don't know how to do that either lol)

Sorry for being a noob lol.

---

### Post by ukripper on 2007-11-19
Did you draw flow diagram or wrote any requirements before coding?

You should go through your requirements atleast before you do coding!

---

### Post by jviscosi on 2007-11-19
Is it a requirement that you draw each field in the display individually?  Is that what you meant by the bars?

Anyway you could try using a StringBuilder and then iterating the characters.  It might reduce your code complexity.  If you had set up an array of TextBoxes on your form to store the values, it might look something like this (assuming the TextBox numbering starts with 0 on the right):

```

Dim sb as StringBuilder = new StringBuilder("12345")

Dim i as Integer
For i = sb.Length - 1 to 0 step -1
     Dim s as String = sb(i)
     textBox(sb.Length - i - 1).Text = s
Next i

```This is iterating backwards so it can fill the calculator fields from right to left.

I do much more C# than VB.NET and I don't have my IDE In front of me so the syntax might be slightly off but something along those lines could work.

There's almost certainly a more optimized way to do this but that's left as an exercise for the student.  ;-)

---

### Post by giambrone on 2007-11-19
Thanks for the replies guys... Been alot of help

:KS

---

### Post by mips on 2007-11-19
[http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Would have been the correct place ;)

---

### Post by giambrone on 2008-01-05
I guess it would have been the right place.. but since I'm no "l33t h4xor" programmer, using a language for Windows, it would probably have got me beaten up :P

Thanks anyway though :)

---

### Post by Peyton on 2008-01-06
Wait, you need to convert a string into an array of characters?

```
Dim hello As String = "Hello."
Dim helloArray As Char() = hello.ToCharArray()
```

---

### Post by giambrone on 2008-01-13
I'll try putting the exercise into a context (we stopped the project in order to revise for our Unit 1 exams).

I've been asked to write a program in visual basic (now using Vis. Studio 08 Express) that will take any entered number and show it as it would do on a calculator display (E.g. the seven segments that light up to make each number).
I figured that it would be easiest to write a subroutine that draws each number digit by digit. This way I would only have to do the numbers 0 to 9 and then put it into each place (units, tens, hundredths...) 

We've just learned about arrays and I was wondering how I could take the input number (lets say 1234567) and store it somewhere, take the 7, convert that, take the 6 and convert that etc.

I sound ungrateful towards all of the code and help posted- but I'm still a nub and have no idea if it would work, nor how to apply it

:)

---

### Post by bapoumba on 2008-01-13
ubuntuforums is not a resource to get homework or assignments done, sorry. Thread closed.

---

