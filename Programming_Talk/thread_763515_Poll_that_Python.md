---
title: "Poll that Python"
date: 2008-04-23
forum: Programming Talk
---

### Post by Lau_of_DK on 2008-04-23
Gents,

I have been searching high and low to find a suitable development suite for Linux, but most options seemed like glorified text-editors. I however settled with the Qt integration in Eclipse, which is a really nice way to work with C++. 

I also noticed how popular Python has become but I want to raise some questions about it. It seems slow, even simple physics demonstrations (samples from their own website) seem sluggish to say the least and the whole syntax of the language seems "immature" and disorganized. So my question to you guys is this: Are there any other reasons to use Python than the fact that you dont know how to use C++ ?

/Lau

---

### Post by ghostdog74 on 2008-04-23
post your question to comp.lang.python.

---

### Post by tseliot on 2008-04-23
I love both Python and C++ (which I use with QT4).

As regards Python's syntax, maybe you should have a look at Python 3000. They're working on it.

As regards the fact that Python is not as fast as C++ or C, you're right. However this is not the point. No one is developing kernels in Python, etc. Using the right tool for the job is what really matters. For example I wouldn't write scripts in C++.

---

### Post by Lster on 2008-04-23
I use Python but for none of those reasons.

---

### Post by Tuna-Fish on 2008-04-23
I use python mainly because when I get an idea, it usually takes less than a tenth of the time to implement in python than c++. Then, after I got a working prototype, I test it, profile it, and if it is too slow, reimplement in a faster language. Usually, I don't have to. Most parts of a program aren't time-sensitive.

---

### Post by Lau_of_DK on 2008-04-23
> **Tuna-Fish said:**
> I use python mainly because when I get an idea, it usually takes less than a tenth of the time to implement in python than c++. Then, after I got a working prototype, I test it, profile it, and if it is too slow, reimplement in a faster language. Usually, I don't have to. Most parts of a program aren't time-sensitive.

Alright, that approach makes alot of sense to me. 

One thing I wondered about, was the fact that Eve Online was ported to Linux using Python, which caused a performance drop of 10-15%. I would have guessed that games/application ported to Linux should actually expect performance increases instead of drops as Linux is a better OS?

---

### Post by Tuna-Fish on 2008-04-23
And yes, I know c++. And no, I wouldn't use it ever unless I absolutely have to. C++ is fun when done alone, but I've seen just too many large projects disintegrate to steaming piles mainly because they used c++. Even plain old c is better, at least in it when you look at code, you have some idea what it does. In c++, all bets are off.

---

### Post by Tuna-Fish on 2008-04-23
> **Lau_of_DK said:**
> One thing I wondered about, was the fact that Eve Online was ported to Linux using Python, which caused a performance drop of 10-15%. I would have guessed that games/application ported to Linux should actually expect performance increases instead of drops as Linux is a better OS?

Eve used python on all platforms. The main reason for the performance drop is graphics drivers. They still kinda suck in linux.

---

### Post by Lau_of_DK on 2008-04-23
> **Tuna-Fish said:**
> And yes, I know c++. And no, I wouldn't use it ever unless I absolutely have to. C++ is fun when done alone, but I've seen just too many large projects disintegrate to steaming piles mainly because they used c++. Even plain old c is better, at least in it when you look at code, you have some idea what it does. In c++, all bets are off.

You actually made 2 statements that are in conflict with each other:
-1) "I know c++"
-2) "when you look at c++ you dont know whats going on"

:)

[QUOTE=Tune-Fish]Eve used python on all platforms. The main reason for the performance drop is graphics drivers. They still kinda suck in linux.[/QUOTE]

Very intesting, I did not know that.

---

### Post by RIchard James13 on 2008-04-23
> **Lau_of_DK said:**
> I also noticed how popular Python has become but I want to raise some questions about it. It seems slow, even simple physics demonstrations (samples from their own website) seem sluggish to say the least and the whole syntax of the language seems "immature" and disorganized. So my question to you guys is this: Are there any other reasons to use Python than the fact that you dont know how to use C++ ?

