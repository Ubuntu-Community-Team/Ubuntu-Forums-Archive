---
title: "C++ Including stuff"
date: 2010-02-07
forum: Programming Talk
---

### Post by Ravenshade on 2010-02-07
Please note I have not solved the original topic instead I have learned that my understanding of how to structure C++ code isn't perfect, far from it, so I have to learn more about it before including files in any form. 

We have moved onto pointers on page 2.

--------------------------------------------------------------------------------------------------------------------------


Just a quick question. I see that the #include feature is available but due to my newbness I am unsure of the extent. 

Does it work like PHP? In so much as:


#include </myListOfStuff.cpp> 

then that would insert my list of stuff at the top as if it were part of the same file. I'm starting to get a lot of variables that I'd like to put somewhere nice n neat is all. 

Also do they require a special extension?

If it's not that way, but it is possible, please let me know.

---

### Post by MadCow108 on 2010-02-07
I do not quite get what you want, so a general answer

#include is an extremely primitive preprocessor directive
it just says: paste that file into this one

generally you should only include so called header files (.h extension) which do not contain implementation code (except when using templates) but just declaration of functions which the code files need.
Header files should be designed to be independent of include order and allow multiple inclusion.
The latter is archived by include guard preprocessor directives:
#ifndef _SOME_HEADER_DEFINE_H
#define _SOME_HEADER_DEFINE_H
// declarations
#endif

if you have many global variables (which you should not in good program) and problem with name clashes, put them in namespaces

---

### Post by Ravenshade on 2010-02-07
Okay, let me make it clearer for anyone. 


Php can include a header, footer, main, and any other file and essentially compile to output one single page. 

I have a lot of variables that would like to be included, but not written in the main program, to clear up the essential code. Therefore, the variables could be included on another page say for instance. 

"myGlobalVariables" - contains variables that the main() needs to run or compute functions. 
"myPlayFVar" - contains variables that are need by the game but not main()
"myResVar" - contains none-essential variables for loops etc and not play() or main()

Really it's so that I can seperate my variables and edit them in different windows, or don't accidentally delete variables. I don't have problems with clashes I just want to essentially paste the page into the main program and hopefully at function level...if possible.

---

### Post by MadCow108 on 2010-02-07
as you should avoid global variables where possible I don't quite see the sense in that.
If you have so many global variables that you need to split them in different files to keep an order something is seriously wrong with the design
but it is possible to do that in c++ because #include does what you want.

Using include in local scope is generally not a very good idea because it makes the code very hard to read, but it works as expected.
Just keep your functions small and bound to a single task and consider organizing your variables in structs/classes and you shouldn't need the include in weird places.

Note that you can split up your code into separate units compile these units and link these together with the linker.

just compile the file with -c flag and then run the compiler again on the resulting object files to get a running program

---

### Post by Ravenshade on 2010-02-07
They're not exactly global, at least not all of them. There are some variables I'd like to be global, but I tend to define quite a number within my functions for those functions and they're starting to clutter. Tis all. 

And one function isn't picking up a defined variable.... but that is a design fault

---

### Post by LKjell on 2010-02-07
Technically you can write whatever you like in the header file. However you should only include function declarations. 

Another thing with include is that it will only be included once. So say that you have two files with the same include statement. Only one of them will be included assuming you use the header guard.

---

### Post by MadCow108 on 2010-02-07
> **Ravenshade said:**
> They're not exactly global, at least not all of them. There are some variables I'd like to be global, but I tend to define quite a number within my functions for those functions and they're starting to clutter. Tis all. 

And one function isn't picking up a defined variable.... but that is a design fault

Sounds as if you should split up your functions into more smaller ones.
A good function is only a few lines of code with only very few variables, and a single dedicated task.

Never write huge 300 line monster functions which try to do everything, there hard to maintain, as your probably already realizing.

---

### Post by Ravenshade on 2010-02-07
Well they are only a few lines long. Unfortunately it isn't picking up the variables initialized in the play() even when the checkHP() is summoned from within it. 

So I was going to move the variables up a level.

---

### Post by Ferrat on 2010-02-08
> **Ravenshade said:**
> Well they are only a few lines long. Unfortunately it isn't picking up the variables initialized in the play() even when the checkHP() is summoned from within it. 

So I was going to move the variables up a level.

Sounds like you need to do pass them as args, preferably pointers for later when you need to go back up you can return the pointer :)

---

### Post by Ravenshade on 2010-02-08
Tad advanced for me at the moment I'm afraid. I can't find a good tutorial on pointers that make one bit of sense.

---

### Post by dwhitney67 on 2010-02-08
> **Ravenshade said:**
> Tad advanced for me at the moment I'm afraid. I can't find a good tutorial on pointers that make one bit of sense.
Consider buying a book that discusses C++.  Or just go through this tutorial until, hopefully, the subject matter sinks in.

