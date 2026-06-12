---
title: "What's wrong with OOP?"
date: 2012-03-16
forum: Programming Talk
---

### Post by hoangtu on 2012-03-16
Recently I read many leangthy articles say how bad OO is. Among those are Paul Graham's and he series of articles on this site: [http://www.geocities.com/tablizer/oopbad.htm](http://www.geocities.com/tablizer/oopbad.htm) (I haven't read all, since I don't have much time). Basically, everything about OO is bad. I failed to see. It may not be the perfect solution, but it's not as they claim. I read a more objective article: [**Modular Programming Versus Object Oriented Programming (The Good, The Bad and the Ugly)**]("http://www.petesqbsite.com/sections/express/issue17/modularversusoop.html"), and the author made a good point that certain paradigm is more suitable for certain domains. For example, OOP is very suitable for multimedia and entertaiment industries such as "Music software designers, Recording studios, game designers, even book publishers, and video production groups" . He pointed out that people in these industries tend to think in term of objects more.

What's wrong with building abstraction by encapsulate data and behavior into class, and provide the class as a package to be used as it is without worrying about the details? C does this as well. In C, we also specify a set of interfaces to the client in .h file, implement it in .c, and if the source is proprietary, we can always provide the interface only.

What's wrong with classification? How can you program a game in a procedural or functional way, where it's counterintuitive to model objects in real world? Even Lisp supports OOP as well. In C, we can define low level struct, and if we want to transform one struct to another, we have to base on the memory layout of each struct. We would end up writing OOP feature for automatic transformation anyway.

Because this is talking about paradigm, so we should not be specific about one language, so we don't say thing like the object model in Java is dictated by Object, or C++/Java is too verbose.

Finally, object oriented or whatever is just a way to organize source code. Instead of millions lines of code in our main, we divide it into smaller units and store it different locations (files), and the main only uses a nice interface from these modules (which is usually only one line) to invoke certain functions when needed. The act of dividing and organizing code into logical entities (class, functions, struct...) and physical entities (files, directories) is a logical (science) and creative (art) task. I don't think one paradigm is suitable for every situation.

Can anyone, especially from anti-OO camp explain this to me?

---

### Post by r-senior on 2012-03-16
> **hoangtu said:**
> For example, OOP is very suitable for multimedia and entertaiment industries such as "Music software designers, Recording studios, game designers, even book publishers, and video production groups" .
Account, Customer, Product, Vehicle, Office, Department, Aeroplane, Patient, Student, Course, Employee, RetailOutlet, ShoppingCart, TextBuffer, Window, Button, Plant, Reactor, State, Country ...

OOP is good for modelling all kinds of objects in all kinds of user-space applications. That doesn't mean it's always the best choice, but it's not always a bad choice either.

---

### Post by satsujinka on 2012-03-16
There's nothing wrong with OOP, if you like it and it works for you then use it.

That said, I don't really care for OOP. I feel that it's an unnecessary abstraction that really only gets in the way of me getting things done. Basically, I want to specify to the computer what to do (and how to do it in imperative languages) I don't really want to spend time figuring out if I can personify aspects of a system and the figure out what kinds of messages they should accept.

As far as games go... procedural and functional (graphical) games do exist, it isn't even that difficult to imagine. At the end of the day an object is just data and functions, whether they're together or separate makes no difference to a computer. This can be taken a step further, if you don't have structures in your language you can just pass a bunch of data to a function and pretend that it's all one thing.

Remember, to the computer everything is just 1's and 0's there aren't even any negative numbers at the hardware level. Whatever abstractions we use to code are merely constructs that exist solely in our own heads. There are no strings, chars, floats, doubles, Cats, Dogs, etc. only 1's and 0's. However you want to group them is entirely up to you.

---

### Post by 3177 on 2012-03-16
> **satsujinka said:**
> There's nothing wrong with OOP, if you like it and it works for you then use it.

That said, I don't really care for OOP. I feel that it's an unnecessary abstraction that really only gets in the way of me getting things done. Basically, I want to specify to the computer what to do (and how to do it in imperative languages) I don't really want to spend time figuring out if I can personify aspects of a system and the figure out what kinds of messages they should accept.

