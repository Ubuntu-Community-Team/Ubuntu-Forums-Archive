---
title: "true/false question"
date: 2012-11-20
forum: Programming Talk
---

### Post by littlerunaway on 2012-11-20
Hi everybody.
so I'm new here and new to programming in general so my questions might sound a bit too...dumb.

I need to write a program that switches between 2 modes. it does one thing, and if I press a certain number it does something else.
if I press it again it goes back to the first mode.
what would be the best way to take a variable and switch it between 2 options (like true/false or 1/0)? 

I still haven't exactly figured out this whole bool type variable and how do I check weather it's true or false. 

(I'm working with the c99 version)

---

### Post by MG&amp;TL on 2012-11-20
> I still haven't exactly figured out this whole bool type variable and how do I check weather it's true or false. Standard C doesn't have a boolean variable. What you can do is check whether something is 0 or not. If it's 0, then it returns false. If not, it returns true.

Example:

```
#include <stdio.h>

int main() {
    int test = 0;
    if(test) printf("This won't happen\n");
    if(!test) printf("This will happen!\n");

    int test1 = 1;
    if(test1) printf("This will happen!\n");
    if(!test1) printf("This won't happen.");
    
    return 0;
}

```...this works with any data type, not just int, AFAIK.

---

### Post by littlerunaway on 2012-11-20
But we've been told that we can use bool variable if we include <stdbool >. or am i wrong?
and suppose i do what you offered, how do i use one variable and switch it's value between 1 and 0?

---

### Post by MG&amp;TL on 2012-11-20
> **littlerunaway said:**
> But we've been told that we can use bool variable if we include <stdbool >. or am i wrong?
and suppose i do what you offered, how do i use one variable and switch it's value between 1 and 0?
 
You can, but for your purposes, you probably don't need to.
 
Just set it to 1 (or more) or 0, depending on how you take input.

---

### Post by littlerunaway on 2012-11-20
But how do i switch between 1&0 ?for the same variable?

---

### Post by littlerunaway on 2012-11-20
I mean i can think of ways but i wanted something like var =!var;but i think i need a variable that can get only 2 values for that

---

### Post by Vaphell on 2012-11-20
*var = !var* will work, try it.

---

### Post by littlerunaway on 2012-11-20
Are you talking about a bool type or an int type?

---

### Post by MG&amp;TL on 2012-11-20
Dare I ask what is wrong with (for example, pseudocode):
 
*flag = 0*
*If condition*
*flag = 1*
*Else *
*flag = 0*
 
?
 
Although vaphell's suggestion will work as well.

---

### Post by littlerunaway on 2012-11-20
I need to go back and forth between 1&0 with the same condition . meaning first time condition means frog=1. next time the same condition means frog=0

---

### Post by Bachstelze on 2012-11-20
> **MG&TL said:**
> Standard C doesn't have a boolean variable. 


I am not sure what you mean by "a boolean variable", but standard C certainly does have a bool type since C99. Also note sure what "this" refers to in

> **MG&TL said:**
> ...this works with any data type, not just int, AFAIK.

*EDIT:* Okay...

> **MG&TL said:**
> You can, but for your purposes, you probably don't need to.
 
Just set it to 1 (or more) or 0, depending on how you take input.

What is this? There is a type bool, its purpose is to represent boolean values. Of course you don't "need" to use it, and you don't "need" to use an int, either. You could use a float, or a struct, or whatever. But a bool is the right thing to use. Not an int or anything else.

---

### Post by Bachstelze on 2012-11-20
What I said above notwithstanding, just because a variable can only take two values does not necessarily mean it should be made a bool. A bool can not take any two values, it can only take the values true and false. This is a good use of bool:

```

bool found = false;
for (int i=0; i<n; i++) {
    if (t[i] == SOME_VALUE) {
        found = true;
    }
}
```

This is a bad one:

```
bool turn = true;
for (;;) {
    /* Play */
    turn = !turn;
}
```

it should be:

```
#define WHITE 1
#define BLACK 0

int turn = WHITE;
for (;;) {
    /* Play */
    turn = (turn == WHITE) ? BLACK : WHITE;
}
```

A good rule of thumb is: add a question mark after the name of your variable. If you can answer the resulting question with yes or no, make it a bool. Otherwise, don't.

---

### Post by littlerunaway on 2012-11-20
So i do need to use a bool type variable?that's my problem. Do i give an initial value of true or 1? and how do i check which value it holds? with frog=1 condition?

---

### Post by littlerunaway on 2012-11-20
I meant frog ==1 of course

---

### Post by dwhitney67 on 2012-11-20
> **Vaphell said:**
> *var = !var* will work, try it.

Yep.

Another way (assuming var is initialized to either 0 or 1)...
```
var ^= 1;
```

And with C99 style:
```

#include <stdbool.h>
...
bool var = false;
...
var ^= true;

```

---

### Post by littlerunaway on 2012-11-20
We haven't learnt that one so im not sure what it means

---

### Post by dwhitney67 on 2012-11-20
> **littlerunaway said:**
> I meant frog ==1 of course

You can do that.  A simple if/else is all that is required.  Depending on circumstances, it is sometimes helpful to use a terciary-style of statement.

Examples:
```

#include <stdbool.h

int main(int argc, char** argv)
{
    bool args_given = (argc > 1);

    if (args_given)
    {
        // parse command-line options
    }
    else
    {
        // no command-line options given
    }
    ...
    return 0;
}

```
```

...
printf("The value is %s\n", (value ? "true" : "false"));
...

```

---

### Post by Bachstelze on 2012-11-20
> **littlerunaway said:**
> So i do need to use a bool type variable?that's my problem. Do i give an initial value of true or 1? and how do i check which value it holds? with frog=1 condition?

What does "frog" even mean? Whether you should make it a bool or not depends on this. In any case, as such it most likely fails the bool test of my post #12.

---

### Post by littlerunaway on 2012-11-20
Frog is a variable that should get true or false. how the programs behaves depends on what frog hold. frog also should change between 1&0 under the same conditions

---

### Post by Bachstelze on 2012-11-20
That's not what I meant. Why is your variable named "frog"?

---

### Post by dwhitney67 on 2012-11-20
> **littlerunaway said:**
> Frog is a variable that should get true or false. how the programs behaves depends on what frog hold. frog also should change between 1&0 under the same conditions

You indicated that you wished to use C99.  Thus don't use 1 or 0, but true or false instead.  Include the header file <stdbool.h>

```

#include <stdbool.h>

int main()
{
    bool frog = false;

    // Using the NOT operator
    frog = !frog;    // now frog is true
    frog = !frog;    // now frog is false

    // Using the XOR operator
    frog ^= true;    // now frog is true
    frog ^= true;    // now frog is false

    ...
}

```

P.S.  These statements are equivalent:
```

frog ^= true;

// and

frog = frog ^ true;

```

---

### Post by littlerunaway on 2012-11-20
No reason. someone just gave it that name on this thread

---

### Post by Bachstelze on 2012-11-20
It was "flag"... Anyway, not knowing what exactly your program does or what the variable represents, I can't say whether you should make it a bool or not, just refer you to the last paragraph of my post #12.

---

### Post by dwhitney67 on 2012-11-20
> **Bachstelze said:**
> What does "frog" even mean?

I think it was meant as a joke... "bool frog" == "bullfrog".

---

### Post by littlerunaway on 2012-11-20
What i need to know is not if i need a bool or not. i just want to know how to use it. do i give it true /false or 1/0 ? and how do i check what a bool type variable holds.

---

### Post by dwhitney67 on 2012-11-20
> **littlerunaway said:**
> What i need to know is not if i need a bool or not. i just want to know how to use it. do i give it true /false or 1/0 ? and how do i check what a bool type variable holds.

](*,)

Have you not paid any attention to the examples that I have provided???

---

### Post by Elfy on 2012-11-20
> **littlerunaway said:**
> Hi everybody.
so I'm new here and new to programming in general so my questions might sound a bit too...dumb.

I need to write a program that switches between 2 modes. it does one thing, and if I press a certain number it does something else.
if I press it again it goes back to the first mode.
what would be the best way to take a variable and switch it between 2 options (like true/false or 1/0)? 

I still haven't exactly figured out this whole bool type variable and how do I check weather it's true or false. 

(I'm working with the c99 version)

> **littlerunaway said:**
> But we've been told that we can use bool variable if we include <stdbool >. or am i wrong?
and suppose i do what you offered, how do i use one variable and switch it's value between 1 and 0?

> **littlerunaway said:**
> We haven't learnt that one so im not sure what it means

The forum is not a homework service.

> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.There doesn't seem to be much in the way of your work here - when you've done some and need help or hints with THAT - post again.

Closed

---