[http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

You seem to be asking a lot of questions, that frankly are trivial.  It is almost as if you are using the forum to learn C++, instead of actually taking the initiative to open a book and teach yourself.  It is quite pathetic.

---

### Post by Ravenshade on 2010-02-08
Oh shush, I'm asking questions that quite frankly puzzle me and if you noticed I'm not asking the same question twice.

I'm at this moment creating a game in c++ it might only be text based, but it's a start and it's playable. The questions that I'm asking are all helping me work out certain kinks. 

I asked about including information to see if it works in a similar fashion to php, clearly it does not so I'm going to have to work out a different theory. Args is a little above my level at the moment but once I find a program that uses it in a practical sense I'll be fine. 

I am already using cplusplus, c++ games, c++ game programming. They're helping a lot and there are a lot of questions I had that have been solved thanks to them.

---

### Post by dwhitney67 on 2010-02-08
> **Ravenshade said:**
> Args is a little above my level at the moment...
Please spare the drama.  Within the same tutorial I provided earlier, there is a section that discusses parameter passing to functions.  It's not rocket science.

[http://www.cplusplus.com/doc/tutorial/functions/](http://www.cplusplus.com/doc/tutorial/functions/)

Try to grasp the fundamentals of the language before attempting game development, or for that matter, any other complex endeavor.  Your questions are welcome, but please show that you have made at least a slight effort to do your own research.

Btw, PHP != C++.  A lot of the syntax may look the same, but one could argue the same about English and Latin.

---

### Post by Ravenshade on 2010-02-08
I've already gone through all of the tutorials. Pointers made no sense (still not sure what they might be used for). On the other hand, I have been using functions, my problem is not with functions...

as I've found out functions can't have sub-functions (at least my g++ returned an error)

It also meant that I've got a crap load of variables. (Between 10 - 20) which is why I asked the question about classes, in relation to whether it works similar to css. 

The only questions I've asked, we're not covered in those tuts, or were not explained enough (which is where the questions come from)

---

### Post by dwhitney67 on 2010-02-08
Are these variables related to each other?  Could they possibly be defined within a struct (or class)??

If so, then you could pass them around as one entity, not 20.

You should _rarely_ ever have to define/use a global variable in C++.  Pointers, often times are merely used in an effort to save memory resources and copying time.  Pointers are generally not passed to functions, since C++ provides the ability to pass the objects by _reference_.

---

### Post by dwhitney67 on 2010-02-09
Btw, here's a simple program that employs the use of pointers, references, vector, string, class, etc.

Let use know if you have any questions; I have added comments to the areas that I thought were relevant.
```

#include <vector>
#include <string>
#include <algorithm>    // std::for_each
#include <iostream>     // std::cout, std::endl;


class MyData
{
public:
   // constructor
   MyData(int age, const std::string& name)
      : myAge(age), myName(name)
   {
      // nothing to be done here; the class was initialized above.
   }

   // accessor methods for setting and getting the class' data.
   void age(int newAge) { myAge = newAge; }
   int  age() const     { return myAge; }

   void   name(const std::string& newName) { myName = newName; }
   std::string name() const                { return myName; }

   // method, that is declared within the class, but is not really part of it.
   // used merely to display the contents of the MyData class.  Because it is
   // declared as a 'friend', it has access to the private data members of the
   // class.
   friend std::ostream& operator<<(std::ostream& os, const MyData& data)
   {
      os << data.myAge << " " << data.myName;
      return os;
   }

private:
   // data that is only accessible via the accessor methods, or friends.
   int         myAge;
   std::string myName;

   // declared, but not implemented, thus preventing usage
   MyData();
};


// pass vector by 'reference'.  The vector contains allocated MyData objects.
void updateAge(std::vector<MyData*>& data, const int years)
{
   for (size_t i = 0; i < data.size(); ++i)
   {
      const int age = data[i]->age();

      data[i]->age(age + years);
   }
}


// helper function for displaying a MyData object
void display(const MyData* data)
{
   // deference data, thus allowing the ability to call it's operator<< method
   std::cout << *data << std::endl;
}


// another helper function for destroying a MyData object
void destroy(MyData* data)
{
   delete data;
}


int main(void)
{
   // local declaration
   std::vector<MyData*> theData;

   // add to the vector two MyData objects allocated on the heap
   theData.push_back(new MyData(22, "David"));
   theData.push_back(new MyData(45, "Goliath"));

   // display all of the data within the vector
   std::cout << "Before update..." << std::endl;
   for_each(theData.begin(), theData.end(), display);

   // now manipulate this data
   updateAge(theData, 2);

   // re-display all of the data within the vector
   std::cout << "\nAfter update..." << std::endl;
   for_each(theData.begin(), theData.end(), display);

   // destroy allocated memory
   for_each(theData.begin(), theData.end(), destroy);

   return 0;   // optional
}

```
Pay careful attention to the usage of pass-by-reference.  Also, carefully examine the class construct.  A struct and a class are identical in every way, except by default, data/methods in a class are 'private'.

---

### Post by Some Penguin on 2010-02-09
> **Ravenshade said:**
> I've already gone through all of the tutorials. Pointers made no sense (still not sure what they might be used for). On the other hand, I have been using functions, my problem is not with functions...

as I've found out functions can't have sub-functions (at least my g++ returned an error)

It also meant that I've got a crap load of variables. (Between 10 - 20) which is why I asked the question about classes, in relation to whether it works similar to css. 

The only questions I've asked, we're not covered in those tuts, or were not explained enough (which is where the questions come from)

Pointers are very, very, very basic.  Really.  They're memory addresses with type data applied for the convenience of the programmer and compiler.

And I thought that you were pooh-poohing classes and calling C++ logical and easy...

---

### Post by MadCow108 on 2010-02-09
> **Ravenshade said:**
> I've already gone through all of the tutorials. Pointers made no sense (still not sure what they might be used for). On the other hand, I have been using functions, my problem is not with functions...

as I've found out functions can't have sub-functions (at least my g++ returned an error)

It also meant that I've got a crap load of variables. (Between 10 - 20) which is why I asked the question about classes, in relation to whether it works similar to css. 

The only questions I've asked, we're not covered in those tuts, or were not explained enough (which is where the questions come from)

of course functions can have sub functions, the can even be recursive! (until you run out of stack space, which is many many levels of recursion)
```

// prototypes (=declarations, usually in header files)
int f(int);
int subf(int);
int subsubf(int);

// implementation (=definition, usually in c files)
int f(int a) {
  return subf(a);
}

int subf(int a) {
  return subsubf(a);
}

int subsubf(int a) {
 return a*2;
}

```

If you really don't get pointers, then C++ is the wrong language. You can write C++ code without using raw pointers by using advanced techniques like RAII, but before your able to do that you have to know your pointers!
C++ is one of the hardest to learn because of its many subtleties and confusing design.

I recommend learning an easier language like python first, it totally skips pointers and many other difficult parts of C like languages but is still just as powerful for most applications.
Maybe come back to C/C++ later.

---

### Post by Ravenshade on 2010-02-09
> **Some Penguin said:**
> Pointers are very, very, very basic.  Really.  They're memory addresses with type data applied for the convenience of the programmer and compiler.

And I thought that you were pooh-poohing classes and calling C++ logical and easy...

Easier than fudging Java. -_-; It's also a good language to start with, I've found that learning C++ has greatly increased my adaptability to reading through the code of other languages. (Except Fortran, Haskell and LISP of course). 

Also, classes are a load of rubbish. Learn by doing! Especially with computer languages. Did you know (gonna sound patronizing) that C was the only language to be issued with computers free of charge? Meaning C and its derivatives are really supposed to be learned in the same way. At least, that's my opinion and so far it's working. 

Anyone tell me exactly why I would use pointers? (It's a question that isn't answered in any of the tutorials I've read, such as cplusplus.com/doc/tutorials) 

----Updates main title---
[B]
@MadCow[/B]
...odd

> void game(){

void healthCheck(){
}
} 

returned an error: { before } 

Probably my misunderstanding of void really. But at the moment all of my functions are outside of each other. 

> //////////////////
List of Variables
List of declared functions

followed by all my functions

Followed by main()

followed by game()

end file
//////////////////

Perhaps some of my syntax was wrong, that's always a factor.


-----------------------------------------------------------------------------------------------------------------------------

So pointers... without thinking about memory addresses (because e that's a bit complex) can pointers be used to point to separate data within a class? *heads off back to the tutorials with a better understanding*

I resurrect my other topic to talk about classes once I've sussed out pointers.

---

### Post by MadCow108 on 2010-02-09
if you don't like classes, why are you using c++?
At your level C++ is not much more than C with classes (the old name of C++ btw)
If you don't understand the benefits of classes, I doubt you will understand the other strengths of C++ (strict typesafety, templates and generic programing (STL), template metaprogramming ...)

use C, it does not have classes and a much cleaner, slimmer design (and you _cannot_ write non trivial programs without really understanding pointers)

C++ although a derivative of C is really not learned the same way. Knowing C is just the basis of learning C++
Proper C++ programming is radically different from C programming.
You just need to know C (and its drawbacks) so you know why C++ offers you other possibilities at solving problems and understanding its underlying memory model (although you have to interact with it less often than in C).

---

### Post by matthew.ball on 2010-02-09
> **Ravenshade said:**
> Easier than fudging Java. -_-; It's also a good language to start with, I've found that learning C++ has greatly increased my adaptability to reading through the code of other languages. (Except Fortran, Haskell and LISP of course).
Yeah, because the investigated languages are all imperative - they share essentially the same base "logic" as C. I'm actually surprised you can't read Fortran though, it is also imperative.

> Also, classes are a load of rubbish. Learn by doing! Especially with computer languages. Did you know (gonna sound patronizing) that C was the only language to be issued with computers free of charge? Meaning C and its derivatives are really supposed to be learned in the same way. At least, that's my opinion and so far it's working.
Classes are rubbish? Spoken like someone who is an expert in their field!

It would perhaps be difficult to just "find" some of the advantages to object-oriented programming without reading about the theoretical core behind it. Unfortunately there is no "shortcut" - you just have to do some learning, why make it hard on yourself? Seriously.

> Anyone tell me exactly why I would use pointers? (It's a question that isn't answered in any of the tutorials I've read, such as cplusplus.com/doc/tutorials)
A quick search on google has returned *pages* of information on why you would want to use pointers - it's obvious you have done very little research yourself here.

I can't speak for everyone else here but basically, I'll gladly try and help you in anyway I possibly can, but you have to take the first step and show some willingness. The second you said "sorry too advanced for me" or whatever is the point where I gave up. We're not here to hold your hand, and no one in the "real-world" will either.

If this hasn't dented your ego too much, and you still want to give it a go, please just do a little bit of reading. Honestly it's worth it. You'll be able to come back and pose proper questions - again, I am sorry if this is harsh, but unfortunately I fear it has to be.

---

### Post by nvteighen on 2010-02-09
Uh...

Pointers are just that, pointers that point to something. If a variable is a name for an object, a pointer to that variable is like a library card holding information where to find the box with the data... The same as with a library card for a book, you can modify the card if you feel the data is outdated or, alternatively, use the card and go find the book, you can manipulate the pointer's information or follow the pointer to do something to the data it points to (*dereferencing*).

So. When you declare or give a value to a pointer, you give an address in. When you take the pointer's value, you get the address where the information you want is located. 

Ok, but of course the useful thing is that you can use the pointer's value (the address of some object) to get the object it points to. That's done with the * operator, which makes you effectively go to the address held by the pointer. So:

```

int *ptr; /* Written this way to avoid confusions. See below. */
int mynumber = 12;
ptr = &mynumber; /* & is the address operator */
*ptr = 13; /* Ok, now mynumber is 13, because we 'followed' the pointer. */

```

That's all there is to the concept of pointers. The only thing is that the way you declare them in C and C++ is totally counterintuitive, as it uses the * operator when you're actually setting the pointer's value... but, **int *a = &something;** is the same as **int *a; a = &something;**.

Another subtility is that arrays and pointers are that close to eachother (if not the same) that you can interchange them. An array works as a pointer to the first element of an allocated region of memory, so that a[i] and *(a + i) are the same. But in C++ you better use std::vectors rather than C-like arrays.

Ok, what's this useful for? Well... mainly for cases when you want your data persist after the call stack is wiped out after the function returns. You surely know everything you declare in a function is lost when this returns... so, what if you want something stay there? You use a pointer that points to a region of memory that isn't in the stack so it isn't wiped out... that region is called the heap and it lacks automatic management in C and C++.

It's true that C++ reduces the amount of pointers used around compared to C because of a lot of features it introduced, but they can still appear from then to then, specially in cases in which you can't return an object for some reason and your only way out is by passing a pointer to it... even then, references are a much better way to go.

About classes, I'll refrain from commenting about how wrong that idea is. Time and practice will show you they're a powerful ally to construct your code with. It's true that C++ puts a lot of stupid features into its OOP idea, but you can live without using them... anyway, those are language-specific issues, not the concept's. OOP has proven to be a great way to map the human way of thinking in objects into programming, therefore making the programmers' lifes much easier.

---

### Post by Ravenshade on 2010-02-09
Classes as in going to a lecturer and sitting down and looking at a computer screen while listening to someone babble kind of classes >_<. 

Classes in C++ if they work anything like they do in CSS (which they appear to... 

for example. Declare the overall object. (Lets call it p for paragraph) then define which particular article of the class I want. So p.fred and p.george would have different features but they'd do the same thing as what p would do naturally. ) 

Hopefully there's more to it than that, (particularly in the syntax area)

My problem is that I don't understand the syntax or how to write them just yet. 

In terms of my program, I'm not sure I'll need to use pointers just yet unless I'm using classes and I'm hoping I'll be able to use pointers to point to different parts of the classes. So pointing  p*george (pointing p at george to get the data from george?, Of course I'm unsure if that'd work in practice)

**nvteighen**

Everything in a function is wiped once it ends. Fair enough, I'm not sure if I'd want any information to stay in a function just yet. (I haven't found a need for anything like that just yet, that's not to say I won't, perhaps I could create some kind of configuration settings that will adjust how the program is outputted and the information is the same every time the function is run (according to user input))

Thankfully I hope never to touch OOP, I understand that it works in a similar way to Haskell in terms of programming AI (or I could have completely mis-understood my lecturer while discussing different languages in Object Orientated programming last week).

Assigning objects to memory however was one of the reasons why I chose C++ because it's one of the faster languages available. (Faster than Java at least). (Has anyone noticed I have a pet hate against Java? Hehe)

---

### Post by MadCow108 on 2010-02-09
your not going to get around using pointers.
learn it now!
you currently try to use very bad patterns (like tons of variables and includes to group them...) to avoid using pointers. This is not good learning.
If you really don't want to, use a language without pointers...

Also learn classes now! The basics a very simple. At least have a look at C structs (which are in a sense a precursor to real classes)
And you are going to have to touch OOP (it has nothing to do with haskell or any specific language). It is an absolute necessity to at least grasp its concept, even if you choose use other design concepts.

You can only get around using pointers up to a certain degree by using functional programming.
But C is not a very good language for that. If you want to use this style use Lisp, Haskell or Python.

also java is not much slower than C++
I doubt you currently utilize (or need!) the few speed advantages C++ offers.

I hope you don't plan for an career in programming. With your current attitude you are destined to fail.

---

### Post by CptPicard on 2010-02-09
> **Ravenshade said:**
> 
Thankfully I hope never to touch OOP

It's one of the most pervasive paradigms around in programming, regardless of its specific implementation in a language, so that hope is in vain :)

> I chose C++ because it's one of the faster languages available. (Faster than Java at least). (Has anyone noticed I have a pet hate against Java? Hehe)

Well, at your phase, learning general program construction and design skills (especially in the OOP area :) ) would be more important than caring about "speed"... besides, Java is actually among the fastest of languages that are not C or C++.

An annoying feature of *both* Java and C++ especially for learners is exactly the learning curve of typical static-typed object-oriented design. Not knowing what kind of object to put where can really stump you to begin with (I know this was a problem for me back then). C++ adds the complication of having to be much more careful about the little details so that your program doesn't just break... at least in Java you get nice stack traces.

---

### Post by Ravenshade on 2010-02-09
@MadCow

I'm aware that one day I'll have to use pointers and if it works with classes and points to things in classes, then that'll be perfect and I'll use them as soon as I implement classes. (Before that I want a few more characters (as in none playable characters) so that I actually have types that I want to put information into)

Just for the record I haven't used #include<file> for anything other than iostreams, strings, amongst other libraries and since people are so against it I'm assuming C++ likes to be a contained language (for the most part). 

I have looked at structs, though they made less sense than classes so I think I'll throw myself in the deep end with classes. (On the other hand, that could be me not understanding the syntax and realizing they're a helluva lot easier and more sensible to use than classes)

I promise I'll touch OOP in a few hundred years >_> jk jk, I know I'll have to get around to it some time, just thankfully, not yet. 

I want to avoid functional programming. (Which is Haskell and Lisp I believe) Heads and Tails confuse the hell outta me. (I do have an assignment where I do have to make some sort of program out of haskell and believe me, I am not looking forwards to that assignment, {a{a,{}}} = Not logical. 

In the sense of speed I probably don't need the advantage that C++ provides but it is generally acknowledged that once you learn C++ or C then it's easier to break into Java. (The learning theory: Foundations first^_^)

With my current attitude I'm only just starting out dammit. I'm not planning on doing it for a career, I'm planning to do it for fun. 

@CptPicard 

First of all, nice to meet you, great username!

T_T I know, one day I'll be fluent in C++ and OOP. Then I'll be king of the world. (Until the moment I realise that C++ has been outdated and no one uses it any more).

Stack traces? Now theres something I'm not familiar with. If I can cope with C++ (currently not doing the best of jobs) and putting the code into the right places, then logically my code will be better typed, better commented and in an order that everyone would understand. That's something that I am coming to realize and see as a benefit rather than an disadvantage.

---

### Post by Some Penguin on 2010-02-09
> **Ravenshade said:**
> @MadCow

I'm aware that one day I'll have to use pointers and if it works with classes and points to things in classes, then that'll be perfect and I'll use them as soon as I implement classes. (Before that I want a few more characters (as in none playable characters) so that I actually have types that I want to put information into)
  Just think of pointers as addresses on a really, really long street (memory, that is).  Just as with the real world, it's possible to have addresses that are no longer valid (never assigned or building already demolished, for instance...)... and the addresses of objects don't have to be contiguous.  It's also possible to increment or decrement pointers, which would correspond to driving up and down that street.   And if you go looking into places where you don't have permission to visit, the local gangs kill you, causing a segmentation fault or memory protection error.  ;) >  I have looked at structs, though they made less sense than classes so I think I'll throw myself in the deep end with classes. (On the other hand, that could be me not understanding the syntax and realizing they're a helluva lot easier and more sensible to use than classes)   Structs are inherited from C, which had structs and unions but no classes.  A lot of C code would have been no longer valid if C++ lost 'em.  >  I want to avoid functional programming. (Which is Haskell and Lisp I believe) Heads and Tails confuse the hell outta me. (I do have an assignment where I do have to make some sort of program out of haskell and believe me, I am not looking forwards to that assignment, {a{a,{}}} = Not logical.    Depends on what you're using it for. e.g.  list_minimum = (minimum of head of list, list_minimum (rest of list))  is fairly direct.  Of course, it also relies on sane implementation of tail recursion to prevent stack overflow on long lists, and there are ways to write it that involve an explicit iterator instead of function calls.    > In the sense of speed I probably don't need the advantage that C++ provides but it is generally acknowledged that once you learn C++ or C then it's easier to break into Java. (The learning theory: Foundations first^_^)
   Used to be a common teaching path.  I think Java found favor as 'first significant programming language to teach' some years ago, however.   > Stack traces? Now theres something I'm not familiar with.   'Stack' as in 'call stack'.    - function c called by function b with some arguments
- function b called by function a with some arguments
- function a called by main with some arguments
- main
 When function c returns, the top of the stack is removed, and perhaps function b calls another function, resulting in another stack frame (which will contain such things as the arguments passed in and a return address to jump to).  And so forth.  Local variables are also stored on the stack, at least if they're small-ish.  Dynamically allocated stuff, however, is stored on the heap; the pointers themselves will be on the stack if the pointers themselves have been passed as arguments in or are local variables.  So when something explodes, you can check the stack to find out where you were, and hopefully see what exploded and why.  > If I can cope with C++ (currently not doing the best of jobs) and putting the code into the right places, then logically my code will be better typed, better commented and in an order that everyone would understand. That's something that I am coming to realize and see as a benefit rather than an disadvantage.   Maintainability and ease of understanding are better for yourself, as well, if you ever think you'll revisit the code.  Also, if you ever look at your own code and can't understand it, there's a pretty decent chance that the reason you can't understand it is that it's actually wrong and won't actually do what you want it to do.

---

### Post by dwhitney67 on 2010-02-09
](*,)

Somehow I think ramming my head against a brick wall would bring more pleasure than following this thread any further.

Ravenwood, good luck with your failures!

---

### Post by Ravenshade on 2010-02-09
*ignores dWhitney* but thanks for your help anyway. 

Some Penguin, you really are 'some' penguin ^_^; Thanks for that explanation. Pointers purely deal with memory assignment then?  (Heavens Juan doesn't explain everything in that tutorial....). In that case, that'll be something to do with the dynamic memory in the next chapter, I'm guessing. (back to practice)

I also agree with that last point, I often get frustrated when people don't comment their own code, then I look at my own code and think...'comment more comment more' so yeah, understanding my own code is essential. That way if I lose track of C++ for a while I can come back to it and continue from where I left off.

---

### Post by matthew.ball on 2010-02-09
> **Ravenshade said:**
> Classes as in going to a lecturer and sitting down and looking at a computer screen while listening to someone babble kind of classes >_<. 
You're still wrong.

So we're going to assume that classes are rubbish - No one would attend a class, let alone sign up for a class. Universities wouldn't be major research hubs.

Obviously this does happen, so we will reject our initial assumption that classes are rubbish.

I'm sorry, but again I have to be harsh. Following from your questions, I get the impression that you are the perfect example of why classes exist.
Not everyone can teach themselves, regardless if they are motivated or not - I'm not calling you stupid, please don't interpret it that way.

I am one of the aforementioned who cannot teach themselves - hence I go to school and put in the required effort. You're only going to get out of school literally what you put in.

My whole point is, programming isn't just a practical activity, the theory is equally (some would even say more) important. The only way to really get this conceptual understanding is by reading.

You have to balance it out, the perfect amount of hacking with the perfect amount of reading.

---

### Post by maraldi on 2010-02-10
> **Ravenshade said:**
> 

Anyone tell me exactly why I would use pointers? 



Pointers are essential in C++ programming of memory management.
Many algorithms and data structures will involve using pointers.

Pointers and arrays are closely connected.  If you use arrays you'll have to learn about pointers.
While an array never becomes a pointer and a pointer is not the same type as an array,
you'll soon learn that array names act like pointer values in nearly every context.

The relationship between arrays and pointers extends to strings.

At first they seem complex but the ideas underlying pointers are simple.
So don't let them hinder your progress.

---

### Post by MadCow108 on 2010-02-10
> **maraldi said:**
> Pointers and arrays are closely connected.  If you use arrays you'll have to learn about pointers.
While an array never becomes a pointer and a pointer is not the same type as an array,
you'll soon learn that array names act like pointer values in nearly every context.

this is not right.
Arrays become pointers in every change of stack frame.
Only in the same frame array's stay arrays and the sizeof operator acts like one would expect.
```

main() {
 int array[10];
 sizeof(array); // ok
 somefunction(array);
}
somefunction(int array[]) {
  sizeof(array); // oh no array is a pointer now! sizeof gives different result
}

```

the declaration syntax somefunction(int array[]) just hides this fact, its the same as somefunction(int * array)

this is one of the most confusing parts of C and almost every learner stumbles over it (especially when they come from high level languages and are used to sizeof type operators just working)

---

### Post by maraldi on 2010-02-10
int *array and int array[] have the identical meaning only when used in a function heading or prototype. Both mean that array is a pointer to int.
The notations are not equivalent in any other context.

---

### Post by nvteighen on 2010-02-10
The reason why **type abc[size]** isn't the same as **type abc[]** or **type *abc** is because while the latter two only specify the existence of a pointer to somewhere, the first one does also allocate a region of memory of size size*sizeof(type).

The a[] only equals a[size] when declaring stuff.

The issue is that in a function interface, while you can do something as weird as:
```

#include <stdio.h>

int sum(int[4]);

int sum(int list[4])
{
    int accu = 0;
    int i;
    for(i = 0; i < sizeof(list); i++)
        accu += list[i];

    return accu;
}

int main(void)
{
    int a[4] = {0, 1, 2, 3};

    printf("%d\n", sum(a));

    return 0;
}

```

that would be utterly restrictive... So, as an array **is** a pointer to its first element, what you usually do is to pass the array as an "array of indefinite size" to gain flexibility at the cost of "losing" the sizeof() operator.

Arrays are pointers, the thing is that the brackets notation can be used to mean two different things. I myself never use "a[]"; either brackets when declaring and allocating a stack array or pointer notation for everything else. That way I always know what I'm doing.

---

### Post by MadCow108 on 2010-02-10
> **maraldi said:**
> int *array and int array[] have the identical meaning only when used in a function heading or prototype. Both mean that array is a pointer to int.
The notations are not equivalent in any other context.

this is exactly the confusing part I meant.
There are two ways of writing the same in one context but in any other context the meaning of each variant is different.

This repeatedly breaks programs because people assume the in declaration [] mean the same as in all other contexts but it doesn't.

The designers should have allowed only the * syntax stating that all arrays decay into pointers when passed to another functions.
Allowing both just introduces countless bugs.

---

### Post by akshayy on 2010-02-10
If you ask me, and my idea for learning pointers is practice.
Implement binary tree, linked lists, stacks, general trees, hashing, some more data structures etc using Pointers. You will get the hang of it. Use recursion also. In GUI programming, there will be call backs for learning function pointers. Also in Signals in unix API.
This is how I learnt as CS student.

And for your original question.
The Include in C++ does not really include the contents of the file. The compiler just watches it while processing! Means only behavior as if they were literally included and part of the source file.

---

### Post by CptPicard on 2010-02-10
I guess this demonstrates well why I believe the confusion over pointers is totally unnecessary *and* would be remedied by learning to program in a more high-level language. If someone is going to have to learn algorithmics and data structure implementations *while* struggling with a concept like pointers, it is going to be slower going than learning the former in a higher-level language, and later on, when the ideas of "indirect reference" and "array index" and so on are ingrained, just swapping pointers for them.

---

### Post by dwhitney67 on 2010-02-10
> **CptPicard said:**
> If someone is going to have to learn algorithmics and data structure implementations *while* struggling with a concept like pointers...
Most C/C++ programmers don't immediately jump into algorithmic programming.  They learn the basics first.  It is whether they succeed at the basics or not that will determine their ability to solve more complex problems.

It bemuses me when someone, who doesn't know jack about a programming language, immediately wants to begin developing a game or other complex application without comprehending the fundamentals, nor the full features of the language.  I'm not referring to you, CptPicard, but to the OP.

---

### Post by Ravenshade on 2010-02-10
matthew.ball

I respectfully disagree. Lets leave it at that. 

maraldi

That's a good description I guess. I haven't found a use for them in the program I'm writing (yet) and it seems by your explanation they're not good for pointing to classes... but rather as others have said and the tutorial the memory space itself. I don't yet have a reason to summon the actual memory (i.e if I figured out what to use the pointer for in my program, would it make my program run better? As yet that's a no because it's a relatively simple program. This is mainly because I haven't used an array yet)

I'll still be practicing them however ^_^

MadCow

You're absolutely right, for a beginner (complete newb) this is very confusing, hence the ceaseless questions and I thank you and everyone else for their help and patience including those that lost said patience. 

Akshayy 

O_O Good job I'm not using the include function for that then, it most definitely does not do the same as PHP. Excellent definition. 

dwhitney

Welcome back to the thread ^_^.

---

### Post by akvino on 2010-02-10
> **nvteighen said:**
> Uh...


Another subtility is that arrays and pointers are that close to eachother (if not the same) that you can interchange them. An array works as a pointer to the first element of an allocated region of memory, so that a[i] and *(a + i) are the same. But in C++ you better use std::vectors rather than C-like arrays.



Why do you suggest use of vectors over use of array? Vector has way more overhead than array. If anything Vector usage should be determined on its application/performance requirements, otherwise it's better to use arrays. :-\"

---

### Post by CptPicard on 2010-02-10
> **akvino said:**
>  Vector has way more overhead than array.

Not that I've ever tested (I tend to use vectors unless I specifically know I always have fixed n units of something) but I always was under the impression that a std::vector template pretty much reduces to an array? (Maybe there's some extra bounds-checking...)

---

### Post by akvino on 2010-02-10
> **Ravenshade said:**
> matthew.ball

I respectfully disagree. Lets leave it at that. 

maraldi

That's a good description I guess. I haven't found a use for them in the program I'm writing (yet) and it seems by your explanation they're not good for pointing to classes... but rather as others have said and the tutorial the memory space itself. I don't yet have a reason to summon the actual memory (i.e if I figured out what to use the pointer for in my program, would it make my program run better? As yet that's a no because it's a relatively simple program. This is mainly because I haven't used an array yet)

I'll still be practicing them however ^_^

MadCow

You're absolutely right, for a beginner (complete newb) this is very confusing, hence the ceaseless questions and I thank you and everyone else for their help and patience including those that lost said patience. 

Akshayy 

O_O Good job I'm not using the include function for that then, it most definitely does not do the same as PHP. Excellent definition. 

dwhitney

Welcome back to the thread ^_^.


PHP Classes / Inheritance are similar to C++ Classes/ Inheritance as a design pattern, but applying classes in C++ is very different from applying classes in PHP. You have to know when to use operator overload, create and use destructors, "Virtual Class and Virtual Function" have different meaning, and creating Singleton or Abstract Class requires application of some very explicit rules in application which are totally different on how PHP handles, or tries to handle Singleton or Abstract Classes.

---

### Post by akvino on 2010-02-10
> **CptPicard said:**
> Not that I've ever tested (I tend to use vectors unless I specifically know I always have fixed n units of something) but I always was under the impression that a std::vector template pretty much reduces to an array? (Maybe there's some extra bounds-checking...)