Why don't you program in assembler, that is faster than C++? If you know the answer to that question you also know the answer to your question.

---

### Post by Lau_of_DK on 2008-04-23
> **RIchard James13 said:**
> Why don't you program in assembler, that is faster than C++? If you know the answer to that question you also know the answer to your question.

Haha, good comment. 

The question I put forth was seriously meant, though stated in what I believed was a humours way. I just didn't see anything in Python to draw me away from C++, so I was looking for some of you old-school Python sharks to educate me. And you're still welcome to drop some links or examples if you have seen something incredible done in Python.

---

### Post by CptPicard on 2008-04-23
> **Lau_of_DK said:**
> 
I have been searching high and low to find a suitable development suite for Linux, but most options seemed like glorified text-editors.

Actually, with a dynamic language like Python, a glorified text editor is all you need -- and interestingly, all your development suite can be, because stuff like type tracking is harder than in C++. Then again, you need tools with statically typed languages exactly because you need to keep your types straight... the language just allows a solution to a problem it itself causes. :)


> I however settled with the Qt integration in Eclipse, which is a really nice way to work with C++. 

Hmm... if you want Qt integration and C++, KDevelop should be your first port of call really. I didn't even know there is any Qt integration with Eclipse.

> It seems slow, even simple physics demonstrations (samples from their own website) seem sluggish to say the least

Sure, but it doesn't even aim for extreme speed. You really need to write a C extension module if speed is an issue. However, for most code, level of abstraction always trumps raw speed.

> and the whole syntax of the language seems "immature" and disorganized.

You'll get used to it... I did. I still am not quite happy with the significant whitespace, but the other language features actually have a logic to them and exploiting them can be powerful, see further below...

> So my question to you guys is this: [quote]Are there any other reasons to use Python than the fact that you dont know how to use C++ ?


Nice troll ;) I know fully well how to use C++, but C++ simply doesn't have anything beyond native-compilation for speed when compared to most high-level languages, and adds a lot of pain and slowness of development and difficulty of abstraction.

Wybiral and I have been hacking on an idea we got less than a week ago. It's a sort of "Remote Procedure Calls over P2P mesh" network where each user is an object of a dynamic datatype... think "serverless IRC where you can call methods on other people". You can freely extend your own object whichever way you want and the new methods are automagically exposed through reflection to be called remotely. Calls and return values are routed over the network, and routing algorithm is also essentially implemented in terms of these remote calls.

Wybiral wrote the first demonstration of method invocation in a weekend, and I just spent some 8 hours maybe total writing the first version of the actual P2P network layer. Total code size is, without routing algorithm, maybe around 500 lines(!) once the object system and network object are integrated. Complete proof of concept is probably around 1k lines, and the rest is just (arbitrary 3rd party) extension over the core functions.

So... yeah... we wouldn't be doing that in C++ unless someone paid us big time... and still probably not :p

---

### Post by samjh on 2008-04-23
I like Python because:

1. It is simple to learn and use.

2. It is widely supported in the Free and Open Source development community.

3. Despite its simplicity, Python is very capable of producing complex software, as long as performance or safety is not critical.

4. It has a comprehensive built-in library.

---

### Post by Quikee on 2008-04-23
> **CptPicard said:**
> 
Wybiral and I have been hacking on an idea we got less than a week ago. It's a sort of "Remote Procedure Calls over P2P mesh" network where each user is an object of a dynamic datatype... think "serverless IRC where you can call methods on other people". You can freely extend your own object whichever way you want and the new methods are automagically exposed through reflection to be called remotely. Calls and return values are routed over the network, and routing algorithm is also essentially implemented in terms of these remote calls.

