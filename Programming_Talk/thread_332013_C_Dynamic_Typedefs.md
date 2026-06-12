---
title: "C: Dynamic Typedefs"
date: 2007-01-05
forum: Programming Talk
---

### Post by Verminox on 2007-01-05
If the "typedef" keyword is not a pre-processor command, and is compiled into the program, then why can't we declare a typedef at runtime?

eg. In my program suppose I use floats by default, and if I run the program with the "--double" argument, I want to be able to use doubles throughout. I thought of putting a "typedef float scalar" or "typedef double scalar" statement, but I can't make a choice at runtime.


How would I go about changing the type used at runtime?

The only way I can think of it is make a "CNumber" base class, and two derived classes "CFloat" and "CDouble" each holding a single number, and using the "new" operator to create a dynamic data pointer to either CFloat or CDouble, but that's too much work....

---

### Post by raevin on 2007-01-05
> **Verminox said:**
> If the "typedef" keyword is not a pre-processor command, and is compiled into the program, then why can't we declare a typedef at runtime?

eg. In my program suppose I use floats by default, and if I run the program with the "--double" argument, I want to be able to use doubles throughout. I thought of putting a "typedef float scalar" or "typedef double scalar" statement, but I can't make a choice at runtime.


How would I go about changing the type used at runtime?

The only way I can think of it is make a "CNumber" base class, and two derived classes "CFloat" and "CDouble" each holding a single number, and using the "new" operator to create a dynamic data pointer to either CFloat or CDouble, but that's too much work....

I don't know if this would really be feasible.

The only way I can really think of is to do a typecast:

```

int var = (argv[1]*)variable_to_change;

```

But...yeah...

---

### Post by Verminox on 2007-01-05
Nah, you still have "int" var.

Also it's not like I want to use it for oen statement, I want to be able to use a type (which I have called "scalar") throughout the program. Currently it is typedef'd as float, but I want to be able to use double if the user wishes at runtime.

---

### Post by raevin on 2007-01-05
> **Verminox said:**
> Nah, you still have "int" var.

Also it's not like I want to use it for oen statement, I want to be able to use a type (which I have called "scalar") throughout the program. Currently it is typedef'd as float, but I want to be able to use double if the user wishes at runtime.

I was just giving an example :)

Typecasting is your only real way of doing so, but even at that...the example I gave wouldn't really work since argv is a char, and it's dang near impossible to convert between a char and an integer without there being conflicts with memory at the least, which would then lead to a whole plethora of problems.

---

### Post by Verminox on 2007-01-05
Well if I use your way I can just use if() statements to check the args and cast accordingly, but then I'd just be casting the variable to something else then.... I can't use that type throughout the program, like in functions, etc. unless I have a hundred thousand type casts all over the place.

---

### Post by raevin on 2007-01-05
> **Verminox said:**
> Well if I use your way I can just use if() statements to check the args and cast accordingly, but then I'd just be casting the variable to something else then.... I can't use that type throughout the program, like in functions, etc. unless I have a hundred thousand type casts all over the place.

Not necissarily...

You might be able to do something like this at the top of a global header file or something:

```

float var = (argv[1] == "double") ? (double*)var : var;

```

---

### Post by Verminox on 2007-01-05
You see you again have "float var" at the left, so the variable gets stored as float anyway, You can't change the type of the variable itself, for use in calculations.

Hence polymorphism was the only way I thought it could work.

---

### Post by hod139 on 2007-01-05
C++ is statically typed, the compiler has to know the types of all variables at compile time.  Without giving this problem much thought, you can try using unions to allocate space for the possible types, and at runtime select the desired type.

---

### Post by raevin on 2007-01-05
> **Verminox said:**
> You see you again have "float var" at the left, so the variable gets stored as float anyway, You can't change the type of the variable itself, for use in calculations.

Hence polymorphism was the only way I thought it could work.

It will get stored as a float by default...but the way the code is, it will do this:

1.  Initialize var as float first
2.  Check if argv[1] does equal "double"
2a)  If so, convert var from "float" to "double"
2b)  If not, it won't do anything

You can't create a variable without a type, and float can easily convert between int and double (as far as I know).

I don't know if I'm still oblivious to what you are getting at, but...yeah...

---

### Post by Verminox on 2007-01-05
raevin: You are right, but after conversion to dobule it will convert back to float when being saved in the variable, because float has only a limited size which is smaller than double, and therefore the double precision will be lost as soon as you have it in "var" and move on to the next statement.

hod139: I'll give unions a try thanks.

---

### Post by raevin on 2007-01-05
> **Verminox said:**
> raevin: You are right, but after conversion to dobule it will convert back to float when being saved in the variable, because float has only a limited size which is smaller than double, and therefore the double precision will be lost as soon as you have it in "var" and move on to the next statement.

I know...but, whenever you convert from one type to another you're always going to lose a certain amount of data...

---

### Post by olejorgen on 2007-01-05
uh.. why do you want this? If you're using uninons you wont save any memory

---

### Post by Jessehk on 2007-01-05
Would I be far off in guessing that this what you're trying to do?