No, vector is 'dynamic array' as a data structure. That means when you erase an element, pending on where you erased it, dynamic array will restructure, meaning shuffle its elements.

---

### Post by Ravenshade on 2010-02-10
I agree, scripting and c++ should never be comparable >_< I think I'll compare things that I'm more comfortable with now (like CSS and HTML)

---

### Post by MadCow108 on 2010-02-10
vectors are effectively just as fast as arrays.
They need minimal more time allocating, as its on heap and not on stack.
and they have an extra check when inserting but this is zero overhead in most cases because a fixed size array needs this too (or else security bug).
Also with modern branch prediction in cpu's this is no issue at all.

Accessing elements is just as fast.

Erasing elements does shuffle the vector but only if you erase an element form the start or middle.
If you need to do that you don't use vectors and you don't use arrays, you use deque's, list's or map's! 

If you really want an vector with a "hole" in the middle, just all the destructor of the element by hand instead of over the remove member function. This is then equivalent in speed to a normal array. (Of course in both cases you have to handle the "hole" in every further operation which is rather stupid design)

Ergo:
In C++ always use vectors for normal application code, I challenge you to show any significant performance drawbacks.
Arrays have their use in heavy numerical calculations where every cycle counts but these things are usually done with external libraries anyway. And if not then you use a fixed size array class like the boost or TR1 array.

