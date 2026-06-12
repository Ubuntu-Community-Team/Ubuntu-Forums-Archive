---
title: "Groovy and Array sizes"
date: 2010-04-20
forum: Programming Talk
---

### Post by Ravenshade on 2010-04-20
Hi, 

I've been looking around at Groovy tutorials but it's a new language and the tutorials aren't yet refined. 

Can someone please tell me how to specify an array size? 

For instance, I want List A to always be the same size as List B. 

So far I'm forcibly making it the same size by putting the same number of variables in it.

---

### Post by Ravenshade on 2010-04-20
.... I should kick myself more often. 


int[] a1 = [15, 3, 2, 5, 8]
int[] b1 = a1

Solved.

---

### Post by Can+~ on 2010-04-20
> **Ravenshade said:**
> .... I should kick myself more often. 


int[] a1 = [15, 3, 2, 5, 8]
int[] b1 = a1

Solved.

I don't know Groovy, but I suspect that you're creating a shallow copy with that. Is that what you really want? b1 will act like a reference to a1.

---

### Post by Ravenshade on 2010-04-21
It works some how like the way it does in java, and not understanding the mechanics I'm surprised it works myself. 

It appears to copy everything that is in the first array to the second array and I can then use the first array and transfer the information between the two. It works fine for some reason. 

It was a work around, due to the fact I don't know that much syntax about java or groovy and I couldn't find a way to deal with the size of the array directly. Java accepts a forced array size and if I made a user interface to input data I could probably have incremented the space by making the size of the array the same as the number of values added. Well that was java. 

Unfortunately, I can't seem to do the same eg array.length(12) kind of thing works in Java but not in Groovy where arrays need to be defined by the values in there and by arrays I mean lists.

---

