---
title: "C++: For and Vectors?"
date: 2011-06-10
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-06-10
Alright so let me begin this by saying hello and thanks to all the people on this forum who helped me to get started on programming 

And also for solving my very Rookie doubts:

Alright I know this is very easy to understand but even though
I'm not getting it, I would like to have a deep understand on this for being able to use them as easy I use "cout" and "cin".

-----------------------------------------------------------------
Warning this is gonna be slightly large.

OK first we have this code:

```


using namespace std;
int main()
{

vector<int> v;

int i;                                                                      
i = 1;                                                                             

v.push_back(i);

cout << v[i];

cin.get();
return 0;
} ///:~


```

Till there everything is OK I get that the "v[i]" means 
that "v" contains "i" right? 
if im wrong feel free to tell me.

Now this one its giving me a good headache:

```


using namespace std;
int main()
{

vector<int> v;                                                                 

unsigned int i;

for(i = 0; i < 10; i++)
v.push_back(i);

for(i = 0; i < v.size(); i++)
cout << v[i] << endl;

cin.get();
return 0;
} ///:~



```

The lines:

```


for(i = 0; i < 10; i++)
v.push_back(i); 


```

I get that for the integer "i" first: 

(It gets the value of "0")

Then:

(If the value from "i" its less than 10)

Then:

(It adds 1 to that value till it reaches 10).


After that we put it inside the vector, Nothing weird till there
Though if I'm wrong please tell me.


Now this:

```


for(i = 0; i < v.size(); i++)
cout << v[i] << endl;



```

Alright I know that as for now the "i" variable its contained inside the vector but, why are we using it again? 

i mean this changes aren't going to affect "i" behavior, Cause if  write this:

```


unsigned int i;
v.push_back(i);  
for(i = 0; i < 10; i++)


```
 

It will not work it will do weird stuff.

And if when I do write the following:

```


for(i = 0; i < v.size(); i++)
v.push_back(i);   
cout << v[i] << endl;
                        


```


I get, nothing. Just a blue screen 
(My terminal has blue backgroud.)

Why this happens?


And getting back to the the line:

```


for(i = 0; i < v.size(); i++)
cout << v[i] << endl;                                                                 


```

("i" equals to "0") 

Thats something easy to get.

but (if "i" < v.size() then i++)

What?

OK whats the vector size why is: (nothing) I mean the Book 
I'm studying from says that that value is self-explanatory.

but "i" increase its value by 1 if this is the case....

For not making this too long the output of this code is:


```


0
1
2
3
4
5
6
7
8
9


``` 



I know i can do this without vectors anyway why to use them but according to the book they will be used on the next pages.



So anybody could give me a hand on this please:KS

---

### Post by ThatCoolGuy220 on 2011-06-10
Must add i wrote them line by line I'm not copy paster kind of people I like to understand stuff

---

### Post by JupiterV2 on 2011-06-10
To solve this problem you need to overcome one simple thing: variables change.

The statement:
```
for (int i = 0; i < 10; i++)
    v.push_back(i);
```

'i' is just a variable containing a number. So, for each iteration (each loop) of the for loop, the number contained in the variable 'i' is incremented '++' by one. So, were you to unravel this loop, it would like like (be inequivalent to):

```
v.push_back(0);
v.push_back(1);
v.push_back(2);
...

v.push_back(9);
```

In my above example, the variable 'i' only has scope local to the for loop. In your code, 'i' is in the same scope as both loops, so you can reuse it. The second for loop resets the variable to '0' and then increases it by one until it reaches the size, v.size(), of the vector, which happens to be 10.

And remember, we humans might count from 1-10 but a computer counts from 0-9. That is why you usually see:

```
for (i = 0; i < 10; i++) {...} /* count from 0 to 9 */
```

...but you could just as easily do:
```
for (i = 1; i <= 10; i++) {...} /* count from 1-10 */
```

In the case where you wrote:
```
for(i = 0; i < v.size(); i++)
v.push_back(i);   
cout << v[i] << endl;
```

Better code layout would save you here. When you don't use curly braces, only the next line is included in the loop. So, this is what happened:

```
/* this loop exits when i == 10;
for(i = 0; i < v.size(); i++)
    v.push_back(i); /* vector is filled with 0-9 */
 
cout << v[i] << endl; /* i == 10 */
```

You're actually accessing an index of your vector which has not been initialized. I'm not sure but I think in C++ this is undefined behaviour (anyone know for sure?).

BTW, its good that you write from scratch, you'll retain the things you learn better. Copy and paste just teaches you keyboard shortcuts and nothing else.

---

### Post by SledgeHammer_999 on 2011-06-10
> **ThatCoolGuy220 said:**
> Alright so let me begin this by saying hello and thanks to all the people on this forum who helped me to get started on programming 

And also for solving my very Rookie doubts:

Alright I know this is very easy to understand but even though
I'm not getting it, I would like to have a deep understand on this for being able to use them as easy I use "cout" and "cin".

-----------------------------------------------------------------
Warning this is gonna be slightly large.

OK first we have this code:

```


using namespace std;
int main()
{

vector<int> v;

int i;                                                                      
i = 1;                                                                             

v.push_back(i);

cout << v[i];

cin.get();
return 0;
} ///:~


```

Till there everything is OK I get that the "v[i]" means 
that "v" contains "i" right? 


WRONG! v[i] means "show the value that "v" has at "i" position". Or in your case in the second position. REMEMBER: In C++(and C) everything begins counting from 0 not 1. So you're looking for v[0] == i == 1. v[i] (v[1]) doesn't exist yet. Your vector at this point holds one element, not two.

