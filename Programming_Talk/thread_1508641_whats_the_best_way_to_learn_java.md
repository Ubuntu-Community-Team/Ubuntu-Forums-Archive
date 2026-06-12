---
title: "whats the best way to learn java?"
date: 2010-06-13
forum: Programming Talk
---

### Post by insanity99 on 2010-06-13
i want to learn java so need good reading material, some people have suggested 'head first JAVA' though it was written in 2005, what do you guys think is best?

---

### Post by simeon87 on 2010-06-13
Whatever approach you take, be sure to get reading material that covers Java 1.5 or higher as certain features were introduced in that version that you'll want to know. Other than that, there's no 'best' way of learning Java. Simply install Java, an IDE like Eclipse and work your way through exercises or try to make a basic program.

---

### Post by lykeion on 2010-06-13
It really depends on what your background is and what your purpose is.
Do you have any previous experience with Java? 
Do you have any previous programming experience in any language?
What is your purpose of learning Java? (learn a programming language, learn object-orientation, create your own applications, other)
If you answer these questions it would be easier to recommend some books/learning resources.

There's a 2nd edition of "Head First Java" (2009 or something), and if I was a new to Java I would do best in learn the foundation before worrying about keeping up to date with the latest features.

If you want a reference book to keep I'd suggest "Core Java Vol. 1" but first I'd recommend you find some beginner tutorial on the net and start with trying to write a simple application (maybe just in a text editor because a large IDE could take some time to learn as well)

---

