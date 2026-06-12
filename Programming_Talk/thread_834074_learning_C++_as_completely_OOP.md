---
title: "learning C++ as completely OOP"
date: 2008-06-19
forum: Programming Talk
---

### Post by Rhaddad on 2008-06-19
#include <iostream>
using namespace std;
class mainprog
{
	private : int add(int a,int b)
	{
		return a+b;	
	}

	public : int main ()
	{
		new mainprog;
		return 0;
	}

	private : mainprog()
	{	
		cout << "Hello World! " << "Please enter first number" << "\n";  
		cin >> a;
		cout << "Enter Second Number" << "\n";
		int b;
		cin >> b;
		cout << "result is: " << add(a,b);
	}//error here

}


hello, I already have programming experience with imperative type languages such as VB and Delphi. but i'm trying to learn C++ as a completely OOP language. and i get an error the error is
addition.cpp:25: error: expected unqualified-id at end of input

---

### Post by issih on 2008-06-19
There are quite a few errors with your code as it stands.

Going through it function by function:

"add" is fine, no problems.

"main" should not be declared within a class, it lives outside of class structures at global scope. you also use the new operator totally unnecessarily, and poorly. You should use "new" to assign something to a pointer, which you then must explicitly delete at a later date. Using new means you accept responsibility for the memory management of the created object.

In this case you should simply create a variable of the type you want with a declaration line like:

mainprog myProg; 

This types the variable as mainprog and gives it a name myProg. In c++ a variable is immediately instantiated using the object's constructor (you can of course pass parameters if the constructor takes any) and placed on the stack. the program will then delete that memory when the variable goes out of scope automatically. You only need use new for more advanced behaviour.

"mainprog" shouldn't be typed as private unless you are using some clever design pattern like a singleton. As it stands the constructor method is private so noone can create an instance of the class. The method also doesn't declare the variable 'a' before it is used.

Finally, class declarations must end with a ; after the final }. you should also note that declaring the functions as you are doing directly inside the class definition rather than using stubs and declaring the functions outside the actual definition is equivalent to using the 'inline' compiler hint. So that code is likely to be merely copied directly into place wherever it is referenced, rather than being maintained in a v table, its up to you to decide if thi is ok :)

Amended (untested) code is below:

```

#include <iostream>
using namespace std;
class MainProg
{
	private :
		 int add(int a,int b)
		{
			return a+b;
		}


	public :
		 MainProg()
		{
			int a;
			int b;
			cout << "Hello World! " << "Please enter first number" << "\n";
			cin >> a;
			cout << "Enter Second Number" << "\n";
			cin >> b;
			cout << "result is: " << add(a,b);
		} //error here
};

public : int main ()
{
MainProg aProgram;
return 0;
}

```

---

### Post by Rhaddad on 2008-06-19
Oh I see, so the Main method must be outside a class..aghaa!!!

that works thanks

however, i tried to further extend the classes in this little program ( i know it's very silly, but it's just to learn) but i still get errors

#include <iostream>
using namespace std;


class addition1
{
	private :int a;
	private :int b;
	
	public : int getadd(int a,int b)
	{
		return a+b;
	}
	
	public : addition1()
	{
		//this.a = a;
		//this.b = b;
	}

};



class mainprog
{

	public : mainprog()
	{	
		cout << "Hello World! " << "Please enter first number" << "\n";  
		int a;
		cin >> a;
		cout << "Enter Second Number" << "\n";
		int b;
		cin >> b;
		addition1() myadd;
		int result = myadd.getadd(a,b);
		cout << "result is: " << result;
	}

};

	int main ()
	{
		new mainprog;
		return 0;
	}

---

### Post by ilrudie on 2008-06-19
private int a;  instead of  private :int a;

the way you have the program written though those two class variables are not necessary.

Also I have not coded c++ in a very long time so I may be wrong.

---

### Post by issih on 2008-06-19
The line instantiating the addition1 class is wrong:

