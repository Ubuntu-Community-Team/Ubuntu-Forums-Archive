---
title: "C++ question"
date: 2008-05-17
forum: Programming Talk
---

### Post by jus71n742 on 2008-05-17
I am not sure what kind of loop I want to use for this but I am thinking a for or if statement.
what I am trying to do is for example I have an input of say 44 and for each 10 I give someone a point so an input of 44 is 4pts. 
I would also like to figure out the flip side of that 
say input is 4 is minus 1 so the input would result in -4 pts.

I have been reading but can't get a clear understanding of how to go about it 

any assistance is greatly appreciated

---

### Post by amingv on 2008-05-17
I don't see where the loop fits in; you could just use integer division (if you want to discard the rest):

[PHP]int a = 44;
int b = 10
int points = a/b //gets assigned 4[/PHP]

Can you explain a little more, if that's not what you want to do?

---

### Post by jus71n742 on 2008-05-17
points is going to be a variable to keep a running total so in my other example 44 = 4 pts then the other was -4 pts then your total will be 0 ( they will all be added up later) I have  points set up as a completely separate int.  there will be a few more statements to input numbers I am just getting my pseudo code done right now

---

### Post by thadeoc on 2008-05-17
if you mean that given an input value you want to add one point for each 10 in the input, and subtract one point for each 1 left over, try:
```

int input = 44;
int points = input / 10; //points is set to 4
input = input % 10; // input is set to 4
points -= input;

```

---

