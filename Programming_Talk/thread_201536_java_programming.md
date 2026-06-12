---
title: "java programming"
date: 2006-06-22
forum: Programming Talk
---

### Post by babyboss on 2006-06-22
my program objective: user input an integer, my program is supposed to print out all of its subsets:

e.g. user input 3,
my program output:
{}
{1}
{2}
{3}
{1, 2}
{1, 3}
{2, 3}
{1, 2, 3}

order doesn't matter

I have been thinking about it for a few hours, it really confuses me, the number of digits, and the value to be print... ect.

---

### Post by Xzallion on 2006-06-22
so you need to take a integer from user input, and have it list all the numbers that happen singularly, or do you need it to output like in your post?  Can you clarify what exactly its supposed to output for me?

If your wanting it to output like what you have in your post, I think I know how to do that.

---

### Post by babyboss on 2006-06-22
exactly the same lists of sets, but it could be in different orders.

---

### Post by Xzallion on 2006-06-22
Hmm okay im working on something, I will post what I figure out.  Also, is there a limit to the user input or does it need to be able to accomodate any number no matter how large?

---

### Post by babyboss on 2006-06-22
only one input at a time. Thx

---

### Post by Xzallion on 2006-06-22
Im still working on the actual code to see if im correct, but heres the idea im using in case it helps you or others get this done faster.

First determine the decimal positions of the user input Integer.  Do this by using a simple formula where decimalCounter starts out as 10. use this in a while loop that ends when ((userNumber/_decimalCounter)<1)
```

if(_userNumber/_decimalCounter > 0){
	_decimalPosition++;
	_decimalCounter = _decimalCounter*10;
}

```

if the number is one digit (1-9) it will not go through the if statement, otherwise we know its at least 2 decimals, and we change the 10 to 100 by multiplying by 10.  now we repeat and find out if its 3 decimals or not, and repeat as needed.

Then you just have to set it up to output the "{", then do a loop to output the number, comma, and the next number.  Start this loop after the initial single sets are done. then after the loop add the ending "}" kinda like this

```

System.out.print("{");
for(int i = 0; i<decimalPosition; i++){
  System.out.print(number);
  System.out.print(",")
}
System.out.print("}\n");

```

I know this isn't a great example, but I hope it gets the idea across.  I will try to finish the code and get a working version going.  Let me know if this helped any.

---

### Post by Arndt on 2006-06-22
[QUOTE=babyboss]my program objective: user input an integer, my program is supposed to print out all of its subsets:

e.g. user input 3,
my program output:
{}
{1}
{2}
{3}
{1, 2}
{1, 3}
{2, 3}
{1, 2, 3}

order doesn't matter

I have been thinking about it for a few hours, it really confuses me, the number of digits, and the value to be print... ect.[/QUOTE]

I think XZallion and I have got quite different ideas on what your problem is, but here is mine: You get an input integer number N, then you first (at least conceptually) form the set of numbers from 1 up to N: {1, 2, 3, ..., N}. Then you want to list all possible subsets of this set.

Here is one way to do it: think of each subset as an N-position binary number, where each bit represents whether a particular number is present in the set or not. So, when N = 3,  {} is (0 0 0); {1, 2, 3} is (1 1 1); {3} is (0 0 1), for example.

If you know that N is always so small that the bits will fit in an integer in the language, you can use bit operations on it; otherwise set up an array with N elements (bits, chars, integers, they will only get set to 0 or 1). Start them all at 0. Then, perform a binary addition of 1 on the array (0 0 0 becomes 0 0 1). Walk through the array and print the numbers which are indicated by a 1 (and braces and commas appropriately): {3}. Do this repeatedly until you get all zeroes again. (0 0 1) + 1 = (0 1 0), ... (1 1 1) + 1 = (0 0 0).

I've left out things and given you no code, but maybe it makes sense anyway.

---

### Post by Xzallion on 2006-06-22
I don't quite understand what Ardnt suggested, but I probably should mention my experience in Java is only two courses in high school.  With that said, im not making too much progress, my idea is bulky and complicated.  It would probably be better for someone else to help you.  But I will continue to think about this and would like to see the actual code that can accomplish this if anyone else posts a way to do it.

Untill someone else helps out more then I can, I will continue to work on this, but enough for tonight, im off to bed here soon.

---

### Post by ynef on 2006-06-22
Arndt has already posted the solution to the problem -- you should implement it and see that it works.

---

### Post by Xzallion on 2006-06-22
I was actually kinda implementing a similiar thing, I just didn't explain it very well.  But Arndt's idea does look like it works and I will take your word for it ynef.

The first part of my code found out how many decimals N would be, then I was attempting to set up an array of numbers based off the number of decimal places N occupies.  I got stuck after that, and have to admit I don't know how to bit operations or implement the binary math on the array concept that Arndt suggested.  But guess I have something else to teach myself now :D

---

