---
title: "Basic C++ pointers question."
date: 2009-01-12
forum: Programming Talk
---

### Post by aj_ on 2009-01-12
```

class Car{
    int x;
    int y;
};

int main(){
    Car* pFerrari = new Car;
    delete pFerrari;
    return 0;
}
```

Ok, I have some trouble understanding what happens here. When I create a pointer to an object on the heap, how does the default constructor handle 'Car* pFerrari = new Car;'? Does it allocate memory on the heap for all the data members, and then store the addresses in pFerrari? How would I do such a thing in my own constructor? Would a simple 'x = 0;' automatically add that value to the heap without needing the 'new' keyword, because the object itself is there? And would that memory be automatically deleted when the object goes out of scope?

What if 'y' was a pointer to an int? Would I be forced to create my own default constructor?

Hope you can understand my rambling mess :).

---

### Post by jespdj on 2009-01-12
There is nothing special that you would have to do in your constructor.

The 'new' operator allocates space on the heap for the whole object (all the member variables), and calls the constructor with the 'this' pointer pointing to the allocated space.

It then returns the address to the object on the heap, and you're storing that address in the pointer 'pFerrari'.

---

### Post by aj_ on 2009-01-12
Ah, so pFerrari only holds one address (the object's 'this' pointer)? How then does the compiler know where each of the member variables are? Does it just count up from pFerrari, using the size of each variable?

What if I declare another variable inside a Car class method (say 'int z = 0;')? Would that also be on the heap?

Thanks :).

---

### Post by slavik on 2009-01-12
> **aj_ said:**
> Ah, so pFerrari only holds one address (the object's 'this' pointer)? How then does the compiler know where each of the member variables are? Does it just count up from pFerrari, using the size of each variable?

What if I declare another variable inside a Car class method (say 'int z = 0;')? Would that also be on the heap?

Thanks :).
you are correct

---

### Post by leg on 2009-01-12
> **aj_ said:**
> Ah, so pFerrari only holds one address (the object's 'this' pointer)? How then does the compiler know where each of the member variables are? Does it just count up from pFerrari, using the size of each variable?

What if I declare another variable inside a Car class method (say 'int z = 0;')? Would that also be on the heap?

Thanks :).

vtable/offsets

The address held in pFerrari is the address of the start of the memory for the object. The virtual table holds the names and offsets (offset being the distance from the base address) of each of the variables and functions for it. An object inside it would just be another variable except that when you access it is an address to another object with its own vtable.

Thats how I learnt it anyway.

---

### Post by aj_ on 2009-01-12
> **slavik said:**
> you are correct

On both counts? Because I just wrote a little program to help me understand these things better, and the results seem to indicate that even if the object is on the heap, variables created in a class method will be on the stack. Here it is:

```

#include <iostream>

using namespace std;

class Person {
	public:
	Person();
	~Person();
	void PrintMethodVar()const;
	int age;
	int* pHeight;
};

Person::Person(){
	cout << "---------------------------" << endl;
	age = 5;
	pHeight = new int(100);
}

Person::~Person(){
	cout << "---------------------------" << endl;
	delete pHeight;
}

void Person::PrintMethodVar()const{
	int x = 0;
	cout << "&method_var: \t" << &x << endl;
}

int main(){
	int stack_var = 1;
	Person* pJoe = new Person;
	cout << "&stack_var: \t" << &stack_var << endl;
	cout << "pJoe: \t\t" << pJoe << endl;
	cout << "&age: \t\t" << &pJoe->age << endl; 
	cout << "pHeight: \t" << pJoe->pHeight << endl; 
	cout << "&pHeight: \t" << &(pJoe->pHeight) << endl;
	pJoe->PrintMethodVar();
	delete pJoe;
	return 0;
}
```

And the output:

