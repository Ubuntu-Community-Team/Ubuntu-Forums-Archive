---
title: "c++ invalid use of a class?"
date: 2008-04-22
forum: Programming Talk
---

### Post by chris200x9 on 2008-04-22
Hi I'm writing a class and I want to invoke the print function and I keep getting the error invalid use of a class, my code looks like this:

my cpp
```
 
#include "/home/chris200x9/Desktop/test4/Pet.h"
#include <iostream>
using namespace std;
Pet::Pet(string n, int a, int w, string t)
{
	n = name;
	a = age;
	w = weight;
	t = type;
	
	

}
Pet::~Pet(void)
{
};

 int Pet::Gain( int gain)
{
	return weight + gain;
	};
	
 int Pet::Loss( int loss)
{
	return weight - loss;
};

void Pet::Print()
{
	cout << name << endl;
	cout << age << endl;
	cout << weight << endl;
	cout << type << endl;
}
int main()
{
	Pet one;
	one.Pet.Print ("mincha",14,4,"dog");
	return 0;
}

```

and my header file looks like this:

```
 

#include <string>

using namespace std;

class Pet
{
private:
    string name;
    int age;
	int weight;
	string type;

public:
	Pet(void);
	Pet(string name, int age, int weight, string type);
	~Pet(void);
	void Print(void );
	int Gain( int gain );
	int Loss(int loss);
};

```


any help would be much appreciated :)

---

### Post by mortenkjeldgaard on 2008-04-22
There are several errors in your code. First, in the main function, you need to have:

        Pet one( string("mincha"), 14, 4, string("dog") );
        one.Print();

Next, in the constructor, you are not saving the parameters passed, you need to have:

        name = n;
        age = a;
        weight = w;
        type = t;

Finally, it is not good style to put the complete path to the .h file in the #include statement. You should just have:

#include "Pet.h"

If you need to specify a different path for Pet.h, use the -I switch when you invoke the C++ compiler.

Good luck!

---

### Post by dwhitney67 on 2008-04-22
> **mortenkjeldgaard said:**
> There are several errors in your code. First, in the main function, you need to have:

        Pet one( string("mincha"), 14, 4, string("dog") );
        one.Print();

Your reply was almost spot on, however encapsulating the string-literals in the string() constructor is not necessary.

The OP should consider declaring the constructor parameters as const, and furthermore, passing the string parameters by reference (thus preventing the deep-copying of the strings).  For example:
[PHP]
Pet(const string &name, const int age, const int weight, const string &type);[/PHP]

As for the default constructor that takes no arguments, I would get rid of the declaration, perhaps specifying the remaining constructor using the 'explicit' type.

The other error not mentioned is in the main() function.  The following statement:
[PHP]one.Pet.Print ("mincha",14,4,"dog");[/PHP]
should be
[PHP]one.Print();[/PHP]

P.S.  OP - if you decide to pass your strings by reference, the hard-coded string literals will need to be defined separately.  For example:

[PHP]const std::string name( "mincha" );
const std::petType( "dog" );
...
Pet one( name, 14, 4, petType );[/PHP]

---

