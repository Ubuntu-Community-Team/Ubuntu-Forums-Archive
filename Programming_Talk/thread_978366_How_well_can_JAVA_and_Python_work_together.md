---
title: "How well can JAVA and Python work together"
date: 2008-11-11
forum: Programming Talk
---

### Post by Kilon on 2008-11-11
I know there is a project called Jython , that uses JAVA from inside Python. I was wondering if I can take advantage of both JAva libraries and enormous documentation and python simple syntax and ease of use. 

I guess it should be possible , but I was wondering how well it works on UBUNTU and MAC OS.

---

### Post by Sorivenul on 2008-11-11
Actually just tried this last month.  Works fine on Ubuntu. I still prefer pure CPython.
  
Some insight and resources:
[The Official Jython User Guide]("http://www.jython.org/Project/userguide.html")
[From IBM]("http://www.ibm.com/developerworks/java/library/j-jython.html")
[A nice Jython introduction]("http://www.javalobby.org/articles/jython/")

---

### Post by loell on 2008-11-11
that, will entirely depend on the specific java based components that you'll be using for desktop integration.

---

### Post by Kilon on 2008-11-11
**@ Sorivenul: ** Thank you , I knew the jpython link but I did not know the other links. I will look into your links. Why you still prefer CPYTHON ?

**@ loell:** Well as I start I will dealing with databases and MySQL. Of course I will be using Swing and other JAVA classes.  But I would not mind to use pygame for example or make something difirent. Are there any limits to what jpython can do and work properly , or will I take a risk if I am writing Jpython instead of jave? 

At the moment I trust JAVA because I have seen that it plays very nicely with both UBUNTU and MACOS but   I want the ease of use of python as well. In short as Queen sing "I want It ALL" :)

---

### Post by CptPicard on 2008-11-11
To be exact, Jython is a Python implementation running on top of the JVM. I hear it works great, haven't really done all that much in it though... my JVM-scripting has been Clojure and Groovy so far. :)

---

### Post by pmasiar on 2008-11-11
> **Kilon said:**
> Of course I will be using Swing and other JAVA classes.  But I would not mind to use pygame for example or make something difirent. Are there any limits to what jpython can do and work properly , or will I take a risk if I am writing Jpython instead of jave? 

At the moment I trust JAVA because I have seen that it plays very nicely with both UBUNTU and MACOS but   I want the ease of use of python as well. In short as Queen sing "I want It ALL" :)

Is short, you cannot have it all :twisted:

Java was **designed** to be separate (and incompatible, "platform-independent") world back in mid-90ties, when there were many platforms. Now it is mostly between Windows proprietary platform, free software (Linux, BSD etc) and ... Java in the middle.

Even lots of efforts are spent to make Jython to catch up with Python, Sun neglected Jython for 10 years, and there still could be many C-world libraries not implemented in Jython, like you mentioned pygame: it is not trivial and obvious to port C libraries to Jython, and not all are available. CPython is the mainstream for a reason: because it is the mainstream, used by vast majority of developers, and most use one of free platforms.

Programming, as any other engineering discipline, is about compromises, about making choices. Learn to deal with it. Making right choices (and rejecting other possibilities) makes code cleaner. ;-)

---

### Post by Kilon on 2008-11-11
**@ CptPicard :** "Make it so" :lolflag: thanks for bringing into my attention those two scripting languages , I checked them and seem very interesting. 

**pmasiar: ** Yes you are righ, that is also made clear in jpython website, that the support for CPython libraries is limited. Too bad I cannot use PyGame. But it is not a huge issue, I have studied python find it very easy and like it so i though why not give a try to Jython . I have no problem coding in Java, Python and Jython depending on my projects need. 

The same website says that the suppport for JAVA databases through Jython is almost 100% that is why I want to give it atry. I wnat to make an MySQL database frontend. I mainly worried with MAC OS . UBUNTU is well behaved with pretty much all the languages , but experienced problem with MONO and Python 2.6 in MAC OS 10.4. I know it is a complicated issue that is why I try to follow the simplest approach . I do not want to be another Open Source developer who abandons his project because he was too ambitious but not capable enough.I like to set achievable and preferably very easy goals.   

That is why I want you the real jython programmers to warn me about potential problems. This may save enormous amount of time and concentrate my efforts where it matters most.

---

### Post by directhex on 2008-11-11
I'm sure this will lead to a flame war, but...

IronPython allows you to write .NET apps using Python language, and interop fine with any .NET libraries (or native libraries, which as per usual increases risks of non-cross-platform code)

As suggested, Java was never really designed with the idea that people would want the JVM but not the Java language. Conversely, .NET is designed to allow multiple languages to interop fine with the core classes

