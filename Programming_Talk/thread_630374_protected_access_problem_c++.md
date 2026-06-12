---
title: "protected access problem c++"
date: 2007-12-03
forum: Programming Talk
---

### Post by carl.alv on 2007-12-03
Hi all!

I have a virtual base class and two derived ones. I make an array whose type can be chosen at runtime from the derived classes. It looks like this:

```
class Base {
 protected:
   int _x;

 public:
   virtual void foo(Base**) = 0; 
}

class Derived1 : public Base {

 public:
   void foo(Base** b) {
      for(int i = 0; i < N; i++)
        cout << b[i]->_x + 1 << endl;
   }
}

class Derived2 : public Base {

 public:
   void foo(Base** b) {
      for(int i = 0; i < N; i++)
        cout << b[i]->_x - 1 << endl;
   }
}

int main(){
  int c;

  Base** b = new Base*[N];
  if(c == 0){
    for(int i = 0; i < N; i++)
      b[i] = new Derived1;
  }else{
    for(int i = 0; i < N; i++)
      b[i] = new Derived2;
  }

  return 0;
}
```

My problem is that the compiler tels me:

```
 error #453: protected member "Base::_x" is not accessible through a "Base" pointer or object
```

I'm a little confused now, since i believed that "protected" members could be accessed by the class and the derived classes members, am I wrong?

Thanks in advance for any help.

---

### Post by carl.alv on 2007-12-03
By the way, any suggestions to improve my way of choosing type at runtime are very welcome  :)

---

### Post by smartbei on 2007-12-03
In order to access the protected member, you would do:
```

this->_x

```
What you are doing is trying to access the member variable of a different instance of the base class, which is input to the foo function (No cheating!! :D).

In fact, I am not at all sure what you are trying to do...Perhaps if you give a little more detail as to your goal it would help me/others better understand why you chose to do things in this specific way. It doesn't appear that the **type** of the array is what is being changed at runtime - rather it appears the printing behavior is the difference. Perhaps this could better be done useing a paramater to a printing function:
```

   void foo(Base** b, int diff) {
      for(int i = 0; i < N; i++)
        cout << b[i]->_x + diff << endl;
   }

```
With diff changing according to your needs.

---

### Post by carl.alv on 2007-12-03
Your right, I am trying to access the _x member of a different instance of the same class, and I thought I could achieve this by using "protected", which I believed was made for cases like this. I do not actually intend to print the value of _x (I just used it for the example), in fact i make some calculations with it.

Yes, actually the type does not change, I am just using a pointer to the base class to point to the derived classes, so allowing me to choose the derived class at runtime. What I am not sure off is if this is a healthy way of doing it. I do not do downcast of the pointer because i have functions that receive the array as a parameter, and I want them to be able to receive any of the derived classes.

So any idea of how to access directly a protected member of a base class from a derived one without having to call a function like get_x() ??:confused:

Well I should also say that the reason i don't want to call a function to do this is because my program (a simulation program) has to do the calculations millions of times and i think that getting to _x through a function is slower than accessing it directly (please rectify me if i'm wrong).

---

### Post by smartbei on 2007-12-03
You're right, that removing a function call is a valid optimization (though I am not sure exactly how much of an effect this will have in your case).

Let me explain exactly what protected means. There are three possible states for a class member variable: public - anyone at all can access it, protected - only classes that inherit from it can access it, and private - only methods in the class itself can access it. What you appear to misunderstand about protected is that a derived class can only access a protected variable of the **instance it derives from**.

I guess I don't understand why you are not doing something like:
```

#include <iostream>

using namespace std;

class Base
{
protected:
	int *_x;
	int length;

public:
	void setData(int* nData, int len) { _x = nData; length = len; }
};

class Derived : public Base
{
public:
	void foo();
};

void Derived::foo()
{
	int i = 0;
	for (i = 0; i < this->length; i++)
	{
		cout << this->_x[i] << endl;
	}
}

int main()
{
	Derived d;
	const int size = 10;
	int arr[size], i;
	for (i = 0; i < size; i++)
	{
		arr[i] = i;
	}
	d.setData(arr, size);
	d.foo();
}

```
With several foo functions if you want different actions on the same data, or you could indeed have several derived classes if you want different actions on different sets of data.

