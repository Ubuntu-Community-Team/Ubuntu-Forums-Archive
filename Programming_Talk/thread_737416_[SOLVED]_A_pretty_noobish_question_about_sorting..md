---
title: "[SOLVED] A pretty noobish question about sorting."
date: 2008-03-27
forum: Programming Talk
---

### Post by Tomosaur on 2008-03-27
Hola, amigos!

My head is crammed full of code at the moment for my final year uni project and I have hit a snag which is proving to be incredibly frustrating. I hope someone can help me out. I'm doing this in Java, but if anyone can just give me some pseudo-code or anything really to help me get past this hurdle I will love you forever.

Ok, here's the problem. I have an array of integers. I need to sort the **indexes** of these arrays. What I mean is, I have an array of integers with 7 elements in the array, I need to create a new array of 7 elements, but which holds the indexes of the elements in the first array. Something like this:

```

unsortedElementArray = [157] [118] [398] [265] [111] [80] [599]

(The indexes of the above elements are used to create
a new array. The index of the element with the highest
integer is placed in sortedIndexArray[0], index of
element with lowest integers goes in sortedIndexArray[6].

sortedIndexArray = [6] [2] [3] [0] [1] [4] [5]

```I hope that's clear enough?

I realise this is probably a fairly easy problem but to be honest my head is all over the place right now with this project and some personal stuff I won't bore you with, and every time I try to get this working I just get incredibly frustrated and feel like smashing the hell out of my computer. Nothing I've tried works :(

I could use a different data structure but the nature of the project means using arrays makes everything so much easier.

If anyone can help I'll be very grateful!

Thanks,
Tom

---

### Post by CptPicard on 2008-03-27
Well, if your array is "arr", then you create an array of the same length, index_arr[], and fill it with 0, 1, 2... arr.length-1.

Now, you run any of your sorting algorithms on index_arr, using arr[index_arr[i]] for the actual comparison value for placing the index at i in its new position in the sorted index_arr.

---

### Post by Tomosaur on 2008-03-29
Thanks for that, had to expand a little on your suggestion in order to finally get it working but you got me on the right track!

---