```

typedef T int; /* or float, or double, or char, depending on compile arguments? */

typedef struct list {
    T data;
    list *next;
} list;

```

?

In that case, you're going to want to use void *pointers. It's ugly; I know. If you want it easier, use templates in C++.

---

### Post by hod139 on 2007-01-05
My understanding of what Verminox wants to do it this:

```

TYPE variable; // can be either float or double depending on **run-time** args

```

Then when running the code
```

./a.out double

```

and all instances of TYPE will become double.  The trouble is that at compile time C++ needs to know all the types (at least the size) and it cannot make this replacement. 

I think the best question asked so far though was by olejorgen, and I'll also ask it, What are you trying to do?  Maybe generics will be your best solution, or something with unions.  As pointed out unions won't save you any memory, but it will allow you to use multiple data type representation.

---

### Post by slavik on 2007-01-06
> **Verminox said:**
> If the "typedef" keyword is not a pre-processor command, and is compiled into the program, then why can't we declare a typedef at runtime?

eg. In my program suppose I use floats by default, and if I run the program with the "--double" argument, I want to be able to use doubles throughout. I thought of putting a "typedef float scalar" or "typedef double scalar" statement, but I can't make a choice at runtime.


How would I go about changing the type used at runtime?

The only way I can think of it is make a "CNumber" base class, and two derived classes "CFloat" and "CDouble" each holding a single number, and using the "new" operator to create a dynamic data pointer to either CFloat or CDouble, but that's too much work....
there are 3 stages from C code to compiled binary:
1. Preprocessor (called 'cpp', this is what the first compiler for C++ was, a C++ to C translator).
2. Compilation (this is where the typedef is actually interpreted by the compiler, that's why you can't have it dynamic)
3. Linking (that call to the OpenGL function, where is it? this is when it gets put into your code or left alone if you want to link at run time).

---

### Post by Klipt on 2007-01-06
You can do it in C++ if you use templates. Write your whole program in a template, and then write a wrapper main function calls a float version, or a double version of the program depending on options. The compiler will generate statically checked versions for float, double and any other type you use. E.g:

```
#include <iostream>

using std::cout;
using std::cin;
using std::endl;

template<class Num>
class program
{
	public:
		static int main()
		{
			cout << "Enter a number:\n";
			Num n;
			cin >> n;
			cout << n << "x2 = " << (2*n) << endl;

			cout << "Enter a character and press <enter> to quit.\n";
			char c;
			cin >> c;
			
			return 0;
		}
};

int main()
{
	cout << "Choose (f)loat, (d)ouble or (i)nt: ";
	char c;
	cin >> c;
	
	switch (c)
	{
		case 'f':
			return program<float>::main();
			break;
		case 'd':
			return program<double>::main();
			break;
		case 'i':
			return program<int>::main();
			break;
	}
}

```

---

### Post by Mirrorball on 2007-01-06
I'd keep it simple and just use doubles.

---

### Post by Verminox on 2007-01-06
olejorgen, hod139, Mirrorball: I used float and double as examples, but here is the real deal:

I have with me a calculator program that parses commands/expressions and evaluates it.

I have also made an arbitary precision library using C++ classes to store very large numbers with very high decimal precision.

Now, if the user wants to use the program for calclating small numbers, using the APL will be useless because it will take loads more time for calculation of easy numbers.

So I want the user to decide at runtime what datatype he wants to work with.... float/double/aribtary precision.

The problem of "Unions wont save you any memory" is not applicable, because If i store an empty object of my AP class, it wont be a problem. I just want to save calculation time by using floats or doubles for small numbers.

---

### Post by Klipt on 2007-01-06
> **Verminox said:**
> Now, if the user wants to use the program for calclating small numbers, using the APL will be useless because it will take loads more time for calculation of easy numbers.

Dynamic typing would also slow things down.

Speaking of arbitrary precision, there's a free highly optimised [library](http://www.mpfr.org/) for that which you may want to look at.

---

### Post by Verminox on 2007-01-06
There are many APLs out there, but I wanted to write my own for the heck of it. I program as a hobby any way, so just doing it for fun and to get better at it.

You wouldn't download "HelloWorld.cpp" from another site for your first tutorial would you? :p

PS: Speaking of optimization, my program is highly unoptimized using extensive OOP so no point using optimized C functions because my program is going to snail around anyway lol.

---

### Post by olejorgen on 2007-01-06
Then I'd just use templates like suggested before.

---

### Post by Verminox on 2007-01-06
Why not use polymorphism though? Other than my APL class, I can have a class say CDouble that acts just as a class holder for the "double" datatype, and make them both derive from a base "CNumber" class that defines virtual operator overloaded functions.

Then I can have something like:

```

CNumber* NewNumber(){
    if( UserHasChosenAribtraryPrecision ){
         return new CBigNum();
     } else {
          return new CDouble();
     }
}


// somewhere down the line....

CNumber* MyNumber = NewNumber();


```