---

### Post by akvino on 2010-02-10
> **MadCow108 said:**
> vectors are effectively just as fast as arrays.
They need minimal more time allocating, as its on heap and not on stack.
and they have an extra check when inserting but this is zero overhead in most cases because a fixed size array needs this too (or else security bug).
Also with modern branch prediction in cpu's this is no issue at all.

Accessing elements is just as fast.

Erasing elements does shuffle the vector but only if you erase an element form the start or middle.
If you need to do that you don't use vectors and you don't use arrays, you use deque's, list's or map's! 

If you really want an vector with a "hole" in the middle, just all the destructor of the element by hand instead of over the remove member function. This is then equivalent in speed to a normal array. (Of course in both cases you have to handle the "hole" in every further operation which is rather stupid design)

Ergo:
In C++ always use vectors for normal application code, I challenge you to show any significant performance drawbacks.
Arrays have their use in heavy numerical calculations where every cycle counts but these things are usually done with external libraries anyway. And if not then you use a fixed size array class like the boost or TR1 array.


[i]
Vectors are inefficient at removing or inserting elements other than at the end. Such operations have O(n) (see Big-O notation) complexity compared with O(1) for linked-lists. This is offset by the speed of access - access to a random element in a vector is of complexity O(1) compared with O(n) for general linked-lists and O(log n) for link-trees.[/i]

