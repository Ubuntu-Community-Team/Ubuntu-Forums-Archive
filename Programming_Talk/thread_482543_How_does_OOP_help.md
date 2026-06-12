---
title: "How does OOP help?"
date: 2007-06-23
forum: Programming Talk
---

### Post by blah blah blah on 2007-06-23
Ever since I was introduced to C++ I've wondered what does OOP do to help?

---

### Post by DougB1958 on 2007-06-23
OOP supports design and programming habits (e.g., encapsulating related code and data together, coding abstract ideas in forms that can be used in many settings rather than recoded in slightly different forms, etc.) that improve code modularity and reusability. These things are very helpful for large or long-lived projects. On the other hand, for small projects, the design and programming habits of OOP impose overhead that isn't likely to pay for itself.

---

### Post by pmasiar on 2007-06-23
OOP allows to pack together data (object) and code (methods) and  define where objects of similar but different behavior (ie subclasses of same class) be substituted by each other, or inherit behavior from superclass.

---

### Post by blah blah blah on 2007-06-23
I can do those things as easily with non-opp code.

---

### Post by samjh on 2007-06-24
Show us a large example - something involving more than say 10,000 lines of code, excluding whitespaces and comments - that include the usage of multiple code libraries, and preferably includes a GUI.  Extract some code fragments from that example to show how you can achieve OOP using a non-OOP language easier or as easy as using an OOP language.

As said before, OOP is most beneficial in large and complex projects.  So using small examples are worthless.

I'd be very interested in seeing a demonstrated example from a complex, large project.

[EDIT]

Had to add some extra qualifiers due to disingenuous answers.

1. Cleanliness and ease of implementation must be part of the primary design consideration for the project.  ie. no OS kernels, firmware, or the like, which have other priorities.

2. Project must involve OO implementation using a non-OOP language.

3. A clear demonstration must be shown that the OO implementation using a non-OOP language is easier or as easy as, an implementation using an OOP language.

---

### Post by Tomosaur on 2007-06-24
OOP is simply a paradigm - you do not have to use it, but many (most?) programmers seem to prefer it. If you take a look at C, for example, you'll see that all of the work is done by procedures and functions. This is fine if you view your application as simply a set of instructions to perform some task.

Over time, however, people began to find that this approach wasn't flexible enough, and was inconvenient (although not impossible) to design and build large applications around. This is where the idea of objects comes in. Rather than looking at your code as a big list of instructions, if you say 'Well, all of this code here is based around a particular operation', then it's much easier to abstract, and thus much easier to design. It allows you to think about your code at a much, much higher level than procedural code does. Thus, for example, if you're writing say, a simple platform game, it is easier to think about the code in terms of Levels, Characters, Power-ups, Actions etc etc. If you're using procedural code, you're kind of forced into thinking about the code in terms of low level stuff like moving sprites around on screen, drawing levels, setting up events, and of course, the main game loop.

None of it REALLY matters that much, since even with OOP code, the end result (after compilation into machine code) is simply a big list of instructions. It doesn't make your programs better, and there's nothing you can do with OOP that you cannot do with procedural code. Many people just find OOP code easier to think about, design for, and maintain. Procedural code tends to be of a lower level, and thus can cause problems in large applications due to the sheer amount of detail the design process needs to cover.

It's all just a matter of preference really, but for large software, OOP certainly reigns supreme at the moment. Languages like C++ allow you to combine OOP and procedural, but you can 'kind of' emulate OOP in, for example, C. 

OOP-centric (some would say 'obsessed') languages like Java are incredibly easy to design for, but are 'less powerful' than less OOP-centric languages.

---

### Post by Choad on 2007-06-24
you can code procedurally in an oop language just fine

you cant code objects very well in a non oop language

simple as

---

### Post by tpg on 2007-06-24
> **samjh said:**
> Show us a large example - something involving more than say 10,000 lines of code, excluding whitespaces and comments - that include the usage of multiple code libraries, and preferably includes a GUI.
Isn't GNOME written using non-oop C? That's quite a big project.

---

### Post by Choad on 2007-06-24
> **tpg said:**
> Isn't GNOME written using non-oop C? That's quite a big project.
not to mention linux lol

---

### Post by samjh on 2007-06-24
> **tpg said:**
> Isn't GNOME written using non-oop C? That's quite a big project.You didn't comprehend my question.