---

### Post by pmasiar on 2008-11-11
> **directhex said:**
> Conversely, .NET is designed to allow multiple languages to interop fine with the core classes

It actually was Jython developer [http://en.wikipedia.org/wiki/Jim_Hugunin](http://en.wikipedia.org/wiki/Jim_Hugunin) who get hired to led that change in .NET focus: C# for libraries, dynamic languages for app, all running on VM optimized also for dynamic languages. Even MSFT does something right occasiaonally ;-) And Sun lost their best chance to beat MSFT in it's own game.

---

### Post by Sorivenul on 2008-11-11
> **Kilon said:**
> **@ Sorivenul: ** Why you still prefer CPYTHON ?
Honestly, I don't do a lot of Java work.  Python works for me, and when I do Java work standard Java works for me.  

> At the moment I trust JAVA because I have seen that it plays very nicely with both UBUNTU and MACOS but   I want the ease of use of python as well. In short as Queen sing "I want It ALL" :)
As has been said, you can't have it all.  Both Java and Python work fine on OSX and Linux.  Learn both, use what you like best.  For me that's mostly Python.

---

### Post by Kilon on 2008-11-11
There is no issue of flame war at least from my side. I love all 3 , Python, Java and .NET and would love to combine them . 

The thing with ironpython is that I read somewhere it has somewhat limited suuprot for .NET classes as Jpython has limited support for CPython classes. Java on the other hand is a bit messy with its library, people have complained about the easy of use of some libraries. 

I must confess I am at some dilemma. Ok yes I have decided to follow JAVA route, but I have big books for all 3 of them so I can at any point code in any of the 3. DirectHex says that .NET works fine with UBUNTU and of course windows, you say JPYTHON also works fine. Maybe if I do more search I could find a way to make ironpython work like a charm as well. 

So I cannot flame any of the 3 , because I really like all 3. I cannot understand why we should fight for a computer language. MySQL which i study works with all of them just fine. 

So I know that I want to mix some python inside my code and make it as high level as possible. I know that I wont have the time to go low level or use advance programming techniques so I would have to say with the condition that I do not experience any big problems both JPYTHON and ironpython are very good candidates.  It seems to me that JPYTHON is the most well behaved because of its full compliance with JAVA , I cant say the same for iRONPYTHON. But I am not sure cause I have not coded in any of them that is why I wantde to hear what people who use them have to say.

Obviously I will have to code with them to see for myself the advantages and disadvantages.

---

### Post by directhex on 2008-11-11
> **Kilon said:**
> There is no issue of flame war at least from my side. I love all 3 , Python, Java and .NET and would love to combine them . 

The thing with ironpython is that I read somewhere it has somewhat limited suuprot for .NET classes as Jpython has limited support for CPython classes. Java on the other hand is a bit messy with its library, people have complained about the easy of use of some libraries. 

I must confess I am at some dilemma. Ok yes I have decided to follow JAVA route, but I have big books for all 3 of them so I can at any point code in any of the 3. DirectHex says that .NET works fine with UBUNTU and of course windows, you say JPYTHON also works fine. Maybe if I do more search I could find a way to make ironpython work like a charm as well. 

So I cannot flame any of the 3 , because I really like all 3. I cannot understand why we should fight for a computer language. MySQL which i study works with all of them just fine. 

So I know that I want to mix some python inside my code and make it as high level as possible. I know that I wont have the time to go low level or use advance programming techniques so I would have to say with the condition that I do not experience any big problems both JPYTHON and ironpython are very good candidates.  It seems to me that JPYTHON is the most well behaved because of its full compliance with JAVA , I cant say the same for iRONPYTHON. But I am not sure cause I have not coded in any of them that is why I wantde to hear what people who use them have to say.

Obviously I will have to code with them to see for myself the advantages and disadvantages.

Not having used it, I can't comment on Jython, but IronPython loses nothing. .NET has a construct called the Common Language Runtime, the CLR, meaning all languages which target the CLR can use the CLR fully - whether it be C# or VB.NET or even a bizarre pointless language like BrainFuck.NET

IronPython leverages an extra piece of tech, the DLR (Dynamic Language Runtime) which makes it possible for loosely-typed languages like Python to plug into the CLR - other systems like IronRuby also rely on the DLR. You can access **any** .NET code from any CLR language. What you don't get is **language** extensions, such as LINQ (part of C# 3.0)

