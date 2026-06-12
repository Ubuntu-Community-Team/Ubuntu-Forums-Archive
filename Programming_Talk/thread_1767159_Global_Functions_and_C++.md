---
title: "Global Functions and C++"
date: 2011-05-25
forum: Programming Talk
---

### Post by pieman711 on 2011-05-25
I've been trying to get back into programming after a long ime out and wanted to go to C++ (Previous experience only of basic).
I've been using "learn C++ in 21 days" and allegro5 to try and get one of my old games working. So far I've managed to get it working to some extent and am refining the code before carrying on to add new features.
The bit I am stuck with is that I have a few global variables and have read a lot about how bad these can be, especialy as code gets more complex. 
I've got a function that creates a the level data from a class 'level' but the int variables face, spriteX, spriteY, doorX, doorY and key all need to be global so that I can then read them back in different functions later? I've tried to read about on the subject but can't quite get my head around it. Any advice or a pointer to a good tutorial about this would be great thanks.


```

 void CreateLevel(level x){

        if (MapLoad(x.getname(), TRUE)){
            fprintf(stderr,"Failed to load map :(\n");
            return FALSE;
        }

    face = 3;
    spriteX = x.getstartX();
    spriteY = x.getstartY();
    doorX = x.getdoorX();
    doorY = x.getdoorY();
    key = x.getkeys();

}

```

---