I wanted a demonstration of a large complex project with OOP, where implementing it using a non-OOP language is as easy or easier than using an OOP language.

GNOME is written using C (because of GTK+), implementing its own object model, hence making it quasi-OO.  But I'm pretty sure that a comparable implementation using C++ probably would have resulted in cleaner code and usage.  Hence it doesn't answer my question.

[quote=Choad]not to mention linux lol[/quote]Yet again, didn't answer my question.

You have omitted the fact that Linux is an OS kernel, which is primarily the domain of C, due to its speed and portability.  Cleanliness or ease of implementation are secondary considerations for an OS kernel.

The GNOME example was a more relevant answer.

---

### Post by steve.horsley on 2007-06-24
The main way that OO helps is by containing details within sub-areas of a program, and preventing the need to know implementation details from leaking to other code. Imagine using a radio where you had to adjust the varicap voltage to 3.118 volts and select IF filter #2 to listen to your favourite radio station. Or a car where to start it, you have to adjust the cchoke to 2/3 and pump the accelerator three times before pressing the starter button. These are examples of internal implementation details leaking out unnecessarily to the user. These days, radios just have station buttons or a frequency dial) and cars don't require you to know what angle the butterfly vavles are set at - they just have a start button. OO in software allows you to think of software modules as components, and allows the creators to hide the details, containing them within that module, keeping as simple an interface to the users as possibble. Now, this can be done with non-oo languages, but the fact that the code and the state data don't come bundled together make it much harder to achieve this modularisation, and I think it becomes very much more likely that a project will end up with spaghetti like interdependencies between different parts that use much mode knowlege of how other parts of the project work.

---

### Post by amireldor on 2007-06-24
> **samjh said:**
> 
GNOME is written using C (because of GTK+), implementing its own object model, hence making it quasi-OO.


How do they do that? I mean, *"quasi-OO"* in C.
I consider myself a C++ programmer and not a C programmer so I have no idea how its done.

---

### Post by blah blah blah on 2007-06-24
> **samjh said:**
> Show us a large example - something involving more than say 10,000 lines of code, excluding whitespaces and comments - that include the usage of multiple code libraries, and preferably includes a GUI.  Extract some code fragments from that example to show how you can achieve OOP using a non-OOP language easier or as easy as using an OOP language.

As said before, OOP is most beneficial in large and complex projects.  So using small examples are worthless.

I'd be very interested in seeing a demonstrated example from a complex, large project.

[EDIT]

Had to add some extra qualifiers due to disingenuous answers.

1. Cleanliness and ease of implementation must be part of the primary design consideration for the project.  ie. no OS kernels, firmware, or the like, which have other priorities.

2. Project must involve OO implementation using a non-OOP language.

3. A clear demonstration must be shown that the OO implementation using a non-OOP language is easier or as easy as, an implementation using an OOP language.

I don't really have time for that.

> **steve.horsley said:**
> The main way that OO helps is by containing details within sub-areas of a program, and preventing the need to know implementation details from leaking to other code. Imagine using a radio where you had to adjust the varicap voltage to 3.118 volts and select IF filter #2 to listen to your favourite radio station. Or a car where to start it, you have to adjust the cchoke to 2/3 and pump the accelerator three times before pressing the starter button. These are examples of internal implementation details leaking out unnecessarily to the user. These days, radios just have station buttons or a frequency dial) and cars don't require you to know what angle the butterfly vavles are set at - they just have a start button. OO in software allows you to think of software modules as components, and allows the creators to hide the details, containing them within that module, keeping as simple an interface to the users as possibble. Now, this can be done with non-oo languages, but the fact that the code and the state data don't come bundled together make it much harder to achieve this modularisation, and I think it becomes very much more likely that a project will end up with spaghetti like interdependencies between different parts that use much mode knowlege of how other parts of the project work.

I can do that in non-OOP too.

---

### Post by samjh on 2007-06-24
> **lKyPN8xZQG said:**
> I can do that in non-OOP too.Give us all a demo.

I know it's possible, but it would be good to see how neatly it can be done (I mean that seriously, not sarcastically).

> **lousygarua said:**
> How do they do that? I mean, *"quasi-OO"* in C.
I consider myself a C++ programmer and not a C programmer so I have no idea how its done.I lack the skill to explain it.  Here's what the GNOME documentation has to say: [http://developer.gnome.org/doc/GGAD/cha-objects.html](http://developer.gnome.org/doc/GGAD/cha-objects.html)

