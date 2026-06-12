---
title: "Is Java suited for me?"
date: 2011-08-23
forum: Programming Talk
---

### Post by cyb3r_sn4k3 on 2011-08-23
I am doing a couple of projects for school but they want GUI :(. But I am only fluent in C sharp which unfortunately is hard to program without Visual Studio which does not support Linux :mad: (I know other languages like C, C++ etc but I am not familiar with their GUI options) So I am thinking of taking up Java which I heard has good GUI support and also can be scripted very easily in Linux \\:D/ . So my question is whether Java will be good for my needs that is 

1) Easy to design GUI (Something like winforms would be nice)
2)Support for "advanced features" like communicating with mobile phone through bluetooth
[OPTIONAL]Create apps for Java enabled phones.


Or should I go for something else (please recommend).
Also, I heard that Java has several variants, which will be suited for me if I do decide to learn Java?

Thanks In Advance :)

---

### Post by lisati on 2011-08-23
*Thread moved to **Programming Talk**.*

---

### Post by Nytram on 2011-08-23
It's possible to program in C#/.net with Linux, using MonoDevelop. It's not quite as good as Visual Studio but is pretty decent.

---

### Post by cyb3r_sn4k3 on 2011-08-23
> **Nytram said:**
> It's possible to program in C#/.net with Linux, using MonoDevelop. It's not quite as good as Visual Studio but is pretty decent.


Yes, I have tried MonoDevelop but I'll take 5 times more time than I'll take in visual studio. And I read somewhere that Java can be developed in Eclipse and others which have seamless support for Linux

---

### Post by vikas barnes on 2011-08-23
You can use netbeans. 
You should start with Java SE.

---

### Post by cyb3r_sn4k3 on 2011-08-23
> **vikas barnes said:**
> You can use netbeans. 
You should start with Java SE.

Does it have support for mobile apps?

---

### Post by Nytram on 2011-08-23
> **cyb3r_sn4k3 said:**
> Yes, I have tried MonoDevelop but I'll take 5 times more time than I'll take in visual studio. And I read somewhere that Java can be developed in Eclipse and others which have seamless support for Linux

My reasoning was, that learning a new IDE is quicker than learning a new language, at least for me it is.

---

### Post by cyb3r_sn4k3 on 2011-08-23
> **Nytram said:**
> My reasoning was, that learning a new IDE is quicker than learning a new language, at least for me it is.

Very true, but right now I am looking for support on mobile devices also. And also I am in the mood for learning a new language :P

---

### Post by PaulM1985 on 2011-08-23
Netbeans does support mobile apps, but I think this is Windows only because there isn't a linux version of Java ME.

Eclipse provides support for Android programs.

I find Netbeans more useful in general and the interface for GUI design is quite good once you get used to it.

Paul

---

### Post by cyb3r_sn4k3 on 2011-08-23
So Netbeans is the way to go I guess :D

---

### Post by PaulM1985 on 2011-08-23
> **cyb3r_sn4k3 said:**
> So Netbeans is the way to go I guess :D

It depends exactly what you want to do.

Websites with server side code, databases programs, standard desktop applications, I would say Netbeans.

