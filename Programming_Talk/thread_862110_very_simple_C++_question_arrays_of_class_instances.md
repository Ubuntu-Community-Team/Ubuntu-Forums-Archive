---
title: "very simple C++ question: arrays of class instances"
date: 2008-07-17
forum: Programming Talk
---

### Post by CC_machine on 2008-07-17
is this the right way to use classes? i modded some code from cplusplus.com just to see if this would work, and it did:
```

// example: one class, two objects
#include <iostream>
using namespace std;

class CRectangle {
    int x, y;
  public:
    void set_values (int,int);
    int area () {return (x*y);}
};

void CRectangle::set_values (int a, int b) {
  x = a;
  y = b;
}

int main () {
  CRectangle rect[2];
  rect[0].set_values (3,4);
  rect[1].set_values (5,6);
  cout << "rect[0] area: " << rect[0].area() << endl;
  cout << "rect[1] area: " << rect[1].area() << endl;
  cout << "Am i still here?";
  return 0;
}

```

this runs perfectly fine:

> 
ccmachine@andrewiv-portable:/media/sda7/ccmachine/c++$ ./a.out 
rect[0] area: 12
rect[1] area: 30
Am i still here?
ccmachine@andrewiv-portable:/media/sda7/ccmachine/c++$ 


somebody told me this is a bad idea... is it? makes sense to me, but then again i don't know much about the language.

any help would be gladly appreciated. i'm more or less a complete newbie in C++ in general, but i've used Visual Basic 6(a long time ago) and done some interesting things with C++ and SDL (keyboard-controlled box moving around with collision detection and moving with another box, (but not using classes) for example) before.

i really want to use classes, as game-type programming (bullets, enemies etc) should be object-oriented. arrays for these things in VB6 was a total mess.

---

### Post by Tony Flury on 2008-07-17
Why do you think it is wrong ?

It is a very simple use of a class but it does not seem to be wrong

The power of classes (to my mind) come from two different concepts : 

[LIST=1]
[*]Encapsulation - The data and the actions on that data are defined together.
[*]Inheritance/Polymorphism - were a class is seen as derived from something else.
[/LIST]

In your example you have encapsulation - the data and actions are defined entirely in the class (you could imagine you could have a draw method, or fill or stretch). Also the two data elements x & y are private to the class which i think is also key.

Inheritance/Polymorphism - you don't have that in your simple example, but you can imagine have a class called shape which defines some basic operations and data, and then your Rectangle class would inherit from that (as would classes such as Square, triangle, circle, elipse).

---

### Post by issih on 2008-07-17
Looks ok to me, C++ as a first stab at grasping OO methodology is going to be a hard learning curve. Other languages like java or c# make the concepts somewhat simpler by burying the complexities of pointers references and memory management, you can then concentrate on getting the hang of coding using polymorphism and carefully defined public class interfaces to modularise your code.

Not trying to put you off at all, if you really want I'm sure you can go with c++ from the start, it'll just make life a bit tougher for you.

---

### Post by dwhitney67 on 2008-07-17
> **issih said:**
> Looks ok to me, C++ as a first stab at grasping OO methodology is going to be a hard learning curve. Other languages like java or c# make the concepts somewhat simpler by burying the complexities of pointers references and memory management, you can then concentrate on getting the hang of coding using polymorphism and carefully defined public class interfaces to modularise your code.

Not trying to put you off at all, if you really want I'm sure you can go with c++ from the start, it'll just make life a bit tougher for you.
I don't buy this argument.  In Java, "pointers" are called handles and their use is essential to any application using complex objects.

Also, it is possible to write a semi-complex application in C++ (or C) that do not utilize pointers whatsoever.  Either way, the use of pointers is done when there is a need for such, not because it is a part of the language.  One should not be fearful of using pointers.  They are not "cursed" by the witches of hell.  They are just facets of the language that a grade-school child could learn/understand.

This bias that you and other have against pointers, and in general C/C++, is so profound and often times incorrect.  C and C++ are two languages, that without a doubt, are used in more applications than C#, Python, and Java.  And the reason for this is because they are the choice languages for everything from s/w defined radios, cell phones, flight s/w, embedded systems, satellite, rockets, etc.  I would not be half-surprised if the software application in my Citizen watch was programmed in C.

The argument that C/C++ is too hard to learn is a cop out; basically when one uses this argument, they are admitting that they are not as bright as their peers, or that they are not up to the challenge.  That's fine, not everybody will master programming, just like not everybody will master the cello or the violin.  But don't sway someone to learn a different language simply because of your failings.  If you have nothing positive to add to the discussion, don't say anything at all.

Thank you.

/rant

---