---

### Post by kknd on 2007-06-24
OOP : "Divide and conquer".

Divide the problem and encapsulate the code. Its much clearer and less bug prone.

---

### Post by winch on 2007-06-24
> **samjh said:**
> Show us a large example - something involving more than say 10,000 lines of code, excluding whitespaces and comments - that include the usage of multiple code libraries, and preferably includes a GUI.  Extract some code fragments from that example to show how you can achieve OOP using a non-OOP language easier or as easy as using an OOP language.

This is just pushing the thread off topic. The whole point of an OOP language is to take the idiom of objects into the language and out of the code.

The same way iterators build looping through an array into the language.

```

for (i = 0; i < array.length; i++)
{
    print(array[i])
}
becomes
foreach (item in array)
{
    print(item)
}

```

The whole point of an OOP language is to make writing OOP code better (easier, faster, less bugs etc.) than a non OOP language. Unless you have fairly unique requirements or the OOP language is rubbish it is going to be easier to write OOP code in an OOP language, that's the point of OOP languages.

The OP was asking why use OOP in the first place which is a much harder question to answer.

---

### Post by blah blah blah on 2007-06-24
> **samjh said:**
> Give us all a demo.

I know it's possible, but it would be good to see how neatly it can be done (I mean that seriously, not sarcastically).

well, here goes:

Let's use a special langage were + is a combiner for either numbers or functions (for the sake of clearness) and letters as numbers or functions. Say you have this program:
```
Q+W+E+R+T+Y+U+I+O+P+A+S+D+F+G+H+J+K+L
```
You could abstract it like this:
```

(
Q+W+E+R+T+Y
+
U+I+O+P+A
)
+
(
S+D+F
+
G+H+J+K+L
)

```
or
```

Z = Q+W+E+R+T+Y
X = U+I+O+P+A
C = S+D+F
V = G+H+J+K+L
(Z+X)+(C+V)
```

I hope that made some sense.

---

### Post by Lster on 2007-06-24
> well, here goes:

Let's use a special langage were + is a combiner for either numbers or functions (for the sake of clearness) and letters as numbers or functions. Say you have this program:
Code:

Q+W+E+R+T+Y+U+I+O+P+A+S+D+F+G+H+J+K+L

You could abstract it like this:
Code:

(
Q+W+E+R+T+Y
+
U+I+O+P+A
)
+
(
S+D+F
+
G+H+J+K+L
)

or
Code:

Z = Q+W+E+R+T+Y
X = U+I+O+P+A
C = S+D+F
V = G+H+J+K+L
(Z+X)+(C+V)

I hope that made some sense.

Although I've programming in both for a while now, I've never thought of it like that - that is a really good way of putting it.

---

### Post by blah blah blah on 2007-06-24
> **Lster said:**
> Although I've programming in both for a while now, I've never thought of it like that - that is a really good way of putting it.

Thanks

---

### Post by aks44 on 2007-06-24
One big feature of OOP is inheritance, and the ability to manipulate an object without knowing its actual type (interfaces, virtual functions anyone?).

Implementing such a behaviour in a non-OOP language is of course possible, but it leads to things like the GTK+ "object model" (very interesting reading BTW, thanks samjh for the link). My eyes are still bleeding... :p

---

### Post by tturrisi on 2007-06-24
A friend who is one of the original painter developers explained this to me once:
He said,, "there's code, there's spaghetti code & there's oop".
Code, written any way at all for a small program is just fine & will work well.
Spaghetti code is where the developer only gave thought to the present requirements and failed to consider what would occur as new features need to implemented into the program, and the result is a new feature that breaks old features, followed by modifications/workarounds in old code, followed by new features that break existing, and the loop goes on & on until the program becomes so inefficient that a complete rewrite becomes necessary.  There's a lot more software and web apps coded this way than people realize!   And with oop you do not have this situation at all.  It is more economically viable to take the extra time in te beginning & start w/ oop.

---

### Post by pmasiar on 2007-06-24
> **lKyPN8xZQG said:**
> I can do those things as easily with non-opp code.

> **lKyPN8xZQG said:**
> I don't really have time for that.

I can do that in non-OOP too.