You just need:
```
addition1 myadd;
```

You don't add braces to the type name.

If your constructor took arguments, it would be like this:
```
addition1 myadd(arg1, arg2)
```

You are also still badly misusing "new". calling "new mainprog" in your main method creates an instance of mainprog on the heap, which you have no reference to, you therefore can't delete it, voila one memory leak.

create your mainprog as:
```
mainprog myprog
```

and it is created on the stack, and is deleted when the variable myprog goes out of scope.

If you really want to use new, the correct syntax is :
```
//to create instance of mainprog on heap and store a pointer to it
//N.B. the * indicates that pMyProg is a variable holding a //pointer to an object of type mainprog
 
mainprog * pMyProg = new mainprog();

//to delete instance once finished with it
delete pMyProg;
```

---

### Post by issih on 2008-06-19
I don't think you are 100% right ilrudie...

For java it would be:
```
private int a;
```

but in c++ you specify method access with

private:

Generally the class declaration is split into sections so that :
```

class MyClass{
private:

int privateMethod1();
bool privateMethod2();

public:

int publicMethod1();
};
```

The access modifier applies to all methods below it until another is specified, it doesn't work like java where it has to be specified on a per method basis.


You are right that the class doesn't need those fields though :)

---

### Post by Rhaddad on 2008-06-19
Thanks for all your help guys, to code Completely OOP in C++ it's alot different than java btw i know some of the attributes are useless, i'm just putting them in to learn how to program OOP in C++.

..... But i only have one problem now

this code compiles

```

#include <iostream>
using namespace std;




	
class addition1
{
	private :int a;
	private :int b;
	
	public : int getadd(int a,int b)
	{
		return a+b;
	}
	
	public : int geta()
	{
		return a;
	}
	
	public : int getb ()
	{
		return b;
	}
	
	public : addition1(int a1, int b1)
	{
		a = a1;
		b = b1;
	}

};
class mainprog
{

	public : mainprog()
	{	
		cout << "Hello World! " << "Please enter first number" << "\n";  
		int a;
		cin >> a;
		cout << "Enter Second Number" << "\n";
		int b;
		cin >> b;
		addition1 myadd (a,b);
		cout << "result is: " << myadd.getadd(a,b) << "\n";
		cout <<  "First number was " << myadd.geta() <<"\n";
		cout << "second number was " << myadd.getb() ;
	}

};

	int main ()
	{
		mainprog TheProg;
		return 0;
	}


```

and i do this by g++ addition.cpp -o addition

however i want the addition1 class on a new file(just like java in eclipse) and then compile, however this wont work. Can someone point me on how to do it?

---

### Post by ilrudie on 2008-06-19
as issih pointed out my c++ is rusty but if I recall correctly the class definitions generally go in a .h file with the same name as your .cpp.  Then to include a class from another file you need to #include something.h

of course replace something.h with the correct .h file.
this allows you to use the class defined in the something.h file in your other classes/code.

I believe the #include is called a pre-compiler instruction which actually just copies the text of the .h file right into the code before passing it to the compiler.

Linking the two compiled programs may require some extra effort which is generally why c++ projects have a makefile to automate the compiling and linking.

hope this helps until issih can post a better answer.

---

### Post by issih on 2008-06-19
I have to admit, I'm a bit lax on this bit myself...

The "correct" way to do these things is to separate all your files into a "header" and a "main". The header should contain the class definition, with all non trivial methods present merely as stubs.

The main portion then contains all the method definitions.

Any files that then use a class defined in another file include the appropriate header file.

You can then compile the whole shebang using make:

[http://www.eng.hawaii.edu/Tutor/Make/](http://www.eng.hawaii.edu/Tutor/Make/)

I admit I often cheat at this bit, because I've not used make enough to be comfortable, so I'll bow out here :)

As you are starting fresh, I recommend you learn to do things following best practice. Maybe start another thread asking about make and good practice compilation?

---

