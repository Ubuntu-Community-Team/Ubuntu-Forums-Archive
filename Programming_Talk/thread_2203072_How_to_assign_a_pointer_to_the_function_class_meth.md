---
title: "How to assign a pointer to the function class method?"
date: 2014-02-01
forum: Programming Talk
---

### Post by cdb10 on 2014-02-01
How to assign a pointer to the function class method?
I have for example a piece of code:
```

struct struct1
{
         double (*fun1)(int*);
};


class class1
{
         private:
                  double method1(int*);
         public:
                  void mehod_main();
};


void class1::method_main()
{
         struct1 str;
         str.fun1 = &class1::method1;
}



```
This instruction is incorrect:
```
str.fun1 = &class1::method1;
```
What is the correct?

---

### Post by ofnuts on 2014-02-01
Not sure it can be done (how would you use it? there would be no object associated to it).  But why do you need to do that?

---

### Post by dwhitney67 on 2014-02-02
> **cdb10 said:**
> 
What is the correct?
Unless you plan to call a static method, as was indicated in the previous post, you will require an instance of the object to which the function belongs to before you can call it.


Here's a simple example:
```

#include <iostream>
#include <cmath>


template <typename T>
struct DoCalculation
{
	typedef double (T::*Function)(double);

	DoCalculation(T* instance, Function function)
		: theInstance(instance),
		  theFunction(function)
	{
	}

	double performCalc(double val)
	{
		return (theInstance->*theFunction)(val);
	}

	T* theInstance;
	Function theFunction;
};


struct SquareRoot
{
	double op(double val)
	{
		return std::pow(val, 0.5);
	}
};

struct Square
{
	double op(double val)
	{
		return std::pow(val, 2);
	}
};

int main()
{
	SquareRoot sqr;
	Square     sq;
	double     value = 9.0;

	DoCalculation<SquareRoot> dc1(&sqr, &SquareRoot::op);
	DoCalculation<Square>     dc2(&sq,  &Square::op);

	double squareRoot = dc1.performCalc(value);
	double square     = dc2.performCalc(value);

	std::cout << "The square root of " << value << " is: " << squareRoot << "\n"
	          << "The square of " << value << " is     : " << square
	          << std::endl;
}

```

---

