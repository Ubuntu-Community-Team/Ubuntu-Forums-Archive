---
title: "C++ code error: glibc detected: ./a.out: free(): invalid pointer"
date: 2010-10-18
forum: Programming Talk
---

### Post by Asdra on 2010-10-18
Hello,

I'm making a basic calculator program that runs off of arbitrary precision arithmetic (APA).  So far, everything's been working...until recently, when I found out that for select cases only - I have no idea why only select cases instead of all or none - two of my functions, my addition and subtraction functions, will get the following error as taken from the terminal window:

*** glibc detected *** ./a.out: free(): invalid pointer: [some hexadecimal value]
Aborted

Most of the time, this is the general error I get, complete with a memory map which I have no idea how to read at my present level of knowledge and expertise.  If I try my addition function, I sometimes get the above error, but usually get something like this:

a.out: malloc.c:3096: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_end & pagemask) == 0)' failed.
Aborted

Again, I have no idea why these functions only fail sometimes, but work perfectly most of the time.  I've also done some minor testing on my own, and found out that in the cases where the program aborts like this, it will always fail after a function is finishing; the function will work exactly like it's supposed to, but the moment the function is done and about to exit the error comes up.

What's going on in my code?  If additional information is needed, I will provide it.  On that note, here is the code for the related segments of my program:

```
int main()
{
      int choice;//to get user's choice
      string num1, num2;
      
      cout << "Please enter the first number:\n";
      getline(cin, num1);
      cout << "Please enter the second number:\n";
      getline(cin, num2);
      
      //INCREMENTAL TEST 1: make sure strings are right
      cout << "First number is " << num1 << endl;
      cout << "Second number is " << num2 << endl;
      
      //prompt user for choice of function test
      
      return 0;
}
``````
void addition(string operand1, string operand2, int base)
{
      int i;
      normalize(operand1, operand2);
      string answer(operand1.size() + 1, 0);
      for(i = answer.size() - 1; i >= 1; i--)
      {
            answer[i] += (operand1[i-1] + operand2[i-1]) % base;
            if(operand1[i-1] + operand2[i-1] > base)
                  answer[i-1] = (operand1[i-1] + operand2[i-1]) / base;
      }
      convertString(operand1);
      convertString(operand2);
      convertString(answer);
      cout << operand1 << " + " << operand2 << " = " << answer << endl;
}
``````
void subtraction(string operand1, string operand2, int base)
{
    int i;
    string temp;
    bool neg = false;
    if(lessThan(operand1, operand2))
    {
        temp = operand1;
        operand1 = operand2;
        operand2 = temp;
        neg = true;
    }
    normalize(operand1, operand2);
    string answer(operand1.size(), 0);
    for(i = answer.size() - 1; i >= 0; i--) 
    {
        answer[i] += (operand1[i] - operand2[i]);
        if(operand1[i] - operand2[i] < 0 || answer[i] < 0)
        {
            temp = operand1;
            answer[i] += base;
            answer[i-1]--;
        }
    }
    convertString(operand1);
    convertString(operand2);
    convertString(answer);
    if(neg)
        cout << operand2 << " - " << operand1 << " = -" << answer << endl;
    else
        cout << operand1 << " - " << operand2 << " = " << answer << endl;
}
``````
void normalize(string &operand1, string &operand2)
{
      int i, difference;
      string temp;
      if(operand1.size() > operand2.size())
      {
            difference = operand1.size() - operand2.size();
            temp = operand2;
            operand2.resize(temp.size() + difference);
            for(i = 0; i < difference; i++)
            {
                  operand2[i] = 0;
            }
            for(i = 0; i < operand2.size() - 1; i++)
            {
                  operand2[i+difference] = temp[i];
            }
      }else if(operand2.size() > operand1.size())
      {
            difference = operand2.size() - operand1.size();
            temp = operand1;
            operand1.resize(temp.size() + difference);
            for(i = 0; i < difference; i++)
            {
                  operand1[i] = 0;
            }
            for(i = 0; i < operand1.size(); i++)
            {
                  operand1[i+difference] = temp[i];
            }
      }
}
```

---

### Post by GeneralZod on 2010-10-19
Where is convertString(...)? Also, there are two logical errors:

a) You are assigning 

```

operand2[i] = 0;

```

in normalize(...) where I presume you mean

```

operand2[i] = '0';

```

(I'm assuming you are trying to left-pad with "0"s, but may be wrong on this ... ?) and similarly for operand1; and

b) You are reading outside the bounds of temp in normalize(): add  

```

assert(i < temp.size());

```

before 

```

operand1[i+difference] = temp[i];

```

and

```

operand2[i+difference] = temp[i];

```
to see this (you'll need to #include <assert.h>).

EditL 

Woah - how did I miss this? More importantly, you're writing past the end of operand1/2.  Temporarily remove the other asserts, and add these in the relevant places to see:

```

assert(i+difference < operand1.size());

```

```

assert(i+difference < operand2.size());

```

Further edit:

And unless this is some homework exercise that has arbitrary restrictions on what libraries you are allowed to use, you can replace the padding with leading 0's with one line of code.  See [http://www.cplusplus.com/reference/string/string/insert/](http://www.cplusplus.com/reference/string/string/insert/)

---

### Post by Asdra on 2011-01-05
Awesome, thanks!  I'll give that a shot and see what happens.  And no, this isn't a homework assignment (probably obvious given the late response), it can basically be chalked up to "I was bored one day".

EDIT: The insert worked!  It does EXACTLY what it's supposed to do now.  Thanks very much!

---

