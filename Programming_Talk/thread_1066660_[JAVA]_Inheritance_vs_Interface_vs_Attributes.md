---
title: "[JAVA] Inheritance vs Interface vs Attributes"
date: 2009-02-11
forum: Programming Talk
---

### Post by ufis on 2009-02-11
I hope that this will be a fairly interesting (maybe only for newer people) discussion around OO with specific implementation in Java.

Which of the following would be the best/correct/preferred method to implement some Objects dealing with Vehicles. Please provide reasons for your choice.

1. Inheritance:
[PHP]class Vehicle {
}

    class Car extends Vehicle {
    }

        class Sedan extends Car {
        }

        class Coupe extends Car {
        }

    class Motorcycle extends Vehicle {
    }

        class Fourwheeler extends Motorcycle {
        }

    class Cart extends Vehicle {
    }

        class Gocart extends Cart {
        }[/PHP]

2. Some inheritance with Interfaces
[PHP]class Vehicle {
}[/PHP]
[PHP]interface Car {
}

interface Motorcycle {
}

interface Cart {
}[/PHP]
[PHP]class Sedan implements Car {
}

class Coupe implements Car {
}

class Fourwheeler implements Motorcycle {
}

class Gocart implements Cart {
}[/PHP]

This then also brings up a secondary question:
How far do you specialize down the inheritance tree before attributes should be used to differentiate between different Objects?
On the one hand, do you go as far as:
[PHP]class RedSedan extends Sedan {
}[/PHP]
or on the other end
[PHP]Vehicle myCar = new Vehicle();
myCar.setType(Sedan);
myCar.setColour(Red);

Vehicle myFour = new Vehicle();
myFour.setType(Fourwheeler);
myFour.setColour(Blue);
[/PHP]
or do you stop somewhere in the middle?
[PHP]Car mySedan = new Car();
mySedan.setType(Sedan);

Car myCoupe = new Car();
myCoupe.setType(Coupe);[/PHP]
Where in the inheritance hierarchy do you stop?
Vehicle?
Car/MotorCycle/Cart?
Sedan/Coupe/Fourwheeler/GoCart?
RedSedan/BlueSedan/... ?

---

### Post by CptPicard on 2009-02-11
Interesting questions, which have some interesting implications to the whole basic assumptions of OOP in general.

"Coding to interfaces" is considered a virtue... putting functionality into an inheritance hierarchy is at least to begin with to be avoided. This is because you risk creating a so called "fragile base class" ... if the semantics of base class functionality changes, you need to fix bugs all the way down to the hierarchy bottom at worst, and there is little compiler enforcement is able to do to help you. The needed refactoring can be huge.

Only use class inheritance if you have very clearly given yourself reasons why you want to use the method dispatching mechanism given to you by inheritance in *this particular* hierarchy. In Java specifically, you only have one hierarchy that is able to carry functionality per class, so you need to choose with care as to what functionality really "belongs to this type".

This is one thing C++ has on Java -- multiple inheritance *is* useful, and some more modern languages such as Ruby and D have realized this and are making use of Mixins, which are essentially interfaces with code. In Python, of course, whatever happens to be present in the object's namespace is the interface, and the class just gives a template starting point for those names.

Now.. just off the cuff, in these kinds of examples you're giving, I might make the top level types really general interfaces (such as Vehicle -- unless there is something like a registration number for each one) and write functionality in more concrete classes such as Car. It is conceivable that Motorcycle behaves sufficiently differently from Car that hacking their base Vehicle functionality together would be questionable (2 vs 4 wheels and all). Sedan can inherit Car if it is really functionally different -- otherwise the car-type could be a variable.

When it comes to attributes, the question is fairly straightforward... first, you need to ask if the concept in question is a variable that needs to be read and set. If it is, the choice is obvious. In the case of the "red sedan" the car's colour doesn't really change during its lifetime (unless you paint it), but if you can avoid adding classes to inheritance hierarchies for no good reason, you should -- so colour can be taken as an attribute of car. It can, actually be taken as an attribute of Vehicle (or, mandating getColour() in the Vehicle interface, which would probably be my preferred choice).. you always need to push these sorts of common attributes as high up in the hierarchy as you can.

There are big issues in making "colour" an inheritance issue -- type explosion is one, and the ambiguity at which level exactly you should be inheriting the colour branches. Do you have RedVehicle and YellowVehicle or do you have RedSedan and YellowSedan? You probably would want RedVehicle so you didn't have to have RedSedan and RedMotorcycle at the leaf level...

Also, using color meaningfully as class-type information in code is ugly. Generally you're dealing with a Vehicle that just came somewhere, so you'd have to use "instanceof" to resolve the type to get the colour, at which point you're essentially reading a variable. I find it hard to think of cases where you could actually use compile-time overloaded method-call resolution meaningfully on vehicle colour (or, alternatively, inside the classes, using overrides of functions instead of a variable-check).

It's a pity that esp. beginning programmers have to think about this kind of nonsense when they could be actually hacking away at interesting problems.. it holds people back from achieving things early on. I still find myself rather often knowing exactly what I want to do, but ending up with with stupid "which inheritance hierarchy does this functionality belong to" type philosophical questions whose resolution is essentially meaningful only in terms of some design-pattern esoterica.

Common Lisp of course got OOP right from the start -- type hierarchies only concern data, and runtime method-call dispatching happens based on all method arguments, not just the type of "this".

EDIT: Forgot to mention one strategy for this color-type information if you really insist on making it a type-information level thing, and want to get rid of the hierarchy problem -- marker interfaces. Just create an empty interface "Red" and tag anything that is Red with that interface. It would be of course a totally contrived solution for this, but in Java "Serializable" works exactly like this.

---

### Post by Quikee on 2009-02-11
OOP is in my opinion all about roles, responsibilities and behaviour. If you think that the sub type doesn't have any special behaviour in your "great play of objects" then if doesn't make sense it exists. In such a case making it as an attribute "discriminator" makes a more sense.

---

### Post by gmclachl on 2009-02-11
Simply put it boils down to is-a or has-a. From you example Car is a type of Vechile, Sedan is a type of Car. Red has a relationship with the car. 

George

---

### Post by CptPicard on 2009-02-11
> **gmclachl said:**
> Red has a relationship with the car. 

Or, more like the other way around "car has-a colour"... which happens to be red.

---

### Post by gmclachl on 2009-02-11
Which is what I meant

---

### Post by CptPicard on 2009-02-11
And one important design consideration to take into account is also that is-a and has-a have an interplay... when some top level class has-something, then all its children also "have" the same thing, and this is actually what, in the data view of things, makes things interchangeable... the method-dispatching stuff is then added on top of that.

---

### Post by badperson on 2009-02-11
I think I would keep Motorcycle as a subclass of Vehicle and make FourWheeler an interface

I agree with the other IS-A HAS-A thoughts.
bp

---

