---
title: "c++ vocabulary"
date: 2007-07-03
forum: Programming Talk
---

### Post by zerobinary on 2007-07-03
i don't get what is loop invariant mean 
can someone plz help me

---

### Post by hod139 on 2007-07-04
Here is wikipedia's definition: [http://en.wikipedia.org/wiki/Loop_invariant](http://en.wikipedia.org/wiki/Loop_invariant)
What don't you get?

---

### Post by zerobinary on 2007-07-04
i don't get what is invariant and 
this means a loop invariant is an invariant used to prove properties of loops.
so loop invariant is something that is not changing ???????
and that do they mean by a predicate that will always keeps its truth value throughout a specific sequence of operations, is called (an) invariant to that sequence.

---

### Post by Paul820 on 2007-07-04
zerobinary, it tells you in the book what an invariant is. It's chapter 2 - section 2.3.2 'Designing a while statement'. If you read that section he tells you all you need to know.

---

### Post by zerobinary on 2007-07-04
i did he say is something unchange but the point is i don't quite get what did he meant 
and i have read it 3 time just don't understand 
i know i sounds like a lie but it is the truth i seriously don't get what does he means plz come back and help me plz
I asked because after reading that section i don't get it 
they say loop invariant which is a property that we assert will be true about a while each time it is about to test its condition which I still don't get it after reading it more than 3 times plz come back and help 
i need ur help and is invariant same as loop invariant because it looks kind of the same in accelerated c++
they give us an example like this in the book 
but i still don't get it
```

//invariant:we have written r rows so far
int r=0
while (r!=rows) {
//we can assume that the invariant is true here
//writing a row of output makes the invariant false
std::cout<<std::endl;
//incrementing r makes the invariant true again
++r;
}
basically i don't get what does their comment mean

```

---

### Post by nitro_n2o on 2007-07-05
First of all a predicate is a term used in Logic, which means a statement that is either true or false.. 
An invariant is not something essential to completely understand in order to program. It's mainly used to verify the correctness of your program in terms of logic and computations. You need this when you are trying to mathematically prove that your program will do what it should do. (YES,it's PAIN) 

Simply, and invariant is something you assume it has a certain value, most of the time the value TRUE, before executing the loop and it should hold the same value when the loop is over. 

In the while loop example you posted, i think wht they r trying to say is that "r" denotes the number of rows (lines) written to the screen in total.. 
Assuming that you haven't written anything you started with r=0 (TRUE), then without looking at the loop if you state that r is an invariant that represents number of line written, everybody should believe it.... Why? because, in your implementation you output a line and increment r. Thus, regardless whatever you do, "r" will be the number of line written by the loop

Hope that helps

---

### Post by Paul820 on 2007-07-05
zerobinary, nirto_n2o has explained it for you. Don't worry about it too much. It's not imperative that you learn it but it does help. If you need some more help just ask. I will try to answer the best i can.

---

### Post by zerobinary on 2007-07-05
thx for the help u has offered me and thx i have finally understand what does it mean and thank u for taking ur precious moment to help me

---

