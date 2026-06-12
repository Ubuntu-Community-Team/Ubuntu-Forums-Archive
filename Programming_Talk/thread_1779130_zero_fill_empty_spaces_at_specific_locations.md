---
title: "zero fill empty spaces at specific locations"
date: 2011-06-10
forum: Programming Talk
---

### Post by rcktsingh on 2011-06-10
Hi Guys,

I have a small question. I have a file in the following format: 
> 
1 2                                                 <---- a space between 1&2
1 2 3
1 2
1 2 3 4
2 4


The values in the code actually represent numbers(not necessarily single digit), but they can be any number, can be floating point values too.

Input file: For a particular row, each number is separated from another by a single whitespace (the separator can't be anything other than whitespace).

My task: I want to zero fill the empty spaces in such a way that it looks like this, i.e. fill up the empty spaces in such a way that it gives me a nice matrix-looking format:
> 
1 2 0 0
1 2 3 0
1 2 0 0
1 2 3 4
2 4 0 0


Output file: Same rule applies. For a particular row, each number is separated from another by a single whitespace only.

Language used: Python(or may be Shell, if that's possible)

I know there is this function called zfill, but I don't think that would be much of a help to me. 

My solution: Find the (maximum length/2) of each line, using len and max functions. Then, using split(), fill up with zeros at appropriate places of each line. I am afraid it might turn into a dirty code and I'm sure _there are better ways_ to accomplish this task. 

Any suggestion is welcome. 

Thank you!

---

### Post by simeon87 on 2011-06-10
What do you do when a number is more than one digit? For example:

```
 1 0.3 400 4
 2   5   3 1
40  30   5 5
```

Is that how you want it? In that case the algorithm is not very difficult:

- For each column i, determine the maximum width m_i (3 digits, 2 digits, etc)
- Let k be the number of spaces between the columns
- For each number per line:
-- Determine width of number
-- Determine if additional spaces are needed in front (relative to m_i) and add them
-- Write the number and additional spaces, if any
-- If there is at least one more number:
--- Write k spaces

---

### Post by rcktsingh on 2011-06-14
Thank you. This helped. and Yes. thats how my solution should have looked like.

---

