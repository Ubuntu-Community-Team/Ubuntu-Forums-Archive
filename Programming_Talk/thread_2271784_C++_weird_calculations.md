---
title: "C++ weird calculations"
date: 2015-04-01
forum: Programming Talk
---

### Post by Tristan_Williams on 2015-04-01
I already know Java, Bash, and a small amount of Python.
I'm going through online C++ lessons.

My current project is to write a program that:
1) Takes an int as input from the user
2) Calculates the sum of all even ints between 2 and input
3) Outputs the sum
4) Repeating until the user presses enter with no value entered



It compiles successfully, but the calculations have really weird behavior.

The first number I enter gets calculated correctly.

If the next number is a single-digit number, the same value is ouput that was output from the first number,
and it will keep outputting the same number as long as you enter single-digit numbers.

If I enter a two digit-number, the first (tens place) digit is ignored, so the second (ones place) digit is calculated, with
the new value being output. 

It seems that, from the second input onward, the most significant digit is ignored.



Here is the code:
```

#include <iostream>
#include <cstdio>
#include <sstream>
using namespace std;

int sumOfEvenInts (int stopValue)
{
    int start = 2;
    int sum = 0;
    int i = start;
    int stop = stopValue;
    
    while (i <= stop)
    {
        sum += i;
        i += 2;
    }
    
    return sum;
}

int main ()
{
    string userInput;
    int input;
    int finalSum;
    
    do
    {
        getline(cin, userInput);
        stringstream(userInput) >> input;
        
        finalSum = sumOfEvenInts (input);
        
        cout << "Sum: " << finalSum << endl;
    } while ((getchar()) != '\n');
    
    return 0;
}

```

---

### Post by GeneralZod on 2015-04-01
As a clue: if you enter:

10**<enter>**

getline will eat up the **<enter>** (though the **<enter>** won't appear in userInput - it is discarded).  What then will be the effect of the subsequent call to getchar? What will be the userInput if we do 

10**<enter>**

again?

[http://www.cplusplus.com/reference/string/string/getline/](http://www.cplusplus.com/reference/string/string/getline/)
[http://www.cplusplus.com/reference/cstdio/getchar/](http://www.cplusplus.com/reference/cstdio/getchar/)

---

### Post by Tristan_Williams on 2015-04-02
> **GeneralZod said:**
> As a clue: if you enter:

10**<enter>**

getline will eat up the **<enter>** (though the **<enter>** won't appear in userInput - it is discarded)

Okay, I see what you're saying. Thanks a lot

---