### Post by CC_machine on 2008-07-17
thanks everyone. i'll agree though, C++ is difficult to begin with. no matter what i do i cant get this class to work the way i want it to, and just keep getting more and more confused. is there anything simpler i could start out with? similiar to VB on windows? maybe not that simple, but i definitely don't want to go into scripting. gedit & g++ are fun and all, but i'd like to become productive sooner. you know, making apps that are actually useful. :confused:

i code for fun, but C++ ain't fun until you have a good grasp of the language. also, i find the CLI extremely limiting but using SDL for GUIs is yet more complicated. i tried adding classes to a simple SDL program and it spat out like 50 errors.

---

### Post by Tony Flury on 2008-07-17
> **CC_machine said:**
> thanks everyone. i'll agree though, C++ is difficult to begin with. no matter what i do i cant get this class to work the way i want it to, and just keep getting more and more confused. 

What errors/problems are you getting ? Given what i think you want the code to do it seems to work fine.

> 
is there anything simpler i could start out with? similiar to VB on windows? 

I am not sure you could do an object oriented program that is simpler. Well you could, but what would be the point.

---

### Post by Can+~ on 2008-07-17
> **CC_machine said:**
> thanks everyone. i'll agree though, C++ is difficult to begin with. no matter what i do i cant get this class to work the way i want it to, and just keep getting more and more confused. is there anything **simpler i could start out with? similiar to VB on windows?** maybe not that simple, but i definitely don't want to go into scripting. gedit & g++ are fun and all, but i'd like to become productive sooner. you know, making apps that are actually useful. :confused:

i code for fun, but C++ ain't fun until you have a good grasp of the language. also, i find the CLI extremely limiting but using SDL for GUIs is yet more complicated. i tried adding classes to a simple SDL program and it spat out like 50 errors.

Please stay away from Visual Basic.

Also, if you want to start programming, forget about GUIs, SDL, OpenGL, and all the graphic glory for a while. Make a program that works, then make it better, then optimize it. And later you add the interface and buttons over it.

Please check the pinned:
[http://ubuntuforums.org/showthread.php?t=796494](http://ubuntuforums.org/showthread.php?t=796494)

---

### Post by issih on 2008-07-17
Frankly, Mr DWhitney you are making some very wrong assumptions about my intelligence (If you really must know, I have a first class degree in physics from Cambridge University), and not grasping the point I was making at all.

Just so we are clear I am a c++ programmer, I have spent the last 4 years writing a large iterative program that runs on a supercomputing cluster using mpi techniques as part of a PhD. Don't go around casting aspersions when you have no idea who you are addressing.

Secondly you merrily state that java uses pointers under the hood...um duh I know, I was making the point (quite clearly) that it hides the complexities of them from you. Pointers by themselves are not complicated, but getting them wrong can cause nasty, hard to debug memory management errors. C++ is harder than java or c#, end of story, no argument to be had. I was not trying to put him off, something I stated quite specifically, I was merely pointing out that it would be easier to get a handle on how OO programming works without having to get a handle on the complexities of memory management (and with classes it can get subtle with things like deep vs shallow copying and the need to overload the copy constructor/ equality constructor, need for virtual destructors etc).

Most importantly you state you can write a program in c++ without using pointers...true as you can basically treat it as C with classes in place of structs.... If you do that however you are missing the whole point of OO, in that you will never use Polymorphism. Pointers/References are absolutely essential to the operation of this feature, which is in essence the entire heart and soul of OO programming, which the OP makes it clear is what he wants to learn.

If you want to be stroppy fine, but constrain your rants to the facts you know, not opinions.

I am not impressed....at all

---

### Post by Felson on 2008-07-17
While dealing with pointers is a little bit harder, but IMO it is well worth the effort. Yes, you have the power to shoot yourself in the foot, as many a book and a prof have pointed out, but so what? That is how you learn. I personally think it is better to understand what is going on under the hood, then to stick your head in the sand pile.

flame bait
Knowledge != Intelligence
Known many an MCSE that couldn't solve there way out of a paper bag. But as long as the were using X version of windows, they were almost useful. 
/flame bait

---

### Post by issih on 2008-07-17
Its a matter of learning things bit at a time or going for everything at once..

If you just want to begin to get your head around basic procedural code flow, almost anything will do, even basic.

if you want to begin to grasp memory management at a lowish level you need to look at something like C.

If you want to understand OO programming you need to learn an oo language, and I more importantly how polymorphism works, and how to use it to your benifit.

Starting with C++ is like trying to learn French by picking up a novel and trying to read it. Yes, in the end, bit by bit, by sitting with a dictionary and translating each word, slowly gleaning the grammatical constructs, you will manage to learn it. It is usually faster however to start with a simple book designed for the novice. That's how human beings generally learn things.

In the end though, the validity of any teaching/learning method is subjective, and highly dependant on the pupil. There is no correct answer here, only opinion and advice. People should have the "intelligence" to know that and behave accordingly

---

