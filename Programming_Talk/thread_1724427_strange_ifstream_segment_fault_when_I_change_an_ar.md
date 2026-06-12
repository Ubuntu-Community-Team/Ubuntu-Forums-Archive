---
title: "strange ifstream segment fault when I change an array size"
date: 2011-04-08
forum: Programming Talk
---

### Post by thomashsu on 2011-04-08
Hi guys,

     I've met a quite strange segment fault error while running a small program.


The code is like:

#include <fstream>
#include <iostream>

using namespace std;

// the size of buffer which is used to load the data in datain.txt file

const long TEST_DATA_SET = 5000000;

int main(){

// Eclipse shows the segment fault is on below line:
// What's weird is:  
// If I modify the TEST_DATA_SET to a smaller value, like 50000
// then everything works fine.
// This file contains 5M line of data in it, size is 
// approximately 70MBytes
//--------------------------------------------------------------
	ifstream fin("datain.txt");           
//--------------------------------------------------------------

    if(!fin)
        return -1;

    // The array to store all data in that file.  
    int testdata[TEST_DATA_SET];

    int i = 0;
    while(!cin.eof(),i < TEST_DATA_SET )
    {
        if (cin.fail())
        {
            cerr<<"illegal data";
            cin.clear();
        }
        fin >> testdata[i];
        i++;
    }; 
// ... other code


Anyone has idea on this??

Thanks a lot:D:D

---

### Post by thomashsu on 2011-04-08
CPU : Intel i5 460M
MEM : 4G
OS  : Ubuntu 10.10 x86_64
GCC : 4.4.5 (Ubuntu/Linaro 4.4.4-14ubuntu5)

---

### Post by MadCow108 on 2011-04-08
the array is too large for the stack. it is seldom larger than 8mb.
use the heap (new/delete or std::vector)
```
int * testdata = new int[TEST_DATA_SET];
...
delete [] testdata;
// or
#include <vector>
std::vector<int> testdata(TEST_DATA_SET, 0);
```

your while loop condition is also not correct, use the and operator &&

---

### Post by thomashsu on 2011-04-08
Cool! 

Thanks MadCow108~~ :popcorn:

---

### Post by cgroza on 2011-04-08
You really have to use a standard container for this kind of job.

---

