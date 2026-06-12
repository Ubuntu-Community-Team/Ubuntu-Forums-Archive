---
title: "C++ Arrays"
date: 2010-02-15
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-15
Okay, is it possible once an array is defined.... C++ for an example, 

to be able to get an array to check itself? 

so theoretically

if 
num[1] == num[1] or num[2] or num[n] (where n could be any position in the array)

then 
cout << num [1]


It's just a general problem which I have to apply to three languages >_> I thought I had the basic solution worked out but then realised it would return a few more numbers than I wanted.

---

### Post by LKjell on 2010-02-15
Yes and no. Depends on what type of comparison you want to do.
Ask yourself this: if you have two pointers with equal values but different memory location does ptr1 == ptr2 evaluates true?

---

### Post by MadCow108 on 2010-02-15
what exactly do you want to do? Your questions are very hard to understand...
find an element?
use find()

get an array with unique entries?
use unique()

you'll probably find what you need here:
[http://www.cplusplus.com/reference/algorithm/](http://www.cplusplus.com/reference/algorithm/)

and yes you can compare array elements again whatever you want (also them self) as long as the comparison is well defined.

---

### Post by Ravenshade on 2010-02-15
If I have an array with the values 3, 5,  6, 9, 9, 3, 4, 5

I want to put all the numbers into the correct part of the array. (done). 

Then I want to print out all of the unique numbers. 

so 3, 5, 6, 9 , and 4. 

My original idea (since I've got to do it in three languages)

was 

p = position of array

if array[p] ==!n && array[p+1] ==!n
Then output number. 


Basic pseudo debugging told me that wasn't going to work. Essentially I want array [0] to check against [0] through maximum size of the array in this instance thats 8 and check for all instances of duplication. 

I've also got to do this the hard way, no cheating by using a one function kill.

I am looking at the unique function however

edit

Unique function doesn't work.

---

### Post by SemiBuz on 2010-02-15
```
int numbers[] = {1, 2, 4, 4, 7, 8, 8, 9};

for (int i = 1; i < (sizeof(numbers)/sizeof(int)); i++)
{
    if (numbers[i] !=  numbers[i-1]) {
        cout  << "Number [" << i << "]: " << numbers[i]  << endl;
    }
}

```

---

### Post by Ravenshade on 2010-02-15
That's the version I came up with, mix up the numbers and you get random results...

edit

which is why I need it to compare the entire array and not just -1 (my version was +1)

---

### Post by SemiBuz on 2010-02-15
[Sort]("http://en.wikipedia.org/wiki/Sort_%28C%2B%2B%29") them ?

---

### Post by Ravenshade on 2010-02-15
-.-" 

Thanks.

---

