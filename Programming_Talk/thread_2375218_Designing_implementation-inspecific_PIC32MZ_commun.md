---
title: "Designing implementation-inspecific PIC32MZ communication classes in C++"
date: 2017-10-23
forum: Programming Talk
---

### Post by chengche on 2017-10-23
[COLOR=#242729][FONT=Verdana]  Alright everyone, that title may seem like a significant amount of technobabble, so let me explain what I'm trying to do.[/FONT][/COLOR]
[COLOR=#242729][FONT=Verdana]I'm starting to break into the PIC32family, specifically the[ PIC32MZ]("http://www.kynix.com/Parts/3596895/PIC32-HMZ144.html") series, namely because I'm starting to want to do things that I want more horsepower for than an AVR can deliver. I've been reading a bunch of tutorial docs and source on the subject, but I figured I'd bring this question here.[/FONT][/COLOR]
[COLOR=#242729][FONT=Verdana]What I'm trying to do is develop a set of classes for the communication interfaces in C++ such that they are unit-inspecific; that is, a generic class that is initialized with the number of the communication interface unit; essentially "one set of code for any number of interfaces". Let me give you an example.[/FONT][/COLOR]
[COLOR=#242729][FONT=Verdana]We know from the datasheet that the PIC32MZ family has 6 4-wire SPI modules. [This example]("https://code.google.com/p/pic32-examples/source/browse/trunk/showroom/calculator/spi.c"), while it (presumably) works, it has a number of things that I consider undesirable for my uses:[/FONT][/COLOR]

[LIST]
[*]It's in C. I want to use classes to help with my data management, so preferably I'm looking for a C++ solution. Obviously, it'd take me all of ten minutes to rewrite this code, but see the next point.
[*]It's specific to SPI2. This means I'd need an individual class for each of the six SPI units, even if I only need one or two. What I'd like to develop is a unified class for SPI, such that I can call one class and declare the unit number (1 to 6) in the constructor and have it initialize the appropriate one. Basing off the above example, the constructor would look like so:
[/LIST]
[COLOR=#242729][FONT=Verdana]SPI::SPI (uint baud, uint u_num){     // Some discrimination of what u_num is     // Setup}[/FONT][/COLOR]
[COLOR=#242729][FONT=Verdana]Things I've considered, but thrown-out/decided against/unsure if feasible or how to do:[/FONT][/COLOR]

[LIST]
[*]If/else/switch statements in each method. This is the obviously easiest of all possible routes, but also the dumbest and the most sub-optimal. Every time the method calls, it would have to evaluate which unit to assign the parameters to which is wasted time.
[*]Function pointers from Microchip functions into arrays for calls. So, SPI1-6 functions such as configure, send byte, etc. would map into an array, when the class method calls it plugs the unit number (stored in a class variable) into the array and pumps the parameters in to the function referenced by the pointer table.
[*]Macros. Using the register macros provided by Microchip somehow to my advantage, although I have no idea (not afraid to say that one) how I would use that or to my advantage. Again, the gut feeling is it'd have to be some sort of pointer table.
[*]Raw addresses. I seem to remember that the datasheet gives the addresses for the registers in the memory space, although it's hard to draw a reference to them right now on demand. I believe they were virtual addresses - my main issue with this is that I don't have a clue how to leverage virtual memory from a high-level context (I've always understood that the OS and CPU manage virtual memory to physical address mapping, but how that translates up the totem pole I have no idea of), and so I wouldn't have any idea how to make the class work. Essentially, if I could figure it out (providing this was feasible), I could figure out the association (offset) between say, SPI1 registers and SPI2 registers and make the class methods auto-apply that offset depending on the unit class variable.
[/LIST]
[COLOR=#242729][FONT=Verdana]EDIT: Found the SPI register map along with virtual addresses, apparently starting at 0xBF821000, although it's of little comfort so far.[/FONT][/COLOR]
[COLOR=#242729][FONT=Verdana]Thank you if any of you can help.
[/FONT][/COLOR]

---

### Post by spjackson on 2017-10-23
Welcome to the forums.

> **chengche said:**
> 
[LIST]
[*]It's specific to SPI2. This means I'd need an individual class for each of the six SPI units, even if I only need one or two. What I'd like to develop is a unified class for SPI, such that I can call one class and declare the unit number (1 to 6) in the constructor and have it initialize the appropriate one. Basing off the above example, the constructor would look like so: 
[/LIST]
[COLOR=#242729][FONT=Verdana]SPI::SPI (uint baud, uint u_num){     // Some discrimination of what u_num is     // Setup}[/FONT][/COLOR]
[COLOR=#242729][FONT=Verdana]Things I've considered, but thrown-out/decided against/unsure if feasible or how to do:[/FONT][/COLOR]

[LIST]
[*]If/else/switch statements in each method. This is the obviously easiest of all possible routes, but also the dumbest and the most sub-optimal. Every time the method calls, it would have to evaluate which unit to assign the parameters to which is wasted time. 
[*]Function pointers from Microchip functions into arrays for calls. So, SPI1-6 functions such as configure, send byte, etc. would map into an array, when the class method calls it plugs the unit number (stored in a class variable) into the array and pumps the parameters in to the function referenced by the pointer table. 
[/LIST]

This sounds like straight-forward polymorphism.
```

class SPI {
    SPI(uint baud);
    virtual ~SPI();
    virtual void someFunction();
    virtual void someOtherFunction();
};

class SPI1 : public SPI {
    SPI1(uint baud);
    ~SPI1();
    void someFunction();
    void someOtherFunction();
};

class SPI2 : public SPI {
    SPI2(uint baud);
    ~SPI2();
    void someFunction();
    void someOtherFunction();
};

SPI * genericObject = new SPI1(2400); /* or SPI2... or SPI6 */

genericObject->someFunction(); // Calls the right method through the vtable according to the actual type at runtime.

```
Am I missing something?

---

### Post by Rocket2DMn on 2017-10-23
Agreed that this sounds like basic polymorphism.  If you have devices that are extremely similar, they can share a common parent (possibly abstract) class.  The only thing I would add is that you could use a factory class/function that returns the appropriate implementation of your interface based on parameters like baud and u_num.  You would never have to change your client code as you add more implementations later, particularly if you can load those params dynamically from the command line, environment variables, or a config file.  Then instead of
```

SPI * genericObject = new SPI1(2400); /* or SPI2... or SPI6 */

```
you get:
```

SPI * genericObject = SPIFactory.create(baud, u_num);

```
(Maybe there's a more appropriate way to make factories in C++, but you get the idea.)

---

