---
title: "C++ and Object Oriented"
date: 2010-06-06
forum: Programming Talk
---

### Post by sonyaslm83 on 2010-06-06
Hi,

I am learning programming and I am familiar with C++, but I need to brush up on Object Oriented. I was wondering if someone could maybe help me out with Object oriented using C++.

---

### Post by dwhitney67 on 2010-06-06
That's a extremely vague request.  What specifically do you require that you could not learn from a typical C++ book?

---

### Post by trent.josephsen on 2010-06-06
My advice, if you're still learning, is to (temporarily) forget about OOP and focus on learning the tools of the trade.  OOP is generally not useful for small programs (less than, oh, 500 to 1000 lines, depending on the language and lots of other things).  Learn to use loops, arrays, std::map, functions, structures, pointers, header files, and Makefiles, and write and debug several somewhat useful programs of a few hundred lines without using classes, first.  Then you will have the tools to effectively design OO programs instead of just creating classes left and right like I once did in Java.

What resources are you using to learn?

---

### Post by sonyaslm83 on 2010-06-06
I have a C++ program that I need to change into an object oriented approach.

---

### Post by dwhitney67 on 2010-06-06
> **sonyaslm83 said:**
> I have a C++ program that I need to change into an object oriented approach.

What does your program do?  Can you relate the functions (if any) to an object?  When developing OO s/w to meet requirements, look for "nouns" in the requirements, and then look for the "verbs" which represent what the "nouns" can do.

For instance, for an ATM (Automatic Teller Machine), it can read ATM cards, prompt the operator for a PIN, accept deposits, allow withdrawals, and finally provide account balance information.  The ATM itself is the object, and the actions it provides will define its methods (or functions).

Thus:
```

class ATM
{
public:
   ATM(const std::string& locationID);

   void displayMenu();

protected:
   void   readCard();
   void   promptForPIN();
   bool   verifyPIN();
   void   performWithdrawal();
   void   performDeposit();
   double getBalance();

   // etc

private:
   std::string myLocationID;
};

```
Of course, I made up the above.  There's undoubtedly a better solution, but hopefully it helps somewhat in understanding OOP.

---

### Post by nvteighen on 2010-06-06
Wait a second... if you've learned C++ without OOP, then chances are that you just learned C using a C++ compiler...

C++'s key difference with its ancestor C is that it added native OOP support to the language; yet, there are people using C-like C++ code ignoring all the stuff that, in the end, distinguishes C++ from C.

Anyway, the idea behind OOP is that you model your code focusing on "objects". You think of "things" that "do" (methods) stuff and have some attributes that identify them. That's all of it and it's a pretty intuitive way of coding that you probably started emulatings somehow without any native syntax constructs... Then, you jump into each language's implementations.

---

### Post by sonyaslm83 on 2010-06-06
I have a moving program for a moving company.   I wondering what my objects and classes might be?   Can you help me with that?

---

### Post by sonyaslm83 on 2010-06-06
> **sonyaslm83 said:**
> I have a moving program for a moving company.   I wondering what my objects and classes might be?   Can you help me with that?
   My program will allow a user to enter in the amount of miles of the move and the program will calculate the amount of gallons of diesel used and determine how much time the move took.   The program will calculate the packing time based on how long it takes to pack a certain box.  Then the user can enter in the weight of the shipment it will tell how many hours it took to complete the move.

---

### Post by Some Penguin on 2010-06-06
Sounds like a homework problem.  "Please design my solution for me" isn't a very good use of the forum.

---

### Post by Tony Flury on 2010-06-06
You have already been told what to do - ignore C++ for the moment - work out what your classes and methods are. Identify your nouns and verbs ..

---

### Post by dwhitney67 on 2010-06-06
To move something from A to B requires a vehicle of some sort.  The vehicle could be a car, a truck, or an ox-cart.  Based on the fact your **Vehicle** uses diesel, I'm going to assume it is a **Truck**.

I used bold-fonts for the words Vehicle and Truck in the paragraph above, because these stand-out as nouns/things.  To compute how much time a Vehicle takes to complete a journey from A to B typically requires additional information, such as distance and speed traveled.

Let's say the Vehicle has an attribute that represents the MPG the vehicle can travel for each gallon of diesel.  Given the distance of the journey, you should easily be able to compute the quantity of fuel required.

As for the time it took, merely knowing how long it took to pack an assortment of boxes does not, to the best of my knowledge, account for travel time of the vehicle.  It can only account for the time *prior* to the actual move.

Thus you either 1) have insufficient requirements, or 2) have neglected to post all of them.

Back to the Vehicle; in code it could appear something such as:
```

class Vehicle
{
   Vehicle(unsigned int mpg);

   virtual ~Vehicle();

   // this method will compute the ratio of distance/myMPG.
   double expectedFuelUsage(const double distance) const;

protected:
   unsigned int myMPG;
};

```

Box could be another object, which given a static time factor, could provide timing details on how long it takes to pack a box of a certain dimension.

```

class Box
{
public:
   static double PACKING_TIME_FACTOR;   // in hours?

   Box(double width, double height, double length);

   // this is easy: myWidth * myHeight * myLength
   double volume() const;

   // volume() * PACKING_TIME_FACTOR
   double estimatePackingTime() const;

private:
   double myWidth;
   double myHeight;
   double myLength;
};

```

Based on the triviality of this exercise, I will conclude that it is a school assignment, not something being developed for a fortune-500 company (ie. UPS).  Therefore I suggest you put forth an effort to complete as much of this assignment as possible on your own before asking another question.

This forum has a policy against posting homework questions.

---