As far as games go... procedural and functional (graphical) games do exist, it isn't even that difficult to imagine. At the end of the day an object is just data and functions, whether they're together or separate makes no difference to a computer. This can be taken a step further, if you don't have structures in your language you can just pass a bunch of data to a function and pretend that it's all one thing.

Remember, to the computer everything is just 1's and 0's there aren't even any negative numbers at the hardware level. Whatever abstractions we use to code are merely constructs that exist solely in our own heads. There are no strings, chars, floats, doubles, Cats, Dogs, etc. only 1's and 0's. However you want to group them is entirely up to you.

Exactly.
2 different ways to get the same general end result.

But if I had to give a reason OO is bad.... it would be simply because its newer.

---

### Post by Pierrick584 on 2012-03-16
Looks like who wrote that was realy realy mad, there's not much explanation, OO is usefull, but no one ever forced anyone to do OO... if someone want to work in assembly, thats his own choice

---

### Post by CptPicard on 2012-03-16
Well, there are two things about typical OOP-languages that give you the horrible explosion of design patterns that are used to engineer around the problems produced by the language: static typing and single dispatch. I have a suspicion that in particular the combination of the two is the root cause of some critcisms of OOP as it currently exists mostly.

Essentially, OOP-ness is a matter of an extensible type system where operations on items of some data type are bound to the type itself. This idea that "operations belong to a certain single level of a type hierarchy" can be a bit problematic... essentially, in method calls, there is always the implicit "this" parameter, that is the only parameter of the call that is used to resolve the actual implementation of the function to be invoked. In "real life" this is not always the case -- multiple-dispatch languages decouple the type from the operations on the type much more nicely.

Also, static typing causes a lot of "typing" -- at least in duck-typed languages your interfaces are sort of implicit -- a thing just works if it can at runtime respond to some kind of a message, as was the original Smalltalk-style idea of OOP.

---

### Post by ofnuts on 2012-03-16
> **satsujinka said:**
> 
That said, I don't really care for OOP. I feel that it's an unnecessary abstraction that really only gets in the way of me getting things done. Basically, I want to specify to the computer what to do (and how to do it in imperative languages) I don't really want to spend time figuring out if I can personify aspects of a system and the figure out what kinds of messages they should accept.OOP It's not a matter of personification. It's a matter of finding/describing common things to avoid coding them twice. It's also a fairly efficient way to reduce the knowledge you need to code, because you only care about the differences... 

Granted, there is no real "methodology" to find an optimal class hierarchy (maybe because there is no such beast), and design patterns are mostly a glorified set of cooking recipes. But this allows us to show some creativity...

---

### Post by satsujinka on 2012-03-16
> **ofnuts said:**
> OOP It's not a matter of personification. It's a matter of finding/describing common things to avoid coding them twice. It's also a fairly efficient way to reduce the knowledge you need to code, because you only care about the differences... 

Granted, there is no real "methodology" to find an optimal class hierarchy (maybe because there is no such beast), and design patterns are mostly a glorified set of cooking recipes. But this allows us to show some creativity...

That's hardly an OO specific activity. You try to reduce the amount of duplicate code you write in any language and is not a feature unique/specific to OO.

I would go on to say that OO doesn't add any special abilities to that field that aren't covered by dynamic languages, functional languages, or to some extent duck typing languages (whether they be static or dynamic.)

---

### Post by xytron on 2012-03-17
The author in the following article makes OOP sound much like a fad;

