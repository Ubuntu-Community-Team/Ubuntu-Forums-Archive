---
title: "Python: Array of characters, extracted of another array by position?"
date: 2008-11-09
forum: Programming Talk
---

### Post by PryGuy on 2008-11-09
Good day to you all!
I've got a problem here. I've got an array that looks like this: ["10011", "11001", "01000"]. These are settings, can be true or false. I have to create another array from this one, taking only first, second, third, etc. characters. The new array should look like this: ["1", "1", "0"] (taking first character), ["0", "1", "1"] (taking second character), etc. Is that possible? 

Thank you!

---

### Post by loell on 2008-11-09
something like,

[PHP]
binarylist = ["10011", "11001", "01000"]

bin_separated_chars = []

for item in binarylist:

  bin_separated_chars.append( [item[0], item[1], item[2]])

print bin_separated_chars
   



[/PHP]

---

### Post by PryGuy on 2008-11-09
Well, it's not PHP, it's Python, sorry... :(

---

### Post by loell on 2008-11-09
> **PryGuy said:**
> Well, it's not PHP, it's Python, sorry... :(

:lolflag:

try to run that on a php interpreter and you'll have a syntax error, it doesn't have a dollar sign on its variables. ;)

i use [IMG]http://ubuntuforums.org/images/editor/php.gif[/IMG] 
to enclose the python code. 

though i agree why does vbulletin named it PHP code? silly button name and description. :D

---

### Post by PryGuy on 2008-11-09
Sorry, I just saw "PHP code" above your example... :(

---

### Post by PryGuy on 2008-11-09
Bravo!!!=D>=D>=D>
Thank you so much!

---

### Post by loell on 2008-11-09
no problem. :)

happy python learning. :KS

---

### Post by PryGuy on 2008-11-09
is it multi-array array? :)
another quick question, how do I get a single value, not an array that I get saying 'print bin_separated_chars[0]'?

---

### Post by loell on 2008-11-09
print bin_separated_chars[0][0]
print bin_separated_chars[0][1]
...

---

### Post by PryGuy on 2008-11-09
You are my hero! :) Long live Python!!!

---

