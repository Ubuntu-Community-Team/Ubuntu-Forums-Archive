---
title: "Eclipse :An Internal error occured during Launching &quot;"
date: 2010-05-06
forum: Programming Talk
---

### Post by hasanm3 on 2010-05-06
Hi,
I am very novie C++ progrmmer trying to compile a simple  programe below-

#include<iostream>
using std::cout;
using std::endl;

#include<iomanip>
using std::setw;


int main ()
{
    int a[10];

    for(int i=0; i<10; i++)
    a[i]=0;

    cout<<"Element"<<setw(13)<<"Value"<<endl;

    for(int j=0; j<10; j++)
    cout<<j<<setw(13)<<a[j]<<endl;

    return 0;    
}

I can compile this easily in GCC but everytime im trying to compile this in
eclipse i get a error message"An Internal error occured during Launching "

I tried to compile other hello.cpp they work fine.

It happens to me before as well GCC works fine and Ecilipse giving me trouble.

Any one has any idea please..i really like ecilipse IDE.

I am using ubuntu 8.04.

Thanks in advance.

---

