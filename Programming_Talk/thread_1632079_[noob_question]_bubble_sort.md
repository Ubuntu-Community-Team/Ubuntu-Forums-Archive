---
title: "[noob question] bubble sort"
date: 2010-11-27
forum: Programming Talk
---

### Post by sandtracks on 2010-11-27
hello there,

sorry to be making my first post directly here without introducing myself but i am exhausted after hours of banging up against a brick wall. i need another opinion.

i have just started studying IT and we were recently going over data structures and algorithms and naturally bubble sort was one of the first. 

Now we have an example in our book and from the book's website it is possible to download an example program (which is already compiled so i cannot look at the code). When I looked at the example last week, I became seriously confused as I could not match the code to the example and when I did some googling and found out what bubble sort does i was even more confused. When I look at other examples from the internet and work them out step by step it works.

I asked my lecturer this morning if the example is correct and he just said "yes, yes there are just many steps in between that are not shown in the example". So here i am again and after a couple more hours frustration and i still do not agree.

If anyone could be kind enough to look at this example for me, could you tell me whether you think it is a bubble sort or not?

I would be mighty grateful :) (the link to the example is down below)

[bubble sort]("http://yfrog.com/72bubblep")

[IMG]http://img254.imageshack.us/img254/7958/bubble.p[/IMG]
[IMG]http://yfrog.com/72bubblep[/IMG]

---

### Post by squenson on 2010-11-27
Yes, it is a bubble sort example.

The algorithm is:

```
From the first element to the last but one
    Compare this element with all the other elements on the right
        If one element on the right is lower, swap the elements
    End loop
End loop
```

So, you compare 45 with all the other elements; when it finds 7, you swap the elements, so the list becomes 7 45 etc
You continue with the second element and compare it with all the others, etc.

It's called "bubble sort" because the "ligher" elements move to the top of the list.

---

### Post by Arndt on 2010-11-27
> **sandtracks said:**
> hello there,

sorry to be making my first post directly here without introducing myself but i am exhausted after hours of banging up against a brick wall. i need another opinion.

i have just started studying IT and we were recently going over data structures and algorithms and naturally bubble sort was one of the first. 

Now we have an example in our book and from the book's website it is possible to download an example program (which is already compiled so i cannot look at the code). When I looked at the example last week, I became seriously confused as I could not match the code to the example and when I did some googling and found out what bubble sort does i was even more confused. When I look at other examples from the internet and work them out step by step it works.

I asked my lecturer this morning if the example is correct and he just said "yes, yes there are just many steps in between that are not shown in the example". So here i am again and after a couple more hours frustration and i still do not agree.

If anyone could be kind enough to look at this example for me, could you tell me whether you think it is a bubble sort or not?

I would be mighty grateful :) (the link to the example is down below)

[bubble sort]("http://yfrog.com/72bubblep")

[IMG]http://img254.imageshack.us/img254/7958/bubble.p[/IMG]
[IMG]http://yfrog.com/72bubblep[/IMG]

Maybe it is, if each "Durchlauf" (traversal) means going first from one end and then from the other end, too. It seems to me that that is what is happening. I would call it bubble sort, too.

---

### Post by lisati on 2010-11-27
There are a number of sites available with animations of different sorting algorithms that you might find interesting. Sadly FF appeared to lock up on my first choice, but here's another: [http://www.sorting-algorithms.com/](http://www.sorting-algorithms.com/)

---

### Post by sandtracks on 2010-11-27
> **squenson said:**
> Yes, it is a bubble sort example.

The algorithm is...

Thanks very much everyone. 

Back to the books and the code. 

The bubble sort examples I was looking at were all of the type: 

```
Compare positions 1 + 2 then swap if 1 > 2 
then compare next two positions and swap if 1 > 2
continue until all positions have been compared without any swaps being made
list is sorted

```

and this is why i was confused. I did not find any examples working like this one. Doh! Guess i should dig deeper next time.

I will try creating my own algorithm tomorrow.

---

