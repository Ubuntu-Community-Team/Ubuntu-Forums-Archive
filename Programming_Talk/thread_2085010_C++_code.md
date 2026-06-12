---
title: "C++ code"
date: 2012-11-17
forum: Programming Talk
---

### Post by Gwaro on 2012-11-17
Hello.

I am trying to write a c++ program to compute the total, average , highest and lowest score of n students. The code below does almost all, except it gives a memory location of the highest value after sorting an array of marks instead of giving the value itself. Where have I gone wrong?

```

//Program to compute students total marks, highest score, lowest score  and the //average .
#include <iostream>
#include <algorithm>

using namespace std;

int n (0);

int main ()
{
    cout << "Enter the number of students: \n";
    cin >> n;
    int i (0), mark [n], total (0), av (0);

    for (i=0; i < n; i++ ){
    cout << "Enter marks\n";
    cin >>  mark [i];
    total += mark[i];
    }

    av = total / n; // Find an average of all the marks.

    sort (mark, mark + n);
    cout <<"Lowest: " << mark[0] << ". Highest: " << mark[n] << endl;
    cout << "Total Marks: "<< total << endl;
    cout << "Average: " << av << endl;
    return 0;
}
```

---

### Post by lisati on 2012-11-17
*Thread moved to **Programming Talk**.*

---

### Post by GeneralZod on 2012-11-17
You should print the value of mark[n-1], not mark[n].

Also, variable length arrays are not standard C++.

Also also, the average should probably be a float/ double.

---

### Post by bouncingwilf on 2012-11-17
If this is a homework project then you really need to sort it out yourself but as a clue - what is the highest allowable index No. of the array mark ( bearing in mind indices start from 0)?

Bouncingwilf

---

### Post by Gwaro on 2012-11-17
> **GeneralZod said:**
> You should print the value of mark[n-1], not mark[n].

Also, variable length arrays are not standard C++.

Also also, the average should probably be a float/ double.


That worked! I just wanted to get the idea and thanks for your help.

---

### Post by Gwaro on 2012-11-17
> **bouncingwilf said:**
> If this is a homework project then you really need to sort it out yourself but as a clue - what is the highest allowable index No. of the array mark ( bearing in mind indices start from 0)?

Bouncingwilf

n-1

---