Wybiral wrote the first demonstration of method invocation in a weekend, and I just spent some 8 hours maybe total writing the first version of the actual P2P network layer. Total code size is, without routing algorithm, maybe around 500 lines(!) once the object system and network object are integrated. Complete proof of concept is probably around 1k lines, and the rest is just (arbitrary 3rd party) extension over the core functions.

Interesting idea. Do you have a home page / wiki page for more information and to track the progress?

---

### Post by Lau_of_DK on 2008-04-23
Picard,

Very impressive, almost as good as in C# on Windows. But then taking the collective wisdom of people in this thread, the reason for using Python is that its simple and easy to use, but you have to accept bad performance and safety (suppose you mean stability?).

To me it just seems like a bad trade - Take C# on Windows, its super fast, very intuitive, nice syntax and has great performance. When technology like that exists Python just seems like a major step backwards. But then again, im the conservative type :)

Is there a single advantage in using Python over C# ?

---

### Post by Quikee on 2008-04-23
> **Lau_of_DK said:**
> Picard,

Very impressive, almost as good as in C# on Windows. But then taking the collective wisdom of people in this thread, the reason for using Python is that its simple and easy to use, but you have to accept bad performance and safety (suppose you mean stability?).

Stability? Stability is not compromised, but yes - you compromise performance over ease and speed of programming. Even so - you still can optimize the slow parts if needed and re implement it in C. IMHO such a combination of high level and low level (when needed) language programming is much more powerful than programming in only one language. 

> **Lau_of_DK said:**
> 
To me it just seems like a bad trade - Take C# on Windows, its super fast, very intuitive, nice syntax and has great performance. When technology like that exists Python just seems like a major step backwards. But then again, im the conservative type :)

Is there a single advantage in using Python over C# ?

Nevertheless.. Python is IMHO still a lot easier and faster to work with than C# or Java. It is not a coincidence that dynamic languages like Python and Ruby are greatly being adopted by Microsoft to include them into .Net (IronPython, IronRuby) and Sun to include them in JVM (Jython, JRuby).

---

### Post by CptPicard on 2008-04-23
> **Quikee said:**
> Interesting idea. Do you have a home page / wiki page for more information and to track the progress?

No, I mean.. we're just fooling around with the idea. It *is* surprising how powerful and general the whole framework is turning out to be... things just nicely fall into place in the style of "oh, we'll just apply what we already have..."

If we get anything real out of this that is hackable by others, there may be an SVN up soon :)

> **Lau_of_DK said:**
> 
Very impressive, almost as good as in C# on Windows. But then taking the collective wisdom of people in this thread, the reason for using Python is that its simple and easy to use

Don't underestimate that "easy to use" part. The reason why we've got a nice prototype running so quickly is exactly the duck typing system and certain straightforwardness of expression... as far as performance goes, the flexibility of the object system helps us exactly where performance is not a critical issue. If there ever are performance issues, C is there for us... but of course, this is supposed to be a sort of experimental testbed anyway, so accessibility of code is a huge issue.

I imagine that as far as language features that make this possible are concerned, Java would be just as good a fit as C# -- just more verbose and rigid. Can't really pass judgement on C# on the issue as I've never used it though.


But you know, *the* ultimate language for this application would be Lisp -- the macro system would make mapping Lisp functions to nested network message objects so easy it's scary... too bad we suck at Lisp :p

I mean, if you have person A calling B.process(C.getData()), the current evaluation rules unfortunately transmit the data from C.getData() to A first, then to B, and then B processes it and returns result to A.

However, in Lisp you can just decompose the S-exps so that the innermost part -- '(getdata 'C 'someitem) -- is sent to B first and evaled there... :) incredibly powerful stuff you can do with higher level language constructs.

---

### Post by Lau_of_DK on 2008-04-23
> **CptPicard said:**
> No, I mean.. we're just fooling around with the idea. It *is* surprising how powerful and general the whole framework is turning out to be... things just nicely fall into place in the style of "oh, we'll just apply what we already have..."

If we get anything real out of this that is hackable by others, there may be an SVN up soon :)