[http://en.wikipedia.org/wiki/Vector_%28C%2B%2B%29](http://en.wikipedia.org/wiki/Vector_%28C%2B%2B%29)

---

### Post by CptPicard on 2010-02-10
> **akvino said:**
> No, vector is 'dynamic array' as a data structure. That means when you erase an element, pending on where you erased it, dynamic array will restructure, meaning shuffle its elements.

Sure, but you'll have to do a rearrangement/reallocation manually in that situation as well if you use a plain array. I fail to see where the particular, vector-specific overhead is. You've got to compare operation for operation...

---

### Post by MadCow108 on 2010-02-10
> **akvino said:**
> [i]
Vectors are inefficient at removing or inserting elements other than at the end. Such operations have O(n) (see Big-O notation) complexity compared with O(1) for linked-lists. This is offset by the speed of access - access to a random element in a vector is of complexity O(1) compared with O(n) for general linked-lists and O(log n) for link-trees.[/i]

[http://en.wikipedia.org/wiki/Vector_%28C%2B%2B%29](http://en.wikipedia.org/wiki/Vector_%28C%2B%2B%29)

I guess you should go over data structures again.

This is valid for any linear blocked memory data structure not just for vectors. A stack array is a such a structure too.

---

### Post by akvino on 2010-02-10
> **MadCow108 said:**
> I guess you should go over data structures again.

This is valid for any blocked memory data structure not jsut for vectors. A stack array is a such a structure too.

I guess given the literal interpretation of the statement above you can say it is the same for arrays, but there is a bit more to Vectors than it meets the eye. Vector will adjust its size and shuffle elements, and this is not just on erasing but appending too. On top of it, adding more members to the vector results in additional re-copy of the Vector, with yet new shuffle. 

Array is static, no changes after its allocation. 

My complaint was that you suggested 'always use vectors', vs. use vectors where speed and performance do not count.

---

### Post by CptPicard on 2010-02-10
You're not getting it, akvino. An array behaves just as badly in insertion/deletion, you just have to write the code for it yourself.

A vector is under the hood an array, with the code you'd have to write...

---

### Post by MadCow108 on 2010-02-10
vector does not shuffle its elements all the time it does that on request (just like a stack array)
it resizes only when its to small. This means you choose a to small starting size. A stack array just crashes in this case! This is hardly better.

My suggestion still stands.
Always use vectors (or fixed size dynamic arrays to enforce a certain design)!
I say that as someone who has implemented various vectors and am working in the field of high performance computing.
But if you like I adapt it:
Always use vectors except you want to enforce a design with fixed size buffers (then use higher level fixed size arrays but not stack arrays) except you can prove by extensive profiling that the vector is to slow. Then check if you are using the right data structure.  If that is proven(!) consider redesigning your software there is probably something wrong.
When even that does not hold use your stack arrays for the negligible performance increase you get at the cost of development speed, safety and reusablity.

But I also give you one point, using C++ STL vectors (and STL in general) will increase code size and compiling time.
If this is an issue don't use the STL (but even then I recommend implementing a )higher level data structure which is less generic (like void pointer array/vector)

---

### Post by akvino on 2010-02-10
> **CptPicard said:**
> You're not getting it, akvino. An array behaves just as badly in insertion/deletion, you just have to write the code for it yourself.

A vector is under the hood an array, with the code you'd have to write...

A vector is under a hood an array, but you have to keep in mind, when you delete, or add elements to it, you have additional CPU and Memory overhead which result in slower execution than with the array. 

This is fine, if you understand what it does, and how it does it, and you are not competing for every CPU cycle, otherwise try to use array if you can. 

It is more efficient to allocate BIG array with unused elements at the compile time, than expect Vector to handle dynamical allocation for additional members of the Vector. 

If you ever apply for a job in Trading industry you better not tell them to use 'Vector' as you please.:!:

---

### Post by akvino on 2010-02-10
> **MadCow108 said:**
> 

My suggestion still stands.
Always use vectors (or fixed size dynamic arrays to enforce a certain design)!
I say that as someone who has implemented various vectors and am working in the field of high performance computing.



Ouch... 

I wrote dynamic arrays at my BSCS Data Structures class... I know how Vector grows, and shrinks. 

Tell me if you have vector of 50 elements and you want to add another 60, what happens?

If you have a vector of 50 elements and you delete 20 from random locations in the vector, what happens?


Then tell me what happens if you have array[120], with 50 allocated elements and add another 60 - what happens?

If you have an array[120] with 50 elements in it, and you delete 20 from it, what happens?

---

### Post by dwhitney67 on 2010-02-10
> **akvino said:**
> Ouch... 

I wrote dynamic arrays at my BSCS Data Structures class... I know how Vector grows, and shrinks. 

Tell me if you have vector of 50 elements and you want to add another 60, what happens?

If you have a vector of 50 elements and you delete 20 from random locations in the vector, what happens?


Then tell me what happens if you have array[120], with 50 allocated elements and add another 60 - what happens?

If you have an array[120] with 50 elements in it, and you delete 20 from it, what happens?

Your argument is fading...

Let's talk about apples and oranges.  Both are nearly round, and on occasion each comes in a green color.

If I knew that my vector would need to possibly store 120 elements, then I would size it as such.  Then when I have populated it with 50 elements, and then need to add 20 more, or even 70 more, there's no issue.  Similar to the scenario you presented with the array.

If you have an array of size 50, and need to add another 20 elements, well then you are stuck with reallocating the memory and copying over the contents. (you may not need to do this manually, depending on the data stored in the array... realloc can operate on simple data).

Now, would I use a vector in an embedded application... probably not, unless I could guarantee that it's size would not change throughout the lifetime of the application.  Allocating memory is a slow process, and may require the copying of data... regardless if using a vector or an array.

---

### Post by CptPicard on 2010-02-10
> **akvino said:**
> A vector is under a hood an array, but you have to keep in mind, when you delete, or add elements to it, you have additional CPU and Memory overhead which result in slower execution than with the array.

How exactly does a static array make additions or deletions any faster than on a vector?

I am getting the feel that you're again not comparing the same operations -- you're allowing for some special more efficient implementation on the static array in some specific case that is perfectly implementable on a vector as well, but you choose to compare to a "one by one" deletion or whatever instead.

---

### Post by akvino on 2010-02-10
> **dwhitney67 said:**
> Your argument is fading...

Let's talk about apples and oranges.  Both are nearly round, and on occasion each comes in a green color.

If I knew that my vector would need to possibly store 120 elements, then I would size it as such.  Then when I have populated it with 50 elements, and then need to add 20 more, or even 70 more, there's no issue.  Similar to the scenario you presented with the array.

If you have an array of size 50, and need to add another 20 elements, well then you are stuck with reallocating the memory and copying over the contents. (you may not need to do this manually, depending on the data stored in the array... realloc can operate on simple data).

Now, would I use a vector in an embedded application... probably not, unless I could guarantee that it's size would not change throughout the lifetime of the application.  Allocating memory is a slow process, and may require the copying of data... regardless if using a vector or an array.


My argument is not against Vector, nor Array. My argument is to use Vector where it fits vs. using it all the time.

---

### Post by CptPicard on 2010-02-10
> **akvino said:**
> My argument is not against Vector, nor Array. My argument is to use Vector where it fits vs. using it all the time.

Which it does essentially all the time. Unless you need an absolute guarantee against resizing (as per dwhitney67) and would prefer an overflow, or something like that.

---

### Post by akvino on 2010-02-10
> **CptPicard said:**
> How exactly does a static array make additions or deletions any faster than on a vector?

I am getting the feel that you're again not comparing the same operations -- you're allowing for some special more efficient implementation on the static array in some specific case that is perfectly implementable on a vector as well, but you choose to compare to a "one by one" deletion or whatever instead.

Here we go again. If I wanted to write high performance application I would use array. 
If I wanted to write Social Networking code, where you could add/delete your friends, then I would use Vector.

The point being, don't assume that Vector is the best solution all the time, and it should be used based on requirements and not all the time.

---

### Post by CptPicard on 2010-02-10
> **akvino said:**
> 
The point being, don't assume that Vector is the best solution all the time, and it should be used based on requirements and not all the time.

I would be using it "essentially all the time" as I have not yet managed to get out of you a good example of why it is bad to use it, and why a static array is more efficient. In particular, in an asymptotic sense, their behaviour is the same, if you allow for same implementations of algorithms on them, which you aren't doing, it seems.

EDIT: There *may* be special cases where the store management discipline of the standard vector is suboptimal, but 1) that stuff can be controlled, 2) those are rather special cases, which do not fall under "essentially all the time".