What I'm not particularly well versed on is how well IronPython behaves with normal boring .py files (i.e. regular files you'd run with normal Python), but IronPython is designed more about letting you write .NET code with Python syntax than running Python code as-is. A simple GTK#/IronPython example would look something like this:
```
import clr
clr.AddReference('gtk-sharp')
import Gtk

def delete_event (o, args):
    Gtk.Application.Quit ()

def say_hi (o, args):
    print "Hello, World!"

Gtk.Application.Init ()
w = Gtk.Window ("Hello, Gtk# World")
w.DeleteEvent += delete_event
b = Gtk.Button ("Say Hello")
b.Clicked += say_hi
w.Add (b)
w.ShowAll ()
Gtk.Application.Run ()
```

Those Import and AddReference bits at the top are how you'd gain access to any .NET library on your system (from libanculus0.3-cil to libwebkit1.0-cil and everything in between)

---

### Post by pmasiar on 2008-11-11
I agree with 95% of what you said (just adding that DLR was **designed** for IronPython), except

> **directhex said:**
> DLR (Dynamic Language Runtime) which makes it possible for loosely-typed languages like Python to plug into the CLR 

That's often-repeated misunderstanding. 

Python is strongly typed, but dynamically typed, using late binding. We had this discussion about types many times, you somehow missed it? ;-)

---

### Post by wmcbrine on 2008-11-11
An annoyance with Jython is that, until recently, it was still at the Python 2.2 level. There's now a Jython 2.5 beta, but it hasn't made it into Ubuntu yet.

Apart from that, for the things I've tried it with, Jython has worked fine. IronPython (at least on Ubuntu) has not, I regret to say.

I'm not a Java guy myself, so I'm happy with CPython.

---

### Post by Kilon on 2008-11-12
The problem is that MONO and MACOS do not work well together. I have read recent posts because I keep investigating by google all opinions on the matter that GTK# is not quite there yet and that QT is more appropriate, also MONO further slips away cause it Works under X11 in macos which I do not like. 

On the side of JYTHON I read that is very very slow , much slower than CPYTHON. While Java in some cases can be even faster than C++. Of course I should be asking myself if I really need speed, mainly because I do intent on building CPU hungry applications, but you never know. 

And then of course is the issue of converting JAVA into Jython or .NET into IronPython. Does it worth it ? The good news with JAVA that is so much documentation out there and APIs for just about everything, so that basically means that it is easier for me to get the knowledge and maybe find more people to work with as I would really like to participate in a project.    

Of course I would not consider Python in any way if it was not so easy to write it. Not that I am not confident with Java, it looks to me verysimilar to C++ and C++ is a language I have spent some decent time with. But then again I would probably said the same with C#. 

At them moment I decided to follow JAVA but If I can utilize python in any way possible that would be a great gain for me.

---

### Post by tinny on 2008-11-12
> **directhex said:**
> I'm sure this will lead to a flame war, but...

IronPython allows you to write .NET apps using Python language, and interop fine with any .NET libraries (or native libraries, which as per usual increases risks of non-cross-platform code)

As suggested, Java was never really designed with the idea that people would want the JVM but not the Java language. Conversely, .NET is designed to allow multiple languages to interop fine with the core classes

Groovy is a dynamic language specifically designed for the JVM / Java class library. Ive also used Jython and its good, however it does feel a little retrofitted IMO. 

Groovy also has a very good web framework designed for use with it, Grails.

Personally when I want to code Python I use Python (there is nothing wrong with the Python runtime and web frameworks).

2 cents spent...

---

### Post by directhex on 2008-11-12
> **Kilon said:**
> The problem is that MONO and MACOS do not work well together. I have read recent posts because I keep investigating by google all opinions on the matter that GTK# is not quite there yet and that QT is more appropriate, also MONO further slips away cause it Works under X11 in macos which I do not like.

Hasn't been true for a while. GTK# on Mac now uses native painter code, as worked on by Immendio.

---

### Post by Kilon on 2008-11-12
> **directhex said:**
> Hasn't been true for a while. GTK# on Mac now uses native painter code, as worked on by Immendio.

Ok let me ask this ... what does not work properly in MONO? How well behaved is Ironpython ? I tried some GTK# examples in my MACOS and experienced some crashes and enormous windows and general weird behavior. But I must confess I had not the time to test ironpython.

I think I am abit confused with the all thing.

---

### Post by pmasiar on 2008-11-12
> **Kilon said:**
> On the side of JYTHON I read that is very very slow , much slower than CPYTHON.

I am not sure what are your sources, I recall Jython author Jim Hugunin at Pycon05 talk about Jython: he implemented Jython for JVM to prove how badly JVM is designed, and ended up being surprised how decent performance he got. And that performance was the reason why MSFT hired him to implement IronPython for CLR.NET - he would not get hired if Jython was a bomb.

