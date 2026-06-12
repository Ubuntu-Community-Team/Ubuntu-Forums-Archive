---
title: "Multilevel Classes (C++)"
date: 2009-07-09
forum: Programming Talk
---

### Post by shynthriir on 2009-07-09
First off, if my explanation is not sufficient let me know and I'll post a coded example.

My program has two classes (airplane and airplaneEngine). airplane has two instances of the airplaneEngine class created inside of the private section (leftEngine and rightEngine).

In the airplaneEngine class, there are 'getter' functions for the private data members in the airplaneEngine class, but I can not access these functions because the these functions are in the private section of airplaneEngine (and no, I am not allowed to simply move them to public) and airplane is not allowed to access them.

I feel there might be a way to do all this with pointers, or something completely different that I am not seeing yet. If anyone can guide me in the right direction I'd be most appreciated.

---

### Post by Zugzwang on 2009-07-09
If you have a case where you need to access private members of a class you do not have access to, then either there exist some public methods for doing indirectly what you want or there's something wrong with the overall design.

Pointers won't help you here. You might also ask the engine developer to list your airplane class as a friend, but this is normally bad design.

---

### Post by shynthriir on 2009-07-09
This is actually part of a school assignment, which is why I said in some places it had to be a particular way. I'll post some code snippets...

Disclaimer: I am NOT asking you to rewrite it all for me, just guide me to where I need to head next.

In airplane.h
```
#include <string>
#ifndef _AIRPLANE_
#define _AIRPLANE_

using namespace std;

class airplane {
private:

  string         make;
  string         model;
  airplaneEngine engineLeft;
  airplaneEngine engineRight;
  float          weight;

public:

  int setMake(string makeName);
  string getMake();

  int setModel(string modelName);
  string getModel();

  int setWeight(float weightValue);
  float getWeight();

  int setLeftEngine(string, string, int, float);
  int getLeftEngine(string); // return with pointers?

  int setRightEngine(string, string, int, float);
  int getRightEngine(string); // return with pointers?

};

#endif
```

In airplane.cpp
```
#include "airplane.h"
#include <string>

using namespace std;

///////////////
// This block contains all the setters and getters for airplane class
int airplane::setMake(string makeName) { make = makeName; }
string airplane::getMake() { return make;}

int airplane::setModel(string modelName) { model = modelName; }
string airplane::getModel() { return model; }

int airplane::setWeight(float weightValue) { weight = weightValue; }
float airplane::getWeight() { return weight;}

int airplane::setLeftEngine(string makeName, string modelName, int rpmValue,
                            float weightValue) {
  engineLeft.setMake(makeName);
  engineLeft.setModel(modelName);
  engineLeft.setRPM(rpmValue);
  engineLeft.setWeight(weightValue);
}
int airplane::getLeftEngine(string returnField) {
  if      (returnField == "make")   { return engineLeft.getMake();   }
  else if (returnField == "model")  { return engineLeft.getModel();  }
  else if (returnField == "rpm")    { return engineLeft.getRPM();    }
  else if (returnField == "weight") { return engineLeft.getWeight(); }
}

int airplane::setRightEngine(string makeName, string modelName, int rpmValue,
                            float weightValue) {
  engineRight.setMake(makeName);
  engineRight.setModel(modelName);
  engineRight.setRPM(rpmValue);
  engineRight.setWeight(weightValue);
}
int airplane::getRightEngine(string returnField) {
  if      (returnField == "make")   { return engineRight.getMake();   }
  else if (returnField == "model")  { return engineRight.getModel();  }
  else if (returnField == "rpm")    { return engineRight.getRPM();    }
  else if (returnField == "weight") { return engineRight.getWeight(); }
}
// -- end block
///////////////
```

In airplaneEngine.h
```
#include <string>
#ifndef _AIRPLANEENGINE_
#define _AIRPLANEENGINE_ 

using namespace std;

class airplaneEngine {
private:

  string make;
  string model;
  int    rpm;
  float  weight;

public:

  int setMake(string makeName);
  string getMake();

  int setModel(string modelName);
  string getModel();

  int setRPM(int rpmValue);
  int getRPM();

  int setWeight(float weightValue);
  float getWeight();

};

#endif
```

In airplaneEngine.cpp
```
#include "airplaneEngine.h"
#include <string>

using namespace std;

///////////////
// This block contains all the setters and getters for airplaneEngine class
int airplaneEngine::setMake(string makeName) { make = makeName; }
string airplaneEngine::getMake() { return make;}

int airplaneEngine::setModel(string modelName) { model = modelName; }
string airplaneEngine::getModel() { return model; }

int airplaneEngine::setRPM(int rpmValue) { rpm = rpmValue;}
int airplaneEngine::getRPM() { return rpm; }

int airplaneEngine::setWeight(float weightValue) { weight = weightValue; }
float airplaneEngine::getWeight() { return weight;}
// -- end block
///////////////
```

---

### Post by Zugzwang on 2009-07-09
I don't see your problem. The getters and setters are obviously *not* private in the engine class.

---

### Post by shynthriir on 2009-07-09
But to access the data members of airplaneEngine via an airplane object, I know how to set them, by using the setters in airplane and passing all four appropriate values, but to access them in a getter function through the airplane object is where the problem is.

The getter functions in the airplane class as they stand run different getter functions of the corresponding airplaneEngine class depending on which one you are asking it to based on the function parameter. The problem exists that each getter in airplaneEngine returns a different type (2 are stings, 1 is int, 1 is float) which means the getter function of the airplane class would return something different depending on the parameter.

