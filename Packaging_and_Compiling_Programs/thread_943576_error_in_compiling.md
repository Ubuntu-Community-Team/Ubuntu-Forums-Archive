---
title: "error in compiling"
date: 2008-10-10
forum: Packaging and Compiling Programs
---

### Post by abhilashm86 on 2008-10-10
cout,cin,endl are not executing when i compile following code........#include<iostream>
int main()
{
int a[10],i,search;
cout<<"enter size of array"<<endl;
int n;
cin>>n;
cout<<"enter elements in ascending order"<<endl;
for(i=0;i<n;i++)
cin>>a[i];
int key;
cout<<"enter key element to be searched"<<endl;
cin>>key;
int low=0,high=n-1;
int bin=search(a,low,high,key);
if(bin==1)
cout<<"search sucessfull"<<endl;
else
cout<<"unsuccessfull search"<<endl;
}
int search(int a[],int low,int high,int key)
{
while(low<high)
{
int mid=(low+high)/2;
if(key==a[mid])
return 1;

else if(key<a[mid])
return search(a,low,high-1,key);
else
return search(a,low+1,high,key);
}
}


error its giving is..............
abhilash@abhilash-desktop:/bin$ sudo gcc binary.cpp
binary.cpp: In function ‘int main()’:
binary.cpp:5: error: ‘cout’ was not declared in this scope
binary.cpp:5: error: ‘endl’ was not declared in this scope
binary.cpp:7: error: ‘cin’ was not declared in this scope
binary.cpp:15: error: ‘search’ cannot be used as a function


please help

---

### Post by InfinityCircuit on 2008-10-10
Your code is impossible to debug without clear spacing and indentation.  Please either host the text file somewhere or fix the indentation.  At the moment it looks odd that you don't have spaces between your function operators.

---

### Post by sokopok on 2008-10-10
cin, cout, ... live in the std namespace, so you should qualify these symbols with that namespace. You have 2 options:

1.
#include<iostream>
**using namespace std;**
int main() {
  int a[10],i,search;
  cout<<"enter size of array"<<endl;
.....

2.
#include<iostream>
int main() {
  int a[10],i,search;
  **std::**cout<<"enter size of array"<< **std::**endl;

---

### Post by WW on 2008-10-12
sokopok is correct.  Also, your program is C++, not C, so you should compile it with **g++**, not gcc.

And you should *not* need sudo to compile your program.  It looks like you are compiling your program in the /bin directory.  This is a bad idea! Why don't you work on your program in your home directory?

---

