---
title: "[SOLVED] c++, triple loop"
date: 2009-01-01
forum: Programming Talk
---

### Post by ChanTico on 2009-01-01
Hi, I'm trying to write to a program where the intergers 1-10 are placed in a triangle such that the number above is equal to the difference of the two below.

Which is basically the same as putting the number 1-10, in any order and trying every combinaion. Is there a better way than using 10 loops?

I wrote the program and just got a flashing cursor, for a long time. Editing the code, I got this,

> 

int num [1], n(0); //My intergers

while (n<2)
{
num [n] =1; n++;
}

while (num[1] <11)
{
while (num [0] <11)
{
cout << num [1] << num [0];
num [0]++;
}
num [0]=1; num[1]++;
}


Which prints, all number 11 through 99, excluding any with zeros.

But.

> 

int num [2], n(0); //My intergers

while (n<3)
{
num [n] =1; n++;
}
while (num [2] <11)
{
while (num[1] <11)
{
while (num [0] <11)
{
cout << num [1] << num [0];
num [0]++;
}
num [0]=1; num[1]++;
}
num [0] =1; num [1]=1; num [2]++;
}

Appears to just crash, I only see a cursor flickering. I tried google and people seem to think that triple loops work fine. Is there anything obviously wrong?

---

### Post by slavik on 2009-01-01
if the cursor is just flickering, that means the program is still running.

I am trying to understand what you want to achieve ... are you looking for all possible combinations that would be achieve the mentioned triangle?

also, are there any other limits?

is this a valid triangle?
```

  1
 / \
8---9

```

---

### Post by ChanTico on 2009-01-02
No, there are ten numbers in every triangle.

---------a
-------b-----c
---d------e------f
g------h------i-----j

Where d=abs(g-h), b=abs(d-e) etc. Every number one through ten must appear once and only once. I can't see a more clever way other than going through all 10! combinations. I suppose 10 must be on the bottom.

The code above is what I did when I was trying to find why it wasn't working.

---

### Post by stderr on 2009-01-02
You can nest as many loops as you like. You could have 1000 nested while loops without any problems.

The issue is that you've only declared two spaces for integers in your int array, and you're trying to use three.

int num [2]

The two doesn't mean "go up to 2", so num[0], num[1] and num[2]. 
It means "I want two of whatever type in this array".

So in your first while loop you're trying to access num[2], which doesn't exist. 

You need to specify 

int num[3]

to get it to work.

In fact, if you stick a cout in the first loop, you see that it's failing to set num[2], it doesn't bother trying to increment n, and so it gets stuck in the while loop with n always = 2.

---

### Post by jmartrican on 2009-01-02
Its stuck on the first loop.

---

### Post by ChanTico on 2009-01-02
Thanks! Problem solved. Chears for the info arrays.

---

