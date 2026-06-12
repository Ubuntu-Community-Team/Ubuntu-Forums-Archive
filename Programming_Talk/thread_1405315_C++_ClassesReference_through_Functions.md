---
title: "C++ Classes/Reference through Functions"
date: 2010-02-12
forum: Programming Talk
---

### Post by Enrui on 2010-02-12
Excuse me, I'm having problems with my code. 


```

void buyNewCar()

class cars
{
private:

string carModel;
unsigned int topSpeed, acceleration;
unsigned int price;

public:
cars (string, usigned int ts, usigned int acc, usigned int pri);
~cars();

string modelOfcar()
{
return (carModel)
}

.... *and so on*

}

cars::cars (string car, int ts, int acc, int pri)
{
carModel = car;
topSpeed =  ts;
acceleration = acc;
price = pri;

}

*add the destructor*

int main(){

cars alpha ("ford", 85, 75, 1500);

cars new ("opel", 90, 60, 2000);

buyNewCar()

}

void buyNewCar(){

cout << "Entering a sales negotiation for a " << new.returnCarModel();

while (*price >= 13000){

cout << "negotiation";

}


```This doesn't work due to beta not being declared as a possible car earlier. I could declare it as a class member, but that seems kinda pointless when I want the data to be declared in main.

I'm also a little stumped with that while function towards the end but that's something I'm working out on my own


Edit 

I've tried to declare it after the class, that failed.

---

### Post by dribeas on 2010-02-12
What is it that you are trying to achieve?

In general terms, you can get rid of all the pointers in the class. 

About the buyNewCar(), what is beta meant to represent, what do you want to use it for? What is the buyNewCar() function meant to do?

---

### Post by Enrui on 2010-02-12
If I remove the pointers the class goes bust 

The buyNewCar() is supposed to enact the transaction every time a buying in transaction is made. 

So the program itself would be the dealer. 

Someone would try to sell a car to the dealer and therefore the buyNewCar would run, which would return the model of this new car which we do not know before the user/the person who is selling the car enters the details. 

That's why it's retrieved from main.

However, the new car needs to be able to change.

beta represents another car, perhaps any other car.

---

### Post by MadCow108 on 2010-02-12
remove the pointers, if it "goes bust" -> fix it.
All these dynamic memory allocations are completely pointless and make the whole thing very fragile and hard to maintain.

I do not quite get what your problem is.
But your design seems a little strange.

Cars and different types of cars is actually a prime example for polymorphism. You should consider it in your design.

---

### Post by Enrui on 2010-02-12
Numerous sources I have found contradict your statement Madcow and the sources I have tell me that this way is better than other methods. As a beginner in C++ I'm afraid I cannot support that statement with personal experience. 

My problem is precisely this:

