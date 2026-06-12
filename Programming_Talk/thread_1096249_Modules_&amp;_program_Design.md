---
title: "Modules &amp; program Design"
date: 2009-03-14
forum: Programming Talk
---

### Post by SLeigh1213 on 2009-03-14
Can anyone help me?  I have homework due tomorrow and I am stuck on #1.  Here is my issue:  Rewrite the following pseudocode so that the user input and calcuations are each in a spearate module.  Include a comment at the beginning of each module that describes the purpose of that module.  A line containing a comment should bening with a single quote (').  You should have a data entry module, a calculation module, and an output module. 

start
  num quantityOrdered
  num itemPrice

  print "Enter an Order Quantity"
  read quantityOrdered

  print "Enter the Items Price"
  read itemPrice

  if quantityOrdered > 100 then
        discount =.20
  else
        if quantityOrdered > 12 then
               discount =.10
        else
               discount = 0
        endif
  endif

  total = price * quantityOrdered
  total = total - discount * total
  print total
stop


All help ASAP would be greatly appreciated.

---

### Post by jpkotta on 2009-03-14
No one's going to help you unless you have specific questions.  Read the stickies.
[http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

---

### Post by SLeigh1213 on 2009-03-14
Sorry, my question is, how do I create a module for data entry?

---

### Post by lisati on 2009-03-14
> **SLeigh1213 said:**
> Sorry, my question is, how do I create a module for data entry?

I suspect that the answer can be found in what you understand to be a "module" and what you understand to be "data entry"..... perhaps there is something in your course notes that can help.

EDIT: here's a hint as to what might be expected: [http://www.computerhope.com/jargon/d/dataentr.htm](http://www.computerhope.com/jargon/d/dataentr.htm)

---

### Post by namegame on 2009-03-14
It would really help if you were to tell us what language you are using as well. There are multiple approaches to your problem. Although somewhat trivial for any other purpose than learning, you could implement your solution with an OOP design, although an imperitave design would be as equally effective given the simplicity of the problem.

So basically, we need more information to help you.

---

### Post by slavik on 2009-03-14
> A line containing a comment should bening with a single quote (')

I smell BASIC.

EDIT: I also think that module == function

---

