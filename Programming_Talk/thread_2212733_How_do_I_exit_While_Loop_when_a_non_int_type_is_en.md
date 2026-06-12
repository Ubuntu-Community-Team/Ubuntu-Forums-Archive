---
title: "How do I exit While Loop when a non int type is entered? Java"
date: 2014-03-22
forum: Programming Talk
---

### Post by Wiking on 2014-03-22
How can I make a while loop that will exit the loop when a non** int** value is entered?

So if they type in a letter the loop will exit? In java please.

thanks

---

### Post by ofnuts on 2014-03-23
What the user enters is not an int, it's always a string. Then some part of the code may try to interpret that as the representation of an integer, and can fail for several reasons, one of them being that what has been entered is not all digits. YOu should be able to catch this, either by testing the string before trying a conversion, or by putting the conversion in a try/catch block and exiting the loop in the catch part.

---

### Post by EddyDreizehn on 2014-03-30
I'm cant Java. But there must be a function like "atoi" - "ascii to integer". That means, the function converts the ascii-string to a integer. 
If it's not possible, because its no integer, the function returns "-1" or something like a empty string. 
Another way is to with "try catch" : Try to push the input string in a int variable. Catch break the loop. 

For break the loop is in most languages the keyword "break". If you only will break the current loop, then "continue"...

---

### Post by ofnuts on 2014-03-30
> **EddyDreizehn said:**
> I'm cant Java. But there must be a function like "atoi" - "ascii to integer". That means, the function converts the ascii-string to a integer. 
If it's not possible, because its no integer, the function returns "-1" or something like a empty string. 
Another way is to with "try catch" : Try to push the input string in a int variable. Catch break the loop. 

For break the loop is in most languages the keyword "break". If you only will break the current loop, then "continue"...

For your information, in Java this is [Integer.parseInt(String)]("http://docs.oracle.com/javase/7/docs/api/java/lang/Integer.html#parseInt%28java.lang.String%29") that conveniently throws a NumberFormatException if something is amiss.

---