[http://www.devx.com/opinion/Article/26776/1954]("http://www.devx.com/opinion/Article/26776/1954")

OOP can be useful especially in GUI programming, and now that the GUI is king it seems fated to remain around for awhile.

I agree with the author that eventually we will see machines capable of interpreting human instructions in human languages. WolframAlpha while still in early development is a step in this direction.  One just enters questions, variables and equations and out pops the answer.  In many cases those queries would have involved writing a small program.

OOP is a fad in that what was basically not a very complicated idea (a new way to organize program data and functions) was elevated by many to an arcane and difficult subject.
There are even books on the philosophy of OOP.

Striving for simplicity is always best.  Sometimes that may mean using OOP.

---

### Post by CptPicard on 2012-03-17
> **xytron said:**
> 
I agree with the author that eventually we will see machines capable of interpreting human instructions in human languages.

Programming language designers have often tried to mimic human languages in their designs, and the end result has always been pretty disastrous. It may be possible that computers will just magically "know what we mean" from interpreting actual human language (which probably would mean we built a strong AI), but as far as programming goes in the sense that we currently understand it -- giving an exact computable description of a program -- I actually believe that languages that are less ambiguous and more suitable of actually giving such a description, will win the day.

---

### Post by trent.josephsen on 2012-03-18
The real problem with OOP is how overblown it is in academia compared to how useful it is IRL.  With (often inexperienced) professors teaching Java in first year CS classes, CS education tends to turn out a lot of (not *mostly*, but quite a few) code monkeys that don't know how to really solve problems, but just throw more abstraction at something until they feel they've simplified the problem sufficiently when really they're increasing the complexity of the solution a thousandfold.

Is OOP a fad?  Yes.  Is it also occasionally useful?  Yes, that too.  You shouldn't remove it from your solution space because it's overused any more than you should try to apply it for every problem you're confronted with.

---

### Post by hoangtu on 2012-03-19
Sorry for not replying the thread for a while.

One of the complain about OO is that it does not reflect the real world because not everything in the eral world is object. However, I think people play with word on this one rather focus on the idea. Let's not call it object, but call it concept. An object in OOP reflects a real world concepts, not an object as in noun. For instance, kicking is an action which can be modeled by a class named Kick along with its attributes  to present it as a concept:

```

class Kick{
private:
     int velocity_;
     int force_;
public:    
     Kick(int velocity, int force):velocity_(velocity),force_(force){}
     virtual ~Kick(){}

     void high(Fighter target){ /*implement high kick */ }
     void mid(Fighter target){ /*implement mid kick */ }
     void low(Fighter target){ /* implement low kick */ }

     int get_velocity() const { return velocity_; }
     int get_force() const { return force_; }
};

class Fighter{
private:
     int health_;
     int ki_;
     Kick kicking_stance_;
public:
     enum AttackPosition {
           high,
           mid,
           low,
     };

     FIghter(int health, int ki, int kick_stance):health_(health), ki_(ki), kicking_stance_(kick_stance){}
     virtual ~Fighter(){}

     void kick(Fighter target, AttackPosition pos){
          if (pos == high)  kicking_stance_.high(target);
          else if (pos == mid) kicking_stance_.mid(target);
          else kicking_stance_.low(target);
     }
};

```

So, what's the problem here? I think one of the reason people  complain that is, Kick is not an object in real world itself. Only live entity like human, horses can kick. Another example is, if I got an Invoice class, should object of invocie, invokes actions like invoice.save(), invoice.send()? For this reason, we have patterns, design and design principles because pretty much people can invent different ways to present a concept. As a consequence, OO is accused for low reusability, despite the abstraction is for concept reusability. In the example above, other people might put Kick concept inside an abstract class Fighter, while other might define the MartialArtStyle abstract class, and put    kick action inside it as a abstract method. For this reason, it's more difficult to reuse, since if there's a more complicated object system, a member function of an object may operate on the abstract data type of that object, and inside the abstract data type, it operates on other abstract data types as well.

This is what I got from the articles. Correct me if I'm wrong.

However, I still don't think it's the fault of the paradigm, but rather, the language. Let's consider another scenario:

[LIST]
[*]An ancient wizard has a powerful spell which can turn objects (such as tea cup) into living entity like human being.

[*]There's a tea cup in front of him 

[*]The old wizard casts the spell on the tea cup to make it live.
[/LIST]

     In language like Java, the problem is that I have to plan ahead for TeaCup object. If I want to have a tea cup to behave like human, I have to:

[LIST]
[*]Write an interface for shared human behaviors, such as talk(), walk(), and let TeaCup implement it.

[*]Since not all TeaCup can talk, and I want to model the real work closely so other can understand, the TeaCup must not always talk.

[*]So, I define a TeaCup hierarchy, which (for simplicity, I will create one) has TalkingTeaCup inherits from TeaCup (which is the normal one), and implements the shared human behaviors interface.
[/LIST]

     Look at this way of constructing concept, we can see that it creates overhead. In this case, instead of a tea cup with has varied behaviors, we got different versions of TeaCup which varies a little in behaviors. This is just another simple case. Imagine if it applies for a large and complicated system.

     There's no way for me to keep the TeaCup object as simple as it is, because TeaCup is a TeaCup, it can't operate on it own until the wizard gives it a life. Thus, TeaCup must not contain any related behaviors to make it "lively"  (to prevent issue like whether invoice should save() / send() or not). Dynamic behaviors will be added later after the wizard casts life spell on TeaCup.

     I don't think we can add methods to TeaCup if we don't write it in class or implement via interface. Although, Java can dynamically add more class with varied parameter at runtime with Dynamic Object Mode (which we have to do more work)l: [http://dirkriehle.co...005/plopd-5.pdf](http://dirkriehle.co...005/plopd-5.pdf) . In C, we can have an array of function pointers, however, this approach is not convenient, since it operates on low level, so it's error-prone and it is strong typing, which make it less flexible.

      With function as first class object, it creates a more elegant way to solve the above problem. Consider this piece of Lisp code (I'm learning, so pardon me if it's not elegant) written for this scenario:

```

//I have to use C comment because our forum does not support Lisp comment style.

//collection of wizard spells. In Lisp, a variable is just a list, which might be a single value, or a list of symbols/values/**functions**
(defparameter *wizard-spells* nil)

//class object with its attributes consists of name and action
(defstruct object name action)

/* This is the wizard spell for giving an object a life. Here you can see, upon calling this function, it will add function talk and walk into the     variable action of the class object */
(defmethod giving-life ((o object))
  (princ ( type-of o))
  (princ " is now as lively as human!")
  (push #'talk (object-action o))
  (push #'walk (object-action o)))

//wizard spell for making an object become poisonous, so if someone contacts with the object, they will die a moment later
(defmethod poison ((o object))
  (princ ( type-of o))
  (princ " is covered with poison."))

//talk action, which is a human behavior
(defun talk ()
  (princ "Hello I can talk now"))

//walk action, which is a human behavior
(defun walk ()
  (princ "Hello I can walk now"))

//add spells to spell collection of the wizard
(push #'giving-life *wizard-spells*)
(push #'poison *wizard-spells*)

//create a teacup
(defparameter *tea-cup* (make-object :name "TeaCup" :action nil))

//funcall will execute the functions inside the variables.
(funcall (nth 1 *wizard-spells*) *tea-cup*)
(funcall (nth 0 (object-action *tea-cup*)))
(funcall (nth 1 (object-action *tea-cup*)))

```

In sum, OOP creates or more flexible way for "creativity" (in which we call design, where people can create different abstractions for the same concepts. This might be a good or bad thing). Those are the ideas I "suddenly" got it after practicing with Lisp for a while. Not sure if it's to the point or not, so If you guys can verify it, I am really thankful.

---

### Post by anewguy on 2012-03-19
The one thing (okay, everyone can laugh now - one thing - hee hee ;) ) I haven't picked up on at all yet is object oriented.  However, I think more people do that informally than they realize.  We all group similar items, things that are "related", it's just a matter of how we express that.  The same holds true with design and programming.  Relational databases, done correctly, express object orientation - don't repeat when you don't need to, keep things encapsulated.  I've seen what I would call "good" object orientation in some things I've gone through - "print" object, "camera" object, etc., etc..  But as with anything, a human can make a real mess of it.  And I've seen some real messes.

I figure I'm good enough at messing things up so I don't need another tool in the THAT toolbox.  However, for programming, I do keep telling myself I need to really sit down and just do it.  It's logical.  It's structured.  It forces one to keep things encapsulated instead of pieces of code spread all over the place.

With all that said, do I personally think it's the best for all situations.  No.  But there is no one size fits all in the computer business, no matter what side of things you're on.  No hardware, no software, no compiler, no IDE and surely no programming paradigm. 

Just my 2 cents worth - if it's worth that.

Dave ;)

