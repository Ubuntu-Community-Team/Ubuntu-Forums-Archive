---
title: "Simple &amp; Weird Question About C++!?"
date: 2008-09-27
forum: Programming Talk
---

### Post by f.ben.isaac@gmail.com on 2008-09-27
```
template <class genericData>
void Calc(genericData a, genericData b, const char sign)
{
cout<<"Result is: "<< a sign b <<endl;
}
```

Assume genericData is an int.
sign carries one of the operators - + / * %.

I want a and b, be calculated generically. I do not want to use switch, nor if elses. if a = 7, b = 2, and sign = '+' ...
I want a sign b, produces 9 ...
The above code does not work...
It only works when i set it as

cout<<"Result is: "<< a <<sign<< b <<endl;

Result appear as 7+2 ... No calculation performed...

Any help would be appreciated ...

---

### Post by Lux Perpetua on 2008-09-27
> **f.ben.isaac@gmail.com said:**
> ```
template <class genericData>
void Calc(genericData a, genericData b, const char sign)
{
cout<<"Result is: "<< a sign b <<endl;
}
```

Assume genericData is an int.
sign carries one of the operators - + / * %.

I want a and b, be calculated generically. I do not want to use switch, nor if elses. if a = 7, b = 2, and sign = '+' ...
I want a sign b, produces 9 ...
The above code does not work...
It only works when i set it as

cout<<"Result is: "<< a <<sign<< b <<endl;

Result appear as 7+2 ... No calculation performed...

Any help would be appreciated ... C++ and compiled languages in general don't allow programs to modify their source code, which is effectively what you're trying to do. If you insist on this behavior, try an interpreted language like python with an "eval" function. 

In C++, you will not escape having to parse your input and choose the operator appropriately. If your valid input consists of the characters '+', '-', '*', and '/', then you will need either a table of function pointers or code that explicitly checks the value of the input and chooses a function appropriately.

---

### Post by John164918a on 2008-09-27
You could make it look a bit like it was doing that by encasing a switch statement inside a function called 

```
operation (genericData a, genericData b, const char sign)

```

I say that because when compiled the program will have to take a decision as to what operation will be performed based on the character. But then I suppose the whole point of your function is to not have to do that. I'm pretty sure you would have to have a switch somehere.

Theres an operator that has 3 inputs but I dont think you can redefine it, only overload it.

---

### Post by dribeas on 2008-09-27
C++ is a compiled language and you are trying to get results based on runtime values (your 'char sign'). You can change your code into a different design, with switch statements, or function pointers / functors instead of the 'char' parameter.

```

template <typename T>
void calc( T a, T b, std::binary_function<T,T,T> const & op )
{
   std::cout << op( a, b ) << std::endl;
}

void caller()
{
   int a = 10, b = 11;
   calc( a, b, std::plus<int>() ); // prints 21

   int ad = 11.0, bd=1.0;
   calc( a, b, std::minus<int>() ); // prints 10
}

```

---

### Post by f.ben.isaac@gmail.com on 2008-09-27
THANKS for CLARIFICATION! Now i Know

---

