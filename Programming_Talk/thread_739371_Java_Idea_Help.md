---
title: "Java Idea Help"
date: 2008-03-29
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-03-29
Hi i am looking for a Java program idea.

I am fairly Java proficient and would like an idea that could stretch my skills.

I have been making programs but none have been to meaningful other that a way to fill my hard drives.

I accept all ideas except for servlets because i don't know how to do those. But please explain in fair detail.

Also if it involves Artificial Intelligence then you can't expect much because AI is a little hard for me but do able.

Thank You

---

### Post by CptPicard on 2008-03-29
I'd suggest you move on to some other language. Honestly, Java is a boring workhorse language, but you can't really stretch your mind with it because the language's constructs are just simply too plain :)

Being a functional programming geek and wanting to be able to run my stuff on a VM (because we've got a heterogenous machine base), I'm currently looking into [Scala]("http://www.scala-lang.org/docu/files/ScalaByExample.pdf").

---

### Post by LaRoza on 2008-03-29
> **Mr.Macdonald said:**
> Hi i am looking for a Java program idea.

I am fairly Java proficient and would like an idea that could stretch my skills.

I have been making programs but none have been to meaningful other that a way to fill my hard drives.

I accept all ideas except for servlets because i don't know how to do those. But please explain in fair detail.

Also if it involves Artificial Intelligence then you can't expect much because AI is a little hard for me but do able.

Thank You
Based on this, I would suggest you learn how to do servlets.

You said:

* I am fairly Java proficient
* [I] would like an idea that could stretch my skills

Learning how to use Java in a new area would fulfill this.

---

### Post by pmasiar on 2008-03-29
Servlets in Java are horribly boring and use tons of boilerplate code. Avoid Java for web apps if you can! Web frameworks for Java are designed for sites with 10K pages and complicated design, but it does not sacle down: to make simple app you have almost all the config tricks as big app does (only for smaller amount of pages). That's why so many Java web app developer stampeded to Ruby on Rails.

For something cool to do in Java, look at Google's Android: API for opensource mobile phones. Port some games to it.

Or learn something useful: Learn RoR, or even better, Python and TurboGears or Django. Satchmo is whole e-commerce in Python/Django. And learn AJAX.

---

### Post by Mr.Macdonald on 2008-03-30
A few questions


Does RoR need an interpreter like a Java servlet and tomcat
Does RoR output html or a similar like PHP ( i didn't like PHP, to complicated )
Is RoR simpler than PHP and does it come with Documentation like java docs

Is Ajax what google uses
Can Ajax manipulate files on my server ( read / write )
Does Ajax need an interpreter like a Java servlet and tomcat

Is python like perl because i have heard that perl is complex
Is python interpreted
Is it better than Java in your opinion with backing please
Does python need an interpreter like a Java servlet and tomcat

Is Turbo gears all web
Does it need an interpreter like a Java servlet and tomcat

which is better Django or Turbo


[SIZE="4"]Finally What should i learn first if i would like to make my website better ( don't laugh ) [http://macdonald.webhop.org]("http://macdonald.webhop.org")
And why does everyone seem to dislike java[/SIZE]

I have found java capably of everything i have wanted to do except simple web application and java can do servlets

---

### Post by LaRoza on 2008-03-30
> **Mr.Macdonald said:**
> 
Does RoR need an interpreter like a Java servlet and tomcat
Does RoR output html or a similar like PHP ( i didn't like PHP, to complicated )
Is RoR simpler than PHP and does it come with Documentation like java docs

Is Ajax what google uses
Can Ajax manipulate files on my server ( read / write )
Does Ajax need an interpreter like a Java servlet and tomcat

Is python like perl because i have heard that perl is complex
Is python interpreted
Is it better than Java in your opinion with backing please
Does python need an interpreter like a Java servlet and tomcat

Is Turbo gears all web
Does it need an interpreter like a Java servlet and tomcat

which is better Django or Turbo

And why does everyone seem to dislike java[/SIZE]

I have found java capably of everything i have wanted to do except simple web application and java can do servlets

Ruby needs the Ruby interpreter. Obviously, RoR would output code for web pages, how else would it work? I don't know if it is simpler, look it up.

Anyone can use Ajax, and google amoung others use it. Ajax is a client side script that communicates with a server. It can send information to the server and a script on the server can do the server side manipulations. Ajax is client side. (Something needs to be on the server though)

Python is like Perl, in purpose and general design. They have different philosophies, and were designed at different times. Both are interpreted, and both can be compiled to byte code. Python can be used on the Java platform, with Jython. Is Python better? It is a tool. What is better, a 3/8" or 1/4" wrench?

Turbogears uses Python, it is just a framework.

They are both frameworks try them out and see for yourself. (I don't use them)

Java is needlessly complex, and has a very difficult to follow standard library. A simple program requires enough code to kill an elephant, and there are other languages that are easier to use. Java has great uses in many areas, embedded and such.

---

### Post by BlackJavaBean on 2008-03-30
> **Mr.Macdonald said:**
> A few questions
Is python like perl because i have heard that perl is complex

Yes, Python and Perl are similar - but they have some pretty major differences. But with a background in Java - either of these shouldn't be hard to pick up fairly quickly. Perl is A LOT easier to work with compared to Java, because it is weakly typed (I believe the only two types are $calars and @rrays). With Java under your belt, though you may find yourself trying to declare Java primitives in your Perl code for a while. Complexity is all relative in most modern languages.

---

### Post by LaRoza on 2008-03-30
> **BlackJavaBean said:**
> Yes, Python and Perl are similar - but they have some pretty major differences. But with a background in Java - either of these shouldn't be hard to pick up fairly quickly. Perl is A LOT easier to work with compared to Java, because it is weakly typed (I believe the only two types are $calars and @rrays). With Java under your belt, though you may find yourself trying to declare Java primitives in your Perl code for a while. Complexity is all relative in most modern languages.

I like Python's typing system better than Perl's. Both are dynamic, but Python is strongly typed, whereas Perl is weakly typed.

There are a bunch of data types in Python (and Perl), but you do not need to explicitly declare them as such.

```

>>> x = 2
>>> type(x)
<type 'int'>
>>> y = 1.
>>> type(y)
<type 'float'>
>>> z = "LaRoza"
>>> type(z)
<type 'str'>
>>> 

```

---

### Post by themusicwave on 2008-03-30
There is a lot of cool things you can do with Java.  Java is definitely a workhorse, but sometimes that is what you need.

If you want to expand your Java skills, learn some decent design skills and have fun all at the same time I recommend the book _Developing Games In Java_  by David Brackeen.

It will take your through the creation of a 2D side scroller all the way to a 3D First Person Shooter all in Java.

Many will tell you C or C++ is the only langauge for games, but Java can perform fairly well there too.  Also, sometimes it is fun to push the limits a bit.

---

### Post by CptPicard on 2008-03-30
> **themusicwave said:**
> There is a lot of cool things you can do with Java.  Java is definitely a workhorse, but sometimes that is what you need.


Yeah, it's a workhorse and even I use it as just that. But I must admit that the language's limitations are very severe -- you can't do the kind of low-level hacking you can do with C or C++, and you can't do the kind of high-level hacking you can do with HLLs. It just forces you to go "meh" all the time in all directions.

Scala seems like a step in the right direction for the JVM though... check out the Path Finding programming challenge, I just submitted my own, it's in Scala.

---

### Post by Mr.Macdonald on 2008-03-30
**Python**

I have been messing around with python and i like it

How does the GUI compare to like Java or C++, does Python have its own GUI library as Java does (i think it does) or does it Interpreter use the systems GUI.

I thought python was strongly type but when i do simple scripts it isn't
this is what i do in terminal
> 
$python
>>>test="hello"
>>>print test
hello
>>>test = 1
>>>test * 2
2

Not to strongly typed

**C++ or C**

Is C++ as annoying as C, i have done some C and the core dumps and other errors are endless ( maybe its just me ). Using C++ will i get the same deal?

---

### Post by CptPicard on 2008-03-30
> **Mr.Macdonald said:**
> 
How does the GUI compare to like Java or C++, does Python have its own GUI library as Java does (i think it does) or does it Interpreter use the systems GUI.

It's got bindings to all kinds of GUI toolkits. There is no one single "Python GUI library" however in the sense of Swing...

> 
I thought python was strongly type but when i do simple scripts it isn't
this is what i do in terminal

It is. But it is not statically typed, which is what you're probably thinking. You do not need to specify types, but the types are there under the hood and you will get an error if you try doing something that the types do not allow.

> 
Is C++ as annoying as C, i have done some C and the core dumps and other errors are endless ( maybe its just me ). Using C++ will i get the same deal?

"It's just you", but that's how it is with C and C++.. that's why a lot of people prefer a higher-level language...

---

### Post by themusicwave on 2008-03-30
I have been learning Python and I do enjoy the language.

I think it is definitely a great language for many uses.  I know a handful of other languages, probably being strongest in Java right now.

In time you come to realize that languages are really just tools to an end.  Some are stronger to different ends.  If you do progress from Python to Java some things will seem somewhat different.  These aren't necessarily good or bad, just different.

Python differences from Java:

Java is statically types, python is not. Both are still strongly typed.
Java has a different approach to Object Oriented Design.
Java has interfaces, python does not.
Java has abstract classes python does not.
Python has multiple inheritance of classes, Java only supports this for interfaces.
python code tends to be shorter.

Those are just a handful of major differences I have noticed there may be (and most likely are) more.

My advice though it to get good at a language before you hop around.  Many programmers tend to language jump and end up being ok at 10  languages instead of good at 3.  I prefer the second, but it is fun to try new things.

As for your page in general, I would suggest a different color scheme unless you love pink.  Also, simply stating that you passworded your music will not prevent you from being sued potentially.  Whether you locked it up or not you still posted it on a webserver...

---

### Post by Mr.Macdonald on 2008-03-30
Ooh thanks i don't want to be sued but what if i left it in a secret directory that know one knows about and its not posted

about the color scheme i just never really care to much but ill change it

i didn't think i put my site up on this forum but i guess i forgot
and also those Programs are far old and i just never put my new ones up because i don't care enough to
And you got it backwards i am progressing to Python from Java

back to real matters

In python i made a test Module and i can't figure how to import it

its called ~/Desktop/Programs/Python/test.py
I CD over to it then invoked python interpreter and tried to import it but i don't think it worked because my def's aren't executing?? i get this error, the def should display good bye in **es**panol
> 
>>> import test
>>> goodBye('es')
Traceback (most recent call last):
 File "<stdin>", line 1, in <module>
NameError: name 'goodBye' is not defined


heres my code if thats wrong

> 
def hello(lang):
[INDENT]if lang == 'en':[/INDENT]
[INDENT][INDENT]print 'hello'[/INDENT][/INDENT]
[INDENT]elif lang == 'es':[/INDENT]
[INDENT][INDENT]print 'hola'[/INDENT][/INDENT]

def goodBye(lang):
[INDENT]if lang == 'en':[/INDENT]
[INDENT][INDENT]print 'good bye'[/INDENT][/INDENT]
[INDENT]elif lang == 'es':[/INDENT]
[INDENT][INDENT]print 'adios'[/INDENT][/INDENT]


for some reason python compiled (is that the right word) it to a .pyc

By the way Thank You for all your help

---

### Post by pmasiar on 2008-03-30
you need **test.goodBye()**

**import test ** defined only name 'test', but nothing inside it.

or you can do **from test import goodBye**, this defines 'goodBye', but 'test' is not bound to anything.

---

### Post by pmasiar on 2008-03-30
Python is strongly dynamically typed. "2" + 3 is error; weakly typed languages like Perl will calculate 5. But name does not have type info associated with it, only the object has, so you can do x = 2 and x = "3" later. "Dynamic" means that program checks if object has requested method at the runtime, it it does, all is fine. So if you want to define your own say file-like object, you need to define only methods you want to use, not all interfaces somebody decided it should have. Much simpler. And Python allow operator overload, you can define +, looping, itaration etc for your own objects just like standard objects, it makes code more readable.

Because object holds it's type info, you can put multiple objects into a list or other collection, and when you pull them out they "remember" type info and you don't have to cast it like in Java - major simplification. List processing in Python is vastly superior to Java's.

And don't forget exceptions. Java's statically checked exception is major pain, and  people for quick code just catch and ignore all exceptions - which exactly defeats the purpose. Python lets you ignore exceptions you don't want to handle, but if it occurs, it will let you know with full stack trace - and you can decide on which level you want to hande it.

No, programming in Java is so much more hard work, for no additional gain. I try to avoid Java if I can.

---

### Post by jespdj on 2008-03-31
> **Mr.Macdonald said:**
> How does the GUI compare to like Java or C++, does Python have its own GUI library as Java does (i think it does) or does it Interpreter use the systems GUI.
As said above there is no single GUI library for Python, but if you're looking to develop a GUI application for Ubuntu, have a look at [PyGTK](http://www.pygtk.org/), the most used Python binding for GTK+.

---

### Post by LaRoza on 2008-03-31
> **pmasiar said:**
> Python is strongly dynamically typed. "2" + 3 is error; weakly typed languages like Perl will calculate 5.


Sometimes you "23" depending on the language.

---

### Post by LaRoza on 2008-03-31
> **Mr.Macdonald said:**
> 
How does the GUI compare to like Java or C++, does Python have its own GUI library as Java does (i think it does) or does it Interpreter use the systems GUI.


Python uses Tkinter for the standard GUI toolkit. Tkinter isn't pretty, but it works on all platforms that have standard Python. 

Tkinter uses Tcl/Tk.

Python also works with PyQT (QT), PyGTK (GTK), wxPython (wxWidgets), and probably others.

---

### Post by Zugzwang on 2008-03-31
Dear OP,

If you are skilled in Java, there is normally no need to switch to another language. A lot of people here dislike Java, but once you got used to it, you can do a lot of stuff with it.

Also, many of the disadvantages mentioned are a matter of taste. I'll give some examples by quoting a post of pmasiar (just as example!)
> **pmasiar said:**
> Because object holds it's type info, you can put multiple objects into a list or other collection, and when you pull them out they "remember" type info and you don't have to cast it like in Java - major simplification. List processing in Python is vastly superior to Java's.

This is a little bit outdated. Starting with Java 5, you have generics which solves this issue except you want to deliberately store Object of different types into a collection and still use the "special" functions of those (so not always using polymorphism if the objects are of different type). This however is often referred to as bad coding style (in literature).

> **pmasiar said:**
> Because object holds it's type info, you can put 
And don't forget exceptions. Java's statically checked exception is major pain, and  people for quick code just catch and ignore all exceptions - which exactly defeats the purpose. Python lets you ignore exceptions you don't want to handle, but if it occurs, it will let you know with full stack trace - and you can decide on which level you want to hande it.

If you don't want to catch an exception, you can encapsulate it into a RuntimeException. Personally I like static checking because this way I can't forget about exceptions. Furthermore, you can group exceptions by deriving them from self-made base classes to simplify catching. This way, you don't have to type so much. A lot of beginners make the mistake to have empty catch-blocks (and pmasiar probably has seen a lot of them even in "enterprise" code which may easily cause a dislike in Java. I once had the opportunity to rate eight student projects. Six of them didn't catch the IOExceptions when saving a file). 

A third point (I forgot whose has risen it) was the complicated use of the libraries included. This is again a matter of taste. Once you got used to the Java style you find your needed functions quite fast (except for image manipulation, however)! Also the refactoring & GUI building support of Netbeans (never used Eclipse but at least the refactoring is often said to be even superior) raises your productivity by far. The debuggers are also quite mature. 

Some of the limitations of Java will hopefully be fixed with the upcoming releases of Java (support for functional programming, for example).

Conclusion: Please not that the language question is *really* a matter of taste. Of course there are advantages & disadvantages but this applies to any language. Python is preferred by a lot of people here because they are already used to that. Furthermore, a lot of Ubuntu's internals are made with Python. The concerns raised about Java by pmasiar (and others) are definitely true but Python isn't perfect as well.

---

### Post by pmasiar on 2008-03-31
Seems like we could use "why I love/hate Java" thread, linked from FAQ. 

But I recall "Why...Python" and "Why...Perl", and they are missing from FAQ too. :-(

---

### Post by LaRoza on 2008-03-31
> **pmasiar said:**
> Seems like we could use "why I love/hate Java" thread, linked from FAQ. 

But I recall "Why...Python" and "Why...Perl", and they are missing from FAQ too. :-(

They must have gotten lost in an edit, I will look into it.

I am not sure where they went...

---

### Post by Mr.Macdonald on 2008-03-31
Hey in Python how do you set the file to null or ""

f.write("")

????????

---

### Post by LaRoza on 2008-03-31
> **Mr.Macdonald said:**
> Hey in Python how do you set the file to null or ""

f.write("")

????????

You want to erase a file? 

```

open(<filename>,'w')

```

It will create it if there is no file.

---

### Post by Mr.Macdonald on 2008-04-02
no clear all the content

if

f.write("")

then nothing happens

---

### Post by LaRoza on 2008-04-02
> **Mr.Macdonald said:**
> no clear all the content

if

f.write("")

then nothing happens

What do you want to do?

If you have a file, and you want to make it blank, my above code with work.

---

### Post by Mr.Macdonald on 2008-04-02
Sorry i got a id10t error

it worked, thanks

---

### Post by runningwithscissors on 2008-04-03
You know, I used to think that Java isn't really a bad language.

but I've recently been put on this project where the "experienced Java developers" are as thick as a bag of bricks, want class diagrams, UML, SAS/SSS/STS/some-other-three-letter-acronym-****, eclipse, a billion plugins, and endless discussions on "communication" instead of ******* writing code that works!

I hate Java now. And now they want to do "extreme programming". Extreme programming, my balls.

---

### Post by Mr.Macdonald on 2008-04-03
Dude i am on your level ... kind of,

i recently took a programing class at my high school because i thought i would learn something cool, i learned nothing at all. the teacher their is (explicate word).

His goal was to teach TRUE programming with (don't cry) Visual Basic

some things he demanded were
[LIST]
[*]Analysis's of our problem and goal
[*]Variable names to include their type (int intTest = 90) maybe this is a good idea but he is the only one i have ever heard this from
[*]Comment what the benefit that line of code was instead of the function
[*]Lists of every function variable and structure we were going to use
[*]We also needed fake code for everything from sorting to animation
[*]After we did this we were required to get our project approved before coding
[/LIST]

I used to like that teacher because he was funny but now i HATE him

as for Java don't listen to those guys. I feel that the only projects you would need to do that is corporation or large scale stuff. I personally have only written stuff like that when i had a great idea in a class or somewhere else.

I say that diagrams are a waste of my time and why communicate if your doing nothing

---

### Post by CptPicard on 2008-04-03
> **Mr.Macdonald said:**
> 
I say that diagrams are a waste of my time and why communicate if your doing nothing

Well, maybe not totally, but... mostly yes, when you're learning how to become competent.. :) most CS programs have been watered down by corporate needs in the past 10 years. It's sad, but there still are those that actually teach you something you are able to apply on your own.

---

### Post by LaRoza on 2008-04-03
> **Mr.Macdonald said:**
> 
some things he demanded were
[LIST]
[*]Analysis's of our problem and goal
[*]Variable names to include their type (int intTest = 90) maybe this is a good idea but he is the only one i have ever heard this from
[*]Comment what the benefit that line of code was instead of the function
[*]Lists of every function variable and structure we were going to use
[*]We also needed fake code for everything from sorting to animation
[*]After we did this we were required to get our project approved before coding
[/LIST]

I say that diagrams are a waste of my time and why communicate if your doing nothing

Sounds like cargo cult programming. There are many ways of structuring development, and most have their place, but to teach them without saying WHY or other methods is just foolish.

---

### Post by CptPicard on 2008-04-03
> **LaRoza said:**
> Sounds like cargo cult programming. There are many ways of structuring development, and most have their place, but to teach them without saying WHY or other methods is just foolish.

Sounds just like your typical code monkey school education, sadly...

---

### Post by LaRoza on 2008-04-03
> **CptPicard said:**
> Sounds just like your typical code monkey school education, sadly...

Not sadly, those who want to learn will find a way.

I don't really have sympathy for those who blame bad teachers, as I started when I had no internet connection, and no money, and just Windows, and a C++ book. (Oh how misguided I was...)

(I do have sympathy for those that have to be in the class, but it doesn't justify not learning.)

---

### Post by CptPicard on 2008-04-03
> **LaRoza said:**
> 
I don't really have sympathy for those who blame bad teachers...

I do know you're remarkable, but you know, if there is supposedly some form of education, it should strive to work for it to be worth anything. For example, you can't set up an university and then just blame it all on the students if it all goes to hell... there comes a time to look in the mirror.

---

### Post by LaRoza on 2008-04-03
> **CptPicard said:**
> I do know you're remarkable, but you know, if there is supposedly some form of education, it should strive to work for it to be worth anything. For example, you can't set up an university and then just blame it all on the students if it all goes to hell... there comes a time to look in the mirror.

I guess I have a very different perspective, as I never took a class in it, and only do it because I enjoy programming.

I don't know if I could take a "Intro to Programming 101" class. Either the teacher would hate me, or I would hate the teacher.

---

### Post by CptPicard on 2008-04-03
Of course, you're in some in some sense the typical "CS student worth educating". Basic programming is something one has to be able to pick up by oneself in the first place, and you also need to be able to develop your own skills as you go. The real evolution of your mind really happens during the advanced classes, and in particular when you get taught about "problems" in general, instead of something you would call "programming"...

I mean, I didn't learn anything in my studies during my Bachelor's -- that's when you "learn to be a general coder". It was the years I spent getting the Master's I actually met interesting professors who fooled around with my mind enough to give me the ability to grab all sorts of problems on my own and see what I can make of them.

So... I personally feel that pretty much all CS education up to Bachelor's could easily be dumped because you can learn it on your own, and if you're worth your salt, you should be able to in the first place.

However, when you're trying to educate, you need to try to perform yourself -- the onus is not simply on your students to learn. I have a feeling that a lot of people are really failing at this task in our field... then again, those who are educating up to Bachelor's are wasting their effort.

---

### Post by themusicwave on 2008-04-04
Well Said Capt.

Programming education is a bit sad/silly here in the US.  Many professors really have never programmed anything in the real world.  They just know the theory, which is ok until you try to actually build something.

I was lucky to be in the school of engineering where they made us build things and actually finish them.  They made us take the hard math and physics classes we hated, but we did learn to think.

My personal favorite weir prof was a guy who would check our variable names and comments for typos.  Each misspelling was 10% off.  You were not allowed to use any abbreviations.  I had to paste my code into open office and try to spell check it...not pretty...

In the end though een if you have bad profs you will learn if you have the aptitude for it.  Plus sometimes you will get a great prof who will teach you a lot.  One of my favorite profs would spend hours with me after class answering random questions that didn't pertain to class.  He was just happy I wanted to learn and tried to help me along.

---

### Post by CptPicard on 2008-04-04
Musicwave,

I agree with you up to a point. I'm more of a theorist myself, and do not really believe in "building it all the way until it works". Personally, I always stop building anything I start as a hobby once it works up to my satisfaction, and once I feel I have got the learning experience from it I can :)

Theory is Good as you say yourself as regards the hard maths and physics classes. Their purpose is to grow character. :) But my point really was that the "building it until it works" part is what you're supposed to become competent in by yourself. It's the high-level abstract thinking one needs to be taught at.

---

### Post by pmasiar on 2008-04-04
In academia, they teach you to solve problem right way. In practice, your focus is on solving right problem :-)

Programming is a skill, and you can learn it only by doing it. Open source is great because you can read snippets of other smart people's code and learn from it - stuff what might take you long time to figure out by yourself.

---