Don't underestimate that "easy to use" part. The reason why we've got a nice prototype running so quickly is exactly the duck typing system and certain straightforwardness of expression... as far as performance goes, the flexibility of the object system helps us exactly where performance is not a critical issue. If there ever are performance issues, C is there for us... but of course, this is supposed to be a sort of experimental testbed anyway, so accessibility of code is a huge issue.

I imagine that as far as language features that make this possible are concerned, Java would be just as good a fit as C# -- just more verbose and rigid. Can't really pass judgement on C# on the issue as I've never used it though.


But you know, *the* ultimate language for this application would be Lisp -- the macro system would make mapping Lisp functions to nested network message objects so easy it's scary... too bad we suck at Lisp :p

I mean, if you have person A calling B.process(C.getData()), the current evaluation rules unfortunately transmit the data from C.getData() to A first, then to B, and then B processes it and returns result to A.

However, in Lisp you can just decompose the S-exps so that the innermost part -- '(getdata 'C 'someitem) -- is sent to B first and evaled there... :) incredibly powerful stuff you can do with higher level language constructs.

I think I'll read up on Lisp, it sounds interesting. In regards to C#, you should try it. I remember writing a multi-client tcp/ip server and client in a few hours. 

In regards to Python, do you guys have some online examples of simple projects demonstrating the power of the language?

By the by: I retract my statement about Eclipse. I tried compiling the latest version of QDevelop and it actually seems to be the best IDE for the job.

---

### Post by RIchard James13 on 2008-04-23
> **Lau_of_DK said:**
> And you're still welcome to drop some links or examples if you have seen something incredible done in Python.

I have a treeview/listview control. I need to fill it with data from a database. For each row returned by SQL query is placed as a parent node in the treeview. Then each row contains a Foreign Key to another table, I need to run another SQL query based on the first and add that data as a children node to the parent node, also I need to convert another foreign key into a category name for each child node.

Obviously the code could be refactored better, but I fail to see how converting this sort of code to C++ would make it easier to program.

[PHP]    def findCategoryFromFKID(self, FKID):
        """ return the category for a given PK_ExpenditureCategory """
        result = self.accountsDB.runQuery("SELECT txtCategory FROM tblExpenditureCategories WHERE PK_ExpenditureCategory = " + str(FKID))
        if len(result)<1:
            print "error"
            return "error"
        return list(list(result)[0])[0]
    
    def fillLstPayments(self):
        """ Fill the ListBox in the Payments Tab Pane and set its column headings """
        lstPayments = self.queryLstPayments()
        columns = ['Payment #','Total Amount','Date','Method','Payee','Split #','Amount','Category']
        self.addCellRenderers(self.lstPayments, columns)

    def queryLstPayments(self):
        """ Create a GTK treestore containing the values in the tblPayments 
            and then insert that into the Payments Pane ListBox """
        treestore = gtk.TreeStore(str,str,str,str,str,str,str,str)
        for result in self.accountsDB.runQuery("SELECT * FROM tblPayments"):
            payee = self.accountsDB.runQuery("SELECT txtPayee FROM tblPayees WHERE PK_Payee = '"+str(result[4])+"'")
            payee = payee[0][0]
            sub = treestore.append(None, [result[0],"$"+str(result[1]),result[2],result[3],payee,'','',''])
            for subresult in self.accountsDB.runQuery("SELECT * FROM tblPaymentSplits WHERE FK_PAYMENTS = "+str(result[0])):
                treestore.append(sub, ['','','','','',subresult[0],"$"+str(subresult[1]),self.findCategoryFromFKID(subresult[2])])
                                                      
        self.lstPayments.set_model(treestore)
        return self.lstPayments
[/PHP]

---

### Post by CptPicard on 2008-04-23
> **Lau_of_DK said:**
> I think I'll read up on Lisp, it sounds interesting.

