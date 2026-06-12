---
title: "Did you noticed mental upper limit for code size?"
date: 2006-12-19
forum: Programming Talk
---

### Post by pmasiar on 2006-12-19
As we are discussing python vs java vs C++ etc, I was thinking about big projects in python. I cannot say I implemented something really big in python - mostly quick side projects. Nothing like 40MB of source code we had in my previous company... :-)

I had following interesting observation on upper limit of how much code I can hold in my mind's "RAM".

I am kinda lazy to start new module for every new function, so if new function is related to other functions in this module, I tend to hold on surgery before separating functions to multiple modules. Of course I split right away if it is obviously separate functionality, but if not obvious, I may as well to put new function next to existing similar one. For some values of similar.

As code grows, I can add new functions and add functionality, and all is fine. I am perfectly capable to keep in memory up to 60K of code (recently VB and PROGRESS 4GL, I did not actively looked for this upper limit  years ago when I was doing big C projects), but python (and perl) code is so dense (activities per 100 lines) that I am **not** capable to handle 60K of say python code as a unit - when it is 20-25K, I need to restructure it, swap out big chunk of it out as library so I can use it as API without internal details. 

Do you guys noticed something similar? Or my upper limit is less now because i am more experienced (and older)? :-)

---

### Post by jsandys on 2006-12-19
You definately want to chunk your python code into small modules and use objects and methods instead of lots of functions.