So of course Jython will not be as fast as CPython, but performance was surprisingly good, given that Jython uses JVM and Java and not native code and C. Compiler optimization is pretty well known problem, after 50 years of research 8-)

> While Java in some cases can be even faster than C++. 

Only if C++ implements different algorithm, or implements it ineffective way. There is no way Java beat C++ implementing the same algorithm, because C++ does not have JVM overhead.

> Of course I should be asking myself if I really need speed, mainly because I do intent on building CPU hungry applications, but you never know. 

**[COLOR="Red"]Repeat after me: Speed is not a problem until you can prove (and measure!) which part of your code is a problem. Premature optimization is root of all evil[/COLOR]** 8-)

> The good news with JAVA that is so much documentation out there and APIs for just about everything, 

... bad news is that there is **so** much docs there it is hard to make sense of all of it, you need guru advice to find the needle you need in all that haystack.

---

### Post by stevescripts on 2008-11-12
> **pmasiar said:**
> 
**[COLOR="Red"]Repeat after me: Speed is not a problem until you can prove (and measure!) which part of your code is a problem. Premature optimization is root of all evil[/COLOR]** 8-)


That is as well said as can possibly be ...

Steve

---

### Post by Kilon on 2008-11-12
> **pmasiar said:**
> I am not sure what are your sources, I recall Jython author Jim Hugunin at Pycon05 talk about Jython: he implemented Jython for JVM to prove how badly JVM is designed, and ended up being surprised how decent performance he got. And that performance was the reason why MSFT hired him to implement IronPython for CLR.NET - he would not get hired if Jython was a bomb.

So of course Jython will not be as fast as CPython, but performance was surprisingly good, given that Jython uses JVM and Java and not native code and C. Compiler optimization is pretty well known problem, after 50 years of research 8-)

> While Java in some cases can be even faster than C++. 

Only if C++ implements different algorithm, or implements it ineffective way. There is no way Java beat C++ implementing the same algorithm, because C++ does not have JVM overhead.

> Of course I should be asking myself if I really need speed, mainly because I do intent on building CPU hungry applications, but you never know. 

**[COLOR="Red"]Repeat after me: Speed is not a problem until you can prove (and measure!) which part of your code is a problem. Premature optimization is root of all evil[/COLOR]** 8-)

> The good news with JAVA that is so much documentation out there and APIs for just about everything, 

... bad news is that there is **so** much docs there it is hard to make sense of all of it, you need guru advice to find the needle you need in all that haystack.

Ok I have the benchmark that I was referring , but a bit of google can reveal that alot of people experience speed problems with jython. 

[http://blog.dhananjaynene.com/2008/07/performance-comparison-c-java-python-ruby-jython-jruby-groovy/](http://blog.dhananjaynene.com/2008/07/performance-comparison-c-java-python-ruby-jython-jruby-groovy/)

As I said speed is not a big issue for me , I can live with it, Also it explains how and why Java can be faster than C++. I know that in the past JAva was really slow but I have read alto of articles saying that things have dramatically change. 

I know that some people will hate me for this but I am not really impressed by python's libraries, the language itself comes with bare bones , and the documentation is not very good in some case. I have experienced problems with the documentation in WxWidget [http://wxpython.org/](http://wxpython.org/), in some point I was going back to the C++ documentation and that did not make very happy. 

At the moment I do not experience any problems with java documentation , it clear , concise and and the tutorials in sun's website are very beginner's friendly. The language itself unfortunately carries alot of C++ heritage of unnecessary complexity but , it works for me and I have found far more interesting libraries than those I have found on python. The only thing that make me question java is the syntax , I think python is much better there. 

At the moment I am not seeing myself truly embracing myself Jython , maybe in the future if Java disappoint me I will prefer jython or python or wahtever. But I will try my lack with JAVA at them moment.

---

### Post by Sorivenul on 2008-11-12
> **Kilon said:**
> At the moment I am not seeing myself truly embracing myself Jython , maybe in the future if Java disappoint me I will prefer jython or python or wahtever. But I will try my lack with JAVA at them moment.
I personally have never had any of the problems you seem to with Python.  I'm glad you seem to have found a "home" with Java.  Always remember this is about choice and what is best for you and the work you are doing.  Good luck to you.

---

### Post by jacensolo on 2008-11-12
Not to take over this thread, but is there a way to get NetBeans to build swing code in Jython instead of Java, or even work with Jython at all?

---

### Post by Sorivenul on 2008-11-13
> **jacensolo said:**
> Not to take over this thread, but is there a way to get NetBeans to build swing code in Jython instead of Java, or even work with Jython at all?

I believe [Coyote]("https://coyote.dev.java.net/") is your answer.

---

