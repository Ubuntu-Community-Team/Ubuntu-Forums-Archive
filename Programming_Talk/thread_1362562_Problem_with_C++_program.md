---
title: "Problem with C++ program"
date: 2009-12-23
forum: Programming Talk
---

### Post by blasles on 2009-12-23
Hi this is a program originally from C++ for dummies. I was wondering what i did wrong with my modifications.

ORIGINAL
```
]#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

// sumSequence - add a sequence of numbers entered from
//               the keyboard until the user enters a
//               negative number.
//               return - the summation of numbers entered
int sumSequence(void)
{
    // loop forever
    int accumulator = 0;
    for(;;)
    {
        // fetch another number
        int value = 0;
        cout << "Enter next number: ";
        cin  >> value;

        // if it's negative...
        if (value < 0)
        {
            // ...then exit from the loop
            break;
        }

        // ...otherwise add the number to the
        // accumulator
        accumulator= accumulator + value;
    }

    // return the accumulated value
    return accumulator;
}

int main(int nNumberofArgs, char* pszArgs[])
{
    cout << "This program sums multiple series\n"
         << "of numbers. Terminate each sequence\n"
         << "by entering a negative number.\n"
         << "Terminate the series by entering two\n"
         << "negative numbers in a row\n"
         << endl;

    // accumulate sequences of numbers...
    int accumulatedValue;
    for(;;)
    {
        // sum a sequence of numbers entered from
        // the keyboard
        cout << "Enter next sequence" << endl;
        accumulatedValue = sumSequence();
        
        // terminate the loop if sumSequence() returns
        // a zero
        if (accumulatedValue == 0)
        {
            break;
        }

        // now output the accumulated result
        cout << "The total is " 
             << accumulatedValue 
             << "\n"
             << endl;
    }

 
    cout << "Thank you" << endl;
    // wait until user is ready before terminating program
    // to allow the user to see the program results
    system("PAUSE");
    return 0; 
}
```

I tried simplifying ( in RED) but it does not seem to work?
What is wrong with this?



```
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;

// sumSequence - add a sequence of numbers entered from
//               the keyboard until the user enters a
//               negative number.
//               return - the summation of numbers entered
int sumSequence(void)
{
    // loop forever
    int accumulator = 0;
    for(;;)
    {
        // fetch another number
        int value = 0;
        cout << "Enter next number: ";
        cin  >> value;

        // if it's negative...
        if (value < 0)
        {
            // ...then exit from the loop
            break;
        }

        // ...otherwise add the number to the
        // accumulator
        accumulator= accumulator + value;
    }

    // return the accumulated value
    return accumulator;
}

int main(int nNumberofArgs, char* pszArgs[])
{
    cout << "This program sums multiple series\n"
         << "of numbers. Terminate each sequence\n"
         << "by entering a negative number.\n"
         << "Terminate the series by entering two\n"
         << "negative numbers in a row\n"
         << endl;

    // accumulate sequences of numbers...
    int accumulatedValue;
    for(;;)
    {
        // sum a sequence of numbers entered from
        // the keyboard
        cout << "Enter next sequence" << endl;
  
        
        // terminate the loop if sumSequence() returns
        // a zero
        if ([COLOR="red"]sumSequence()[/COLOR] == 0)
        {
            break;
        }

        // now output the accumulated result
        cout << "The total is " 
           [COLOR="Red"]  << sumSequence()[/COLOR]
             << "\n"
             << endl;
    }

 
    cout << "Thank you" << endl;
    // wait until user is ready before terminating program
    // to allow the user to see the program results
    system("PAUSE");
    return 0; 
}
```


Thanks in advance

---

### Post by eewoz on 2009-12-23
What specifically is happening that makes you think the program is not working?

---

### Post by MindSz on 2009-12-23
I haven't done C++ in a while, but I think the problem is that you're calling the sumSequence() function twice where you should only be calling it once.

...oh, and please try to put your code in tags so it's more readable.

---

### Post by dwhitney67 on 2009-12-23
You are calling sumSequence() twice, which is not mimicking what was done in the original program.

You need to get the result from sumSequence(), and then use that result for comparison, printing, etc.

P.S.  Next time post your code in CODE tags.

---

### Post by blasles on 2009-12-23
Sorry bout not using Code tags. Still new to this forum. Which line did i call out sumSequence() twice? (still a tyro in programming)

> What specifically is happening that makes you think the program is not working?
It did not do what it was supposed to do

---

### Post by Queue29 on 2009-12-23
You are calling sumSequence() twice:

```
        if (**sumSequence()** == 0)  // first time
        {
            break;
        }

        // now output the accumulated result
        cout << "The total is " 
             << **sumSequence() **  // second time
             << "\n"
             << endl;
    }
```

Every time you call a function, that function will run. In this case, you are running sumSequence() twice, one in the if statement, and the next time in the cout. It will run both times, and you will probably (depending on user input) get different values returned each time.

---

### Post by blasles on 2009-12-24
So by assigning accumulatedValue = sumSequence();
it will prevent the function from running again by taking it's value?

Thanks alot for all your help :)

---

### Post by lisati on 2009-12-24
> **blasles said:**
> So by assigning accumulatedValue = sumSequence();
it will prevent the function from running again by taking it's value?

Thanks alot for all your help :)

It won't actually prevent it running twice, but will put the result somewhere that your main program can actually use the value it returns. 

Rule of thumb: in general, functions that you call have no way of knowing what you do (if anything) with the results they return. They'll assume you know what you're doing, so unless you design them to repeat a calculation or result on demand, they'll blindly plug away not "knowing" any better.

---

### Post by blasles on 2009-12-25
Finally got it :) thanks alot guys

---

