---
title: "subtracting array contents from other arrays? (c++)"
date: 2010-02-21
forum: Programming Talk
---

### Post by daweefolk on 2010-02-21
I'm gonna try and write a "twenty questions" type game but it will only be guessing a number between 1 and 100 by asking questions like "is it an even number?" "is it evenly divisible by five?" etc. if I wrote out arrays for each question (like for even numbers, array "int even[]" includes 2,4,6,8,etc. and the same type of thing for "int byfive[]").
If I did that, and i made a 'totalnums[]' array, would there be a way to (if user said no, not even) remove all the contents of even[] from totalnums[]?

---

### Post by Some Penguin on 2010-02-21
You might want to use sets for that.  What would you be storing in the arrays -- the numbers themselves?  And what would you store in place of a 'deleted' number, if that's what?

---

### Post by Simon17 on 2010-02-21
Some Penguin, I think he just wants to remove the number and shrink the array.

OP, first of all, I want to question your storing every number in an array. It's completely unnecessary. But assuming you really want to do it.

To remove an element from an array, you just need to move every element behind the deleted element one up. For example, the array
{1,2,3,4,5} and we remove the 2.
Move the 3 into 2's spot, the 4 into 3's spot and the 5 into 4's spot. So we would be left with
{1,3,4,5,5}
(Resizing the array is optional. Just be sure to keep track of how many valid elements there are.)

A better option would be to use std::vector. This implements the remove() functionality for you.

An even better option would be to use std::list. Removing elements from arrays is very slow. Elements can be removed from linked lists in constant time.

---

### Post by dwhitney67 on 2010-02-21
> **Simon17 said:**
> ...
An even better option would be to use std::...
set, as Some Penguin alluded to.

But you are correct; why would anyone want to store an array of numbers from 1 to 100?

This game is simple:

1.  Have the program acquire a random number ranging from 1 to 100.

2.  Prompt the user for a guess or a question.

    Valid question is whether the number is odd or even.

3.  After acquiring the user's guess, tell them if they are correct, or if they have guessed "high" or "low".

4.  Go back to step 2, unless 10 (or say 20) chances have passed.  Typically it would take no more than 1-5 chances.

---

### Post by daweefolk on 2010-02-21
> **dwhitney67 said:**
> set, as Some Penguin alluded to.

But you are correct; why would anyone want to store an array of numbers from 1 to 100?

This game is simple:

1.  Have the program acquire a random number ranging from 1 to 100.

2.  Prompt the user for a guess or a question.

    Valid question is whether the number is odd or even.

3.  After acquiring the user's guess, tell them if they are correct, or if they have guessed "high" or "low".

4.  Go back to step 2, unless 10 (or say 20) chances have passed.  Typically it would take no more than 1-5 chances.

I don't think i was clear about what i wanted to happen. I wanted to make a simple A.I. so the user would (in their head) think of a number (let's say 30). Then the program would ask questions to narrow down the possibilities until it knows what number the user is thinking of. like with thirty: some questions would be "is it even?" true. "is it evenly divisible by five?" true. "is it evenly divisible by three?" true. "Is your number less than fifty?" true. "Is your number 30?" (as 30 is the only number meeting those answers)
If not arrays, what would be the best way to go about this?

---

### Post by Simon17 on 2010-02-21
If you want to do it this way, a simple way to do it would be to have just one array (or whatever container) of the numbers 1-100 and after each question, go through it and remove the elements that don't meet the criterion. For example,

```

foreach n in numbers
    if divisible_by_five(n)
        remove n from numbers
end

if n_elements numbers = 1
    done
else ask another question

```

---

### Post by daweefolk on 2010-02-21
so say i made an array of allnumbers[]. what would be the code to remove allnumbers[3] and if i did that, would the array just go straight from allnumbers[2] to [4]?

---

### Post by Simon17 on 2010-02-21
As I mentioned earlier, an array isn't the best container for the job, but doing this will help you learn something.

I already described how to remove elements from an array. To remove allnumbers[3], you simply move every element after 3 forward one step.

so allnumbers[3]=alnumbers[4];
allnumbers[4]=allnumbers[5];
...
allnumbers[i]=allnumbers[i+1];
up until the end of the array. Get the idea? Write some sort of loop to do this.

---

### Post by Some Penguin on 2010-02-21
You don't, unless you write a sparse array structure or use somebody else's code for that.

---