If I declare a class member inside main() called 'newCar' and from within main summon buyNewCar() (for example newCar(fiesta)

then buyNewCar() should get the details of that class member, for instance, the name of the newCar which is fiesta. Specifically...

classname.nameOfnewCar ... 

Unfortunately I can't seem to do that.

---

### Post by MadCow108 on 2010-02-12
whatever these sources are, they are either wrong or you misunderstood them
your classes will be very hard to handle because they need explicit deletion of all these allocations.
Your program will fatally break on the slightest mistake. You have to check for null pointers and aliasing when dealing with pointers.
Archiving exception safety is basically impossible.
You fragment the memory with lots of small sized allocations (standard allocator is optimized for bigger chunks)
You also lose a little performance through unnecessary indirection and bad locality of reference.

Good (higher level) C++ shines through the lack of raw pointers. C++ is _not_ C
Your simple case is especially easy: just skip the * and the new's and your fine

You could solve your problem by passing a reference of the to-buy car as an argument to your buycar function
```

//
void Dealer::buycar(car & buyee) {
buyee.owner = this;
}

```

---

### Post by mdurham on 2010-02-12
This is a classic case of : "You can lead a horse to water, but you can't make him drink."

Enrui, why don't you take the advice of people who take the time and trouble to try and help you, and that know more about the subject than you? If you don't want advice, why ask a question in this forum?

---

### Post by dwhitney67 on 2010-02-12
I'm wasting a bean here... I Enrui related to RavenWood?

---

### Post by mdurham on 2010-02-12
> **dwhitney67 said:**
> I'm wasting a bean here... I Enrui related to RavenWood?

derived from the same base class perhaps!

---

### Post by nvteighen on 2010-02-13
By the way, there's another important mistake in this code. You can't use 'new' as an identifier (cars new ("opel", 90, 60, 2000);) it's a reserved word... Also, you aren't passing anything to buyNewCar(), so that function won't know about that 'new' car either... And also, you missed some semicola...

About design, I'd suggest you to read more about OOP too.

---

### Post by Enrui on 2010-02-13
If I'm wrong, then would someone please check the tutorials on 

[http://cplusplus.com/doc/tutorial/classes/](http://cplusplus.com/doc/tutorial/classes/)

It contradicts you. 

My apologies about the mistakes I shall correct them immediately. 

Madcow, I know that I am coding to be more precise than most, that is just me. If I make a mistake, wouldn't it be logical not to program with code that you know what it is going to do, or is it logical to program with code that works not how you want it to work (yet it still works). 

I also do have a destructor to delete all of those allocations. I'll try that solution.

Also, what is this OOP, this is the first time I have come across it.

---

### Post by dwhitney67 on 2010-02-13
Do you think you could rewrite your cars class to look like the following?
```

#include <string>

class Car
{
public:
   Car(const std::string& name, const unsigned int ts, const unsigned int acc, const unsigned int pr);

   ~Car() {}

   std::string getCarModel() const
   {
      return carModel;
   }

   // and so on...

private:
   std::string  carModel;
   unsigned int topSpeed;
   unsigned int acceleration;
   unsigned int salePrice;
};

// implement constructor
Car::Car(const std::string& name, const unsigned int ts, const unsigned int acc, const unsigned int price)
   : carModel(name),
     topSpeed(ts),
     acceleration(acc),
     salePrice(price)
{
   // above, member data was initialized.
   // otherwise, nothing more to do here.
}

```
As you will notice, I do not have a fetish with using 'new' at every possible moment.  In your application, if there is a need to use 'new', then it would possibly be for allocating an *entire* 'car' object.  For example, this would not be unreasonable:
```

int main(void)
{
   Car* sportsCar = new Car("Ferrari", 280, 200, 275000);

   ...

   delete sportsCar;
}

```


P.S.  OOP = Object Oriented Programming.

---

### Post by TheStatsMan on 2010-02-13
In the reference you included pointers were used simply to demonstrate the use of the destructor  "The use of destructors is especially suitable when an object assigns dynamic memory during its lifetime and at the moment of being destroyed we want to release the memory that the object was allocated."  In your code they served no purpose. As others have said good C++ code only rarely (if at all) use raw pointers

---

### Post by matthew.ball on 2010-02-13
OOP is Object-Oriented Programming (or Paradigm I guess).

It's interesting that you're using classes in C++ without knowing what object-oriented programming is - you could consider classes the bread-and-butter of object-oriented programming.

Could you point out where the contradiction(s) occur? I'm not going to read that entire page, and as far as I can tell, everything in this thread has been valuable advice so far.

[http://en.wikipedia.org/wiki/Object-oriented_programming](http://en.wikipedia.org/wiki/Object-oriented_programming)
[http://home.swbell.net/mck9/cobol/ooc/paradigm.html](http://home.swbell.net/mck9/cobol/ooc/paradigm.html)
[http://www.ipipan.gda.pl/~marek/objects/TOA/oobasics/oobasics.html](http://www.ipipan.gda.pl/~marek/objects/TOA/oobasics/oobasics.html)

- Read them all, and then read them again just to make sure.

---

### Post by CptPicard on 2010-02-13
> **TheStatsMan said:**
> As others have said good C++ code only rarely (if at all) use raw pointers

And if they do, they are generally in one of the two contexts: either the pointer is used as a means to store a (changing) value to refer to an object "elsewhere" (think data structures that do not own, in resource management sense, their content objects), or otherwise, they genuinely are used to dynamically manage a piece of the heap, in which case the lifecycle problem of the pointed-to object needs to be resolved somehow. Smart pointers are a great help here to wrap the raw pointer with something more safe.

I can't really think of a use of a pointer in "good" C++ that wouldn't fall into those two categories...

---

### Post by Enrui on 2010-02-13
> **matthew.ball said:**
> OOP is Object-Oriented Programming (or Paradigm I guess).

It's interesting that you're using classes in C++ without knowing what object-oriented programming is - you could consider classes the bread-and-butter of object-oriented programming.
.

My apologies for not understanding that OOP is object orientated programming, I thought it was something else entirely.

I'm more familiar with the term Object Orientated Programming than I am with OOP.

dWhitney, I appreciate the help and that wouldn't be too much to ask.

> **dwhitney67 said:**
> 
```

int main(void)
{
   car* sportsCar = new car("Ferrari", 280, 200, 275000);

   ...

   delete sportsCar;
}

```

[COLOR=White]Do you mean // no he doesn't, he does mean car.  (Sorry for dumb moment)
{
cars* sportsCar = new cars("Ferrari....)
...

delete sportsCar

} 
[/COLOR]   


--------------

I've chosen not to make them constants because they might go under the process of repairs or get additions. I could be wrong in this assumption. 

If there's the possibility of something going into the negative numbers wouldn't it be more valid to use int instead of unsigned int?

Third post in a row, my apologies but this is no longer related to the factors in those two posts. 


actually I've solved my original problem, so I'll put this in a new thread....

---

