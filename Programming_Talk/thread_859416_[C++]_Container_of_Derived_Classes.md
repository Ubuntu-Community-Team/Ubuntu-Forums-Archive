---
title: "[C++] Container of Derived Classes?"
date: 2008-07-14
forum: Programming Talk
---

### Post by Dorzu on 2008-07-14
I have a question about C++. I would search for already posted questions/answers except that I do not know quite how to phrase this. I'll do my best.

I have a programming assignment involving inheritance. This is easy stuff. I get the concepts and can even write a simple program that does this. In the course of writing my project, I want to create a container(vector, list, etc.) of derived classes.

Ex: I have a base class, Vehicle, and derived classes, Bus, Car, Boat. I would like to be able to refer to a collection of Vehicles that a Person might own. If the derived classes' sole functionality is implemented from pure virtual functions found in the base class, there should be some way to collect them together, right? How do I do this? Can anyone help me?

---

### Post by CptPicard on 2008-07-14
I'm far from being a C++ god but I'd suspect you'd have to think more in terms of collection of pointers to base class (which can actually point to derived objects) because at least in STL I think you'd get issues with potentially varying "sizeof" of derived objects so calculating space needed by, say, a vector<Vehicle>, would be difficult (impossible?)

---

### Post by Dorzu on 2008-07-14
That's why I was confused. I wasn't sure how differing sizes would be handled. I'll try a collection of pointers then. Thank you very much!

---

### Post by bfhicks on 2008-07-14
I made a little example, it is a pretty standard polymorphism study of inheritance.


```

#include <iostream>
#include <vector>

using namespace std;

class Vehicle
{
public:
	Vehicle()
	{
		cout << "Vehicle created." << endl;
	}
	~Vehicle()
	{
		cout << "Vehicle destroyed." << endl;
	}
	
	virtual void print()
	{
		cout << "I'm a vehicle!" << endl;
	}
	
};

class Car : public Vehicle
{
public:
	Car()
	{
		cout << "Car created." << endl;
	}
	~Car()
	{
		cout << "Car destroyed." << endl;
	}
	
	virtual void print()
	{
		cout << "i'm a car!" << endl;
	}
};

class Boat : public Vehicle
{
public:
	Boat()
	{
		cout << "Boat created." << endl;
	}
	~Boat()
	{
		cout << "Boat destroyed." << endl;
	}
	
	void print()
	{
		cout << "i'm a boat!" << endl;
	}
};


main()
{
	Vehicle* veh = new Vehicle;
	Car* car = new Car;
	Boat* boat = new Boat;
	
	vector<Vehicle*> toys;

	toys.push_back(veh);	
	toys.push_back(car);
	toys.push_back(boat);

	for (int i=0; i < toys.size(); ++i)
	{
		toys[i]->print();	
	}

	delete veh;
	delete car;
	delete boat;
}



```

Output:
```

Vehicle created.
Vehicle created.
Car created.
Vehicle created.
Boat created.
I'm a vehicle!
i'm a car!
i'm a boat!
Vehicle destroyed.
Car destroyed.
Vehicle destroyed.
Boat destroyed.
Vehicle destroyed.


```

---

### Post by dribeas on 2008-07-15
> **Dorzu said:**
> That's why I was confused. I wasn't sure how differing sizes would be handled. I'll try a collection of pointers then. Thank you very much!

Some further study on the problem. In C++ you can get polymorphism only through references or pointers to the base class, but you cannot create containers of references, so the only option is through pointers.

```

int main()
{
   std::vector<Base*> container;
   container.push_back( new Derived1() );
   container.push_back( new Derived2() );
   //...
   for ( std::vector<Base*>::iterator it = container.begin();
      it!=container.end(); ++it )
   {
      delete *it;
   }
}

```

If you tried the following approach:
```

int main()
{
   std::vector<Base> container;
   Derived1 d1;
   Derived2 d2;
   container.push_back( d1 );
   container.push_back( d2 );
   //...
}

```

you'll end up with what is called *slicing* where the container only stores the part of d1 and d2 that is a Base object, and all other data members are removed from the object (in the case Base is instantiable, that is has no pure virtual methods) or a compile error if Base is not instantiable.

---

### Post by Dorzu on 2008-07-16
First of all, thanks to bfhicks. Your example got me started. I'm very grateful.

Dribeas: Thanks to you as well for the explanation. I've deal with inheritance in two separate C++ classes in university, but no one has ever mentioned slicing before now.

---