---

### Post by lisati on 2012-03-19
IMO there is nothing inherently wrong with OOP or any of the other paradigms one could use for programming, it's just that some suit some tasks better than others. 

Speaking of mimicking natural language, need I mention COBOL? :D

---

### Post by QIII on 2012-03-19
Please. Do not mention COBOL!

What is wrong with OOP?  Nothing.  Imperative languages and approaches?  Nothing.

My opinion is that it all boils down to this:  How can snobbery be used to make oneself feel like a superior master of his trade?  How can one academic find a way to look down his nose at another?  How can someone be sure to have everyone else know that they are going with what is in vogue while others are not.

Different approaches solve different sorts of problems.   OOP became popular to solve a particular class of problems that came to the fore for some time.  Those problems still exist and there still need to be solutions for them.  New classes of problems come to the fore moving forward.  They require different approaches.  But they don't mean the other problems can be ignored.

Snobbery, primarily among academics, if you ask me.

---

### Post by anewguy on 2012-03-20
hey, anyone could write spaghetti code in COBOL, but it was also an excellent language for structured programming.  With all of it's data types I even wrote system tools in it way back when when the design and programming staff wanted a tool they could maintain and they worked in COBOL, not in my normal world.  You could do a lot when you wanted to.  Some even did data abstraction way back then by not tying themselves to the included data types, instead just calling a subroutine or subprogram with some clump of data and a generalized word of what was to be done with it.  Within the data was the information that told that subroutine just exactly what to do.
Lousy at optomization, but a LOT of programmers did a LOT with that language for a LOT of businesses on what at the time seemed like amazing hardware, but by todays standard is laughable.