Note that in this example I did not dynamically allocate the int array because it is simpler not too - you should in case you are using large arrays (and obviously if the size changes at runtime). Obviously in that case the memory needs to be released, etc.

If you need to do operations on sets of objects, you may also want to take a look at using the STL vector class.

---

### Post by carl.alv on 2007-12-03
Thank you for your answers :). 

The problem is that my foo() function can be rather complicated and large, and making a single class with all the possible foo's will end up in huge objects of which just a small part is used in a given case. 

It is true that it seems as if I am complicating the problem unnecessarily, and to certain extent I am. The reason for this is that i use to program in C, making a new program for each different simulation. This way one can make programs with rather good performance. I started to look into C++ because I wanted to see if it was possible to make more general purpose applications with a reasonable performance. Until now I can say that my C style programs are at least 15-20% faster than C++ style code, but anyway I have spent a good deal of time learning C++ by myself and I would like to see if something like a reasonable fast C++ more general code can be made ;).

---

### Post by aks44 on 2007-12-03
> **carl.alv said:**
> Until now I can say that my C style programs are at least 15-20% faster than C++ style code,
Such a difference means only one thing: you have not mastered the C++ way yet, and you are probably quite decent at C...
C++ may be a little slower than C but not to that extent. The thing is, you can't "think C" and write good C++ at the same time.



Anyway, back to your problem...
First off, please, please use std::vector instead of raw arrays. There won't be any speed nor memory tradeoff (especially if you call .reserve() beforehand), and it will be way easier to manage. FWIW almost all the STL consists of inlined templates which in the end get optimized away by the compiler.

Also, your design does not do what you expect it to. As smartbei put it, a derived class "D" can only access its base class "B" protected members through a D* pointer.

I'm not sure how to explain that behaviour... when a D::function() accesses a B::member through a D* pointer, it does so "by the inside" (D can access its own members, and B::member is part of D since it is protected). But when D::function() tries to access B::member through a B* pointer, it does so "by the outside" (ie. it can only access the public parts of B through a B*).


Now, I guess you simplified your problem in order to get an answer on that very topic, so I can't really guess what you're up to. My best bet would be: you should use composition rather than inheritance.

The whole point of inheritance being: if D **is-a** (ie. derives from) B then D must behave like if it was a B, in every aspect. You can add more behaviour, or specialize some parts, but anyway D1 and D2 should behave the same from an external POV.

What bothers me in your design is that D1::foo and D2::foo operate on a whole (heterogeneous) array of B* which can be either D1s or D2s. More info on your real problem would certainly help us to help you. ;)


Hope this was not too confusing...

---

### Post by carl.alv on 2007-12-03
Well I actually was thinking on how to use composition in my problem, but up to now i don't know. You pointed out correctly that I do not master OOP, so maybe i'll try to explain my problem as concretely as possible to see if you can help me. I am not putting code for now as I have a lot and i am not sure that someone wants to read all of it (and it must be horrible too ;) ), but if in any case you think it's worth it ill post it.

So, one has a system composed of particles that interact with each other, thel particles plan is to make a "particle" class (rather obvious ;) ), which must contain the information of the actual state of the particle (its position for example), and methods which tell the particle how should it interact with the other particles. For this last part the methods in the particle class must allow an instance to access the state information of all other instances, and some times be able to alter this information too.