---

### Post by Ravenshade on 2010-02-10
Quick question, would you guys mind defining what a high performance application is?

---

### Post by akvino on 2010-02-10
> **Ravenshade said:**
> Quick question, would you guys mind defining what a high performance application is?

In electronic financial markets, algorithmic trading or automated trading, also known as algo trading, black-box trading or robo trading, is the use of computer programs for entering trading orders with the computer algorithm deciding on aspects of the order such as the timing, price, or quantity of the order, or in many cases initiating the order without human intervention.


*Competition is developing among exchanges for the fastest processing times for completing trades. **For example the London Stock Exchange, in June 2007, started a new system called TradElect, which promises an average 10 millisecond turnaround time from placing an order to final confirmation, and can process 3,000 orders per second.[30]. This speed would already be considered a quaint benchmark as competitive exchanges now offer 3 millisecond turnaround times in the US.***



cptPicard - I hope this answers your question of array vs. vector preferences.


[http://en.wikipedia.org/wiki/Algorithmic_trading](http://en.wikipedia.org/wiki/Algorithmic_trading)

---

### Post by CptPicard on 2010-02-10
If I were hiring for algorithmic trading and using this as some kind of a test question, I would be much more concerned about an initial explanation of the matter along the lines of post #46 than an over-use of the vector... :p

On the other hand, if I were trying to get a job somewhere where they don't know how to pre-size their vectors and take all the same storage-management actions *they would have to take with arrays too* in situations as described om #53, I would look elsewhere...

No, it didn't answer my questions... "algorithmic trading" has nothing to do with the behaviour of vector vs. array as far as this discussion is concerned.

---

### Post by akvino on 2010-02-10
> **CptPicard said:**
> If I were hiring for algorithmic trading and using this as some kind of a test question, I would be much more concerned about an initial explanation of the matter along the lines of post #46 than an over-use of the vector... :p

On the other hand, if I were trying to get a job somewhere where they don't know how to pre-size their vectors and take all the same storage-management actions *they would have to take with arrays too* in situations as described om #53, I would look elsewhere...

No, it didn't answer my questions... "algorithmic trading" has nothing to do with the behaviour of vector vs. array as far as this discussion is concerned.

Vector sizes according to the number of elements in it. If you add 60 elements to Vector size 50, it will allocate new memory on the Heap and reserve enough memory for 110 elements, and copy over 50 existing elements, then add additional 60 elements. All of this is overhead, not just memory and CPU, but time. The larger the Vector, the larger the overhead. When we are talking about transactions taking less than 10 milliseconds this could cost you a lot.

This is runtime vs. compile time.

---

### Post by CptPicard on 2010-02-10
Then why aren't you sizing the vector accordingly? It's not like a static array gives you anything for free here, either.

I'm not interested in microseconds, this is simple asymptotic behaviour which doesn't need units to be significant...

---

### Post by akvino on 2010-02-10
> **CptPicard said:**
> Then why aren't you sizing the vector accordingly? It's not like a static array gives you anything for free here, either.

I'm not interested in microseconds, this is simple asymptotic behaviour which doesn't need units to be significant...

Again vector operates in runtime. It is not just adding elements, but deleting too. Once again, vectors purpose is to dynamically allocate enough memory to accommodate all elements.

If I have to size properly vector vs. array for high performance application, I chose sizing array since it is not runtime, and I do not have to worry about additional overhead if some data is deleted or added. 

One more time, you can't bluntly state - use vectors all the time, especially if you don't understand what vector does upon certain actions.

AND "I'm not interested in microseconds, this is simple asymptotic behaviour which doesn't need units to be significant" - **in high performance applications microseconds COUNT.**

---

### Post by MadCow108 on 2010-02-10
Just to clear out some possible confusion on your side:
do you know you can set the size of a vector at compile time?
its as easy as this:
```

vector<int> vec;
vec.reserve(1000); // here you have less speed than stack array, because stack allocations are faster
... // but all further operations are identical(modulo constant in insertion/deletion) in speed

```

If your looking for upper bounds like you're suggesting, then neither the vector nor the fixed size vector are relevant.
**Both** don't provide upper bounds lower than O(N) for all operations (because both are essentially the same, a linear memory block!)

for a better upper bound a tree like structure with O(logN) for all operations is better suited (although also this does not provide same speed for all elements, just an upper bound, so neither of structure  mentioned here are suitable for real-time programming)

Runtime or not runtime is **totally irrelevant** because the vector can be compile time sized as well, it just has the possibility to grow.
The vector will always be a (negligible) **constant** slower than the array in **all** operations.

To sum the operations (upper bound notation) on some chosen structures (there are a lot more, most noteworthy but complicated: fibonacci heaps):
Inserting and deleting in random location,:
  vector: O(N)
  static array: O(N)
  tree: O(logN)
  list: O(1) (not counting iterating to the element)
Inserting deleting at end:
  vector: O(1)
  static array: O(1)
  tree: O(logN)
  list: O(1)
Access to random element:
  vector: O(1)
  static array: O(1)
  tree: O(logN)
  list: O(N)

notice something? yes vector and array are the same! 

If you really believe your right, please provide proof.
Then I better go but to school because all I've been doing the last 10 years was wrong :(
Also I bet you could get a few groundbreaking publications out of implementing a static array with constant time random deletion and insertion, basically all books have to be rewritten :)