So, does COBOL belong in a discussion about OOP?  YeP!!  You want OOP for fast development - try doing much faster than COBOL.  End of my defense.  Just wanted to say that back in the day a lot was done with a language that is laughed at now.  Not everything was move a to b and print.  You could do a lot of even technically oriented stuff with it if you knew what you were doing.  Of course, in those days I was assembler, machine code, core dumps and tracing, EBCDIC hex and binary.  Not many doing that now either - it's all removed from most people.

"OOP"'s - a trip to the past.

Dave ;)

---

### Post by matt_symes on 2012-03-20
Object orientated design is a way of identifying and organising concepts and relationships (objects, polymorphism, information hiding) to help model a problem better. It's how we think about and organise the world around us.

OOP's problems come from the fact that one is constrained by the syntax and semantics of the language used to implement those concepts.

They are two different issues.  There is nothing wrong with OOP at all. 

However, as CptPicard pointed out, it's not always simple to implement those concepts within the confines of a language due to the inherent constraints of that language.

---

### Post by muteXe on 2012-03-20
> **lisati said:**
> IMO there is nothing inherently wrong with OOP

lol, nice pun :)

---

### Post by satsujinka on 2012-03-20
> **matt_symes said:**
> Object orientated design is a way of identifying and organising concepts and relationships (objects, polymorphism, information hiding) to help model a problem better. It's how we think about and organise the world around us.

I've seen that argument before, and as I didn't buy it then I don't now. I really wish someone would stop and find research on the subject matter...but none exist.

Is it true that some people classify things based on their properties? Yes. Is it true that some people classify things based on their abilities? Yes. Is it true that some people classify things on both? Yes. Is it necessary? No.

I've probably expressed this at some point in time, but the way my mind tends to focus on things is as a series of events. So, this happens and that happens and now we have this result. In real life, events are carried out by actors, but in code there's no need to go the extra step of identifying them (the computer is the one doing everything after all.)

---

### Post by matt_symes on 2012-03-20
> Is it true that some people classify things based on their properties? Yes. Is it true that some people classify things based on their abilities? Yes. Is it true that some people classify things on both? Yes. Is it necessary? No.