Now as i was saying i am somewhat tired of writing a new program each time (even if there is a good deal of copy-paste), and I want to make something more modular (not a new idea off course). Therefore i planned to make a base virtual particle class, which has all the properties that are common to all particles, and then use polymorphism to define each particular type of particle (which contains all its particularities :p ). I also have external functions which need to use the information stored on the particles, and i don,t want to define a whole set of this functions for each particle (they would be all the same set except for the fact that they act over particle type 1 or 2), which sounds like a huge waste of.... everything; That is why i tried to use pointers to the base class to point to the different derived classes.

Well I think that is more or less the picture. Any help would be greatly appreciated :)

---

### Post by smartbei on 2007-12-04
I believe in this case a better model would bo something along the lines of:

You have a base particle class. Other particle classes inherit from it and override some (or all) of its methods. Then, you have a simulation class, which **has** a vector of all the particles in the current simulation. This simulation class has a set of methods for performing actions on the whole vector. It access the information in each particle using inline accessor methods, which should not change the performance of your program at all. Thus, each derived class can have the accessor methods overriden with their particle-type-specific code, and the Simulation class needs to know nothing of it.

Does that make sense? This is probably how I would implement what you are trying to do if I understood your goal correctly.

---

### Post by carl.alv on 2007-12-04
Well it makes sense, but i don't yet how could i define the type of vector (vector<Derived1> or vector<Derived2>) at runtime. Can i just load a vector<Base> with the derived classes?

---

### Post by aks44 on 2007-12-04
> **carl.alv said:**
> Well it makes sense, but i don't yet how could i define the type of vector (vector<Derived1> or vector<Derived2>) at runtime. Can i just load a vector<Base> with the derived classes?

You can't have a std::vector<Base> containing anything else than concrete Base instances, BUT you can have a std::vector<Base*> containing pointers to any kind of object that derives from Base.


IOW this is perfectly valid:
```
std::vector<Base*> vec;

vec.push_back(new Base()); // provided Base is not abstract
vec.push_back(new Derived1());
vec.push_back(new Derived2());

for (std::vector<Base*>::const_iterator i = vec.begin(); i != vec.end(); ++i)
  (*i)->foo(); // probably a virtual method
```


However, this WON'T even compile:
```
std::vector<Base> vec;

vec.push_back(Base()); // OK so far
vec.push_back(Derived1()); // boom
vec.push_back(Derived2()); // boom
```



Anyway, smartbei's suggestion is quite good, just make sure as (s)he pointed out that your accessors are inline whenever possible so you don't get a performance penalty.

---

### Post by carl.alv on 2007-12-04
OK! that is just what i needed :), now i can get rid of those dynamic arrays. Thank you very much both of you!

---

### Post by smartbei on 2007-12-04
Glad I could help.

BTW - it's a 'he' :).

---

### Post by aks44 on 2007-12-04
> **smartbei said:**
> BTW - it's a 'he' :).

Heh, as the saying goes... "*assume makes an a** out of u and me*" so I didn't take the chance. ;)

---

### Post by smartbei on 2007-12-04
Ahhh yes. Still, another saying goes:
> 
On the internet men are men, women are men, and kids are FBI agents.

I believe the likelyhood of me being a **female** FBI agent is small enough that you could take the chance :).

---

### Post by Wybiral on 2007-12-04
> **smartbei said:**
> BTW - it's a 'he' :).

*** Pulls out the blue bubble-gum cigar in celebration ***

---

### Post by carl.alv on 2007-12-05
hmmmm, well i just tested two versions of the program in which the only difference is the use of dynamic array or vector to store the objects. The DA version is 4-5%  faster than the vector version :(, I know this does not mean much for some office application but when the calculations take millions of iterations this difference becomes two or three days more of calculation (i am not exaggerating), so i guess ill have to stick to dynamic arrays for the moment :( unless there is some other vector-like class with perhaps less modification capabilities but with faster access.

I should add also that I use also an smaller array of a smaller class and in that case there is no significant difference in performance when I change it to a DA. That means that using vector is not bad for performance as long as you don't use large vectors of large instances.

---