Well, you have rather extraordinary claim: you claim that hundreds of very smart people, each known  by name and each of them bet their professional reputation on OOP are wrong and you, anonymous forum poster,  are right. Don't you think that it would be *your* responsibility to prove that they are wrong? Do you expect all of us just trust your word, even if you do not have time to prove it? At *least* have some links from sources with good reputation to support your extraordinary claims?

Maybe *you* cannot see why OOP is needed for big projects - it is entirely possible that *you* never encountered problems for which OOP is best solutions, and all *your* problems can be as easily be solved without OOP. It does not say anything about OOP - only about your problems you encountered so far. We know nothing about you - for all we know, you can be a dog :-) because [On the Internet, Nobody Knows You're a Dog](http://www.unc.edu/depts/jomc/academics/dri/idog.html) 

BTW it was a joke, in case you missed it.

---

### Post by DougB1958 on 2007-06-24
> **lKyPN8xZQG said:**
> I can do those things as easily with non-opp code.

... along with some similar sentiments expressed later.

But if you use OOP (and understand how to use it well) then (1) the framework of objects and classes helps you design code that is modular, reusable, type-safe, etc., and (b) the compiler does lots of the low-level work of implementing these desirable features.

So yes, you can achieve the same results in a non-OOP language, but I'd dispute "as easily."

---

### Post by blah blah blah on 2007-06-24
> **aks44 said:**
> One big feature of OOP is inheritance, and the ability to manipulate an object without knowing its actual type (interfaces, virtual functions anyone?).

Implementing such a behaviour in a non-OOP language is of course possible, but it leads to things like the GTK+ "object model" (very interesting reading BTW, thanks samjh for the link). My eyes are still bleeding... :p

Is inheritance a set theoretic kind of thing?

---

### Post by Ramses de Norre on 2007-06-25
> **lKyPN8xZQG said:**
> Is inheritance a set theoretic kind of thing?

First you claim that you don't need OOP and then you ask what inheritance is?
Well, if you don't know inheritance you certainly aren't in a position to express yourself about OOP because it's one of the key features OOP brought into programming.
It appears to me that you are rather happy with your current programming paradigm and not at all interested in learning OOP, well then don't. But realize that almost every job in IT nowadays  requires the knowledge of at least one OOP language, that seems quite a good argument to me to expect OOP to be a real advantage over older paradigms...

---

### Post by pmasiar on 2007-06-25
And not only IT jobs require OOP: solving problems with big complex real-world computer systems requires OOP :-)

---

### Post by blah blah blah on 2007-06-25
> **Ramses de Norre said:**
> First you claim that you don't need OOP and then you ask what inheritance is?
Well, if you don't know inheritance you certainly aren't in a position to express yourself about OOP because it's one of the key features OOP brought into programming.
It appears to me that you are rather happy with your current programming paradigm and not at all interested in learning OOP, well then don't. But realize that almost every job in IT nowadays  requires the knowledge of at least one OOP language, that seems quite a good argument to me to expect OOP to be a real advantage over older paradigms...

I'm asking if my understanding is entirely correct. The person who explained it to me didn't make it very clear. Don't jump to conclusions.

---

### Post by slavik on 2007-06-25
X is object oriented, but written in C.

In C++, a class' methods are inside of it:
class { int var; int func(); }

in C, it is outside of the structure:
struct { int var; }
int func(struct *);

OOP in C++/Java/others (except python) imply the first parameter 'this' within the class method implicitly, whereas in C and others you have to do it explicitly.

The drawback to C++/Java OO is that code explodes as you allocate more and more objects, because in C, same methods can be used between all instances of the class (functions can be stored only once, whereas in C++/Java, there is a copy for each instantiated object)

But in C++/Java, if you prefix a method with 'static' I believe that it will create only 1 instance of the method.

---

### Post by Mathiasdm on 2007-06-25
> **lKyPN8xZQG said:**
> I don't really have time for that.
[B]


I can do that in non-OOP too.[/B]


That's not the point. You can probably replace all OOP by procedural programming, but OOP has certain benefits, which is why it's used.