### Post by simeon87 on 2011-05-25
You should learn about classes in C++, for example, [here](http://www.cplusplus.com/doc/tutorial/classes/). You can create a Level object which contains all the information of the level, such as the variables that are now globals. You can then pass the Level object around rather than accessing global variables all the time. This will make it much easier to test your code later for errors.

---

### Post by Blackbug on 2011-05-25
Well, I do agree with post above. you should use a class or you can put all these variables within a namespace. and access these variables from that.
strict c++ counterpart for namespaces are static classes, but even namespaces are good enough and clean.
 
 
#ifndef MyNameSpace_h
#define MyNameSpace_h
 
namespace MyNameSpace
{
    int face;
    int spriteX; 
    int spriteY;
    int doorX;
    int doorY;
    int key;
 
//whatever you want to do further
// you can even overload << operator and print the members..
};
#endif
 
your code will be modified as:
 
#include "MyNameSpace.h"
 
void CreateLevel(level x){

        if (MapLoad(x.getname(), TRUE)){
            fprintf(stderr,"Failed to load map :(\n");
            return FALSE;
        }

    MyNameSpace::face = 3;
    MyNameSpace::spriteX = x.getstartX();
    MyNameSpace::spriteY = x.getstartY();
    MyNameSpace::doorX = x.getdoorX();
    MyNameSpace::doorY = x.getdoorY();
    MyNameSpace::key = x.getkeys();

---

### Post by pieman711 on 2011-05-25
I'm already using classes for the levels:
header:
```

class level
{
    public:
        level(string name, int startX, int startY, int doorX, int doorY, int keys);
        const char *getname() {return lname.c_str();}
        const int getstartX() {return lstartX;}
        const int getstartY() {return lstartY;}
        const int getdoorX() {return ldoorX;}
        const int getdoorY() {return ldoorY;}
        const int getkeys() {return lkeys;}

    private:
        string lname;
        int lstartX;
        int lstartY;
        int ldoorX;
        int ldoorY;
        int lkeys;
};

```Body:
```
level::level(string name, int startX, int startY, int doorX, int doorY, int keys){
    lname = name;
    lstartX = startX;
    lstartY = startY;
    ldoorX = doorX;
    ldoorY = doorY;
    lkeys = keys;
}

level level1("1.Fmp", 1, 1, 3, 6, 2);


```If I create the level object level level1 in a function like InitData() will that object, and all its member variables, only be avaiable in that function or can I access them (eg level1.getspriteX()) from another function?

---

### Post by Blackbug on 2011-05-25
Well, it depends on the lifetime of the object. 
You want to use the "object level1" inside "class Level" member function or outside (any other class)?
 
 
 
I am not very clear what you described
> will that object, and all its member variables, only be avaiable in that function or can I access them (eg level1.getspriteX()) from another function?
 
If you will describe a bit more it will be more understandable.
 
also, made your getter 'read-only'
const char *getname() const
{
}

---

### Post by pieman711 on 2011-05-25
My plan was to create an object of class 'level' for each of the levels (so far 1 to 8 ) so that it could keep track of the particulars of that level. If I create the 'level' level1 in main() it will be available to all the functions I assume?

If I create it inside a function like InitLevels() then when InitLevels() finishes will level1 go out of scope? so that if I call level1.getspriteX() later it sould say 'level1 was not declared in this scope'

As far as I can tell the only way to avoid this going out of scope business would be to make them level1 level2 etc global in which case I'm back where I started with global variables (only now they are objects instead of individual variables)

----Edit

How about this...
I'll have a 'level' object for each of the levels I have maps for and then call a function like:
```
level GetLevelDetails(level)
```

```

level GetLevelDetails(level levelx){ 
    level levelCurrent(levelx.getname(), levelx.getstartX(), levelx.getstartY(), levelx.getdoorX (), levelx.getdoorY(), levelx.getkeys())
    return levelCurrent;
}

```
call it with 
```
GetLevelDetails(level1)
```]that way I can pass the whole level back to the calling function and have those vairables for that level still in scope right? then later in the program I could have 
```

MapSetBlock((levelCurrent.getdoorX()),(levelCurrent.getdoorY()), 49); 

```and it will automatically set teh right doorX interger for the current level?
Sorry if this sounds like basic stuff. I'm entirely self taught and have no one I can ask this kind of thing too.

---

### Post by Blackbug on 2011-05-25
well if you will create Level level1 object inside initLevel() method certainly, after execution of initLevel() method finishes, your Level class destructor will be invoked and object will cease to exist.
 
But, why you want to initialize all levels at the same time?
If its a game then every user will reach next level after clearing the previous one. And, for that there willbe an independent algorithm.
 
Creating all level objects at same time even within initLevel() method will lead to access use of memory, which is not required, because level2 object wont be accessed until level1 is cleared up.
 
I think you should write algorithm for each level in different classes. and should put a controller class above all. This controller class will decide at runtime which object shuold be created.
 
you can also use strategy design pattern if you are following proper OOPS concept..
[http://en.wikipedia.org/wiki/Strategy_pattern](http://en.wikipedia.org/wiki/Strategy_pattern)

---

### Post by pieman711 on 2011-05-25
In the oringinal blitz basic version of the game each level was very short, maybe a matter of seconds, but there was quite a high chance of dying and startng again. It was quite arcadey. I thought loading them up at the start and having them ready to go would make the game quicker when you are flicking backwards and forwards through levels quite quickly.
I'll go and read that wiki article now and have another stab.

---

### Post by psusi on 2011-05-25
> **pieman711 said:**
> 
[/CODE]If I create the level object level level1 in a function like InitData() will that object, and all its member variables, only be avaiable in that function or can I access them (eg level1.getspriteX()) from another function?

If you define it as a local within the function, then it only exists while that function is executing, unless you define it as static.  The name is also only visible to the function, but you can pass a reference or pointer to the object to another function you call, since while the called function is executing, the calling function's locals are still on the stack.  Just make sure that the called function does not try to save that pointer anywhere it could be used later because once it returns, and the calling function returns, the object is destroyed.

Also as blackbug said; ideally you should not be defining instances 1, 2... n of the level class at compile time.  Instead create an instance at runtime with the new operator, and then delete it when you are done with that level.  Then you can do things like define the levels in a config file that you load rather than having to hard code them into the program and recompile to change the level parameters.

---

### Post by dwhitney67 on 2011-05-25
@ the OP -

This may seem like a smart-*** comment/question, but why are you developing code at this point in time?  It would seem that you have not even put together a design for your application.

In OOP, you avoid global variables by encapsulating them within a class.  Since you are developing a game, it would seem logical that at a minimum, you would have a class named "Game" (or "game") that contains the fundamental building blocks (other classes or basic data types) to support this game.

In your main() function, you would have something very minimal like:
```

int main(int argc, char** argv)
{
   Game game;
   game.init(argc, argv);
   game.run();
   return 0;
}

```

---

### Post by pieman711 on 2011-05-25
@dwhitney67:
This project is much more about learning the different aspects of C++ and how they work rather then having a completed game. I wont be too upset if this game never gets finished, I was just using it as a way of testing out different parts of C++ and how they work/don't work. 
One of the things i was struggling to understand in the guide C++ in 21 days is this issue with local and global variables and how to manipulate something like the sprites X coordinate in one place and read it out in another without making it global.

@Psusi
I think a config file will be a goal at some point, when I've cracked this issue I'll look into it. I will probably have started this whole project again before it's finished but right now I'm happy to be learning the different techniques as I use them

---

### Post by dwhitney67 on 2011-05-25
> **pieman711 said:**
> 
One of the things i was struggling to understand in the guide C++ in 21 days is this issue with local and global variables and how to manipulate something like the sprites X coordinate in one place and read it out in another without making it global.


Every object/variable you declare is only valid within the scope it is instantiated in.  Thus if you want something to last the entire time the game (or whatever app) is running, then you will need to ensure that it never falls out of scope.

Here's a simple program in which one object contains yet another object, and is available throughout the lifetime of the app, until the principle object is destroyed:
```

class Object1
{
public:
   Object1(int val) : value(val) {}

   ~Object1() {}

   int getValue() const { return value; }

private:
   int value;
};

class Object2
{
public:
   Object2(const int iters)
      : iterations(iters),
        obj1(50) // it is here that obj1 is constructed!
   {
      // obj1 will already be constructed before reaching here
   }

   ~Object2() {}   // obj1 will get destroyed

   int doSomething()
   {
      int sum = 0;

      for (int i = 0; i < iterations; ++i)
      {
         sum += obj1.getValue();  // obj1 is alive and well
      }

      return sum;
   }

private:
   int iterations;
   Object1 obj1;
};

int main()
{
   Object2 obj2(10);     // instantiate an Object2 object
   obj2.doSomething();   // call a method to do something

   // here, obj2 falls out of scope and hence is destroyed
}

```

Note that when allocating memory, the allocated memory will persist until it is reclaimed (freed).  However, the "handle". or pointer, to that memory may cease to exist.  For example:
```

if (some_condition)
{
   int* ptr = new int(20);  // allocate int object on the heap

   *ptr = 30;   // change value in memory from 20 to 30
}

*ptr = 40;   // oops!  Can't do... ptr is no longer in scope.

```

I hope these explanations help a bit.

---

### Post by pieman711 on 2011-05-25
that has defintiely helped a lot. Just to clarify when the memory is still assigned and the ptr is out of scope that is memory leak and that memory is usless until the program is quit? 
I think I'm going to have to go back over this thread and start this part of the program again from a new angle with what you have all said. I think I'll have a break for tomorrow. 
Thanks a lot guys!

---

### Post by dwhitney67 on 2011-05-25
> **pieman711 said:**
> Just to clarify when the memory is still assigned and the ptr is out of scope that is memory leak and that memory is usless until the program is quit? 

Yep... that is indeed a memory leak.  Fortunately the system will recoup the memory when the application exits.

---

### Post by Blackbug on 2011-05-25
The memory leak will be until you will use

delete ptr;

its a thumbrule, whenever use 'new' operator to allocate memory use 'delete'

---

### Post by psusi on 2011-05-25
> **Blackbug said:**
> The memory leak will be until you will use

delete ptr;

its a thumbrule, whenever use 'new' operator to allocate memory use 'delete'

By definition, if it has leaked, then you don't have a ptr to delete.

If you really need to be able to refer to the object anywhere and have permanent lifetime, then you can make it a static member:

```

class foo {
    static int x;
};

main()
{
    foo::x = 5;
}

```

It is basically a global but wrapped in the class namespace.  This is slightly better than a global since it helps to avoid namespace collision ( someone else using the same name ), but still should be avoided if possible.

In your case you don't even want a global.  Since you have the level class, then everything that needs to manipulate the members of the level class should be put in member functions of the level class.  This keeps all of the code that manipulates the data close to the data itself, which is called encapsulation, and is one of the major benefits of OOP.  If you need to, you can have some other function manipulate the variables in the level class via a pointer or reference, like so:

```

std::string GetLevelName(level &levelx){ 
    return levelx.name;
}
```

Note the & so that the level is passed by reference.  To adhere to the principal of encapsulation, rather than define a global function that takes a level reference, it is better to just make GetLevelName a member function of the level class, like so:

```

std::string level::GetLevelName()
{
    return name;
}

```

Let's take a look at your initial idea:

```

level GetLevelDetails(level levelx){ 
    level levelCurrent(levelx.getname(), levelx.getstartX(), levelx.getstartY(), levelx.getdoorX (), levelx.getdoorY(), levelx.getkeys())
    return levelCurrent;
}
```

There are a few things to note about this.  First, you are passing a level by value, so a new one is created when the function is called.  Then you create yet another level object on the stack, and finally, copy that object to the caller in the return statement.  This is rather inefficient and the whole function seems pointless since in the end, it just makes a copy of an existing level.

---

### Post by Blackbug on 2011-05-25
I admit, I typed incorrectly, to avoid memory leak its the thumbrule.
thanks for correcting

---

### Post by pieman711 on 2011-05-26
Having a break and sleeping on it has made a big difference. I think I've cracked it.
Instead of having global vars for all the details of the level I have them in a class 'level' they are held privately and I have accessors to get or change them. The scope of the class is only in the function I create it, so if I want to access it anywhere else I have to pass it (or a pointer to it) back to the calling function and pass it as an argument into another function. 

the main adavantage of this is I can't accidently change the vars with another function like...
```

void TestFunction(){
     levelCurrent.setKey();
}

```
then unwittingly call TestFunction();

where as I could with a global and create bugs.

Is all that right or do I need some more reading on the subject?

Thanks again for all your help :)

---

### Post by muteXe on 2011-05-26
If you have a bunch of stuff you need to keep referring to, you could create a singleton class perhaps?

---