You should, from my perspective it's closest to the "only language you'll ever need" than anything has come so far. Very high level -- essentially has all language mechanisms any language can have, and thus covers all paradigms -- with almost no syntax, plus compiles to native. The idea being that when the primitives are very strong, everything else is buildable... it's definitely the language that I aim to move to over the years, but I'm still too bad at it to actually implement anything...

---

### Post by Lau_of_DK on 2008-04-23
[PHP]
sub = treestore.append(None, [result[0],"$"+str(result[1]),result[2],result[3],payee,'','','']) 
[/PHP]

And you gents think that C++ is hard to read? What on earth does that line do? :)

Picard: Thanks alot for you time, you've explained things very well, so I've got some reading ahead of me :)

---

### Post by pmasiar on 2008-04-23
> **Lau_of_DK said:**
> It seems slow,...and the whole syntax of the language seems "immature" and disorganized.

1) the most important speed is "speed to the market", ask your boss. Python beats C++, hands down, no questions.

2) What "mature" language you designed? You have absolutely no clue what you are talking about, and options for this poll just prove it.

If you have as experienced as you pretend you are, you would find FAQ sticky and read "why I love/hate Python", where this horse was beaten to death, multiple times.

---

### Post by Lau_of_DK on 2008-04-23
> **pmasiar said:**
> 1) the most important speed is "speed to the market", ask your boss. Python beats C++, hands down, no questions.

2) What "mature" language you designed? You have absolutely no clue what you are talking about, and options for this poll just prove it.

If you have as experienced as you pretend you are, you would find FAQ sticky and read "why I love/hate Python", where this horse was beaten to death, multiple times.

You made a funny :)

1) True

2) The options for the poll were a joke (and a funny one)

3) Where do you find me pretending to be experienced?

And finally: Calm down friend, its not worth getting all tense about.

---

### Post by themusicwave on 2008-04-23
I do know C++, but I still like the snakes too.  

I haven't used C++ for anything major in a few years, but I am confident I could make a complete application in it if I needed to do so.  I regularly use Java and C# here at work.

I just finished a project at work entirely in Python.  In the end it was about 5,000 Lines of code.  Not all that big, but it worked great.  Even though I was learning Python and TKinter as I worked on the project it still only took me about 2 weeks to develop and a week to test/debug it.  I was working on other projects at the same time too.

This alone just shows me the huge productivity increase of Python.  Just imagine if I already knew Python to the point I know it now, I would have finished much faster.

The project was an installer for a system I built.  I felt Python was well suited to the task.  I made a simple UI in TKinter and then glued together about a dozen installers for various applications I needed.  I also moved files, edited config files and all that other fun stuff installs require.

I simply used IDLE to build the whole thing.  It was light weight, which is nice since my work computer is a single core 1.5Ghz with 512 MB or RAM running Windows XP.

Python is not the end all and be all of programming languages, but with an appropriate task it is quite nice.

---

### Post by Lau_of_DK on 2008-04-23
> **themusicwave said:**
> I do know C++, but I still like the snakes too.  

I haven't used C++ for anything major in a few years, but I am confident I could make a complete application in it if I needed to do so.  I regularly use Java and C# here at work.

I just finished a project at work entirely in Python.  In the end it was about 5,000 Lines of code.  Not all that big, but it worked great.  Even though I was learning Python and TKinter as I worked on the project it still only took me about 2 weeks to develop and a week to test/debug it.  I was working on other projects at the same time too.

This alone just shows me the huge productivity increase of Python.  Just imagine if I already knew Python to the point I know it now, I would have finished much faster.

The project was an installer for a system I built.  I felt Python was well suited to the task.  I made a simple UI in TKinter and then glued together about a dozen installers for various applications I needed.  I also moved files, edited config files and all that other fun stuff installs require.

I simply used IDLE to build the whole thing.  It was light weight, which is nice since my work computer is a single core 1.5Ghz with 512 MB or RAM running Windows XP.

Python is not the end all and be all of programming languages, but with an appropriate task it is quite nice.

