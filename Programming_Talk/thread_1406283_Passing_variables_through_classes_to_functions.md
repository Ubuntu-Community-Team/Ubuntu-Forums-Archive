---
title: "Passing variables through classes to functions"
date: 2010-02-13
forum: Programming Talk
---

### Post by Enrui on 2010-02-13
**C++**

Okay as many of you may or may not know, I'm building a program involving the trading of cars and I can't find the syntax for my problem and I'm sure someone may have come across the problem before. 

A have a class called car containing a string with carModel. The function within the class returns the carModel and it's called returnCarModel()

In order to output this to main() I must write ferrari->returnCarModel();

However theres an option where the user must negotiate the price of the car and I therefore want to carry the data of a "potential->returnCarModel()" I'll figure out how to replace class data later. 

On the other hand I have this function called trade(). 

I've tried passing as parameters but I can't seem to get the right syntax or it doesn't want to grab the data. 

So in trade() if I declare

cout << potential->returnCarModel();

I get the following error. 

In function trade():
error: potential wasn't declared in this scope. 

Is there a way where I can define the class or rather "car*potential = new car{data}" in main() yet use that data in trade()? If so, could I have either a link (to the site) or a hint as to what I might be able to do?

---

### Post by Ravenshade on 2010-02-13
Hmmm 

```
trade(car::potential)
{
info here
}
```

The main problem is getting into car I guess.

---

### Post by Enrui on 2010-02-13
If I use car::potential, I get an issue variable or field 'trade' declared void.

If I use an alternative car*potential then - undefined reference to trade() in main. 

...which gives me an idea.

if I change the declared trade() in main to 

trade(car*potential) then I get 
error expected primary expression before * token

---

### Post by Some Penguin on 2010-02-13
You're not trying to declare one function inside another function, are you?

---

### Post by Enrui on 2010-02-13
No, trade() is prototyped outside of main at the top and declared at the bottom below main(). 

I'm actually trying to get the data from potential so that I can use it within trade()

---

### Post by Some Penguin on 2010-02-13
Then pass it in as an argument, and make sure you have an appropriate method.

I suggest that you pick up a copy of [http://en.wikipedia.org/wiki/The_C_Programming_Language_%28book%29](http://en.wikipedia.org/wiki/The_C_Programming_Language_%28book%29)

While that covers C and not C++, C++ builds heavily upon C and I have a rather strong suspicion that you don't know much about scopes, variable declarations, syntax and the like.

---

### Post by Enrui on 2010-02-13
I'll specify in the first post but this is a C++ project.

That's part of the problem, the arguments that I'm using aren't working and I'm not sure why. Which is why I'm asking.

---

### Post by MadCow108 on 2010-02-13
this means it does not know the expression before the *

the compiler parses the code top to bottom. It must know certain information about types and functions when it encounters them (arguments, return types etc.). This information is provided either by prototypes or the complete definition.

This basically means have the types definitions or prototypes above the usage in the file.
If the definitions are in another file, provide a header file with prototypes and include that
```

int f2(int); // prototype, tells the compiler f2 takes an int and returns int

int f1()
{
  // compiler knows what it needs to know and can create a 
  // function call (even without knowing what this function does 
  // besides taking and returning an int)
  return f2(1);
}

// but we still need a definition of the function or we get a undefined reference during linking
int f2(int a)
{
  return a*2;
}

```
For stuff where no information is needed by the compiler you can use forward declarations to tell the compiler that is defined elsewhere used for pointers to structs and classes)
```

// forward declaration
class car;
// car is never dereferenced so the compiler does not need to know what car exactly is (just that it exists)
void f3(car * c)
{
  if (car == NULL)
   exit(1);
}

// this will not compile if car is not completely defined above (because where dereferencing the pointer meaning we need to know what it points to)
void f4(car * c)
{
  car->a = 5;
}

```

---

### Post by Enrui on 2010-02-13
Thanks for the useful response Madcow, which I have taken great pleasure to read. On the other hand, I have a basic knowledge of how coding works. 

All of my code as far as I am aware are located in the relevant places. 

Prototypes and Definitions at the top. 
Main in the middle
functions at the bottom. 

Onto the code. 

I have car and I defined potential within main. The function that uses it, is at the bottom with no delete function. 

however if I put the argument

trade(car*potential)

I get... undefined reference to trade(), yet it's defined as a prototype above.

---

### Post by MadCow108 on 2010-02-13
undefined reference means there is no code (implementation) found for trade.

a prototype provides the information for the compile stage. But you still have to provide the implementation so that the linker can link the function call and the code.
The implementation may be in another file as long as that file is compiled to and the result passed to the linker (and the code has external linkage which is default)
(the linker is called automatically by gcc)

---

### Post by Ravenshade on 2010-02-13
I think enrui might be trying to say this...

void trade() //declare prototype

main()
{
trade();
}

void trade(parameters)
{
whatever trade do es
}

at least that's the vibe I'm getting.

---

### Post by matthew.ball on 2010-02-13
Wouldn't it be:

```

class Car {
  //whatever a car does
}

void trade(Car* potential) {
  //do your trading here
}

int main() {
  Car *tempCar;
  trade(tempCar);
}
```
I'm pretty sure the order of declaration is important, hence why you would usually define your classes in a header file and #include it in main() - so that it guarantees your classes are defined before main() is called.

[quote=Enrui]Prototypes and Definitions at the top. 
Main in the middle
functions at the bottom.[/quote]
I don't usually provide a function prototype because I just declare and define the functions before main, but if you want to use the quoted form, it's quite easy to translate between the two.

---

### Post by Ravenshade on 2010-02-13
Might be a better idea to get into the habit of using .h files Enrui.

---

### Post by nvteighen on 2010-02-14
Er... when prototyping, you have to state the exact signature of the function... If you have a function defined as **int myfunction(Star mystar, PlanetList the_list, void *whatever)**, you have to prototype it as **int myfunction(Star, PlanetList, void *);**... Otherwise, the compiler won't find the function.

Anyway, please, send us your code so we can follow you and help you much more easily.

---

### Post by Enrui on 2010-02-14
```

class car{
 private
string carModel;

public
car (string carModel);
~car(){}

int returnModel()
{
return (carModel)
}
};

car::car (string carMod):
carModel(carMod)
{}

void trade (car*potential); //Prototype

int main()
{
car*potential = new car ("ferrari");

trade(car*potential) //I'm having a slight problem here, where it doesn't recognize car)
}

void trade(car*potential)
{
cout << "Car is ""<< potential->returnModel()

```Putting that information into the prototype helps

but I get a 

"primary expression expected before *" this is specifically in the trade() inside main

---

### Post by MadCow108 on 2010-02-14
there is no prototype in this code.
Also you don't have to repeat the type in function calls itself.
trade(potential); is enough

I don't know if its convention. But in all programs I recall the main function is the last function in a file (mostly doing nothing else than calling another function)

doing this would save you all the trouble you currently have.

---

### Post by Enrui on 2010-02-14
My apologies put in the wrong prototype. It's correct now.

Thanks Madcow! It compiled successfully, let's check if it works ^_^

Edit

It works!! 

Thanks!

---

