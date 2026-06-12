---
title: "declaring array in struct -function does not declare parameters"
date: 2011-03-30
forum: Programming Talk
---

### Post by kaktus9 on 2011-03-30
hello i'm writing some module for my program computing infix notation equasions
```
#include <iostream> //I/O
#include <stdexcept> //errory-gdyby trzeba by&#322;o wywo&#322;a&#263; funkcj&#281; abort();
//debug purposes only
#include <string>//te 3 dla strlen
#include <sstream>
#include <cstring> 
#include <math.h> //dla % dla liczb double bo by nie posz&#322;o as is d1%d2
int gn=0;
int go=0;
class yard{    
	public:
	
    stack<double> number;   //stos danych liczbowych
    stack<string> oper;     //stos operatorów
	///////////////////
	double inf_minus(double d1,double d2)//;
	{
	return -d1; //zwracanie liczby ze znakiem -
	}
	double inf_porownaj(double d1,double d2){
		return d2<0 ? 0 : (d2==0?1:d1*inf_porownaj(d1, d2-1)); //powownanie liczb do 0 i przez wskaznik
	}
	double inf_mno(double d1,double d2){
		return d1*d2; //mnozenie
	}
	double inf_dziel(double d1,double d2){
		if(!d2){ //jesli mianownik nie !=0
			cerr <<"0-HALT!"<<endl;
			abort();
			
		}
		return d1/d2; //jak mianownik nie 0 to normalnie dzielimy
	}
	double inf_dodaj(double d1, double d2){
		return d1+d2;
	}
    double inf_odejmij(double d1, double d2){
		return d1-d2;
	}
	double inf_modulo(double d1, double d2) 
	{
	if(!d2) {
		cerr<<"0-HALT!"<<endl;
		abort();
	}
	
	return modf(d1,&d2); //modulo specjalizowane-d1%d2 nie dziala
	}
	
	enum {none=0,left,prawa}; //typ wyliczeniowy dla kolejnosci dzialan/operatorow start od 0-nawias left- operator [lewostronny] prawa-operand dla "biegu wstecznego" [rewers znaku]
							
	struct operacje{
		char op; //operator
				 //teraz numerycznie
		double prec;
		double prd;
		double bin;
		double (*inf)(double d1, double d2);
	}
		ops[]{
			{'_', 10, prawa, 1, inf_minus},
			{'^', 9, prawa, 0, inf_porownaj},
			{'*', 8, left, 0, inf_mno},
			{'/', 8, left, 0, inf_dziel},
			{'%', 8, left, 0, inf_modulo},
			{'+', 5, left, 0, inf_dodaj},
			{'-', 5, left, 0, inf_odejmij},
			{'(', 0, none, 0, NULL},
			{')', 0, none, 0, NULL}

			
	};
	......
    
}; 

```
in line 66 i'm getting the function definition does not declare parameters error 
this bit:
```
ops[]{
			{'_', 10, prawa, 1, inf_minus},
			{'^', 9, prawa, 0, inf_porownaj},
			{'*', 8, left, 0, inf_mno},
			{'/', 8, left, 0, inf_dziel},
			{'%', 8, left, 0, inf_modulo},
			{'+', 5, left, 0, inf_dodaj},
			{'-', 5, left, 0, inf_odejmij},
			{'(', 0, none, 0, NULL},
			{')', 0, none, 0, NULL}
};

```
it was working as C and now as C++ it's not
assist please

---

### Post by dwhitney67 on 2011-03-30
> **kaktus9 said:**
> 
it was working as C and now as C++ it's not


C does not have the concept of class definitions, thus I doubt your statement is valid.

As for in C++, you cannot declare an array within a class without a size, much less initialize it within the class.

Declare the array of structs with a size, or declare it as a pointer to the struct, and later when the class is constructed, allocate the memory for it.  When the class is constructed, you can also initialize the array.

For example:
```

class Foo
{
public:
   Foo();

   struct Other
   {
      int x;
      int y;
   };

   // member data
   Other myOtherData[3];
};

Foo::Foo()
{
   myOtherData[0].x = 1;
   myOtherData[0].y = 2;

   myOtherData[1].x = 3;
   myOtherData[1].y = 4;

   myOtherData[2].x = 5;
   myOtherData[2].y = 6;
}

```

P.S.  Another thought; declare/implement a constructor for your operacje "class".  Remember, struct and class are the same, except with respect to access policies.  Data members and functions are defined as public in struct, unless otherwise indicated.  In a class, they are private, unless otherwise indicated.

---

### Post by kaktus9 on 2011-03-30
thanks for fast reply, it  has pointed me in the right direction 
[i've pasted C code into pre-generated template, overlooked that the generate class checkbox wasn't off ]
& that allowed  me to overcome the problem, and yes you were right the C version was not within the class -thus removing the 
class yard{    
	public:
and respective };
removed the problem
and i thought there is something wrong with the array-sometimes late evening coding has it's drawbacks and stupid errors are made
thanks once more 
kudos for you:)

---