[http://www.design-nation.net/en/archives/000438.php](http://www.design-nation.net/en/archives/000438.php)

---

### Post by aks44 on 2007-06-25
> **slavik said:**
> The drawback to C++/Java OO is that code explodes as you allocate more and more objects, because in C, same methods can be used between all instances of the class (functions can be stored only once, whereas in C++/Java, there is a copy for each instantiated object)
Plain wrong. Code sharing happens in C++ & Java just like in C. Aren't you confusing with **inline** functions, which are instanciated inline (as their name implies :p) at the call site?

> **slavik said:**
> But in C++/Java, if you prefix a method with 'static' I believe that it will create only 1 instance of the method.
A **static** method is just a method that can (has to) be called without an instance (ie. no implicit **this** pointer). No more, no less.

---

### Post by blah blah blah on 2007-06-25
> **Mathiasdm said:**
> That's not the point. You can probably replace all OOP by procedural programming, but OOP has certain benefits, which is why it's used.

[http://www.design-nation.net/en/archives/000438.php](http://www.design-nation.net/en/archives/000438.php)

Of course you can but, that's not what I'm talking about. I'm saying that OOP has no advantages in abstraction.

---

### Post by aks44 on 2007-06-25
> **lKyPN8xZQG said:**
> Is inheritance a set theoretic kind of thing?

Inheritance allows you to abstract common functionnality (and optionally data) in a base class, and have the derived classes implement the specifics.

Interfaces are base classes which don't have any implementation at all, they are kind of a "contract" between the interface users and the concrete class implementors.

eg.

You can **Read** and **Write** from a **Stream**, and it has a **DataSize**.
A **File** is obviously a **Stream**, but a **Socket** also is.

Now, let's say you have a function which reads from a **File** that is passed as a parameter. Wouldn't it be nice if that function could also read data from a **Socket**, or any other kind of **Stream**?

Just change a bit your original function so that it takes a **Stream** as a parameter instead of a **File**, and you're done. Your function can now read both from a **File** and a **Socket**.

A year later, you notice that you also need that function to read from a console **Pipe**.
Just implement the **Pipe** class as a **Stream** descendent, and voila... your original function will now also read from a **Pipe**, *without any change*.

That's roughly what inheritance and interfaces are all about.

EDIT:
> **lKyPN8xZQG said:**
> Of course you can but, that's not what I'm talking about. I'm saying that OOP has no advantages in abstraction.I just proved the contrary... ;)

EDIT again:
Can you do that in C?

```
class auto_ptr
{
  myType* ptr;
public:
  auto_ptr(myType* p) : ptr(p) {}
  ~auto_ptr() { delete ptr; }
  myType* operator ->() { return ptr; }
}

void whatever()
{
  auto_ptr p(new myType());
  p->foo();
}
```

Note that
1) auto_ptr can be used just like a plain myType*
2) I don't need to write any **delete** in the **whatever** function body
3) whatever happens, the memory allocated using the **new** (=malloc) directive will *always* be freed

Points 2 & 3 are why OOP is worth it...

---

### Post by tht00 on 2007-06-25
> **lKyPN8xZQG said:**
> Of course you can but, that's not what I'm talking about. I'm saying that OOP has no advantages in abstraction.

Sure it does.

I worked on a project a while back that dealt with a lot of text manipulation and system calls in C++ (something I would call relatively clumsy and messy).  I was able to break down the project structure to be better understandable by encapsulating program functionality with how the project actually worked, using object to model it.

I suppose it is very similar to how functions and methods are used.  Would you also argue that they are not worth using to 'break up' the program?  Similarly, a program _can_ certainly be written without them, but the usage of methods allows simplification and hiding of repetitive or complicated code.

Classes and OOP in general are very similar to how functions/methods are used, except in a larger and more contained setting.

If you don't see the benefit, then you don't know enough about them and/or you're just being stubborn.

---

### Post by harun on 2007-06-25
> **lKyPN8xZQG said:**
> Of course you can but, that's not what I'm talking about. I'm saying that OOP has no advantages in abstraction.

When asking this question myself when first starting out what helped me was to see it as OOP helps people not computers and that is where the advantage lies.

People have a limited ability to keep track of things and remember things. So representing things to them as a few objects to manipulate is easier for them (programmers). Easier meaning they can learn what is going on quicker, be more productive, more efficient,  less error prone, and enjoy it more :-).

---

### Post by blah blah blah on 2007-06-25
> **aks44 said:**
> Inheritance allows you to abstract common functionnality (and optionally data) in a base class, and have the derived classes implement the specifics.

Interfaces are base classes which don't have any implementation at all, they are kind of a "contract" between the interface users and the concrete class implementors.

eg.