I suggest implementing your example from before page once, you'll see you need to do the same for the static array as the vector does under the hood (and probably better than you)

---

### Post by dwhitney67 on 2010-02-10
> **akvino said:**
> 
If I have to size properly vector vs. array for high performance application, I chose sizing array since it is not runtime, and I do not have to worry about additional overhead if some data is deleted or added.
I understand what you are arguing, but in real-time applications, if a vector is used, it is pre-sized during the initialization of the application to the desired size; similar to an array, should the desired size of the array not be known until runtime.

It is after the initialization of the application that one should refrain from further allocations from the heap.  This applies to fidgeting with the size of a vector, reallocating an array via the use of malloc(), calloc(), or realloc().  They're all considered no-no's in a real-time app.  Because of the hidden nature of allocations within STL containers, oftentimes their use is forbidden in real-time applications.

P.S.  Stock trading apps are coming of age; but you should realize that real-time applications have been around for decades, and the principles have remained the same.  A missile guidance system probably could outshine the best-of-the-best trading system.

---

### Post by CptPicard on 2010-02-10
MadCow and dwhitney67 already put it well, but...

> **akvino said:**
> Once again, vectors purpose is to dynamically allocate enough memory to accommodate all elements.

Once again, if you didn't do that with an array when a need arises, you'd crash. This is not a preferable outcome in your super fast stock trading app.