```

---------------------------
&stack_var: 	0xbfa87fd8
pJoe: 		0x9ee5008
&age: 		0x9ee5008
pHeight: 	0x9ee5018
&pHeight: 	0x9ee500c
&method_var: 	0xbfa87fa4
---------------------------

```

---

### Post by quip on 2009-01-12
> **aj_ said:**
> On both counts? Because I just wrote a little program to help me understand these things better, and the results seem to indicate that even if the object is on the heap, variables created in a class method will be on the stack. Here it is:



I assume you are referring to the output of PrintMethodVar.  If so, it is not a class variable; the variable x is not declared with the rest of your class variables, it is a local variable to the method that gets created when the method runs, and destroyed when it ends.

Try declaring x along with your class variables, and then re-running the program, and seeing the output.

EDIT:  Additionally, of course, you would need to remove the const declaration from the method and its declaration, of course.

---

### Post by dribeas on 2009-01-12
> **leg said:**
> vtable/offsets

The address held in pFerrari is the address of the start of the memory for the object. The virtual table holds the names and offsets (offset being the distance from the base address) of each of the variables and functions for it. An object inside it would just be another variable except that when you access it is an address to another object with its own vtable.

Thats how I learnt it anyway.

The virtual table, more specifically, stores pointers to virtual methods. It does not store pointers to member variables or non virtual methods, and it does not store the names of the methods either. 

The reason that virtual methods are considered apart from the rest of methods and attributes is that the virtual table will be overwritten during the creation of derived objects.

```

class Base {
   virtual ~Base();
};
class Derived : public Base {
   virtual ~Derived();
};
int main(){ 
   Base* b = new Derived;
   delete b;
}

```

The construction starts by allocating enough memory for a Derived object. Then it passes the pointer to the allocated memory as 'this' to Base's constructor. There is a single virtual methods (the destructor) so the virtual table has only one element. During the call to Base's constructor, the virtual table holds a pointer to Base::~Base. After Base's constructor completes, Derived's constructor is called, but previously the vtable is updated to point in the first position to Derived::~Derived.

When you call delete on a pointer of type Base, the compiler will make a call to the method held in the vtable, which at this time is not a method of Base, but Derived destructors. That is how polymorphism is implemented. 

The compiler only needs to see Base definition to know where the vtable is and in what position of the table each virtual method pointer is stored. The call to the destructor will end at the appropriate place of the hierarchy since during construction the vtable is updated. By calling through the vtable indirection you are guaranteed to hit the most derived version of the method.

---

### Post by dribeas on 2009-01-12
> **aj_ said:**
> Because I just wrote a little program to help me understand these things better, and the results seem to indicate that even if the object is on the heap, variables created in a class method will be on the stack.

Member data will be stored in the heap, together with a pointer to the vtable. That is what is considered an object instance. All methods, whether static or not are compiled and stored only once in memory to be shared by all object instances. Variables created inside methods have the same rules as variables created inside free functions.

```

void f() {
   std::auto_ptr<int> p( new int ); // allocate in heap
   int q; // allocate in stack
}
class X {
public:
   void f() {
      std::auto_ptr<int> p( new int ); // allocate in heap
      int q; // allocate in stack
   }
private:
   int x;
};
int main()
{
   X x; // allocate in stack
   std::auto_ptr<X> p( new X ); // allocate in heap
}

```

In the code above, p will hold a pointer into heap allocated memory both in the free function f and in the member function X::f, regardless of whether the object is instantiated in the heap or in the stack. Variable q will be allocated in the stack regardless both in f and X::f regardless of whether the X instance is in the heap or in the stack. Member attribute X::x will be allocated in the stack if the instance is allocated in the stack (X x; in main method) or it will be allocated in the heap (std::auto_ptr<X> p; in main method).

I have used std::auto_ptr<> to avoid having to delete the pointers. If you don't know what it is, then you should head straight to your favorite C++ resource and read about it.

---

### Post by aj_ on 2009-01-14
Thank you all. It's crystal clear now :).

---