You can **Read** and **Write** from a **Stream**, and it has a **DataSize**.
A **File** is obviously a **Stream**, but a **Socket** also is.

Now, let's say you have a function which reads from a **File** that is passed as a parameter. Wouldn't it be nice if that function could also read data from a **Socket**, or any other kind of **Stream**?

Just change a bit your original function so that it takes a **Stream** as a parameter instead of a **File**, and you're done. Your function can now read both from a **File** and a **Socket**.

A year later, you notice that you also need that function to read from a console **Pipe**.
Just implement the **Pipe** class as a **Stream** descendent, and voila... your original function will now also read from a **Pipe**, *without any change*.

That's roughly what inheritance and interfaces are all about.

So it's set theoretic?

---

### Post by aks44 on 2007-06-25
> **lKyPN8xZQG said:**
> So it's set theoretic?

It can be
1) purely abstract (what you call "theoric")
2) partially abstract / partially concrete (some "slots" *have to* be implemented in derived classes, but some functionnality is present in the base class, "driving" the derived classes)
3) concrete with some "slots" than *can* be reimplemented
4) totally concrete (derived classes can only add new functionnality)

Classes that fit in points 1 & 2 are not instanciable, they *must* be derived
Classes that fit points 3 & 4 are instanciable, and *can* be extended

FYI point 4 is not very common (kinda useless)

IOW, it's **flexible** ;)

---

### Post by blah blah blah on 2007-06-25
> **aks44 said:**
> (what you call "theoric")

I meant like in math. Anyway I think I get it. It seem like that's not even dependent on a OO paradigm.

---

### Post by slavik on 2007-06-25
> **aks44 said:**
> Plain wrong. Code sharing happens in C++ & Java just like in C. Aren't you confusing with **inline** functions, which are instanciated inline (as their name implies :p) at the call site?


A **static** method is just a method that can (has to) be called without an instance (ie. no implicit **this** pointer). No more, no less.
I have a right to be wrong :P

---

### Post by aks44 on 2007-06-25
> **lKyPN8xZQG said:**
> I meant like in math. Anyway I think I get it. It seem like that's not even dependent on a OO paradigm.

The OO paradigm "backported" that to non-OOP languages.

As a very good example IMHO, look at the link concerning the GTK+ "object system" earlier in this thread. What they're doing, is writing by hand what an OO compiler does for you.

BTW, strange that they even use the "object" word...


And, huh, I'm not a math guy... so I didn't understand "theoric" that way (and I still don't really get what it would mean in a math context)

---

### Post by blah blah blah on 2007-06-25
> **aks44 said:**
> The OO paradigm "backported" that to non-OOP languages.

As a very good example IMHO, look at the link concerning the GTK+ "object system" earlier in this thread. What they're doing, is writing by hand what an OO compiler does for you.

BTW, strange that they even use the "object" word...


And, huh, I'm not a math guy... so I didn't understand "theoric" that way (and I still don't really get what it would mean in a math context)

I guess that would explain why you couldn't answer my question. :)

---

### Post by Tomosaur on 2007-06-25
Regardless of whether or not you view it as 'dependent' on an OO paradigm - the fact of the matter is that it is used in an OO paradigm. Travel is not dependent on cars, but cars allow you to travel. In the same way, inheritence may not be dependent on OOP, but OOP makes inheritance a lot easier to understand and implement.

At the end of the day, it just doesn't matter. If you're happy using purely procedural code, then use that. If not, then by all means take a look at OOP.  It's simply a way of looking at things. It is not inherently better than any other paradigm, it just appears that many developers prefer it over procedural.

---

### Post by blah blah blah on 2007-06-25
> **Tomosaur said:**
> Regardless of whether or not you view it as 'dependent' on an OO paradigm - the fact of the matter is that it is used in an OO paradigm. Travel is not dependent on cars, but cars allow you to travel. In the same way, inheritence may not be dependent on OOP, but OOP makes inheritance a lot easier to understand and implement.

At the end of the day, it just doesn't matter. If you're happy using purely procedural code, then use that. If not, then by all means take a look at OOP.  It's simply a way of looking at things. It is not inherently better than any other paradigm, it just appears that many developers prefer it over procedural.

I want to know how OPP is useful so it does matter.

---

### Post by pmasiar on 2007-06-25
> **lKyPN8xZQG said:**
> I guess that would explain why you couldn't answer my question. :)

as someone said long time ago, one dummy can ask question which not even 10 wise men can answer. :-)

What is your expereince in programming? Which languages did you have experience with? in terms of number of lines of code written, and months/years? what kind of applications?

---

### Post by blah blah blah on 2007-06-25
> **pmasiar said:**
> as someone said long time ago, one dummy can ask question which not even 10 wise men can answer. :-)

