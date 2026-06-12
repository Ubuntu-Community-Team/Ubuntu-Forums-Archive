---
title: "Some help figuring out RTTI in c++"
date: 2011-04-02
forum: Programming Talk
---

### Post by scared0o0rabbit on 2011-04-02
So first, yes this is for a school assignment.  However I'm just including the code that's pertinent to the problem I'm having, which is a compile time error with dynamic_cast.

```

#pragma once
#include <string>
#include <iostream>
#include <cstdlib>
#include <vector>

using namespace std;

class customer{
	public:
		customer(int someTime);
		customer();
		~customer();
		int getArrival();
	private:
		int arrivalTime;
};
class hamburger: public customer{
	public:
		hamburger(int startTime);
		~hamburger();
	private:
		string name;
		int timeToServe;
		int decisiveness;
};
class line{
	public:
		/**
		*void addHamburger(int currentTime)
		*Add's a hamburger to the queue.
		*@param int currentTime the current time value.
		*/
		void addHamburger(int currentTime);
		/**
		*customer getNextCustomer(int currentTime)
		*Gets the next customer in line (or the first VIP platter customer who's
		*been waiting for 10+ minutes, and returns it.
		*@param int currentTime is the current time, which is used for determining VIPs
		*who may need to come up.
		*@return returns the next customer who should goto a cashier.
		*/
		void getNextCustomer(int currentTime, customer tempCustomer);
	private:
		vector<customer*> theLine;
};

int main(){

	int nCashiers = 10; //Number of cashiers

	//Dynamically creates an array of pointers to customer objects.
	//customer** cashier = new customer*[nCashiers];

	line someLine;
	for(int i = 0; i < nCashiers; i++){
		someLine.addHamburger(i);
	}

	customer* cashier = new customer;

	someLine.getNextCustomer(1,*cashier);  //Pops the first item off the line into the customer object pointed to by cashier

	hamburger* ph = dynamic_cast<hamburger*>(cashier); //This will fail if it's not a hamburger.
	if(ph != NULL){ //This will fail if it's not a hamburger.
		cout << "Hamburger customer moving up to cashier.\n";
	}

	return 0;
}


customer::customer(int someTime){arrivalTime = someTime;}
customer::customer(){arrivalTime = 0;}
customer::~customer(){}
int customer::getArrival(){return arrivalTime;}
hamburger::hamburger(int startTime):customer(startTime){

}
hamburger::~hamburger(){}
void line::addHamburger(int currentTime){
	theLine.push_back(new hamburger(currentTime));
}
void line::getNextCustomer(int currentTime, customer tempCustomer){
	tempCustomer = *theLine[0];
	theLine.erase(theLine.begin());
}

```

the error I'm getting is telling me that the class isn't polymorphic, but I feel like I'm totally lost here as to what that means.  Am I not setting one of my classes up right, am I using dynamic cast wrong?

Essentially what I've got is an array of pointers to customer type objects, and I'm wanting to stick various objects in the array that inherit from the customer class, and then check to see what they are.

Any help would be greatly appreciated.

---

### Post by MadCow108 on 2011-04-02
dynamic cast only makes sense when the pointer can mimic several classes with a common interface, aka polymorphic.
you need to mark at least one function of the base class virtual to make it polymorphic.

All functions being overridden in the child class must be marked virtual in the parent class or else they will not be called when you use a pointer of the base type.
to the very least a class intended to be polymorphic must have a virtual destructor.
```
virtual ~customer();
```

[http://www.cplusplus.com/doc/tutorial/polymorphism/](http://www.cplusplus.com/doc/tutorial/polymorphism/)

---

