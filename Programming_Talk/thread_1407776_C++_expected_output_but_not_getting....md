---
title: "C++ expected output but not getting..."
date: 2010-02-15
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-15
If I input 10 for the amount of digits

and
3, 4, 2, 2, 3, 4, 5,6, 18, 5

I should...in theory... (according to the referencing guide) get out eventually

2, 3, 4, 5, 6, 18

unfortunately...I get nothing. 

I'm using n to define a position within a variable. 

EDIT

After I spotted an error, highlighted by a comment, the sorted numbers out put is

134529091 134529431 134514525 3715910

```

#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

bool sorter (int minim, int maxim) 
{
    return (minim < maxim);
}

struct sortClass 
{
    bool operator() (int minim, int maxim) 
    {
        return (minim, maxim);
    }
}mySort;

int main()
{
    int n = 0;
    int numbers[n];
    int a = 1; //continue program
    int b = 0;
    int numberCollection;
    
    

    cout << "This is a program to return a set of unique numbers from an input.\n\n";
    
    while (a <=1)
    {
        cout << "How many numbers do you wish to enter? (if 0 then the program will quit)\n";
        cin >> a;
        while (b < a)
        {
            cout << "\n\nPlease enter a number: ";
            cin >> numberCollection;
            numbers[n] += numberCollection;
            b++;
            n++; //<-this is the error I spotted. 

        }

        
        cout << "\n\nThese are the sorted numbers: ";
        vector<int> sortVect (numbers, numbers+n);
        vector<int>::iterator it;
        sort (sortVect.begin(), sortVect.end(), mySort);
        for (it=sortVect.begin(); it!=sortVect.end(); ++it)
        {
            cout << " " << *it;
        }


        //cout << numbers[n];

        cout << "\n\nThese are the numbers without duplicates: ";
        for (int i=n; i < (sizeof(numbers)/sizeof(int)); i++)
        {
            if (numbers[n] != numbers[n-1])
            {
            cout << numbers[n];
            }
        }
    
        a = 3; //quit entry.
    }

}

```

---

### Post by MadCow108 on 2010-02-15
int n = 0;
int numbers[n];

this is an zero sized array. you can't write into it because it has no space allocated to it (a c-array does not grow like a vector)
Reading from it results in undefined result (= garbage your getting)
(and its forbidden in standard code, gcc just adds this as an extension)

if your using vectors anyway, use them all the way.

Some interesting additions to your code.
sort also works on directly c arrays because a pointer is nothing else than a random access iterator
you can input directly from cin to a vector by using the input_iterators istream_iterator and copy

---

### Post by Ravenshade on 2010-02-15
You mean I need a vector instead of array because vectors are scalable where as arrays are fixed. 

Well great. >_> 

I had completely missed that int n=0...should have realised. Thanks once again MadCow.

---

