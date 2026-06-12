---
title: "Help !!! about function pointer problem..."
date: 2006-10-28
forum: Programming Talk
---

### Post by beachao on 2006-10-28
Hi,
   I got a problem when I try to use a function pointer in different class.I wrote a simple code as below:

***********  funP.h ***********>>>

#include <stdio.h>
class BeCalled
{
    public:
        void Becallfun(unsigned char data);
    private:
        
};

typedef void (BeCalled::*fun_p)(unsigned char);
class Ttest1
{
    public:
        void fun_2();
        fun_p fp2; 
    private:
    
};

class Ttest
{
    public:
        Ttest1 testn;
        void fun_1(fun_p fp1);
    private:
      
};

******** funP.cc *********>>>

#include "funP.h"
void Ttest::fun_1(fun_p fp1)
{
    testn.fp2 = fp1;
    
}       
void Ttest1::fun_2()
{
    unsigned char x[10]={1,2,3,4,5,6,7,8,9,10};
    for(int i = 0; i< 10; i++)
        fp2(x[i]); //---->(1)compiler error
        //(*fp2)(x[i]);  //---->(2)compiler error      
} 

void BeCalled::Becallfun(unsigned char data)
{
    printf("Becalled!!%d\n",data);
}        

int main()
{
    Ttest test;
    Ttest1 test1;
    BeCalled SubCalled;
    //test.fun_1(SubCalled.Becallfun);
    test.fun_1(&BeCalled::Becallfun);
    test1.fun_2();
    return 1;
}

Then the problem I meet is a compiler fail at (1) pointer.
The error message is : "must use .* or ->* to call pointer-to-member function in <((Ttest1*)this)->Ttest1::fp2(...)"
If I change to (2), then the compiler error message is "invalid use of `unary *' on pointer to member".

I have no idea to solve it, please advise me some suggestions.

Thank you very much.

---

### Post by cwaldbieser on 2006-10-28
> **beachao said:**
> Hi,
   I got a problem when I try to use a function pointer in different class.I wrote a simple code as below:

```

***********  funP.h ***********>>>

#include <stdio.h>
class BeCalled
{
    public:
        void Becallfun(unsigned char data);
    private:
        
};

typedef void (BeCalled::*fun_p)(unsigned char);
class Ttest1
{
    public:
        void fun_2();
        fun_p fp2; 
    private:
    
};

class Ttest
{
    public:
        Ttest1 testn;
        void fun_1(fun_p fp1);
    private:
      
};

******** funP.cc *********>>>

#include "funP.h"
void Ttest::fun_1(fun_p fp1)
{
    testn.fp2 = fp1;
    
}       
void Ttest1::fun_2()
{
    unsigned char x[10]={1,2,3,4,5,6,7,8,9,10};
    for(int i = 0; i< 10; i++)
        fp2(x[i]); //---->(1)compiler error
        //(*fp2)(x[i]);  //---->(2)compiler error      
} 

void BeCalled::Becallfun(unsigned char data)
{
    printf("Becalled!!%d\n",data);
}        

int main()
{
    Ttest test;
    Ttest1 test1;
    BeCalled SubCalled;
    //test.fun_1(SubCalled.Becallfun);
    test.fun_1(&BeCalled::Becallfun);
    test1.fun_2();
    return 1;
}

```
Then the problem I meet is a compiler fail at (1) pointer.
The error message is : "must use .* or ->* to call pointer-to-member function in <((Ttest1*)this)->Ttest1::fp2(...)"
If I change to (2), then the compiler error message is "invalid use of `unary *' on pointer to member".

I have no idea to solve it, please advise me some suggestions.

Thank you very much.

The syntax for invoking a pointer to a member function is:
```

object.*member-function-pointer
or
object_ptr->*member-function-pointer

```

I don't see in your code where you actually have an object instance you want to point to, so you may have some other problems, but the compiler is just complaining about your syntax.

There are parts of the STL library and Boost libraries that make working with all sorts of wacky function pointers a lot easier.

---

### Post by beachao on 2006-10-28
> **cwaldbieser said:**
> The syntax for invoking a pointer to a member function is:
```

object.*member-function-pointer
or
object_ptr->*member-function-pointer

```

I don't see in your code where you actually have an object instance you want to point to, so you may have some other problems, but the compiler is just complaining about your syntax.

There are parts of the STL library and Boost libraries that make working with all sorts of wacky function pointers a lot easier.

Hi, 

Thank you for your reply.
For some reason, I need to call the BeCalled::Becallfun(unsigned char data) in Ttest1::fun_2(). Because I need to give some arguments in fun_2().
So, I typedef a fun_p function point to class BeCalled. 
I declare fp2 with fun_p type, is want to indicate the function in class BeCalled.
I use Ttest::fun_1 to transfer the function address of class BeCalled to   fp2 in class Ttest1. Finally, I want to call BeCalled::Becallfun(...) in Ttest1::fun_2().
I know the architecture is complex, but I can't simply this for some reason.        

Thank you very much.

---

