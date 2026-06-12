---
title: "[C++] conversion constructor"
date: 2008-07-17
forum: Programming Talk
---

### Post by StOoZ on 2008-07-17
Well , I have no idea why it happens.
the header file :
> #ifndef _T_HPP
#define	_T_HPP
#include<iostream>

class T{
public :
    T(int) { std::cout<<"ctor with int called\n"; }
    T(const T&) { std::cout<<"copy ctor\n"; } 
private :
    
};


#endif	/* _T_HPP */

main source code :
> #include<iostream>
#include "T.hpp"
using namespace std;

int main(int argc , char* argv[]) {
    
    T t = 111;
 
    return 0;
}


it compiles fine, but when I move the copy constructor to the private section , then it doesnt compile, why??
it doesnt use it in any case , so I have no idea what can cause it.

---

### Post by hod139 on 2008-07-17
It's not obvious, but this line in your source file:
```

T t = 111;

```
is calling the copy constructor.  It is equivalent to writing
```

T t(aaa);

```

If you had done
```

T t;
T t2 = 100; // copy constructor call
t=t2; // assignment operator call

```

I know it's confusing, but operator= does not actually always mean the assignment operator is being used.  Think of it this way, if the program is creating a new object, it's a copy constructor call.  If the object has already been allocated, then it is an assignment.

---

### Post by StOoZ on 2008-07-18
weird , but when I run the program , the text inside the  copy ctor , is never called , only T(int) is called , so thats why im wondering , its like the copy ctor is never called , but it needs to be there :( :confused:

---

### Post by utab on 2008-07-18
[QUOTE=hod139;5407448]It's not obvious, but this line in your source file:
```

T t = 111;

```
is calling the copy constructor.  It is equivalent to writing
```

T t(aaa);

```

Are you sure on this?

If you had done
```

T t;
T t2 = 100; // copy constructor call
t=t2; // assignment operator call

```

As well on this explanation

See this output from g++, on 

   T t = 111;
   T t2 = 255;
   T t1(t);
   return 0;

out:

ctor with int called
ctor with int called
copy ctor

---

### Post by dribeas on 2008-07-18
In this code:
```

T t1( 10 );
T t2 = t1; 

```

As someone has commented before the second line is not a call to operator= but a call to the copy operator. But that is not so clear in your example, as the right side of the assignment is not a T, but an int. 

```

T t = 10;

```

Is translated into:

```

T t = T( 10 ); // Really T t( T(10) )

```

And then optimizing away the copy operator which compilers are allowed to do --which should explain why copy constructor does not seem to execute.

You should explicitly call the constructor as in
```

T t( 10 );  // Calls T( int ) explicitly

```

And, by the way, if you are not really really sure that you want implicit conversions to occur you should mark the conversion constructor as explicit:

```

class T
{
private:
   T( T const & );
public:
   explicit T( int );
};

```

Note that if conversion constructor is marked as explicit the second code snippet does not compile, as it is implicitly converting from int to T before trying the copy constructor.

David Rodríguez Ibeas

---