What is that ?

That is a tree !

What kind of tree ?

That is an oak tree. That is my Oak tree.

What does it do ?

Well, it grows.

What does it have ?

It has leaves.

OO design and programming is  not a panacea for everything but it helps us model the world and it is how we classify things.

---

### Post by satsujinka on 2012-03-20
> **matt_symes said:**
> What is that ?

That is a tree !

What kind of tree ?

That is an oak tree. That is my Oak tree.

What does it do ?

Well, it grows acorns.

What does it have ?

It has leaves.
And what does that prove? How does it have any bearing on what other people might think?

Here's a different example:
What's it doing?
It's growing.
How is it doing it?
Via photosynthesis and nutrient absorption through its roots.
What types of things do that?
Plants.
What properties does it have?
Bark, composite leaves, it's about 20ft tall, and it has branches.
What is it?
An Ash Tree.

Interestingly enough, for a program only the first two questions are necessary. Everything else is just for the benefit of the programmer.

---

### Post by Tony Flury on 2012-03-20
To my mind OOP is a technique that makes some jobs easier - but it is perfectly possible to write awful code in an OO language (especially if you take OOP too far - and try to objectify everythig in sight).

There are also some jobs which OOP is probably not the right technique for or some people who don't like OPOP - and prefer to think functionaly, or procedurally etc.

my take : each to their own - do what you need to to make the program work - make sure you document it so that you and others can maintain it, and whatever paradigm you are using, use sensible names (code wil class1, class2 etc are not helpful - and yes I have had to make changes with code exactly like that).

---

### Post by matt_symes on 2012-03-20
> **satsujinka said:**
> And what does that prove? How does it have any bearing on what other people might think?

Here's a different example:
What's it doing?
It's growing.
How is it doing it?
Via photosynthesis and nutrient absorption through its roots.
What types of things do that?
Plants.
What properties does it have?
Bark, composite leaves, it's about 20ft tall, and it has branches.
What is it?
An Ash Tree.

Interestingly enough, for a program only the first two questions are necessary. Everything else is just for the benefit of the programmer.

That's properties of the tree and that is my point. It helps us organise and classify. That's part of the design process.

OOP is then an attempt to translate that into code.

> To my mind OOP is a technique that makes some jobs easier - but it is perfectly possible to write awful code in an OO language (especially if you take OOP too far - and try to objectify everythig in sight).

I could not agree more.

---

### Post by satsujinka on 2012-03-20
> **matt_symes said:**
> That's properties of the tree and that is my point. It helps us organise and classify. That's part of the design process.

OOP is then an attempt to translate that into code.


Tree's can have properties in non-OO languages, but that's besides the point.

What I showed is that the design process need not get to the point where we introduce actors. All the computer needs is how to do whatever it is we want to do. Classification is entirely unnecessary.

The simple reality is that not everyone thinks the same way. A single paradigm cannot model all human thought. Thus some people, like me, find OO to be counter intuitive and a waste of time.

---

### Post by matt_symes on 2012-03-20
> Tree's can have properties in non-OO languages,

I think you mis-understand me. OO is for humans not the PC.

I am not arguing it's the only way to model a problem in computer software. It does fit in with how we think about the world though and it's an attempt to take that and make it more natural when writing software.

If OO is not right for you then don't use it. It's just a methodology. It's just an abstraction from what the computer understands, designed (at least by intention) to make it easier to think about a problem and implement a solution.

---

### Post by QIII on 2012-03-20
Computers at the machine level are inherently imperative.  That is certainly true.  But it is a mistake to assume that this implies that a purely imparative language is the only, or even the best, approach for all situations.

It certainly wont work well for the work that I do.

But that doesn't mean that OOP programmers should disregard the power of  imperative techniques.  Some "OOP" languages are imperative languages with OOP added in as a bonus.

Those who are fanatics about imperative language often think that those who use OOP languages do nothing more than create objects and obscure problems under a blanket of abstraction.  Some do.  Those who do are probably making things worse for themselves.

