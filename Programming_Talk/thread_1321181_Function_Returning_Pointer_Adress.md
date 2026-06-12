---
title: "Function Returning Pointer Adress"
date: 2009-11-09
forum: Programming Talk
---

### Post by cmwarre on 2009-11-09
Hey guys I'm trying to make a function that returns a pointer address.  Do you mind sharing how I would declare the prototype and how I would assign the pointer when I call it?  Thank you

---

### Post by efexD on 2009-11-09
Assuming you are asking about C++, it's simple.

```

int& getIntPtrAddress()
{
    int someNumber = 10;
    int& address = someNumber;

    return address;
}

```

---

### Post by jimi_hendrix on 2009-11-09
Prototype:
```

//example 1.  This returns the actual address
int *someFunctionA(int arg);

//example 2.  This takes a pointer as well as an arg and stores the data in the pointer's location
void someFunctionB(int arg, int *dest);

```Calling the function:

```

int *foo;
foo = someFunctionA(5); //Example 1
someFunctionB(5, foo); //Example 2

```

---

### Post by cmwarre on 2009-11-09
Oh sorry I was just talking about C.  So here is my program attached.  It's not all done yet 
and I'm still learning so be prepared to find a lot of bugs haha
Basicly I'm trying to write a function for a vending machine simulation program for my class
and this function is how the user chooses the snack that they want.  I just want it to return
the address of the matricie(however you spell that)  element chosen.

---

### Post by dwhitney67 on 2009-11-10
> **efexD said:**
> Assuming you are asking about C++, it's simple.

```

int& getIntPtrAddress()
{
    int someNumber = 10;
    int& address = someNumber;

    return address;
}

```

wtf?

You are returning a reference to a variable that will 'die' as soon as the function returns.  Where the heck did you learn to write code?

---

### Post by dwhitney67 on 2009-11-10
> **cmwarre said:**
> Oh sorry I was just talking about C.  So here is my program attached.  It's not all done yet 
and I'm still learning so be prepared to find a lot of bugs haha
Basicly I'm trying to write a function for a vending machine simulation program for my class
and this function is how the user chooses the snack that they want.  I just want it to return
the address of the matricie(however you spell that)  element chosen.

This is not a forum for seeking assistance with homework!  Consult with your teacher.

However, just to critique your code...

It appears that you have a 2-dim array of int values; why do you need to return a pointer??  Just return the value once you know the row and column of interest.

Btw, wrt code, do you know what a "kitchen sink" refers to?  It is when one plops many different steps into one function.  Try to to simplify your code so that you are not querying the user for input in the same function where you are accessing the data from the 'matrix'.  Also, look into toupper() (or tolower()).

Lastly, insert code within CODE tags; attaching a zipped file is lame.

---

### Post by jespdj on 2009-11-10
> **efexD said:**
> Assuming you are asking about C++, it's simple.

```

int& getIntPtrAddress()
{
    int someNumber = 10;
    int& address = someNumber;

    return address;
}

```
This code is a recipe for disaster.

The int someNumber is on the stack. As soon as the function returns, it disappears. The function returns a reference to a variable that has been cleaned up. This will lead to undefined behaviour. It might appear to work, but there's also a big chance that the program will crash.

---

### Post by silentrebel on 2009-11-10
> **efexD said:**
> Assuming you are asking about C++, it's simple.

```

int& getIntPtrAddress()
{
    int someNumber = 10;
    int& address = someNumber;

    return address;
}

```

The problem is that *somenumber* is declared and defined within a function.  Therefore its scope is restricted to that function.  As soon as the function ends, *somenumber* ceases to exist which means that the address that you've collected that is supposed to point to it will point to nothing (dangling pointer = dangerous, undefined, unwanted behaviour).
You have two choices here: 1) declare somenumber in the context that will call *getIntPtrAddress* so that the int can be passed as an argument to the function and then the function may extract the address and send it back in a return statement; 2) declare *someNumber* dynamically within the function so that it will not disappear when the functions execution is finished:
```

int * bobby;       //create a pointer to an array
bobby = new int;   //attribute a dynamic int to it 
//I haven't tested this code so try it out and let me know if you have trouble with it.

```

So your final code would look like this:
```

//solution 1
void main()
{
     int somenumer = 20;
     int& = getIntPtrAddress(somenumber);
}
int& getIntPtrAddress(anumber)
{
    return &anumber;
}

//solution 2
int& getIntPtrAddress()
{
    int * somenumber;
    somenumber = new int;
    *somenumber = 10;

    return somenumber;
}

```
I've been away a while from c and its relatives so please don't hesitate to point out any erroneous information...

---

### Post by PmDematagoda on 2009-11-10
Closed since the thread is related to a homework question.

---