### Post by limestone on 2010-06-13
[http://www.youtube.com/user/thenewboston](http://www.youtube.com/user/thenewboston)
He's got a ton of tutorials in many different programs and other stuff. And he's a good teacher to..

---

### Post by insanity99 on 2010-06-13
> **lykeion said:**
> It really depends on what your background is and what your purpose is.
Do you have any previous experience with Java? 
Do you have any previous programming experience in any language?
What is your purpose of learning Java? (learn a programming language, learn object-orientation, create your own applications, other)
If you answer these questions it would be easier to recommend some books/learning resources.

There's a 2nd edition of "Head First Java" (2009 or something), and if I was a new to Java I would do best in learn the foundation before worrying about keeping up to date with the latest features.

If you want a reference book to keep I'd suggest "Core Java Vol. 1" but first I'd recommend you find some beginner tutorial on the net and start with trying to write a simple application (maybe just in a text editor because a large IDE could take some time to learn as well)

ok here is my answer to your question: 
Do you have any previous experience with Java?
**none**
Do you have any previous programming experience in any language?
**very little, some python**
What is your purpose of learning Java? (learn a programming language, learn object-orientation, create your own applications, other)
**i simply want to learn a programming language as a hobby, not for any college work or anything, i enjoy learning new things in my own time.**

im not a big fan of video tutorials, dont know why but never liked them.

---

### Post by lykeion on 2010-06-13
Ok, let's see. 

Online resources:
[http://java.sun.com/docs/books/tutorial](http://java.sun.com/docs/books/tutorial)
[http://math.hws.edu/javanotes](http://math.hws.edu/javanotes)

Books :
(use free online resources before you spend big bucks on books, this one  is however good to keep as reference anyway)
Core Java Vol. 1 - Fundamentals

Head First Java is a good beginners book but I'd only recommend it if you like funny stories, quizzes and stuff to lighten up your learning experience.


IDE or text editor:
I'd use an ordinary text editor to write my first Java code. 
You don't need the advanced features of an IDE (refactoring, etc) in the beginning.
If you are a commandline-freak: vim or emacs
If you prefer gui: geany (if you've installed Java correctly there are handy buttons to compile and run the code)

Later on learn an IDE like Eclipse or Netbeans (personally I prefer IntelliJ IDEA - which actually is written in Java too!)

Hope this helps

---

### Post by ankit singh on 2010-06-13
I learnt java using "java for dummies" and when i had enough understanding of java,i went too "Java How to program by Deitel & Deitel".I bet anyone who religiously follow that book,will come out with a beautiful application.

However java is very easy.Best of luck and enjoy it.

---

### Post by KdotJ on 2010-06-13
I used a book called "Java Programming from the Beginning" It was old, doesn't even have Swing in it and it talks about Windows Me/2000. But it is good for learning the programming in general. Variables, data structures, control structures, objects, inheritance, polymorphism etc...

---

### Post by insanity99 on 2010-06-13
thanks for the replys guys, have i done something wrong here?


public class HelloWorld {
	public static void main(string[] args) {
		System.out.println("hello world!");
	}
}

---

### Post by cap10Ibraim on 2010-06-13
is it hard to learn Java if I know C  
I know that java is different it's object oriented unlike C ? 
I'm planning to learn C++ or Java this summer so what do you think ?
ps : I prefer java because i'll will take C++ next winter

---

### Post by trent.josephsen on 2010-06-13
> **insanity99 said:**
> thanks for the replys guys, have i done something wrong here?


public class HelloWorld {
	public static void main(string[] args) {
		System.out.println("hello world!");
	}
}

String is capitalized.

But I would encourage you not to learn Java, **yet**.  There are many things wrong with learning Java early; read [this](http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html) if you are interested to know one perspective.  Java has many strong features for enterprise development, but as a new programmer you won't have the understanding to use them properly and will even be encouraged to misuse them by most tutorials out there.  You don't need to be worrying about all that crap right now.

Stick with Python and learn to use it right.  Write several practical projects of a few hundred lines.  Use Python's standard capabilities to become acquainted with common programming tools, like dictionaries, regular expressions, networking, GUIs, and stuff like that.  While you're at it, learn to use a revision control system and administer a database.  These are just a few things that I would recommend to someone who wants to get into programming, before starting to learn Java.

---

### Post by insanity99 on 2010-06-13
the thing that discouraged me from python was the book 'think python' which most people recommend i read. it started of great, i understood everything i was reading. but the exercises required a lot more maths knowledge than i possess. this for example:

The volume of a sphere with radius r is 4/3 &#960; r3. What is the volume of a sphere with radius 5?
>>> pi = 3.1415926535897931
>>> r = 5
>>> 4/3*pi*r**3 # This is the wrong answer
392.69908169872411
>>> r = 5.0 # Radius needs to be a float
>>> 4.0/3.0*pi*r**3 # Using floats give the correct answer
523.59877559829886
>>> 

i completely get lost there, also there was an exercise where i had to print a grid. i understand how to define and call functions but i would have never been able to do what was required [http://pastebin.com/nZJtf3q2](http://pastebin.com/nZJtf3q2)

---

### Post by trent.josephsen on 2010-06-13
> **insanity99 said:**
> the thing that discouraged me from python was the book 'think python' which most people recommend i read. it started of great, i understood everything i was reading. but the exercises required a lot more maths knowledge than i possess. this for example:

The volume of a sphere with radius r is 4/3 &#960; r3. What is the volume of a sphere with radius 5?
>>> pi = 3.1415926535897931
>>> r = 5
>>> 4/3*pi*r**3 # This is the wrong answer
392.69908169872411
>>> r = 5.0 # Radius needs to be a float
>>> 4.0/3.0*pi*r**3 # Using floats give the correct answer
523.59877559829886
>>> 

i completely get lost there, also there was an exercise where i had to print a grid. i understand how to define and call functions but i would have never been able to do what was required [http://pastebin.com/nZJtf3q2](http://pastebin.com/nZJtf3q2)

If simple concepts (no offense) baffle you in Python, you'll never master Java.  Admittedly, the concept that math is done differently with integers vs. floating point numbers is foreign at first.  But -- guess what -- Java is *exactly the same*.  It's the same way with most languages.  Perl is an exception, which you may be interested in, but the bottom line is that these are simple concepts and switching languages isn't going to alleviate the need to know them.  "You'll never find a programming language that frees you from the burden of clarifying your ideas" (Randall Munroe).  Not even natural languages can compensate for the inability to work through a problem logically.

Fortunately for you, language skills and logical thinking can be learned.  But it won't be easy.  Only bad programming is easy.

That aside, I thought the solution to the grid-printing exercise was, indeed, unnecessarily complicated.

---

### Post by insanity99 on 2010-06-13
i do understand the math that is used in the language. i understand the difference between integers and floats perfectly. i know 7/3 will return an integer while 7.0/3 will return = 2.33333333. the thing i struggle with is the maths the author puts in his exercises 'The volume of a sphere with radius r is 4/3 &#960; r3. What is the volume of a sphere with radius 5?' makes no sense to me. after this point i start to feel like i'm hopeless, and lose my motivation to be honest.

---

### Post by trent.josephsen on 2010-06-13
> **insanity99 said:**
> i do understand the math that is used in the language. i understand the difference between integers and floats perfectly. i know 7/3 will return an integer while 7.0/3 will return = 2.33333333. the thing i struggle with is the maths the author puts in his exercises 'The volume of a sphere with radius r is 4/3 &#960; r3. What is the volume of a sphere with radius 5?' makes no sense to me. after this point i start to feel like i'm hopeless, and lose my motivation to be honest.
Forgive me if I fail to understand the nature of your problem.  Your profile calls you a "college student".  What's your major, if I may be so bold?

---

### Post by lykeion on 2010-06-14
> **trent.josephsen said:**
> But I would encourage you not to learn Java, **yet**.  There are many things wrong with learning Java early; read [this](http://www.stsc.hill.af.mil/CrossTalk/2008/01/0801DewarSchonberg.html) if you are interested to know one perspective.  Java has many strong features for enterprise development, but as a new programmer you won't have the understanding to use them properly and will even be encouraged to misuse them by most tutorials out there.  You don't need to be worrying about all that crap right now.

The article you are referring to is written by two CS professors who are President and VP of something called AdaCore, and they (surprise, surprise) advocate to learn Ada instead of Java. 
One of their argument is that it's too easy to create graphical programs with Java. 
Another argument is that the industry need programmers who know C and pointers.

I don't think theses arguments apply to a guy who wants to learn a language for fun and for his own sake.

> **trent.josephsen said:**
> Stick with Python and learn to use it right.

This I can agree with. Python is a very good language to learn to write good code.

But one thing that merits Java as first language, is that you need to think object-orientation almost from the start.

---

### Post by lykeion on 2010-06-14
> **insanity99 said:**
> the thing i struggle with is the maths the author puts in his exercises 'The volume of a sphere with radius r is 4/3 &#960; r3. What is the volume of a sphere with radius 5?' makes no sense to me.
Well, I guess to make real sense (like, heureka) of this you need to know how Archimedes came up with the pi constant. 
But for the purpose of the exercise you just need to see it as a formula in which you put in the radius and get the volume.

---

### Post by simeon87 on 2010-06-14
> **lykeion said:**
> But one thing that merits Java as first language, is that you need to think object-orientation almost from the start.

That, indeed, is a very good thing. But after that, learn a language where not everything is an object.. Java was my first language too and it forces you to make everything an object. It took quite a while to unlearn that habit, because not everything needs to be seen as an object.

---

### Post by insanity99 on 2010-06-14
> **trent.josephsen said:**
> Forgive me if I fail to understand the nature of your problem.  Your profile calls you a "college student".  What's your major, if I may be so bold?

CISCO networking CCNA, finished semester 2.

ok, i will stick with python since most seem to agree it's a better first language.

---

### Post by trent.josephsen on 2010-06-14
> **lykeion said:**
> The article you are referring to is written by two CS professors who are President and VP of something called AdaCore, and they (surprise, surprise) advocate to learn Ada instead of Java. 
One of their argument is that it's too easy to create graphical programs with Java. 
That is not true.  They state that Java is popular because it is easy to create graphical programs, and go on to say that Java is not appropriate for beginners because it does not adequately prepare programmers for advanced topics.  Nowhere do they argue that ease of creating graphical programs is in itself a cause for concern.
> Another argument is that the industry need programmers who know C and pointers.

I don't think these arguments apply to a guy who wants to learn a language for fun and for his own sake.
I concur.  But that is only a single point of their argument.  Also, I think there are other pitfalls of Java not enumerated in that essay, which is why I said "one perspective".  One additional pitfall would be unnecessary complexity, of which mandatory OO is the greatest perpetrator.  My first "real" language was Java and, like simeon87, I struggled with *non*-OO relationships when I learned another language (Perl).  Many if not most programs do not benefit from OOP.

Personally, I would recommend learning C anyway (but not as a first language), not necessarily because the industry needs C programmers (which is true) but because it's fun.  What's more, C is much closer to the hardware than most HLLs, and the experience will make you a better programmer.  But that's a topic for another day.

---

### Post by KdotJ on 2010-06-14
I agree with the OO issue, as I have only ever really 'programmed' anything useful using java and before that C#. I find the idea of non-OO programming somewhat alien. I like python and am trying out more and more things in it as I play around, I like the way that it does not force  a particular paradigm on you and makes it a great language to learn as a beginner. 

Personally I do understand the point that the article addresses, but I don't agree with them that java is a bad choice for learning as a first language

---

### Post by Some Penguin on 2010-06-14
> **insanity99 said:**
> i do understand the math that is used in the language. i understand the difference between integers and floats perfectly. i know 7/3 will return an integer while 7.0/3 will return = 2.33333333. the thing i struggle with is the maths the author puts in his exercises 'The volume of a sphere with radius r is 4/3 &#960; r3. What is the volume of a sphere with radius 5?' makes no sense to me. after this point i start to feel like i'm hopeless, and lose my motivation to be honest.

Basic calculus.  Univariate integration, Pythagoras and the formula for the area of a circle will quickly get you there.

Imagine a sphere of radius R centered at the origin of 3D space.  You can compute the volume by integrating over Z in [-R,R].  For any given Z value, the radius of the circle in that plane = sqrt(R^2-Z^2) per Pythagoras.

```

volume = integral_{-R,R} (pi * sqrt(R^2-Z^2)^2) dZ   
            = pi * integral_{-R,R} (R^2 - Z^2) dZ       
            = pi * (integral_{-R,R} R^2 dZ  - integral_{-R,R}Z^2dZ)   
            = pi * (2R^3 - (1/3 * R^3 + 1/3 * R^3))   
            = 4/3 * pi * R^3

```

Assuming I've done my calc correctly, of course -- haven't done much integration for years.

---

### Post by trent.josephsen on 2010-06-14
> **Some Penguin said:**
> Basic calculus.  Univariate integration, Pythagoras and the formula for the area of a circle will quickly get you there.
<math snipped>


Your derivation appears correct, but I don't think it helps much.  I suspect, although I could be wrong, that it's not the derivation of the formula that is confusing insanity99, but something else, possibly in the wording of the question.  It's also possible that the OP is simply not familiar with algebra, which is in truth pretty common.

---

### Post by insanity99 on 2010-06-15
i'm just gonna say it, when it comes to maths i suck. because of my CISCO CCNA course i have to know binary maths and i had to learn to convert binary to hex, and i did but it took be twice as long and twice the effort than the rest of my class.i have a MLD but it's never held me back to much, just takes me a bit longer thats all.

i started reading 'A Byte of Python' i think it's an amazing book. really well paced learning and amazing examples.

---

### Post by Vox754 on 2010-06-15
> **Some Penguin said:**
> Basic calculus.  Univariate integration, Pythagoras and the formula for the area of a circle will quickly get you there.

Imagine a sphere of radius R centered at the origin of 3D space.  You can compute the volume by integrating over Z in [-R,R].  For any given Z value, the radius of the circle in that plane = sqrt(R^2-Z^2) per Pythagoras.

```

volume = integral_{-R,R} (pi * sqrt(R^2-Z^2)^2) dZ   
            = pi * integral_{-R,R} (R^2 - Z^2) dZ       
            = pi * (integral_{-R,R} R^2 dZ  - integral_{-R,R}Z^2dZ)   
            = pi * (2R^3 - (1/3 * R^3 + 1/3 * R^3))   
            = 4/3 * pi * R^3

```

Assuming I've done my calc correctly, of course -- haven't done much integration for years.
<snip> No calculus is needed.

The problem is NOT about deriving the formula, the problem is simply using the formula.

```

volume(R) = 4/3 * pi * R^3

volume(5) = 4/3 * pi * (5^3) = 523.598775667

volume(10) = 4/3 * pi * (10^3) = 4188.790205333

etc.

```

<snip>

---

### Post by Boyohazard on 2010-06-25
> **KdotJ said:**
> I agree with the OO issue, as I have only ever really 'programmed' anything useful using java and before that C#. I find the idea of non-OO programming somewhat alien. I like python and am trying out more and more things in it as I play around, I like the way that it does not force  a particular paradigm on you and makes it a great language to learn as a beginner.

Don't look now, but [everything in Python is an object]("http://diveintopython3.org/your-first-python-program.html#everythingisanobject") ;)

---

### Post by KdotJ on 2010-06-25
> **Boyohazard said:**
> Don't look now, but [everything in Python is an object]("http://diveintopython3.org/your-first-python-program.html#everythingisanobject") ;)

lol "AHH DAMMIT!!"
I'm not surprised at all though.... but you know what I meant lol, java is object crazed

---

### Post by trent.josephsen on 2010-06-25
In Java, although not "everything" is an object, classes are mandatory (and it makes for some pretty hideous code when you need to go procedural).  In (say) Perl, OOP is optional, and using it is ugly.  Some languages make it downright impossible to use OOP.  Python is great in that it stays reasonably not-ugly no matter what paradigm you choose for your own code (as long as you follow good practices, which is a whole 'nother question).

---

### Post by phrostbyte on 2010-06-25
> **insanity99 said:**
> i'm just gonna say it, when it comes to maths i suck. because of my CISCO CCNA course i have to know binary maths and i had to learn to convert binary to hex, and i did but it took be twice as long and twice the effort than the rest of my class.i have a MLD but it's never held me back to much, just takes me a bit longer thats all.

i started reading 'A Byte of Python' i think it's an amazing book. really well paced learning and amazing examples.

You must start off improving your mathematical skills, because math is the foundation of computer science.

---

