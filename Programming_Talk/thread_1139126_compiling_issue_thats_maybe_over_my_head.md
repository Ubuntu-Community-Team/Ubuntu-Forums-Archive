---
title: "compiling issue thats maybe over my head"
date: 2009-04-26
forum: Programming Talk
---

### Post by darius2002 on 2009-04-26
Hey guys,

I'm a brand new programmer wanna be, and I have a questions that I cannot find the answer to. My experience so far is with C++ which is the language I choose to start off with. I'm using ubuntu and gcc as my compiler.

Now, I have a few C++ primers that I'm reading everyday and teaching myself with, and I'm just moving into classes, which I find absolutly awsome after it clicked and the lightbulb went on in my head, lol Programming is so fun :D tho it's turning me into a hermit...

anyway, my problem is the same with classes and with functions. in my main.cc file, I #include "function.h" for my header file, which declares my function in the function.cc, where I further define it, awsome, works great .....kinda.

I am finding that I have to also #include "function.cc" in my main.cc for the compiler to include it and compile correctly, otherwise the compiler basically tells me that everything declaired in the header file is not defined anywhere.

To my understanding...I should only have to specify my header file...right? Am I missing something here?

I will show you my 3 files below while I was practicing with a class file, and it gave me the same error until I added #include "enemy.cc" into my main.cc:

main.cc
>  
/* The main.cc file */

#include <iostream>
#include "enemy.h"
#include "enemy.cc"
using namespace std;

int main()
{
    Critter crit1;
    Critter crit2;

    cin >> crit1.m_Hunger;
    cout << "crit1's hunger level is " << crit1.m_Hunger << endl;

    crit2.m_Hunger = 3;
    cout << "crit2's hunger leverl is " << crit2.m_Hunger << endl;

    crit1.Greet();
    crit2.Greet();

    return 0;
}
 

now my header file enemy.h

> 
/* enemy.h */
 
#include <iostream>
#pragma once


class Critter
{
public:
    int m_Hunger;
    void Greet();
};


And last my definitions file

>  
#include <iostream>
#include "enemy.h"
using namespace std;



void Critter::Greet()
{    
    cout << "Hi. Im a critter. My hunger level is " << m_Hunger << endl;
}



I am surely a super noob, and I'm learning from a games programming primer because of all the different C++ primers i found, this one dumbs it down enough for me, and clicks just right for me to learn, lol

---

### Post by Namtabmai on 2009-04-26
You shouldn't need to include "enemy.cc", my guess is that your not including enemy.cc when you call the compiler.

Can you post the command you use to compile this?

---

### Post by darius2002 on 2009-04-26
Oh... yeah sure

$ g++ -Wall main.cc -o main

I thought that the header file since it's included in the main file, would drag enemy.cc along automatically, since the enemy.cc had #include "enemy.h" in it'self.

I've only been at this 2 weeks, sorry, I know it's fairly primitive, lol

---

### Post by shadylookin on 2009-04-26
I compiled with 

g++ -ooutput main.cc enemy.cc

and I didn't need to include enemy.cc

for whatever it's worth isn't cpp the standard c++ file extension? I would consider using that

---

### Post by darius2002 on 2009-04-26
yeah I was using *.cpp as my exention, but then in the book I started using more prominently, all of it's examples were *.cc so I just kinda changed over.

I didn't know that I would have to define all of the source files in my compiling command together. I thought it would know automatically, obviously i don't have a complete understanding of the compiler parameters yet.

But if I had like 50 header files, and 50 different source files to compile together, wouldn't that make one massive compiling command?

---

### Post by Namtabmai on 2009-04-26
cc or cpp, it's your choice really the compiler doesn't care what extension you use. :)

What happened to you was that originally you told the compiler to compile only the code in main.cc. So the compiler had no knowledge of the code in enemy.cc, so it gave you errors to this effect.
Once you told the compiler to compile both main.cc and enemy.cc it knew about all the code so could link it all together as you expected.

---

### Post by shadylookin on 2009-04-26
> **darius2002 said:**
> yeah I was using *.cpp as my exention, but then in the book I started using more prominently, all of it's examples were *.cc so I just kinda changed over.

I didn't know that I would have to define all of the source files in my compiling command together. I thought it would know automatically, obviously i don't have a complete understanding of the compiler parameters yet.

But if I had like 50 header files, and 50 different source files to compile together, wouldn't that make one massive compiling command?

once you get to that you'll be using makefiles and/or an IDE that builds for you.

---

### Post by Namtabmai on 2009-04-26
Yep as good as an IDE is, it's worth learning what is going on underneath.

---

### Post by darius2002 on 2009-04-26
so what i need to do is add an #include "filename.cc" to my main.cc all the time, or, make sure I add "filename.cc" to the compile command to tell the compiler to include these files. Ok, easy enough, so now this becomes less of a how, and more of a why issue for me.

If thats the case...why do I need to include a header file? I thought the header file was to point to a library, or or another source code file. I mean... why not just skip making the header file alltogether, and include the declairations normally in the header file, into the other "filename.cc" itself, and work with one less file?

in other words, combining enemy.h and enemy.cc into one file.
I suppose there are more advanced techniques that rely on this and not yet within my understanding, if so, thats cool, i'll learn in time. I'm not asking you to teach me or anything, lol Im sure there are enough of those around, this is just something I wasn't able to figure out from my book on my own.

---

### Post by Namtabmai on 2009-04-26
Add filename.cc to your compile command, you should never really include a .cc file, only include header files.

A header file describes what that file/class does, while the .cc file implements that functionality. This way you only have to include the header file in other .cc files so they know what a file/class should do. Leave it up to the compiler to figure out where the implementation is.

---

### Post by darius2002 on 2009-04-26
Oooooooooooooh ok :D
I can see where that would be more useful with multiple .cc files

Awsome, thanks for the replies guys. Much appriciated :D

---