> 
If I have to size properly vector vs. array for high performance application, I chose sizing array since it is not runtime, and *I do not have to worry* about additional overhead if some data is deleted or added. 


Why do you not have to worry? Are you all of a sudden prescient about all future accesses when using arrays? And again, why aren't you giving your vector sufficient size to begin with if you had that kind of clairvoyance?

> 
One more time, you can't bluntly state - use vectors all the time, especially if you don't understand what vector does upon certain actions.

Oh, I know full well what *both* arrays and vectors have to do upon certain actions (you just ignore them in the array case), and therefore, I'm quite happy using vectors pretty much everywhere -- even the asm code from vectors shouldn't be too contrived, as it is in the end essentially pointer arithmetic into a contiguous block of RAM, even coming from vector. But this is not the point of the discussion, as I will note below.

You, on the other hand, can't bluntly lecture to me about *microseconds in bold* if your issue obviously is that you don't know you don't have to reallocate your vector n times when you're pushing all your elements individually ;)

> 
AND "I'm not interested in microseconds, this is simple asymptotic behaviour which doesn't need units to be significant" - **in high performance applications microseconds COUNT.**

Your statement about vectors being inferior to arrays because of insertion/deletion performance due to rearrangement/reallocation is strictly in the domain of asymptotic behaviour, so this is why I am not interested in the microseconds. I am interested in why *you* feel the case is as you claim, not whether some algorithmic traders find the constant factors/terms of vector operations too slow (we don't have any evidence of this here, mind you, just your claim).

Don't shift your argument.

---

### Post by akvino on 2010-02-10
> **CptPicard said:**
> 

Your statement about vectors being inferior to arrays because of insertion/deletion performance due to rearrangement/reallocation is strictly in the domain of asymptotic behaviour, so this is why I am not interested in the microseconds. I am interested in why *you* feel the case is as you claim, not whether some algorithmic traders find the constant factors/terms of vector operations too slow (we don't have any evidence of this here, mind you, just your claim).

Don't shift your argument.

I never said Vectors are inferior to Arrays, I simply noted that one shouldn't ALWAYS use Vectors as the choice should be made based on the application and requirements, not developers preference.

---

### Post by akvino on 2010-02-10
> **dwhitney67 said:**
> I understand what you are arguing, but in real-time applications, if a vector is used, it is pre-sized during the initialization of the application to the desired size; similar to an array, should the desired size of the array not be known until runtime.

It is after the initialization of the application that one should refrain from further allocations from the heap.  This applies to fidgeting with the size of a vector, reallocating an array via the use of malloc(), calloc(), or realloc().  They're all considered no-no's in a real-time app.  Because of the hidden nature of allocations within STL containers, oftentimes their use is forbidden in real-time applications.

P.S.  Stock trading apps are coming of age; but you should realize that real-time applications have been around for decades, and the principles have remained the same.  A missile guidance system probably could outshine the best-of-the-best trading system.


Agreed.

---

### Post by MadCow108 on 2010-02-10
> **akvino said:**
> I never said Vectors are inferior to Arrays, I simply noted that one shouldn't ALWAYS use Vectors as the choice should be made based on the application and requirements, not developers preference.

Ok, always is a bit strong word. But I have mentioned cases where you should not use them instead of C arrays and dwhitney added another good one. And for the beginners (with which this forum is mainly populated) always is the best word, they save a lot of C "nonsense" which slows down the learning process and vector is a good starting point into learning the STL.

The important part to me is that you understand that your argument against vectors is wrong.
That vectors have the ability to grow, does not make them slower or structurally different to static stack arrays just the location where the memory is allocated from differs. Even when using iterators and STL algorithms has no speed penalty as its all resolved at compile time to simple pointer operations.

But to please you the next standard will have STL fixed sized arrays (the reason is not speed but already mentioned design issues with vector and you just have to kick out a few lines of code from vector).
These are then identical to stack arrays in every respect except the memory allocation (which should be avoided in the performance hotspots anyway).

---

### Post by akvino on 2010-02-10
> **MadCow108 said:**
> 
The important part to me is that you understand that your argument against vectors is wrong.
That vectors have the ability to grow, does not make them slower or structurally different to static stack arrays just the location where the memory is allocated from differs. 


Here we go again! 

MadCow you know c++ way better than I do. :-) I am learning it back.

---

### Post by nvteighen on 2010-02-10
> **akvino said:**
> Why do you suggest use of vectors over use of array? Vector has way more overhead than array. If anything Vector usage should be determined on its application/performance requirements, otherwise it's better to use arrays. :-\"

Although it's been already discussed at large, I'll answer why **I** suggested vectors over arrays.

I don't care about performance... or well, I do care but in a second thought and only when a human-percievable drawback appears at some code. What I do care is for placing my ideas the best I can in some code. But keep in mind I'm actually not a "normal" programmer... I program for the linguistic interest it has.

But that "linguistic interest" has driven me into being mindful of what data structures, considered as linguistic structures, are the most suited to the human's way of thinking. And a vector has it all to beat an array... It represents much better the idea of a list of things you can resize at will just focusing on the elements, while in order to master the C array you need to know that it is implemented as a pointer to the first element in a certain region of memory... otherwise you'll get confused on why the sizeof() doesn't work in some situations, why segfaults are possible, etc. etc. etc. In other words, in order to map the idea of a "list", you have to keep an eye on stuff that doesn't take part in the concept, but in the way the concept is possible to be represented.

(And C++ vectors aren't actually that way more abstracted... they are type-uniform, for instance)

That's why I suggested vectors... so it's funny to see that you guys were heatedly discussing Big-O notations because of my totally Linguistics-based suggestion... :P

---

### Post by akshayy on 2010-02-11
Don't real time stuff use C, ASM ?

---

### Post by Zugzwang on 2010-02-11
> **akshayy said:**
> Don't real time stuff use C, ASM ?

Not necessarily. Consider games, for example. That's "real time stuff" and they are often written in C++.

---

### Post by Vox754 on 2010-02-11
> **nvteighen said:**
> ...
That's why I suggested vectors... so it's funny to see that you guys were heatedly discussing Big-O notations because of my totally Linguistics-based suggestion... :P
Yeah, this thread was just a big, convoluted misunderstanding.

Basically, you said "use vectors" (because they are high-level).
akvino said "don't always use vectors, use arrays"

That's it people, move on.

---

### Post by CptPicard on 2010-02-11
Well, games just need to be "fast enough". Hard real-time stuff is a bit different; you really need to be able to guarantee an execution time to a tight bound or bad stuff happens.

That said, an STL vector is simple enough that if your real-time guarantees are not strict enough to require an ability to nearly count CPU instructions, it should be sufficiently real-time safe in the sense that its behaviour is at all times completely predictable to a programmer, at least in a case where you don't just obliviously push_back things onto it while not knowing how much is allocated.

This is why I was so completely at odds with akvino's argument -- "surprising" reallocations simply don't happen any more than they do on a raw array.

---