What is your expereince in programming? Which languages did you have experience with? in terms of number of lines of code written, and months/years? what kind of applications?

Programming isn't my profession, I just do it for fun. I've been writing down algorithms for maybe 10 years (if that counts as programing). I've been programing for maybe 2 years. Of the more common ones I know: some assembly, basic, C, C++, clean, fortran, groovy, haskell, java, lisp, lambda calculus, python, ruby, scilab/matlab, and may be a few others.

---

### Post by pmasiar on 2007-06-25
Writing algorithms without debugging the code --- I am not sure how other feels about it, but I would hardly call it programming if someone else was responsible for coding and debugging that algorithm.

In just 2 short years, you went through amazing number of languages. :-) I wish i was as capable lerning new languages as you are!

How far beyond knowing syntax do you know any of mentioned languages? I mean, what is the longest program you wrote and debugged in any of them?

---

### Post by blah blah blah on 2007-06-25
> **pmasiar said:**
> Writing algorithms without debugging the code --- I am not sure how other feels about it, but I would hardly call it programming if someone else was responsible for coding and debugging that algorithm.
true

> **pmasiar said:**
> How far beyond knowing syntax do you know any of mentioned languages? I mean, what is the longest program you wrote and debugged in any of them?

Maybe a few thousand lines.

---

### Post by Tomosaur on 2007-06-25
> **lKyPN8xZQG said:**
> I want to know how OPP is useful so it does matter.

But the the utility is subjective, so you'll never know until you sit down and do it for yourself. We've explained why we find it useful / good / whatever - the next step is for you to try it out (if you are interested, of course) and then see whether your experience matches our claims. 

This is how questions get answered, and how you check whether the answer is satisfactory.

---

### Post by samjh on 2007-06-25
> **lKyPN8xZQG said:**
> I'm saying that OOP has no advantages in abstraction.

OOP allows you to treat data, functions, and procedures, as a single entity.  You can extend this entity to add more data, functions, and procedures, without having to duplicate it.  You can also access data, functions, and procedures within the entity, and you can hide them too.  Not only can you do all the above, but you can do them very easily.

WIth pure procedural, you can do all that, but not as cleanly or easily as using an OOP language.

It's one of those things you need to experience before passing judgement.  It's not the solution to all problems, but it provides a very elegant way to abstract complex software designs.

Try writing a GUI using standard C.  Just a terminal-based GUI will do.  Try making multiple windows on the same screen, pop-up dialog boxes, progress bars, etc.  Do this purely procedurally, using only functions and standard C data types.

Then repeat the same using OOP in C++, using standard C++.  Hint: create a class for a window, and try to extend it to cover different sizes, dialog boxes, etc.

I did something similar in high school using Pascal.  It was a very lengthy exercise (about 3 months) because it was a complex application (motor sport management software) with a complex GUI (all terminal based, similar to N-Curses but written from scratch).  But at the end of it, I appreciated the power OOP.

---

### Post by DougB1958 on 2007-06-25
> **lKyPN8xZQG said:**
> So it's set theoretic?

Yes, if you want to treat OOP mathematically. You can think of a class, C, as a set of (potential) objects, in which case subclass S of C is a subset. It's a subset because the instances of S are all also instances of C, but they differ from "ordinary" instances of C in responding to additional messages beyond the ones that all Cs handle, or responding to some messages differently than "ordinary" Cs do, etc.