Appropriate use of classes and objects is good.  Even code that makes use of objects should often be otherwise expressed by imperative techniques within the classes.

As to the argument that OOP is a fad, you are a bit off the mark, unless you consider something that has its roots in the 50s and 60s as a "fad".

Stepanov's "algebra" argument is patently wrong in its conclusion that OOP is in any way inferior in and of itself.  Yes, you need interesting algorithms.  You need proofs before you arrive at axioms.  Axioms before you arrive at algorithms.  He is right that you must understand them before you can come up with an interface that lets them work.  But a good programmer, regardless of his technique, should understand  both the proof and the axiom, and therefore the algorithm before  starting.   It's the programmer, not the method, that is called into question.

And a good programmer knows when OOP is an appropriate interface for utilizing an algorithm and when it is not.

OOP and Imperative can be married to great effect.

That they often are not and that many OOP programmers are sloppy, thoughtless and bury themselves in needless abstraction is a reflection on them and their training, not the technique itself.

---

### Post by matt_symes on 2012-03-20
@QIII

Nicely put indeed.

---

### Post by QIII on 2012-03-20
> **matt_symes said:**
> @QIII

Nicely put indeed.

Ironically, Stepanov was one of the primary designers of the C++ Standard Template Library.

---

### Post by anewguy on 2012-03-20
QIII - bingo!  It's the programmer, their understanding of the problem(s), their understanding of the solution(s) and the clarity at which they resolve those 2 that makes for good programming.  Any language can be sloppy, and as you mention, some lend themselves to that more than others.   You can bury all kind of things in abstraction to where things really do get lost, just as branch-and-link in assembler, gosub in basic, etc., can be way overdone for what appears to be the programmers ability at expressing what they can do with the language, instead of what they can do to solve the problem.  A good programmer can use any language to arrive at an elegant, thought out, and easy to understand code.  Many programmers abstract themselves to death, to the point that neither themselves or another programmer can come back 6 months later and make changes to the code.  That's the difference between a programmer who programs for the sake of programming, and a programmer who programs to solve a problem.  And all programming is just solving problems of one type or another - business needs, sprite control, deriving the density of the earthen materials above/surrounding the deposit of a needed natural resource, moving that little dude from point A to point B in your game so you can shoot the neighbor or kick his dog through the fence.

You hit the nail on the head - it's not the language, it's not the paradigm.  It's the logic, and the proof of that logic, made into an effective, elegant, simple algorithm that count.  OOP lends itself to that for some problems, not so much for others, just as some languages lend themselves better to solving certain tasks.  There is no right or wrong approach - there's only an effective, elegant solution to a problem.

Dave ;)

---

### Post by xbxb on 2012-03-20
In the Wikipedia page for Object Oriented Programming, roughly 3/4 down the page there is a section called 'Criticism' 

Among the criticisms is this one which I think is especially relevant:

*Paul Graham has suggested that the purpose of OOP is to act as a "herding mechanism" that keeps mediocre programmers in mediocre organizations from "doing too much damage". This is at the expense of slowing down productive programmers who know how to use more powerful and more compact techniques.*

[https://en.wikipedia.org/wiki/Object-oriented_programming](https://en.wikipedia.org/wiki/Object-oriented_programming)

---

### Post by QIII on 2012-03-20
An ad hominem attack formulated on a baseless allusion.

Mediocre programmers and organizations can find concealment for their mediocrity in any language.

Remember, this is a guy with a vested interest in the use of another language -- of his own design.

---

### Post by xbxb on 2012-03-21
Speaking of OOP languages, Linus Torvalds, the creator of Linux, has much to say about C++.

One example:

"C++ is a horrible language. It's made more horrible by the fact that a lot of substandard programmers use it, to the point where it's much much easier to generate total and utter crap with it." 

In this case he was referring to writing kernel code using C++. But as far as I know he has never had anything good to say about C++.

My own opinion: 
C was never meant to be an OOP language. Creating C++ in order to give C programmers a leg up on OOP does neither C programmers nor the promotion of OOP any good. In fact, I don't think anyone could create a worse example of a supposed OOP language than C++.

---