I hear what youre saying, but Python seemed like an odd choise for an installer as Python itself requires an installer? Or atleast to have the interpreter compiled into your own program? Kinda defeats the purpose or have I completely misunderstood?

---

### Post by CptPicard on 2008-04-23
Another slightly Lisp-ish feature that Python has that I think you have overlooked are the tuple and list datatypes that are nicely built in and that have a lot of support all around the language. An associated feature is the generator which lets you "yield" values from the middle of a computation and then just return where you left off when you call the function again.

Lists in particular have list comprehensions which are a convenient form of syntactic sugar for both map and filter, which are also functional programming primitives... and are found in the language as is too. It really changes the way you design programs... you switch from designing a step by step process to transforming data. A very functional-programming like idea, that is.

Having proper first-class functions in the language is a big plus too, beats either passing function pointers or making some kind of object functors any day. I just wish that lambdas and thus closures weren't so nerfed that they just barely exist... it's my only serious gripe with Python's design really.

---

### Post by Lau_of_DK on 2008-04-23
> **CptPicard said:**
> 

Having proper first-class functions in the language is a big plus too, beats either passing function pointers or making some kind of object functors any day. I just wish that lambdas and thus closures weren't so nerfed that they just barely exist... it's my only serious gripe with Python's design really.

Nerfed? Another thing I never quite understood was the concept of Lambdas. Could you explain them as simple as possible please?

---

### Post by RIchard James13 on 2008-04-23
> **Lau_of_DK said:**
> And you gents think that C++ is hard to read? What on earth does that line do? :)

Actually I don't find C++ hard to read but for some applications C++ is more long winded to write programs in, for some applications Python can have problems.

That line for example adds data to the parent node in the treestore

[PHP]sub = treestore.append(None,[result[0],"$"+str(result[1]),result[2],result[3],payee,'','',''])  [/PHP]

sub is the parent node we are adding the data to

None is passed as the first parameter because there are no Nodes this hangs off

The reason for the [] brackets around the second parameter are that the function expects the data as a list and those brackets convert it to a list. Each item in the list is separated by a comma.

result is the tuple returned from the SQL query. A tuple is an immutable list. Normally the data looks like this
(1L, Decimal("17.85"), datetime.datetime(2008, 2, 17, 8, 32), 'CASH', 3L)

[x:y] can also be used as a splicing operator

so result[0] gives me the first field which is 1

result[1] gives me the second field which is 17.85 the "$"+str(result[1]) concatenates a dollar sign onto the front of the value

result[2] and result[3] are similar to result[0]

payee is a string from another database query based on the first actually result[4] fed back into the database to return the associated field

the three '' added at the end are spaces for the child node data.

Each part makes sense when you study and understand the language.

---

### Post by CptPicard on 2008-04-23
Lambda, and the associated closure, is probably the single most powerful feature in programming languages right after recursion... they feature prominently in functional programming and you really get desperately hooked on them once you start using them.

First of all we need to accept that in our language functions are first-class objects, that is, you can build second-order functions by passing a function as a parameter for another function. This is still doable in languages like C by passing the function pointer. So you can like write an iteration that goes over some collection and calls the function pointed to by the pointer.

Now, a "lambda" is an expression that creates an anonymous function "object" on the fly in the code you're in. So you can define a function inside some function, and then return that anonymous function to be passed around somewhere else in code.

The *closure* is the set of bindings that are in force at the time of the creation of the anonymous function. So, the environment the lambda is created in, is "captured" with the lambda and *can be referred to even after you've returned from the function where you create the lambda in*.

This is btw the functional-programming theoretical basis of object-oriented programming.. the closure are the variables of the object, the lambda function is the "message" interface that performs operations on the variables.

Consider this, sort of pseudocode in some language:

```

def make_counter(n):
  let i = n  // this is the captured variable
  my_function = lambda () { i = i + 1; return i }
  return my_function

```

Now in code...