Which now makes me feel like it could be fixed with a variation of overloading where you have multiple instances of the same function but with different return types, but I doubt you can do that. Can you?

---

### Post by issih on 2009-07-09
I concur with zugzwang..the engines getter and setter methods are explicitly set to be public, and should therefore be accessible from external scope.

---

### Post by shynthriir on 2009-07-09
That would imply that somewhere in my main I could so something like...


```
airplane myAirplane;
myAirplane.engineLeft.getModel();
```

But this won't work because engineLeft is private.

Edit: Perhaps my original question wasn't asking what I meant to ask, perhaps this clears it up.

---

### Post by nvteighen on 2009-07-09
Hm... I don't get what your problem is... apart from not including airplaneEngine.h at airplane.h

Let's see... your airplane class has got two private airplaneEngine instances. The getters for airplaneEngine should be public, otherwise, they'll be useless.

But, those two airplaneEngine instances are already "safe"... those are private and only stuff inside the airplane class will be able to modify those instances. Ok, the airplaneEngine **class** will be public, but not those two specific **instances**, which are which you want to save.

The issue is if you want to create a private **class** (a class that you only can use in certain modules). I'm not sure how this is done in C++, but if C++ supports forward declarations for classes (like C and C++ do for structs... it consists on just declaring that a struct exists as a valid typename, but you can't use it if you don't have access to the constructor). That, summed to the Opaque Pointer technique, could be what you need ([http://en.wikipedia.org/wiki/Opaque_pointer](http://en.wikipedia.org/wiki/Opaque_pointer))

I don't know C++, so that's what I can tell you from my general OOP knowledge... Anyway, let me tell you that privacy/publicity of members is not that important, as it's only a way to let the compiler enforce the API... If you want to break it, you'll be able to (a function pointer to the correct place is enough...). More important is to have clever developers that follow the application's design principles :)

---

### Post by shynthriir on 2009-07-09
Okay, I think I found a loophole in the assignment as a whole, which should let me bypass this problem.

Thanks for the help and ideas though. Classes are a new concept for me and while I'm enjoying learning about them, they are a big step to climb if you haven't worked with them before.

---

### Post by Zugzwang on 2009-07-09
Ah, I see what you mean. Well, in order to solve this, add getters to your airplane-class, e.g.

```

airplaneEngine& getRightEngine() {
   return leftEngine;
}

```

In C++, you rather use references than pointers whenever that makes sense.

---

### Post by CptPicard on 2009-07-09
Is there some particular reason why you are dispatching your method calls via those string parameters... it really jumps out at me as particularly nasty-looking design. Either you should just return a reference to the Engine and then call those make and model and so on things, or then perhaps have methods ... getLeftEngineMake()...

---

### Post by dwhitney67 on 2009-07-09
> **shynthriir said:**
> ...

Disclaimer: I am NOT asking you to rewrite it all for me, just guide me to where I need to head next.


I believe Zugzwang offered a solution; that is, add accessor method(s) to your airplane class that allows access to the airplaneEngine objects.

Concerning your comment above, one thing I would recommend is that you desist from wasting system resources and CPU cycles by making deep copies of the strings you pass around as parameters.

The code should look something like this when defining accessors:
```

void setAccessor(const std::string& str);
std::string getAccessor() const;

```

As for the design of the airplane, well for starters, not all airplanes have two engines.  Thus I would recommend that you conjure up a design that defines the basics of an airplane, and from there, subclass specific airplanes objects that match your needs.

Something like:
```

class Airplane
{
  ...
};

class Cessna : public Airplane
{
  ...
};

class Boeing777 : public Airplane
{
  ...
};

...

```

Another thing, in lieu of defining the set accessors for information that should never change once the airplace object is instantiated (i.e make, model, engines), define a class constructor.  Do something similar for the airplaneEngine.

And lastly, when declaring methods in the header file, provide names for the parameters, otherwise you lose the context of what the method is for.  For example:
```

// bad style
void setLeftEngine(string, string, int,float);

// better style
void setLeftEngine(const string& makeName, const string& modelName, const int rpmValue, const float weightValue);

```

Now, the code above is merely an example.  For the particular accessor shown above, I would deep-six it, and declare a constructor that takes similar parameters.

---

### Post by shynthriir on 2009-07-09
> As for the design of the airplane, well for starters, not all airplanes have two engines. Thus I would recommend that you conjure up a design that defines the basics of an airplane, and from there, subclass specific airplanes objects that match your needs.

I pointed that out to the teacher but he thought that would be too much to ask at this point. Once I get the assignment to the point that it works to the standards of the assignment, I will probably manipulate it so that is far more general purpose. I also wanted to take this assignment to play with inheritance as well -- being new with classes this is a good time to practice.

> And lastly, when declaring methods in the header file, provide names for the parameters, otherwise you lose the context of what the method is for.

I normally do, really. I was writing up the basic outline of everything in a rush between classes yesterday while I had some things fresh on my mind, figured I'd worry about cleaning up // organising the code better once I had a chance to sit down and really focus on it.

> Concerning your comment above, one thing I would recommend is that you desist from wasting system resources and CPU cycles by making deep copies of the strings you pass around as parameters.

Took me a minute to digest that, but I get what you're saying. For such a small program it really doesn't matter, though if I want to go 110% then of course. It will probably be something I'll look into once I get the assignment requirements done -- as I said before.

Thanks for the help and ideas!

And BTW: My original problem was fixed when I noticed that the assignment asked that there be a function in airplane that would display all the information about the airplane and the two engines.

---

