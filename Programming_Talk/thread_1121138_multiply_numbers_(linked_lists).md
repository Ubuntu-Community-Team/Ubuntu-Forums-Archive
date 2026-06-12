---
title: "multiply numbers (linked lists)"
date: 2009-04-09
forum: Programming Talk
---

### Post by StOoZ on 2009-04-09
First of all , im not looking for a code!!!!!
any suggestions on how to multiply two numbers , where both are represented by a linked list (one digit for each node) , and create a third linked list , which represents the multiplication outcome.

I bet there is a better way to do it than how we do it "by hand"  , I mean , the usual way with pencil and paper when you do it like:
111
 35
----
 555
333
------

and so on...

---

### Post by johnl on 2009-04-09
One option would be to convert the linked lists into their numeric form, do the multiplication, and then build a linked list of the result.  Whether or not this is easier or better than the 'old-fashioned' method you described is up to you :)

---

### Post by soltanis on 2009-04-09
Computers multiply numbers in a highly efficient manner, if that's what you're asking. If you want a better way to do it by hand, I would suggest googling for a video called "how chinese multiply" or something like that, which shows a very fast and pretty intuitive method for multiplying numbers with multiple digits that is far superior to the long-handed method taught in elementary school.

---

### Post by dwhitney67 on 2009-04-09
> **StOoZ said:**
> First of all , im not looking for a code!!!!!
any suggestions on how to multiply two numbers , where both are represented by a linked list (one digit for each node) , and create a third linked list , which represents the multiplication outcome.

I bet there is a better way to do it than how we do it "by hand"  , I mean , the usual way with pencil and paper when you do it like:
111
 35
----
 555
333
------

and so on...
Construct the number using the digit at each node.  Presumably you know the number of nodes beforehand.
```

value1 = 0;
size   = list1.size
node   = list1.head

while node is not null
     value1 += (node.digit * 10 ^ (size - 1))
     node    = node.next

// repeat for other list to yield value2

result = value1 * value2

```

To convert 'result' to a list, you need to deduce the number of digits in the value; then for each digit, starting at the most significant, insert it into the list.

P.S.  When defining a list, decide whether you will insert at the tail or at the head.  The algorithm/suggestion above assumes that a digit is inserted at the tail.

---

### Post by nvteighen on 2009-04-10
> **soltanis said:**
> Computers multiply numbers in a highly efficient manner, if that's what you're asking. If you want a better way to do it by hand, I would suggest googling for a video called "how chinese multiply" or something like that, which shows a very fast and pretty intuitive method for multiplying numbers with multiple digits that is far superior to the long-handed method taught in elementary school.
Amazing... [http://www.youtube.com/watch?v=sBkdT9N4Y7w](http://www.youtube.com/watch?v=sBkdT9N4Y7w)

---

