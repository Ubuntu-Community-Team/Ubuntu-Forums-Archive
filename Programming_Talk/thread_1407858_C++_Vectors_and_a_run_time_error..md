---
title: "C++ Vectors and a run time error."
date: 2010-02-15
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-15
On the advice of MadCow, I've been converting my array's in this program to vectors, with limited access. (at least that's not complete failure). I had managed to get everything worked out but then this happened. 


The objective of my code is to sort a set of numbers and then remove any duplicates. If that helps with the reading

The code compiles, but on runtime it throws 

```
terminate called after throwing an instance of 'std::out_of_range'
  what():  vector::_M_range_check
Aborted
```

I'm not entirely sure what this means, it gives me no line where the bug might be occuring. Could someone point me to the line. 


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
    vector<int> numbers;
    vector<int> sortVect (numbers.at(n), numbers.at(n+1));
    vector<int>::iterator it;
    int a = 1; //continue program
    int b = 0;    

    cout << "This is a program to return a set of unique numbers from an input.\n\n";
    
    while (a <=1)
    {
        cout << "How many numbers do you wish to enter? (if 0 then the program will quit)\n";
        cin >> a;
        while (b < a)
        {
            int resizeV;
            cout << "\n\nPlease enter a number: ";
            cin >> resizeV;
            numbers.resize(resizeV);
            cout <<"\nSize of numbers is: "<< numbers.size();
            b++;
        }

        while (numbers.at(n) < numbers.size())
        {
            //puts data into the vector where n points. 
            cout << "\n\nPlease enter a number to put into the list.";
            cin >> numbers.at(n);

            n++;
        }

        cout << "\n\nThese are the sorted numbers: ";
        
        sort (sortVect.begin(), sortVect.end(), mySort);
        for (it=sortVect.begin(); it!=sortVect.end(); ++it)
        {
            cout << " " << *it;
        }
        
        cout << "\n\nThese are the numbers without duplicates: ";
        for (n=0; n < (int)numbers.size(); n++)
        {    
            cout << "Element " << n << ": " << numbers.at(n);
            if (numbers.at(n) != numbers.at(n-1))
            {
            cout << numbers.at(n);
            }
        }
        
        


        //cout << numbers[n];

        
    
        a = 3; //quit entry.
    }

}
```

---

### Post by SemiBuz on 2010-02-15
[This]("http://bytes.com/topic/c/answers/637476-how-do-i-use-std-out_of_range") might be what you are looking for ( in other words, vector is *running out of bounds* and you need to find where and why ).

---

### Post by Ravenshade on 2010-02-15
Would some one please tell me how I'm supposed to use this? I've wrapped the try code around every part of my program but still nothing.

---

### Post by dwhitney67 on 2010-02-15
> **Ravenshade said:**
> Would some one please tell me how I'm supposed to use this? I've wrapped the try code around every part of my program but still nothing.

:lolflag:

---

### Post by Queue29 on 2010-02-15
```
for (n=0; n < (int)numbers.size(); n++)
        {    
            cout << "Element " << n << ": " << numbers.at(n);
            if (numbers.at(n) != numbers.at(n-1))
            {
            cout << numbers.at(n);
            }
        }
```

I'm not going to bother doing this for you, but if n=0, then n-1 is -1, which is not in bounds of a vector ( 0<= i <=numelements-1)

---

### Post by Ravenshade on 2010-02-15
Well doesn't that contradict everything I've learned about C++ so far *shrug*  Ah well, I'll have to figure another way around that problem. 

Sorry for the stupidity.

---

### Post by unknownPoster on 2010-02-16
> **Ravenshade said:**
> Well doesn't that contradict everything I've learned about C++ so far *shrug*  Ah well, I'll have to figure another way around that problem. 


I don't see how that contradicts anything at all.

Have you ever seen a legitimate negative street address? It's the same time of logic.

---

### Post by MadCow108 on 2010-02-16
negative addresses are common in higher level languages like python. But they map from the end of the array instead of the start
STL vectors do not provide this feature (but I you could add it in your own container)

---

