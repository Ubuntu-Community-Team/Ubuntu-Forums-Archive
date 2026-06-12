---
title: "Adding digits together?"
date: 2009-11-01
forum: Programming Talk
---

### Post by bartre on 2009-11-01
okay, so I'm in a beginning programming class and they want me to take the date from a user, then add all of the numbers into a single digit.  We're supposed to check and make sure that the date is in mm / dd / yyyy format with the spaces and slashes just like that.  

I get the general idea, but I've got a couple problems.
first, how can I get 3 separate numbers off of the same line?
I would just make it a string, then separate it using substring and toString, but toString is not allowed, as the teacher hasn't shown it to us.

second, how should I go about adding the separate digits together?

---

### Post by Can+~ on 2009-11-01
> We're supposed to check and make sure that the date is in mm / dd / yyyy format with the spaces and slashes just like that. 

I get the general idea, but I've got a couple problems.
first, how can I get 3 separate numbers off of the same line?
I would just make it a string, then separate it using substring and toString, but toString is not allowed, as the teacher hasn't shown it to us.

If the user entered an input "mm / dd / yyyy", then it already is a string. So I'm not sure what you mean, or what your teacher wants.

> second, how should I go about adding the separate digits together?

Dividing a number by 10 (int division):

```
123456 / 10
12345 / 10
1234 / 10
123 / 10
12 / 10
1 / 10
0
```

On the other hand, there's an operation called "modulo" which produces the part that was left behind by the division:

[PHP]>>> 123456 % 10
6
>>> 12345 % 10
5
>>> 1234 % 10
4[/PHP]

That's all I'm saying.

---

### Post by bartre on 2009-11-01
> **Can+~ said:**
> If the user entered an input "mm / dd / yyyy", then it already is a string. So I'm not sure what you mean, or what your teacher wants.

Well, the problem isn't that the input is a string, the problem is that i don't know how to work with it while it is a string, and I'm not exactly sure how to convert it to a proper number.

---

### Post by John Bean on 2009-11-01
> **bartre said:**
> Well, the problem isn't that the input is a string, the problem is that i don't know how to work with it while it is a string
It would help to know the programming language you're using.

---

### Post by bartre on 2009-11-01
sorry, it's java.

---

### Post by 0cton on 2009-11-01
err I am having a hard time understanding what you really want to do.
to transform it into an int you do
Integer.parseInt() throws an exception if it's not a valid number
you can also split it with split("/") (split at "/") if it's different than 3 (the length of the returned array) than it's the wrong format.

---

### Post by John Bean on 2009-11-01
> **bartre said:**
> sorry, it's java.
I'd be sorry too! But never mind, someone has to learn it I suppose ;-)

I'll have to pass I'm afraid..

---

### Post by dwhitney67 on 2009-11-01
It's amazing how many students come to this forum with their homework problems.  I only hope that these students are able to afford a textbook.

Most teachers assign homework and/or exam questions that tests/reinforces the student's knowledge of the subject matter.  It would appear that the OP was either asleep in class, skipped it entirely, or is just plain lazy.

---

### Post by bartre on 2009-11-01
> **0cton said:**
> err I am having a hard time understanding what you really want to do.
to transform it into an int you do
Integer.parseInt() throws an exception if it's not a valid number
you can also split it with split("/") (split at "/") if it's different than 3 (the length of the returned array) than it's the wrong format.

okay, you got it, I want to take the string input by the user and make it an int, and the parseInt method is in the chapter we're on.  I only have one question left then, if i use the split method, will it keep the spaces on the sides of them?

---

### Post by wolterh on 2009-11-01
Given the string 
```
mm / dd / yyyy
```
I would check that:
-Characters mm (0 and 1), dd (5 and 6), yyyy (from 10 to 13) are of numeric type. 
-Characters 2,4,7,9 are equal to '/'. 
-Characters 3 and 8 are equal to ' '. 
If any of those checks fail, return an error saying that the string is malformed. 
If mm are greater than 12, return an error as well. 
If dd are greater than 31 return an error (or perform a check depending on the month to calculate the day limit).
Now, adding all those numbers (m+m+d+d+y+y+y+y) will not be able to be all add up in a single digit. You converting each to a number (there must be some function in java) and adding them, one by one, will be the way to add them all up in a single number (most likely will end up being a 2 digit number).

---

### Post by Rocket2DMn on 2009-11-01
Sorry, we don't do homework help here.  C'mon PT volunteers, you know better!

---