But, as most of the rest of this thread has been saying, OOP has much more pragmatic value than this formal view makes clear (which is not to say that some of us don't love finding some mathematical elegance behind programming languages anyhow :D)

---

### Post by ricrac on 2007-06-25
An answer to the original question, what does OOP do to help. 

Negatives: Larger and slower code
Positives: Objects are larger than they appear.

Code reading can be done in an outline format.
You can read less of the source and "know" less overall (than procedural) and still make reasonable changes.

As a manager/owner, using C++,Java,OOP, programmers are easier to replace.
As a developer, libraries and frameworks are easier to grasp and modify.

Most small and fast code still uses C because it produces better results.
X, compilers, kernel, drivers, servers, etc.
Believe me most of the programmers that are coding the core code you're using on Linux know how to program in C++, but choose not too unless there is a definitive value for the project.
And as you see, as of 2007, most would agree C still reigns supreme.

Java is great for large projects that may need to cross platforms.
C++ is great for application projects with large numbers of simultaneous developers.

The excuse for critical projects written in C++ or other OOP is buy faster hardware and more RAM.
If you using any higher level language perl,python, etc., it doesn't matter. It's slow and fat either way so use OOP if it helps or don't.
The higher level or more OOP you get, the larger it usually gets under the hood and the slower it usually runs.  

If you primarily want a job, learn OOP.
Skillset ranking usually goes... Assembly,  C,  OOP(c++,java),  then Interpretive. Not always accurate to actual skills but that's how critical jobs are delegated and salaries are ranked in my experience. 
Conversely, jobs will be easier to find in the reverse. Interpretive, OOP, C, Assembly.

---

### Post by pmasiar on 2007-06-25
> **ricrac said:**
> If you using any higher level language perl,python, etc., it doesn't matter. It's slow and fat either way so use OOP if it helps or don't.
The higher level or more OOP you get, the larger it usually gets under the hood and the slower it usually runs. .

I. like many other programmers, do web front-end for a database.  Between database connection, query, and browser response, CGI in C is as fast (or slow) as in high-level language like Python. 

But *programmer's productivity* using smart dynamic OOP language like Python skyrockets, compared with statically typed compiled languages. Flexibility and adaptability increases (less lines to modify). Comparing with Python, developing website in Java is painful and sluggish. Not mentioning template languages - of course dynamically typed languages like Python have superior templating engines. And now developers started to create nice dynamic widgets like Java has... I use TurboGears web framework and it is ridiculous how little code you need to get something running, if you know how.

Using self-inspection TG divines heaps of code without even generating it. Object-relation (to database) mapper works like a charm. Templates are smart. Life is good. Programming is fun again :-)

---

### Post by blah blah blah on 2007-06-26
I guess I'm just weird.

---

### Post by ricrac on 2007-06-26
While I agree that python and other OOP and higher level languages can be more "productive" I disagree that python cgi is as fast as C, nowhere near as fast.

Google uses C for search, that's cgi.
Google, Doubleclick, Realmedia, and most other ad servers uses C for ads, that's cgi, it's a lot more complicated than image serving these days.
Akamai uses C for edge side caching, that's the same functions as cgi.  parsing, lookup, templating and page serving.

If the complexity is low enough there is no speed gain.
If the overall load is low enough there is no system load gain.
For code that is going to be "old" by next year, there may be no gain.

Assembly is always faster, period. C next, followed by Java and C++, then python.

Fast enough and good enough for many jobs, python, perl, tcl, and php.

---

### Post by pmasiar on 2007-06-26
> **ricrac said:**
> While I agree that python and other OOP and higher level languages can be more "productive" I disagree that python cgi is as fast as C, nowhere near as fast.

If 96% of your app moves at constant speed, making remaining 4% twice as fast gains you not 50% speedup, but paltry 2%. This is what I ment: 2% speedup migh be not worth the hassle.

> Google uses C for search, that's cgi.

For Google, 2% speedup saves about 4000 web servers, it is serious money for them - but most people don't have that kind of problems. :-)

And Google uses C only for production serch, which does not change: big amount of internal development and non-production stuff is prototyped in Python - and then 5% of the code which takes most CPU cycles is linked as C library. That is sensible use of both Python and C - but only *after* you have functioning application, and you optimized code, and you detected bottleneck, not before.

Google, Doubleclick, Realmedia, and most other ad servers uses C for ads, that's cgi, 

It is possible to use C for that, but as easy to serve ads in any CGI app. But these are niche application: no user interface, static API, no changes.

> Assembly is always faster, period. C next, followed by Java and C++, then python.

Unless I work on something time-critical, why should i worry about raw speed? *time to market* is in most cases more important than raw CPU speed. If you miss market opportunity, who cares about your program? If I cornered market for myself as monopoly, poor suckers will buy any crap from me just to be compatible and pay gladly for yearly upgrade of new bugs - should i mention the company which uses this approach?

---