Mobile apps for Java ME, I would say Netbeans on Windows (Ubuntu didn't have a version of Java ME that I could use when I was trying this)

Mobile apps for Android, use Eclipse.

Paul

---

### Post by stchman on 2011-08-23
Netbeans has a GUI builder OOB whereas Eclipse you have to install Visual Editor.

---

### Post by lykeion on 2011-08-24
> **PaulM1985 said:**
> Mobile apps for Java ME, I would say Netbeans on Windows (Ubuntu didn't have a version of Java ME that I could use when I was trying this)

Well, I used to develop JavaME apps in Linux until iPhone and Android. I used Sun WTK 2.5.2 and when v3.0 came out for Windows I remember there was a long wait for a Linux version which never came, and then came Oracle... However you can still download WTK 2.5.2 for Linux and develop JavaME apps. Sure enough in v3.0 the emulator was improved and it had a better profiler, but for app development in JavaME you still had to test on a real device anyway.

As for IDE both Eclipse and NetBeans are good. Personally I preferred IntelliJ IDEA.

---

### Post by PaulM1985 on 2011-08-24
> **lykeion said:**
> Well, I used to develop JavaME apps in Linux until iPhone and Android. I used Sun WTK 2.5.2 and when v3.0 came out for Windows I remember there was a long wait for a Linux version which never came, and then came Oracle... However you can still download WTK 2.5.2 for Linux and develop JavaME apps. Sure enough in v3.0 the emulator was improved and it had a better profiler, but for app development in JavaME you still had to test on a real device anyway.

As for IDE both Eclipse and NetBeans are good. Personally I preferred IntelliJ IDEA.

I stand corrected, Java ME is possible on Ubuntu.  I obviously wasn't trying hard enough. :-)

---

### Post by dazman19 on 2011-08-25
When I first started Java I didn't like it. Mainly because its higher level and a bit slower than languages like C/C++ but Now I think it's a brilliant language. I write a program and it work on Windows/Mac/Linux, Its great for commercial use. I probably would use a different language if I got into game making, but if you want to make apps then its great.

I have only ever programmed GUI's in Java, C# and For web. 

Java is a cool language, and once you master it you will find the concepts of most other languages will be very easy to pick up.

---

### Post by DangerOnTheRanger on 2011-08-25
@OP: Just what sort of mobile OS are you trying to develop for? Android uses a slightly different-looking variant of Java, which may be what you're looking for. Also, if you're developing for Android, many other (nicer, IMHO) language choices are available - take a look at ASL ([http://code.google.com/p/android-scripting/](http://code.google.com/p/android-scripting/)).

> **dazman19 said:**
> When I first started Java I didn't like it. Mainly because its higher level and a bit slower than languages like C/C++ but Now I think it's a brilliant language. I write a program and it work on Windows/Mac/Linux, Its great for commercial use. I probably would use a different language if I got into game making, but if you want to make apps then its great.

I have only ever programmed GUI's in Java, C# and For web. 

Java is a cool language, and once you master it you will find the concepts of most other languages will be very easy to pick up.

You have 2 misconceptions about Java (and programming languages in general). I'm not sure you still are under the influence of these misconceptions (I couldn't tell from your post), but just in case:

"Slow languages are automatically worse than fast languages" - not true. %99.99 of the time, the primary determining factor of a program's speed is not the language the program is implemented in, but the *algorithms* used inside said program. There are some cases (per-pixel image manipulation comes to mind) where a fast language *is *absolutely necessary, but they are the exception rather than the rule. Also, slow languages like Java or Python make it much easier to implement fast algorithms, due to their higher-level approach.

"Java (or Python or C# or whatever) can't be used for game development because it's slow" is a very common misconception. In fact, I'm using Python (which is even slower than Java) for a game development framework I'm coding (link in my sig) that's written in 100% pure Python. The framerate is still over 60 even with over 300 (admittedly non-textured) models on-screen, with my bottom-of-the-line Intel GPU. How is this possible? Simple: The underlying game engine (which I didn't write), what the CPU will be executing %99 of the time, has it's most processor-intensive parts optimized with better algorithms, and written in C++ when algorithms aren't enough.

---

### Post by cyb3r_sn4k3 on 2011-08-27
> **DangerOnTheRanger said:**
> @OP: Just what sort of mobile OS are you trying to develop for? Android uses a slightly different-looking variant of Java, which may be what you're looking for. Also, if you're developing for Android, many other (nicer, IMHO) language choices are available - take a look at ASL ([http://code.google.com/p/android-scripting/](http://code.google.com/p/android-scripting/)).



You have 2 misconceptions about Java (and programming languages in general). I'm not sure you still are under the influence of these misconceptions (I couldn't tell from your post), but just in case:

"Slow languages are automatically worse than fast languages" - not true. %99.99 of the time, the primary determining factor of a program's speed is not the language the program is implemented in, but the *algorithms* used inside said program. There are some cases (per-pixel image manipulation comes to mind) where a fast language *is *absolutely necessary, but they are the exception rather than the rule. Also, slow languages like Java or Python make it much easier to implement fast algorithms, due to their higher-level approach.

"Java (or Python or C# or whatever) can't be used for game development because it's slow" is a very common misconception. In fact, I'm using Python (which is even slower than Java) for a game development framework I'm coding (link in my sig) that's written in 100% pure Python. The framerate is still over 60 even with over 300 (admittedly non-textured) models on-screen, with my bottom-of-the-line Intel GPU. How is this possible? Simple: The underlying game engine (which I didn't write), what the CPU will be executing %99 of the time, has it's most processor-intensive parts optimized with better algorithms, and written in C++ when algorithms aren't enough.


I am not making apps for android, its "normal" LG phone.

---

### Post by DangerOnTheRanger on 2011-08-27
Hmm. Sorry, I don't know much about what runs on "normal" LG phones, so I can't really help you there :(

---

### Post by cyb3r_sn4k3 on 2011-08-27
> **DangerOnTheRanger said:**
> Hmm. Sorry, I don't know much about what runs on "normal" LG phones, so I can't really help you there :(
It just says it supports java. I think anything that runs on sony ericsson should work on this phone :-)

---

### Post by PaulM1985 on 2011-08-27
You should probably be ok with Netbeans. I am not 100% sure what LG support but I would assume that you would be ok with Java ME. You might notice a difference, I think you said that you used to do C#, with Java ME you don't have things like collection classes (vectors, lists, maps, etc) they are not supported in ME.
Good luck.
Paul

---

