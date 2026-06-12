---
title: "Programming language"
date: 2011-07-24
forum: Programming Talk
---

### Post by Inodoro Pereyra on 2011-07-24
Hello everybody.:)

First, let me say I have made a search, and read several threads on this subject, some which even have the same title as this one.The reason I'm opening this thread is because I didn't find what I'm looking for in any of them.

I've been a member of this forum for almost 2 years now, and my one constant has been that I always come to ask questions, and never to help anybody, because, at the end of the day, I don't know squat about any of this. I don't particularly like that. 

So, my questions are:

1. What would be a good programming language to learn, in order to better understand Ubuntu, and, in the nearest possible future, to be able to develop a good dynamometer program?

2. Can you suggest any books, to learn that language from "0"?

As a bit of a background, I'm an electronics technician (though I haven't worked in electronics for a long time), and have done some programming in the past, mostly hex, on a MC6800 developing kit, and some basic, on my first computer (a TI 99/4A. Yeah, I'm THAT old. :)). That said, I haven't done any programming at all in the last 25 years or so, and the only thing I remember about it is that I used to love hex, and basic...not so much.

So, that's about it. Any help will be greatly appreciated. :D

---

### Post by slavik on 2011-07-24
we will not suggest a language here, there are plenty enough discussions as is. pick any one language (read the sticky threads, please). and if you have specific questions, we will welcome them.

---

### Post by nvteighen on 2011-07-24
(Supongo que sos argentino, por el nick... jajaja. Te respondo en inglés porque son las normas acá...)

There are a couple of sticky threads on these forums that might help you about the basics: compilers, descriptions about programming languages, different kinds of tools and tutorials.

But be aware that Ubuntu is a collection of software written by lots of different people. The Linux kernel is written in C and Assembly, the GNU userland is mostly written in C, some things are written in bash, Python, Perl, C++, LibreOffice/OpenOffice have portions written in Java, etc. Each language is designed for some task and a great deal about programming is to choose the most appropriate one for your problem.

No idea what to use for a dynamometer. Maybe the best would be a combination of some low-level language like C and Assembly to interface with the device and some higher-level one to write a UI. But I've got no clue about this. Also, notice that writing a driver or a device interface is quite far from trivial.

Buena suerte, hermano!

---

### Post by Inodoro Pereyra on 2011-07-24
> **nvteighen said:**
> (Supongo que sos argentino, por el nick... jajaja.

Si, Argentino y nostalgico. :cry:  Gracias por la respuesta.
Back to English.

I will read the stickies now. I've read a bunch of threads about it, and everybody seems to recommend their favorite languages, but no real information as to which is more suitable for a given application. I have absolutely no experience with any of them (not even with Assembler, as I always found programming in hex easier, and more direct), so I don't know where to start.

That said, I'm also interested in any entry level books anybody may suggest on those languages. So far I haven't found any information about them.

Thank you again, Nvteighen, for the reply. Es bueno encontrar a otro Argentino por aca...:D


@Slavik: kinda mean, aren't you? I thought Internet forums were all about helping people out, not judging them.

---

### Post by slavik on 2011-07-24
> **Inodoro Pereyra said:**
> Si, Argentino y nostalgico. :cry:  Gracias por la respuesta.
Back to English.

I will read the stickies now. I've read a bunch of threads about it, and everybody seems to recommend their favorite languages, but no real information as to which is more suitable for a given application. I have absolutely no experience with any of them (not even with Assembler, as I always found programming in hex easier, and more direct), so I don't know where to start.

That said, I'm also interested in any entry level books anybody may suggest on those languages. So far I haven't found any information about them.

Thank you again, Nvteighen, for the reply. Es bueno encontrar a otro Argentino por aca...:D


@Slavik: kinda mean, aren't you? I thought Internet forums were all about helping people out, not judging them.
sometimes I have to be mean. too many threads about suggesting random languages in this forum, trying to cut down on the "use language X because that what I use/like" type posts. we've had too many unproductive discussions about which language is best to learn first.

---

### Post by Inodoro Pereyra on 2011-07-24
> **slavik said:**
> we've had too many unproductive discussions about which language is best to learn first.

Which is precisely the reason I started this thread, after spending a couple of hours reading that kind of threads. 
Either way, I've been reading the stickies (and Wikipedia), and it seems to me (from my completely uninformed point of view) that Python and C++ would be the most suitable options, with Python being easier to use. Is that right? 
Is there any other difference between the 2, that I should be aware of?

---

### Post by ve4cib on 2011-07-25
There are many, many differences between Python and C++.  To many to list here.

Probably the most fundamental difference is that C++ is compiled (your source code gets translated into binary "machine code" that is run directly by the CPU), whereas Python is interpreted/byte-compiled (you run a program that reads your code and compiles & executes it on-the-fly).

The practical offshoot of this difference is that programs written in C++ tend to be faster.  This makes it a good choice for high-performance programs, like OS kernels, games and other graphics-heavy programs, and complex mathematical programs.  However, a C++ program must be recompiled for every platform you use it on (e.g. Windows and Linux need their own separate binary files, and Linux on an amd64 CPU is different than Linux on an ARM CPU).

Python's primary advantage lies in the fact that it is platform independent.  Any program you write in Python* can be interpreted by a Python interpreter running on a different platform without you making any changes.

(*Any program within reason.  Certain libraries are not cross-platform, but that's a slightly complex topic to get into with a beginner.)

What kind of program do you want to write?  This may influence the choice of language more than any other consideration.

---

### Post by slavik on 2011-07-25
since you speak spanish and english, consider the differences between these two languages.

spanish is easier than english when it comes to basic reading/writing (it is more what you hear is what you write than english), but then you get into verb conjugation (and irregular verbs) and suddenly, english becomes easier.

when you start with python, in the beginning you will need to write less code and it will be more flexible than C++. then you will get into some advanced topics where C++ will appear to be easier.

there are many folks who say python is better as a starting language because it doesn't get in your way (versus C, more on that later) since it has a lot of libraries and many common data structures are built in (stacks, queues, lists, etc.) while this is a valid point, I do not quite agree with it due to the fact that your data structure knowledge becomes weak (more on this below).

I think that C is a better starting language. it's major downside is that it is not "batteries included" like python, so if you need any data structures (list, stack, queue, etc.), you have to write your own. in (good) colleges. there is at least a semester spent on just learning basic data structures. C itself has about 30 reserved keywords and the syntax is very simple and straightforward (coming from algol60). this is also where data structure becomes stronger.

with which, we come to a final point around this discussion:
if you learn python, there is no need for you to want to learn C, since python can already do everything that C can and more, easier. as software becomes more and more complex, organizing it via data structures becomes more important. OS schedulers make use of b+ and b- trees ... how many people who only learn python know and really understand how they work? you can follow a manual to fix a complex machine, that does not mean that you understand how it works.

hope that explains it.

EDIT: Another thing to add. Java's main selling point is memory management. I work in application support (I support J2ee containers/servers). The most common error that I can tell you that I would be expecting anywhere that is running on top of Java is "java.lang:OutOfMemoryError." Memory is cheap, unless this is an application that brings in 600M of revenue a year. It is also possible to have memory leaks in Java (we have had situations where we continuously restart a client's app across a cluster, 1 instance at a time).

---

### Post by ve4cib on 2011-07-25
I agree with Slavik's comments about C teaching you *how* things work.  If all you ever learn is Python you'll understand how to *use* a lot of data structures, but not necessarily how they work at a more fundamental level.

The utility of that knowledge is debatable for a beginner.  Learning how to control a car engine via the gas and brake pedals is sufficient for most people, and they can drive quite well.  But some people like understanding how the gas pedal works, controlling the flow of fuel from the tank and into the pistons.  Such knowledge is useful, but not required if all you want to do is drive from point A to point B.

What I'm trying to illustrate is that there's a difference between "learning to program" and "being a programmer."  Being a (good) programmer means you have a good grasp of fundamental data structures (arrays, linked lists, stacks, queues, heaps, trees, etc...), and what circumstances warrant the use of each one.  Good programmers can look at a problem and know what tools (be it data structures, or even what languages) are best for the job.

But not everyone needs to be that kind of programmer.  If you just want to play around with some simple programs to make your own life easier you don't necessarily need to know when you'd want to use a linked list instead of an array.  You might find such knowledge useful, but it's not essential.

---

### Post by karlson on 2011-07-25
> **Inodoro Pereyra said:**
> Which is precisely the reason I started this thread, after spending a couple of hours reading that kind of threads. 
Either way, I've been reading the stickies (and Wikipedia), and it seems to me (from my completely uninformed point of view) that Python and C++ would be the most suitable options, with Python being easier to use. Is that right? 
Is there any other difference between the 2, that I should be aware of?

Let's be clear here.  You should look at the languages not in the way it would be easiest to learn and then try to apply it to the problem you are trying to solve.

You should consider the problem you are trying to solve and think about the tools you want to use for it.  For example if you are writing a program to collect data from a dynamometer it may be prudent to use C instead of C++.  If you are doing a GUI may be Java or C# is the appropriate language to use if you want to do a simple formula for calculation and just print the result may be Perl or Python is the language to use.

In either way you should be looking at what is an appropriate tool to solve the problem and use it rather then doing it the other way around.

P.S. May be R/S, Erlang, or Haskell are better for this then other programming languages mentioned.

---

### Post by Inodoro Pereyra on 2011-07-25
Now that's EXACTLY the kind of information I was looking for. Thanks everyone for taking the time. :D

What I'm aiming to do in the future is building an inertial engine dyno. For those who don't know what I'm talking about, an inertial dyno is basically a big heavy wheel attached to an engine, with a tachometer and a load cell. The dyno works by measuring the torque being applied to the wheel, while the engine is accelerated at full throttle, from idle speed to a given RPM. 
Since the wheel is under more or less constant acceleration (it never stays at a constant RPM), the program needs to do some fast, precise data acquisition (reading the instant torque at the moment the wheel flies through some specific RPM), and then doing all the necessary calculations to display the horsepower and torque (obviously), and to be able to show and print a graph of those parameters. I also want to integrate the readings of an advanced OBD2 scanner to it, so I can have access to other parameters, like fuel trims, Manifold Absolute Pressure, timing advance, etc, and to be able to selectively show any of those parameters in the same graphs when needed. 
Then, of course, I want the software to be user friendly (so a GUI is the only logical choice).
In other words, I want an engine dyno with all the bells and whistles, without having to mortgage my underwear to get it. Now, I know damn well how to do the mechanical part, so now I need to learn how to do the software.

So, being that the most important part is the accuracy in the data acquisition, and the mathematics part, that would mean the best language is C++, right?

---

### Post by karlson on 2011-07-25
> **Inodoro Pereyra said:**
> 
So, being that the most important part is the accuracy in the data acquisition, and the mathematics part, that would mean the best language is C++, right?

No.  C would probably be best.

C++ would work because it's C compatible, but low level data acquisition libraries are usually done in C.

---

### Post by ve4cib on 2011-07-25
For that kind of application C or C++ would be your best bets.  Personally I'd probably use C for something like this, simply because that's what I've used in the past for similar embedded system projects.

Because speed is important you want something that is compiled (which would rule out Python, Java, Lisp, Perl, Bash, and a host of other interpreted/byte-compiled/scripting languages).

For the mathematics, C and C++ don't really offer much over one another.  They use the same variable types, and have the same operations.  If all you need are standard operations (multiplication/division/addition/subtraction, trigonometry, logarithms, exponents, and factorials) then there will effectively be no difference between the two.

If you need to do more complex math (calculating integrals on-the-fly, or large matrix operations) C++ *may* offer more options out-of-the-box, but C would certainly be capable of performing as well or better if you put the time into finding the appropriate libraries.

---

### Post by nvteighen on 2011-07-25
I agree with C (and maybe with some inline Assembly) being the most suitable option for getting the data from the device. You need something that's got access to it and interpreted languages like Python or Java won't give it.

But, you can always mix languages... and C is particularly easy to combine with almost any other language, while doing that with C++ is particularly difficult. So, you could write the backend in C and then write the user interface in a different language, Python being a popular choice for frontends.

---

### Post by Inodoro Pereyra on 2011-07-25
Thanks again everybody. :D

So, C it is, maybe with some Python...?

The math operations are mostly multiplication, and some division, so I'm not really worried about them. What makes or breaks a dyno software is the data acquisition, not only when it comes to accuracy, but also speed (as in number of samples taken in a given time period), and even that can be hardware based to a point. 

My biggest concern, to be honest, is that I'm extremely rusty when it comes to programming, and, even if I wasn't, the programming languages I used to work with are beyond prehistoric by now, so I wanted to make sure I didn't waste my time trying to learn a language that was either too complicated, or wasn't good for the task at hand.

So thank you all for all the info. I guess it's time to start learning me some C now...:D

---

### Post by ve4cib on 2011-07-25
Something else worth considering, besides the raw speed at which you acquire data, is making sure you have a consistent polling rate.  What I mean by that is making sure you get data say every 3ms, as opposed to having delay times like [1ms, 1ms, 4ms, 2ms, 1ms, 3ms, 5ms, 2ms, 2ms, 7ms, 1ms, ...].

Having a reliable rate of data acquisition is sometimes even more important than having a variable gap between your data points.  Even if the last data you had is 15ms old, if you know that every data point is collected with precise 3ms intervals then you can do some math to extrapolate where the current data is likely to be, based on previous trends.  But if the interval between polls is random this math becomes way harder (and is sometimes just impossible).

(The technical term for variation in data acquisition rates is "jitter," in case you come across that term, or need some keywords to put into google.)

---

### Post by Inodoro Pereyra on 2011-07-25
Yeah, I'm considering on using hardware to do the data acquisition. I've yet to decide if I'm gonna do that with an external crystal based clock, or I'm gonna use the engine for it (let's say, take a sample for every turn of the drum, or every half turn, etc).
I still have to make many decisions, hardware wise. I just figured the software would be the most time consuming part, especially considering that I have to learn how to do it, so I wanted to get a head start on it.:)

---

### Post by fdrake on 2011-07-25
sometimes your choice depends more on the hardware/(available drivers) that you use than the software itself.

---

### Post by slavik on 2011-07-25
you can also do something that kismet does. a server/client architecture, where the data being captured is written in one language and the client gets the data via another language, fifos make this really easy (as well as any other sysV IPC). Kismet codes both client and server in C though (not that you have to).

---

### Post by LemursDontExist on 2011-07-25
> **Inodoro Pereyra said:**
> Yeah, I'm considering on using hardware to do the data acquisition. I've yet to decide if I'm gonna do that with an external crystal based clock, or I'm gonna use the engine for it (let's say, take a sample for every turn of the drum, or every half turn, etc).
I still have to make many decisions, hardware wise. I just figured the software would be the most time consuming part, especially considering that I have to learn how to do it, so I wanted to get a head start on it.:)

If you haven't already checked it out, take a look at the [arduino]("http://www.arduino.cc/") as a means for interfacing with your engine.  For quick easy development it is hard to beat - you program it in a variant of C.  

As for the front end - python is certainly a reasonable choice, but I would also suggest considering writing a web application, possibly written in PHP, though any language would work with some sort of CGI.  A web-app front end eliminates the need to deal with gui libraries and, if you want, makes remote access trivial.

---

### Post by ve4cib on 2011-07-25
> **LemursDontExist said:**
> If you haven't already checked it out, take a look at the [arduino]("http://www.arduino.cc/") as a means for interfacing with your engine.  For quick easy development it is hard to beat - you program it in a variant of C.

You can also just use C and compile it with avr-gcc (available on the Ubuntu repos) if you don't want to use the "almost C" variant that Arduino uses by default.

---

### Post by Inodoro Pereyra on 2011-07-25
Now you guys are getting way too technical. Remember when I said my last programming experience was 1/4 Century ago?:lolflag:

> **LemursDontExist said:**
> If you haven't already checked it out, take a look at the [arduino]("http://www.arduino.cc/") as a means for interfacing with your engine.  For quick easy development it is hard to beat - you program it in a variant of C. 

Yeah, that's one of the options I'm thinking about. It's either gonna be an arduino, or a dumb, high speed I/O card. The thing is, as much as the precision in the sampling is important, I'm not gonna be dealing with real high sampling rates here. Even if I take 10 samples per revolution, at 7000 RPM, that's just little more than 1000 samples per second. Using an arduino would certainly make things easier though...

---