I could manage a large LISP program because it was broken into 120 object modules, each by itself could be managed.  In ancient times I could write an memory filling Apple Basic program on my Apple ][e (32K), but writing that much code in assembly would give me a headache.

---

### Post by Wybiral on 2006-12-19
In regards to C++ vs Python (seems more like wybiral vs pmasiar)...

Well, my main reason for saying that I prefer C++ for larger projects is that with C++, you have header files containing a declaration of all of the functions in the corresponding cpp file. This makes it very easy to locate a function, or to simply look up the param type it takes and what it returns.

When a project gets so large that one cannot remember all of the code (which isn't a problem for smaller, simple projects) then conventions like this become a very necessary thing. Also, while I love the way you can declare variables on-the-fly with python, C++ requires you to declare them, so if you find the use of an ambiguous variable somewhere, you can simply look for it's declaration as opposed to having to trace it back to its source (and there could be multiple sources of declaration, so this gets very challenging in python).

Another point to bring up is type safety... When a project does get so large that memorizing the code becomes impossible, the use of functions gets very complicated, especially with classes and operator overloads. So, in python I could have a function like this...

```

def dp(a, b):
   return a.x*b.x + a.y*b.y + a.z*b.z

```

Now, seeing how I know what a and b are (they are vectors, this is a dot product function) this makes sense, but when you aren't sure what a and b are... x, y, and z could be vectors in the class objects a and b for all we know, and this could just be some strange algorithm for adding and multiplying six vectors using operator overloads... unlikely, but this code doesn't help us at all. Not having to specify a type in the function declaration can often obscure the purpose of the function. That function takes in two 3d vectors as parameters and returns a scalar, but it doesn't do a good job of representing it. In C++ however, it is very clear...

```

float dp(vec3 a, vec3 b)
    {return a.x*b.x + a.y*b.y + a.z*b.z;}

```

I know just from looking at it that it takes two 3d vectors as parameters and returns a floating point value. And it doesn't really require that much extra code just to have this kind of security. Naturally, I wouldn't call the function "dp" but you get the point. And suppose I don't know that "vec3" is a 3d vector class, all I have to do is look at my headers for it's declaration, you don't have those kind of conventions in python.

Sure, all of these problems can be solved using better commenting and more descriptive naming conventions, but what if you are working off of someone else's code? You are most likely not going to have a clue what code does what, so you rely on these conventions to figure it out.

Now, with this said, big projects ARE possible in python, I just think for those big projects, C++ is a better solution.

---

### Post by dwblas on 2006-12-21
> You definitely want to chunk your python code into small modulesThe rule of thumb, for any language really, is that you want each function/module to be able to fit on one screen.  If you use that as a rule of them, then your modules will actually be 2 or 3 screen's length, which is manageable by our tiny brains.  It's also much easier to debug and modify as you are dealing with reasonable-sized code chunks.

---

### Post by Wybiral on 2006-12-21
> The rule of thumb, for any language really, is that you want each function/module to be able to fit on one screen. If you use that as a rule of them, then your modules will actually be 2 or 3 screen's length, which is manageable by our tiny brains. It's also much easier to debug and modify as you are dealing with reasonable-sized code chunks.

I'm not sure that I agree that it can be regulated... With very large projects, especially involving very complex algorithms... Laying out your modules in 2-3 function sizes with each being one screen in height is going to get really messy... You'll end up with 100's of modules and sorting through them wont be any easier than one file with 10-20 functions (provided they are properly arranged within the file).

I can see how that would work with small projects, but I think it would be too much for large ones.

Personally, I think modules should be divided by topic... If you're writing a module to handle all of your complex math routines, it probably shouldn't be broken up into tiny pieces, it should just be your complex_math_routine module.

---

### Post by slavik on 2006-12-22
my limit is to understand what needs to be done and what structures I can use, the syntax and little things can be reacreated ... this way, I have the entire C++ implementation of the huffman algorithm in my head. :)

---

### Post by lnostdal on 2006-12-22
(i haven't really read the OPs question or the thread itself .. but i feel like typing something because i'm stuck with a boring (low-level) bug ATM)

whenever something starts to get too complicated i start with wishfull thinking; i pretend my language has support for features it does not - then specify my problem/program as data for this new language

then i try to build a language "up to" this problem-domain - where my wishfull program-code also resides, so i can specify problems like the one i have now in that new, more suitable and natural language

when people talk about problems ("profession-language"? #1) of a certain type they use a specific language to specify the details of the current problem; this makes solving (communicating) hard problems - or problems the current language has poor support for, much easier

this is called "bottom up programming": [http://www.paulgraham.com/progbot.html](http://www.paulgraham.com/progbot.html) .. one builds languages on each new foundation at the bottom "up to" the problem-domain .. well; what i'm trying to say is that one does not need to keep all the layers from bottom to the point we are now in our heads at the same time using this style; one mostly need to think about the immediate layer underneath oneself or the problem one is currently working on .. a good foundation makes the task manageable

#1: i'm not a native english speaker :}

---

### Post by Wybiral on 2006-12-22
"bottom up programming" works very well, I agree. It's usually easier to write smaller, more modular solutions to a bigger problem than it is to solve the big problem from scratch. A good language should allow for this. To solve problems easily, a language should be highly modular and easy to expand. 

That's really why I favor C++ and Python over a lot of languages... Object oriented features like classes, abstraction, and operator overloads allow me to easily visualize the problem in a human readable way. Every level I write in the abstract layers is easy to read and modify.

I especially like C++ because when it comes down to debugging... You have all of your header files as a sort of dictionary of the functions for those solutions you've forgotten how you implemented. So, debugging large projects is just a matter of checking the appropriate header for the function declaration and then you know the in/out and different type definitions for that function/overload. You also know the appropriate .cpp file that corresponds to that .h file. This is a very quick and easy way to locate something and debug.

---

### Post by lloyd mcclendon on 2006-12-23
the big thing for me has been trying to keep methods short, less than 10 lines.  2 blank lines between them and a nice little 3 or 4 line comment on what it is, why it is here, and sometimes if necessary a little bit on how it works.

i have some files that have a bunch of small pieces, i open them up and can immediately tell that i was on point when i wrote it.  it just looks right.  if i see a big method i try to split it up, most of the time this is possible but not always.  i actually have a pretty complex algorithm in one project that is about 150 lines and for the life of me i can't make it better.

the nice thing about java web development is the layered archeticture thing.  i have 5 different packages, each class in a package is very similar to the rest in there.  a lot of times i'm able to use a layer supertype and just have pretty bare classes.  in one project i've got a rather large amount of artifacts but i'm really not afraid to add more.  python scripts to generate the skeleton have been my savior.

---

### Post by dwblas on 2006-12-24
> the big thing for me has been trying to keep methods short, less than 10 linesThat's pretty good.  It is my philosophy that the more experience someone has, the shorter the code bites become because you know that you will have to come back later and modify them or find a problem (in someone else's code of course).  Small modules greatly increase productivity.  It's a mindset like everything else, and if 150 lines is your worst, my hat is off to you.

---

