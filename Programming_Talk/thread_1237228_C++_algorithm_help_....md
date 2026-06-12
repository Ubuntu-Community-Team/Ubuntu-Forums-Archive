---
title: "C++ algorithm help ..."
date: 2009-08-11
forum: Programming Talk
---

### Post by Nuticulus on 2009-08-11
Hi,

I have a "row" class with members pixels[200], int numPixels, and int offset, and an "order" class with members int ord[100] and int off[100].

I also have 2 arrays of rows, row Good1[height] and row Unscrambled[height], of which only the first NumGood1 (int) elements are defined. 
Also there is an order object o, where ord[] and off[] are only defined from 0 to NumGood1 inclusive.

I need an algorithm that:

[LIST]
[*]Only changes the values of Unscrambled[]
[*]Tries to copy elements from Good1[] into Unscrambled[] so that Unscrambled[x].numPixels == o.ord[x] and Unscrambled[x].offset == o.off[x]
[*]Will, if called repeatedly, cycle through all possible solutions.
[/LIST]

Thankyou very much. I have been racking my brains out on this, so I hope someone is cleverer than I am. ;)

---

### Post by nvteighen on 2009-08-11
> **Nuticulus said:**
> Hi,

I have a "row" class with members pixels[200], int numPixels, and int offset, and an "order" class with members int ord[100] and int off[100].

I also have 2 arrays of rows, row Good1[height] and row Unscrambled[height], of which only the first NumGood1 (int) elements are defined. 
Also there is an order object o, where ord[] and off[] are only defined from 0 to NumGood1 inclusive.

I need an algorithm that:

[LIST]
[*]Only changes the values of Unscrambled[]
[*]Tries to copy elements from Good1[] into Unscrambled[] so that Unscrambled[x].numPixels == o.ord[x] and Unscrambled[x].offset == o.off[x]
[*]Will, if called repeatedly, cycle through all possible solutions.
[/LIST]

Thankyou very much. I have been racking my brains out on this, so I hope someone is cleverer than I am. ;)

Heck... can you please tell us what your code is supposed to do? (the task... what's your goal) Because, at first sight, I tend to think this is all overkill.

Anyway, some ideas (these ideas are language-independent):
[LIST]
[*]If you want Good1 to be really untouched, copy-construct the stuff when copying into Unscrambled. Don't pass a reference.
[*]The second part is trivial. Hell, you have written it almost by yourself!
[*]Ok, try using static variable to hold state across stack calls. But I'm not sure there are more than one single solution, is there?
[/LIST]

---

### Post by Nuticulus on 2009-08-11
Thanks for replying so fast.

The code is supposed to unscramble an image that has had its rows scrambled randomly.
In the image is a line of text. I have a table of order objects that correspond to different letters, the idea being that I can identify the first letter from performing a hash function on the image (bit complicated and not really relevant here), and use this to help unscramble the image.

There is more than one single solution.

Thanks for helping out...

---

