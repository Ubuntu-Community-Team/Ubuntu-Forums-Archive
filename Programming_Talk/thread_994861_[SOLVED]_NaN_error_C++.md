---
title: "[SOLVED] NaN error C++"
date: 2008-11-27
forum: Programming Talk
---

### Post by ashmew2 on 2008-11-27
Hi , I just finished this program (I know its below standard , but still ... :P )

> 
#include <iostream>
using namespace std;

float multi(float x,float y)
{
  float a=(x/y),b=(y/x),k=x-y;
  if (k<0)
    {
        k=y-x;
    }
  cout<<"The Difference : "<< k;
  cout<<"\nThe Sum : "<< x+y;
  cout<<"\nThe product : " <<x*y;
  cout<<"\n"<<x<<" is "<<a<<" times "<<y;
  cout<<"\n"<<y<<" is "<<b<<" times "<<x;

}

main()
{
    float a,b;
    cout <<"Enter the Value of First Number : ";
    cin>>a;
    cout<<"Enter the value of Second Number : ";
    cin>>b;
    cout<<"The numbers you entered were "<<a<<" and "<<b<<"\n";
    cout <<multi(a,b);
    return 0;
}


When i run it , it gives me :
> 
Enter the Value of First Number : 3
Enter the value of Second Number : 4
The numbers you entered were 3 and 4
The Difference : 1
The Sum : 7
The product : 12
3 is 0.75 times 4
4 is 1.33333 times 3**[B]nan**[/B]
Press ENTER to continue.




The output is as it should be , but what's with the nan ?
I am using Codeblocks:IDE for C++ and i think it's pretty slick.

Thanks! :D

---

### Post by Phenax on 2008-11-27
```
cout <<multi(a,b);
```
This should just be
```
multi(a,b);
```
Which will get rid of the NaN.

Your function returns nothing, which is NaN (Not a Number).

Your ```
float multi(float x,float y)
``` should probably be ```
void multi(float x,float y)
``` as you're printing directly from that function - it needs no return, and you don't have a return.

---

### Post by dwhitney67 on 2008-11-27
You probably would not have needed the assistance of the Ubuntu Programming forum to resolve this issue if you have compiled your program with the **-Wall** gcc option.

This would have told you that your multi() function has been defined to return a float value, but that none is being returned.  It also would have told you (first) that ISO C++ does not allow the declaration of the main() function with no return type.

---

### Post by monkeyking on 2008-11-27
> **dwhitney67 said:**
> You probably would not have needed the assistance of the Ubuntu Programming forum to resolve this issue if you have compiled your program with the **-Wall** gcc option.


I would also recommend -ansi -pedantic if you need to write portable code

---

### Post by ashmew2 on 2008-11-27
Thanks for the help everyone and ill be sure to add the -Wall option..

Thanks!

---

