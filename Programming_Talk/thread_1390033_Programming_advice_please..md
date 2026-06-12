---
title: "Programming advice please."
date: 2010-01-25
forum: Programming Talk
---

### Post by Schotty on 2010-01-25
Greetings.

I am an old vintage computer programmer with little modern skills, but although I can still recall opcode for the 6502, I am pretty much out of it when I go beyond basic BASH or batch file scripts.

*So here is the 128 Bit Question:*
[INDENT]From those that have actually had to deal with it, what is the least painful cross platoform coding environment?  I see RealBasic (I don't know VB so I guess its gotta be somewhat similar), wxPython, wxGTK, and Java.  Win32, Linux, and Apple compatibility would be the minimal.  No hate towards BSD, but not a huge worry there.  I would hope that what would translate to inclusion of Linux would also include BSD.[/INDENT]
Any tips/advice/roadblocks?  Remember I am a noob to the coding scene essentially, and am looking to getting a bunch of books (all hail amazon) and holing myself up until I can code (just beer breaks).  I got a Mr. Java guy at work that used to do alot of hand assembly and loves C.  But not having much skill there, I doubt a week is all I need but a few months (thats his words -- a week, ya right!).  I am not in expectation of becoming the next Linux overnight, but I also would like to bald naturally (the kid is doing a great job of that for me).

And on a smaller note, I am interested in getting it open sourced as soon as my code isnt too unbearable to read.  But for dealing with others, what tactics does one recommend?  I see alot of people are migrating to svn for version control -- should I start with that?  Any tips or advice on this would be spectacular.  And before anyone needs to point it out -- I know IDE's and brands are like religion and polotics -- everyone has their special one.  But thats the point -- I want to hear about yours.  Preach on!

My apps for the mospart are going to be relatively simple (tools for online tabletop RPG gaming so that we can still get together even in different countries and play Shadowrun, AD&D, battletech, etc), but I dont believe that these days I should even bother with code that isnt somewhat portable.  It was painful enough back in the day porting from Apple and Atari and Commodore.  I am _NOT_ doing that crap ever again :D

Thanks much,
Andrew

---

### Post by nvteighen on 2010-01-25
> **Schotty said:**
> 
*So here is the 128 Bit Question:*
[INDENT]From those that have actually had to deal with it, what is the least painful cross platoform coding environment?  I see RealBasic (I don't know VB so I guess its gotta be somewhat similar), wxPython, wxGTK, and Java.  Win32, Linux, and Apple compatibility would be the minimal.  No hate towards BSD, but not a huge worry there.  I would hope that what would translate to inclusion of Linux would also include BSD.[/INDENT]
Any tips/advice/roadblocks?  Remember I am a noob to the coding scene essentially, and am looking to getting a bunch of books (all hail amazon) and holing myself up until I can code (just beer breaks).  I got a Mr. Java guy at work that used to do alot of hand assembly and loves C.  But not having much skill there, I doubt a week is all I need but a few months (thats his words -- a week, ya right!).  I am not in expectation of becoming the next Linux overnight, but I also would like to bald naturally (the kid is doing a great job of that for me).


First of all, I see you're confusing lots of different things, which in your case is very natural to happen. Some of the languages you listed aren't actually languages but other kind of stuff and some don't even exist (wxGTK...). Nowadays, you've got a jungle of different languages, some highly specialized for certain tasks, which leads to total confusion to any beginner or to someone like you who hasn't followed up the latest developments in programming.

I recommend you to look at the stickies to get the basic information. But, here you have a little list of what are the most referred languages these days (in total random order):
[LIST=1]
[*]C
[*]C++
[*]Java
[*]Perl
[*]Python
[*]PHP
[*]Java
[*]C#
[*]Ruby
[*]Javascript
[*]bash/sh (UNIX/Unix-like OSs only)
[/LIST]

I would recommend you to start with Python rather than with C. It's true that your ASM background would help you to get C, but Python will give you a high-level (i.e. further to the machine internals) cross-platform environment that's got plenty of third-party libraries to get things done; the drawbacks are speed (though lately this is becoming less and less important) and that Python is an interpreted language, so you don't get a native executable (which is why it is cross-platform, actually). C is much nicer for low-level programming, being like a "nicer ASM" to have things work quickly, but it makes concepts more difficult to transfere into code... like ASM also does.

In time you'll hear about other weird stuff like Common Lisp, Haskell, Scheme, Forth, Clojure, R, ...

Stuff like GTK+, wxWidgets (in any of its encarnations), Qt, etc. are libraries, not languages. In this case, all are GUI libraries.

About cross-platform development: It's much more difficult than you think. For example, if you plan to interface somehow with the OS, you're doomed to write platform-specific code... or write the same code for each platform again. Python, for example, helps you a lot with some basic OS operations, but you'll end up with something not portable here and then... either it's a library you're using or a system call or something.

> 
And on a smaller note, I am interested in getting it open sourced as soon as my code isnt too unbearable to read.  But for dealing with others, what tactics does one recommend?  I see alot of people are migrating to svn for version control -- should I start with that?  Any tips or advice on this would be spectacular.  And before anyone needs to point it out -- I know IDE's and brands are like religion and polotics -- everyone has their special one.  But thats the point -- I want to hear about yours.  Preach on!


I suggest you to forget about this topic for a while; don't add yourself unnecessary pressure. Learn things well first and when you get an idea for a project, you'll find out where to get information about that stuff, which, in fact, usually is pure bureaucracy... side-work... I guess you get the idea :P

> 
My apps for the mospart are going to be relatively simple (tools for online tabletop RPG gaming so that we can still get together even in different countries and play Shadowrun, AD&D, battletech, etc), but I dont believe that these days I should even bother with code that isnt somewhat portable.  It was painful enough back in the day porting from Apple and Atari and Commodore.  I am _NOT_ doing that crap ever again :D


Nope... you actually start writing something no matter how unportable it is. Again, pure portable code is really difficult to write... or almost impossible for any average project. You'll always end up writing different versions of the same code for different target platforms; the difference between languages and technologies (e.g. the JVM), of course, lies on the amount and nature of that platform-targeted code.

---

### Post by shadylookin on 2010-01-25
Well developing for the web is probably the most cross platform solution, and it has a wide audience.

---

### Post by jflaker on 2010-01-25
Java and C are cross platform as long as there are no exotic and system specific API's being called...a Java program as an example will run on Windows, Linux, Unix, IBM AS/400 and even an iPhone.

C programs generally need to be compiled on each platform unlike Java (if I am not mistaken) but will run, again, as long as not system specific API's are being called.

---

### Post by Senesence on 2010-01-25
> **Schotty said:**
> My apps for the mospart are going to be relatively simple (tools for online tabletop RPG gaming so that we can still get together even in different countries and play Shadowrun, AD&D, battletech, etc), but I dont believe that these days I should even bother with code that isnt somewhat portable.

I suggest you take a look at the SDL library: [http://www.libsdl.org/](http://www.libsdl.org/)

It provides cross-platform graphics, sound, input, and some other useful things.

Although, as shadylookin said: "developing for the web is probably the most cross platform solution, and it has a wide audience.". So you might want to look at things like Flash, and ActionScript 3.0.

The [Flex SDK]("http://www.adobe.com/cfusion/entitlement/index.cfm?e=flex3sdk") is free, and it can be used to compile AS3 on Linux.

So give that a try, too.

---

### Post by wmcbrine on 2010-01-25
Most portable: C
Easiest, portable enough: Python
Version control: git

Senesence, he's not wanting to write a game, but rather gaming *tools*. I think he won't need graphics or sound. (On the other hand, they are a fun way to learn a new language!)

---

### Post by samjh on 2010-01-25
> **Schotty said:**
> *So here is the 128 Bit Question:*
[INDENT]From those that have actually had to deal with it, what is the least painful cross platoform coding environment?  I see RealBasic (I don't know VB so I guess its gotta be somewhat similar), wxPython, wxGTK, and Java.  Win32, Linux, and Apple compatibility would be the minimal.  No hate towards BSD, but not a huge worry there.  I would hope that what would translate to inclusion of Linux would also include BSD.[/INDENT]
Not all of those options you listed are programming languages.  wxPython is a library for Python (ie. tools you use Python with), and wxGTK doesn't exist (you may be referring to wxWidgets rendered in GTK, which is just wxWidgets). Java and RealBasic are programming languages.

> **Schotty said:**
> 
My apps for the mospart are going to be relatively simple (tools for online tabletop RPG gaming so that we can still get together even in different countries and play Shadowrun, AD&D, battletech, etc), but I dont believe that these days I should even bother with code that isnt somewhat portable.  It was painful enough back in the day porting from Apple and Atari and Commodore.  I am _NOT_ doing that crap ever again :DThe number one cross-platform (ie. compile once and run anywhere) game development tool right now is Java.  It's relatively easy to learn, compared to C, C++, and Assembly.  It has a huge programming community and lots of game development tools to choose from (eg. [GTGE](http://www.goldenstudios.or.id/products/GTGE/) is a simple but capable one).

Python is popular for Linux, but not so much for Mac, and very little following on Windows.  It's quite a capable language and platform though.

---

### Post by Some Penguin on 2010-01-25
Java is *mostly* cross-platform, if you stick with Pure Java (i.e. no JNI).  You will still risk seeing differences in floating-point arithmetic (there's actually a StrictMatch package that sacrifices performance for reproducibility).

I would argue for a novice programmer, it's far more portable than C where you should be worrying about native sizes (for instance, C types don't even have standard sizes -- they have *minimum* sizes, but it would be legal to have twelve-byte shorts, for instance), endianess, and the much greater variability in library availability.  Even error handling is not particularly standard; 'common' errnos come from POSIX, not C, for instance.   Threads, file handling...  

Contrast that to Java, where the set of standard classes and packages is VERY rich.  It creates more work for the JVM implementer, but less for the end user.

---

### Post by wmcbrine on 2010-01-25
> **samjh said:**
> Python is popular for Linux, but not so much for Mac, and very little following on Windows.The Python interpreter comes bundled with every new Mac. Tkinter apps look native.

---

### Post by Schotty on 2010-01-26
thanks for the tips all!

I must apologize since I wrote the post shortly before I got off of work and then hit the sack.  I did know that wx(whatever) is an API extension, however what I had no clarification after rereading it, was that from what I gathered wx(whatever) is pretty portable and simple whether it be C, C++, or Python, and hence the reason I was looking into them.  But I must thank you for the very clear and polite correction.  I humbly apologize for an incomplete/incoherent post.  

Thankfully I am much more coherent now :P

After reading what everyone has said, I am gathering a dive into Python, C, or Java is the consensus.  I do know some C & C++, but the one kicker against that is (aside from nothing but CLI programming) very importable code outside of wx* or SDL when it comes to network or media related code.  I would love to be proven wrong on this one.  I damn near slept thru my college course 5 years ago because of its limited scope and the fact I handed in my homework for the trimester the second day of class (got an A- so I can't complain).  The reason I was leaning Java or wxPython was that portability feature.

As for doing simple unportable stuff first, I may go with you on that, depending on how my first app, a virtual dice bag, goes.  I started one up in Java and wxPython already and I like both languages thus far.  But since I am not going ape with functionality I am hoping to work out any snafu's with making my progams work on Win32 and MacOS earlier, or just say screw it.  Linux is my home and main OS, so if it works there, I am happpy enough.  But I see no reason to exclude unless life gets that miserable.  

As for version control, I think I will take the advice of hold on a while, but eventually go with git.  I read up on that one (forgot about it as being there until wmcbrine reminded me).  It does seem to be alot to iron out along with a new language or two.

Thanks for the advice!  I think I have figured out enough that its gonna be a matter of taste from here onward.  But one more question for the road.

I am really liking wxPython + Python.  But I have noticed that there is a notable change between 2.6 and 3.1.  Any reason _NOT_ to go with 3.1 and rather stay in the 2.6 or 2.8 branch?  From what I have seen thus far, there are alot of nifty functions that, to put it lightly, are already making life much more awesome in 3.1.  

Thanks again,
Andrew.

---