```

counter = make_counter(0)  // counter is a parameterless function

counter()   // 1
counter()   // 2
counter()   // 3
... so on

```

Functors are superficially similar in C++, but a proper closure can "close over" any environment...

---

### Post by Lau_of_DK on 2008-04-23
> **CptPicard said:**
> Lambda, and the associated closure, is probably the single most powerful feature in programming languages right after recursion... they feature prominently in functional programming and you really get desperately hooked on them once you start using them.

First of all we need to accept that in our language functions are first-class objects, that is, you can build second-order functions by passing a function as a parameter for another function. This is still doable in languages like C by passing the function pointer. So you can like write an iteration that goes over some collection and calls the function pointed to by the pointer.

Now, a "lambda" is an expression that creates an anonymous function "object" on the fly in the code you're in. So you can define a function inside some function, and then return that anonymous function to be passed around somewhere else in code.

The *closure* is the set of bindings that are in force at the time of the creation of the anonymous function. So, the environment the lambda is created in, is "captured" with the lambda and *can be referred to even after you've returned from the function where you create the lambda in*.

This is btw the functional-programming theoretical basis of object-oriented programming.. the closure are the variables of the object, the lambda function is the "message" interface that performs operations on the variables.

Consider this, sort of pseudocode in some language:

```

def make_counter(n):
  let i = n  // this is the captured variable
  my_function = lambda () { i = i + 1; return i }
  return my_function

```

Now in code...

```

counter = make_counter(0)  // counter is a parameterless function

counter()   // 1
counter()   // 2
counter()   // 3
... so on

```

Functors are superficially similar in C++, but a proper closure can "close over" any environment...

Wow, thats a powerful way to work. I guess C++'s rigid ay of typecasting kinda gets in the way of Lambdas.

---

### Post by CptPicard on 2008-04-23
It's not an issue of types.. it's a fundamental feature of scope in the language :) You really need to start thinking in terms of bindings instead of variables on stack...

---

### Post by hums07 on 2008-04-23
Python is an interpreter while C/C++ is a compiler.
Program run in interpreter is usually slower than a compiled one but is usually easier to create.

---

### Post by pmasiar on 2008-04-23
> **hums07 said:**
> Python is an interpreter while C/C++ is a compiler.

Wrong. Python source is compiled to .pyc file - something like java class. .pyc can be compiled to binary if desired.

---

### Post by Can+~ on 2008-04-23
> **Lau_of_DK said:**
> [PHP]
sub = treestore.append(None, [result[0],"$"+str(result[1]),result[2],result[3],payee,'','','']) 
[/PHP]

And you gents think that C++ is hard to read? What on earth does that line do? :)

You don't know python, you're looking to an example extracted from a piece of code of someone else, seriously, have you read huge c++ projects and understood them immediately?

You can't base your opinion on someone else's code, make your own, your brain has enough space for handling both.

-I use C and python btw.

---

### Post by Tuna-Fish on 2008-04-23
> **Lau_of_DK said:**
> You actually made 2 statements that are in conflict with each other:
-1) "I know c++"
-2) "when you look at c++ you dont know whats going on"


No, they don't conflict. And if you ever had worked on a large development project (>10 developers, with some new coming and old leaving during the project), you'd know that.

Tell me what the following function does:
[php]
int addstuff(MyClass a, OldClass b)
{
if (a <= b):
return a->x + b;
else return a; 
}
[/php]

That's right, you can't. Not without knowing exactly how MyClass and oldClass work, and what implicit conversions exist. As a fun fact, <=, ->, and + could all have been overloaded. Or if they weren't but for some reason both types have conversion to bool, that might be bool math. or whatever.

The point is, you cannot just dive into a c++ codebase and expect to know what's happening by reading a few lines. In c, you can.

---

### Post by LaRoza on 2008-04-23
Not sure what the OP was thinking or if indeed (s)he was, but thread closed.

See the sticky about Programming Holy Wars OP.

---