Think a std::vector as an array and read this-> [http://www.cplusplus.com/doc/tutorial/arrays/](http://www.cplusplus.com/doc/tutorial/arrays/)

DISCLAIMER: I didn't read the rest of your post. I'll read it later. Maybe your problem is related to your misunderstanding.

---

### Post by ThatCoolGuy220 on 2011-06-10
Thank you Jupiter and Sledgehammer for your responses....

As now I'm going to eat some and workout for a while 

This nite I will be sited on my Laptop realizing stuff

brb.

Oh I will leave it on BTW

---

### Post by ThatCoolGuy220 on 2011-06-10
Im back well,

Arrays:
Well i got little confused about manage memory allocation I assume has nothing to with the memory of the pc?

Thanks Hedgehammer for clearing that stuff about "v[i]"

Well I did a small program with them but as my book will be using vectors

i really hope this gets clearer.....


Add:

JupiterV2

I have been reading what you wrote too and: 

I've been playing around with the code and I almost get it:

```


vector<int> v;                                                                 

unsigned int i;

for(i = 0; i < 10; i++)
v.push_back(i);

int i2;

cin >> i2;

for(i = i2; i < v.size(); i++)
 
cout << "\n" << v[i] << endl;


```

Line:

```


for(i = i2; i < v.size(); i++).


```

Since I requested an input, this gave me a bigger overview of this:


(for "i" that is equal to what we had as input now if "i" its the value of "i" is less than the size of the contents of "v")

Though I experimented by doing this:

```


vector<int> v(10);                                                                 

unsigned int i;


int i2;

cin >> i2;

for(i = i2; i < v.size(); i++)
 v.push_back(i);
cout << "\n" << v[i] << endl;


```

It crashed my laptop for a while :-k #-o
Then it became slow and sluggish till i closed the terminal.


JupiterV2 I don't completely get what you are saying when you tell me to not to use curly brackets

I mean aren´t there a way for not using 2 "for" statements since it confuses me.

---

### Post by JupiterV2 on 2011-06-11
I most certainly did NOT say to not use curly brackets. (Must be getting late, I'm using double negatives! Yikes!)

Let me clarify:

When you use curly braces around the contents of the for loop, everything within the loop is run through. When you omit (don't use) braces, only the first line to follow the loop declaration is called.

An example:
```
#include <iostream>

using std::cout;
using std::endl;

int main (void)
{
  // This loop should print 0-4 AND "whee!" each loop
  for (int i = 0; i < 5; i++) {
    cout << i;
    cout << "wheee!" << endl;
  }

  // This loop should print 0-4, and "whee!" once
  for (int i = 0; i < 5; i++)
    cout << i << endl; // part of the loop
  cout << "whee!" << endl; // NOT a part of the loop

  return 0;
}
```

I would guess that the code that crashed your computer would be because push_back() will reallocate your array as you add new integers, and won't stop until you run out of memory. Your loop takes the size of the vector, which constantly grows, so that the only way it can stop is by running out of memory. That's likely why your laptop crashed.

(BTW, Go Canucks! Go! WOOO!!)

---

### Post by ThatCoolGuy220 on 2011-06-11
Lol sorry was a small misunderstood about the curly brackets;

I gonna read what you wrote now and yeah Go! Canucks!,
My Cousin was on Canada. Next time he will bring me there, such a beautiful country.

---

### Post by slooksterpsv on 2011-06-11
I retract my comments things work differently with C++ than what compilers I used to use.

Oh the reason it fails to work is cause v.size() is changing CONSTANTLY, whenever you push something onto a vector it increases its array size, so we start at 10, we push 1, it makes it 11, so the for loop will never end.

---

### Post by dwhitney67 on 2011-06-11
> **ThatCoolGuy220 said:**
> 
So anybody could give me a hand on this please:KS

I'm not as entertaining as the others.  My suggestion to you is to stop learning C++ from a forum, and instead, take the time to learn it from a book or from an on-line resource such as [http://www.cplusplus.com/doc/tutorial](http://www.cplusplus.com/doc/tutorial).

---

### Post by Petrolea on 2011-06-11
> **dwhitney67 said:**
> I'm not as entertaining as the others.  My suggestion to you is to stop learning C++ from a forum, and instead, take the time to learn it from a book or from an on-line resource such as [http://www.cplusplus.com/doc/tutorial](http://www.cplusplus.com/doc/tutorial).

I agree. Your problem is that you don't even understand the basics of C++ and you already use vectors. First learn about loops, arrays and use of curly brackets and then get to something harder. The link in the post I quoted is a good start. Make sure to read the text also, not just look at code.

---

### Post by nvteighen on 2011-06-11
I agree with dwhitney67. Please, follow that tutorial, which is probably the best one you'll find for your needs.

Your problem is that you don't understand what a for-loop is. In part, because the *for* keyword is slightly cryptic.

The syntax is:
```

for(start; condition; step)
{
    ...
}

```

And the semantics are:
```

Do *start* once. Repeat *action* while *condition* is true and do *step* after each iteration

```

In other words, the "generic" for-loop I wrote above is equivalent to the following while-loop:
```

start;
while(condition)
{
    ...
    step;
}

Take a look on this snippet:
[CODE]
#include <iostream>

int main()
{
    for(int i = 0; i < 10; i++)
    {
        std::cout << i << std::endl;
    }

    return 0;
}

```

Before you compile and test it, try understanding what it does and why does it work.

---

### Post by ThatCoolGuy220 on 2011-06-11
Ok ok. I feel some tension here.

Must said that I saw that comming.

I stated on previous posts, that I'm studying from a book. (Thinking in cpp)

I just had a doubt about the uses os vector with for statement.

Especfically why it had to have 2 "for" statement instead of one to do the job its suppose to do.

I thank you guys since I learned some usefull stuff that got me closer to the understanding of this little part...

---