Just wondering if there is anything wrong in using this instead of templates (dont point out the missing "delete" keyword, I'm aware of my memory).... if there is any obvious design flaw then I'll just use templates as suggested before.

---

### Post by slavik on 2007-01-06
I believe templates were actually there to solve the problem of dynamic datatyping.

---

### Post by Klipt on 2007-01-06
Don't think there's anything *wrong* with polymorphism, just that it's truly dynamic, while templates are resolved statically at compile time, so they're faster but less flexible. Where they do work, though, they work a lot like Python's 'duck typing'.

Then again, they say (premature optimization)^2 = all evil, so maybe you don't have to go for speed...

---

### Post by olejorgen on 2007-01-06
Well, the problem with using polymorphism is that you'll have to use pointers all the time. (And you will loose performance)

---

### Post by Wybiral on 2007-01-06
I haven't been able to read all of these post's so if this has been mentioned or if this isn't the solution you were looking for, then ignore this post.

Maybe using an ambiguous object type would help... Sometimes I use things like this for wrappers when a list of parameters has to be sent to a wrapped function, you can use a vector of ambiguous types to sent a mix of types to one function.

This only solves initializing them and not using them in arithmetic, I don't know what you are using them for, a template might be a better solution...

But, here's an example...

```

#include <string>
#include <sstream>
#include <iostream>

#define INT 0
#define FLT 1
#define STR 2

using namespace std;

string typeString[] = {"Integer","Float","String"};

class object {
	public:
		int    intValue;
		float  fltValue;
		string strValue;
		char type;
		object(){}
		void operator=(int    value){intValue = value; type = INT;}
		void operator=(float  value){fltValue = value; type = FLT;}
		void operator=(string value){strValue = value; type = STR;}
};

string asStr(object &thisObject){
	ostringstream strOut;
	switch(thisObject.type){
		case INT:	strOut << thisObject.intValue; break;
		case FLT:	strOut << thisObject.fltValue; break;
		case STR: return thisObject.strValue;    break;
	}
	return strOut.str();
}

int asInt(object &thisObject){
	switch(thisObject.type){
		case INT:	return thisObject.intValue;       break;
		case FLT:	return (int)thisObject.fltValue;  break;
		case STR: return atoi(thisObject.strValue.c_str()); break;
	}
}

float asFlt(object &thisObject){
	switch(thisObject.type){
		case INT:	return (float)thisObject.intValue; break;
		case FLT:	return thisObject.fltValue;        break;
		case STR: return atof(thisObject.strValue.c_str());  break;
	}
}

int main(){
	object myVariable;

	myVariable = 10;
	cout << asInt(myVariable) << endl;

	myVariable = 10.5f;
	cout << asFlt(myVariable) << endl;

	myVariable = "Ten point five";
	cout << asStr(myVariable) << endl;

	cout << "Variable is type: " << typeString[myVariable.type] << endl;

	myVariable = "10.7";
	cout << asFlt(myVariable)+ 3  << endl;
	cout << asInt(myVariable)+ 3  << endl;
	cout << asStr(myVariable)+'3' << endl;

	cout << "Variable is type: " << typeString[myVariable.type] << endl;
}

```

Word of caution: You have to be careful with ints and floats as the compiler will send an ambiguous warning if it doesn't know what type it is (thus the "f" after the 10.5)

This kind of class can be put in a cpp and header file and used without having to know the details... It really helps with things like python interfacing in c++ because it creates a variable that is *almost* dynamic in c++... Naturally, this takes more memory, but it works very well.

Sometimes there are easier methods with classes and templates, but this will allow you to create mixed type arrays and vectors.

BTW, here is a slightly templatized version that can act similar to the standard template library, it is a string stream that alls you to use it like cout and cin...

```

#include <string>
#include <sstream>
#include <iostream>

using namespace std;

class dynamic {
	public:
		stringstream strValue;
		dynamic(){}

		template <typename T>
		void operator=(T value){strValue.str(""); strValue << value;}

		template <typename T>
		void operator<<(T value){strValue << value;}

		template <typename T>
		void operator>>(T& value){strValue >> value;}

		string c_str(){return strValue.str();}
		int    c_int(){return atoi(strValue.str().c_str());}
		float  c_flt(){return atof(strValue.str().c_str());}
};

int main(){
	dynamic myVariable;

	myVariable = 10.7;
	cout << myVariable.c_int()+ 3  << endl;
	cout << myVariable.c_flt()+ 3  << endl;
	cout << myVariable.c_str()+'3' << endl;

	myVariable = "";
	myVariable << "1";
	myVariable << 2;
	myVariable << 3.5;
	myVariable << 6;
	myVariable << "7";
	cout << myVariable.c_str() << endl;

	myVariable = myVariable.c_flt() * 2;
	cout << myVariable.c_str() << endl;

}

```

Depending on your needs... One of these should help, I use classes like this a lot when I need mixed types, and psuedo dynamic typing in c++.

You could just use such a stream as the type, but this way allows you to add an abstract layer to it so that it looks and feels more like a dynamic type... Other overloads could be added to support mathematical functions and further it's usability, but this should offer an ok base...

---

