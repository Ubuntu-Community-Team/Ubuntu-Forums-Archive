---
title: "Wow @ C"
date: 2007-02-09
forum: Programming Talk
---

### Post by Ben Sprinkle on 2007-02-09
I was just reading up on C, seems perfect for me. I also know a ton of programs are made using C, so it's very popular.

I have tried C++, it was not for me because of the gtkmm crap and limited cross platform.
I have also tried Java, it was pretty cool, what I currently use.

C is also faster then Java I think, and you can use openGL and stuff.

So is C a good choice?

---

### Post by darrenm on 2007-02-09
I'm delving into Python right now and loving it. C seems a lot more typing but you can do more low level stuff with C.

---

### Post by maxamillion on 2007-02-09
Is C a good choice for what? ... You shouldn't chose a programming language simply because "it looks good" you should chose a programming language per implementation.

Example:

-I want to write a fast and efficient data base: C would be a good candidate
-I want to write a multi-platform easily implemented and easily maintained client for the database I just wrote: Java or Python would be good candidates.

---

### Post by Ben Sprinkle on 2007-02-09
Well I was making my site out of nothing but a Java applet, working out so far.

But I would use C for like little text editor projects or 3D cubes and what not.

---

### Post by iblis on 2007-02-09
i'd have to say that C is never a bad language to learn, but i'm admittedly bias. :D

if you want something that you can use to whip up a quick, cool utility, and aren't worried about it using a lot of resources (at least, compared to C),  then i would suggest picking up python, perl, or both.

it also doesn't hurt that there's a nice ubuntu package called 'diveintopython' readily available. (:

---

### Post by LordHunter317 on 2007-02-09
> **Ben Sprinkle said:**
> I have tried C++, it was not for me because of the gtkmm crapGTKMM isn't a requirement for using C++.  I'm not sure where you got that idea.

> and limited cross platform.It's as cross-platform as C++, as least as far as major operating systems are concerned.

> C is also faster then Java I think,At some things and vastly slower at others.

> So is C a good choice?I think learning more about hte languages you've dismissed maybe, because you haven't dismissed them for valid reasons me thinks.

---

### Post by samjh on 2007-02-11
> I have tried C++, it was not for me because of the gtkmm crap and limited cross platform.As LordHunter has said, Gtkmm is not a requirement for C++.  C++ is similarly cross-platform as C.

> C is also faster then Java I think, and you can use openGL and stuff.Usually yes.  Optimised Java is around 15% slower than optimised C.  But you can use OpenGL using Java: look up the JOGL project.

> So is C a good choice?For system programming: yes.  But if speed is not a key issue, then there are more time-efficient alternatives (including Java, which is what you say you're using).

---

### Post by lnostdal on 2007-02-11
> **Ben Sprinkle said:**
> So is C a good choice?

Is beer the best choice?
Is red the best color?
Is going to war the best solution?
Is abortion the best solution?
Which religion is best?
Which drug is best (or worst) - alcohol or other drugs?
Which brush is best? (painting)
What's your favorite kind of meal?

(edit: replace "best" with "good" if you want .. still a problem to answer)

Do you see the major lack of context here? Would you be able to answer any of these questions truthfully -- without asking a _lot_ of new questions in return?

Here is my non-answer to your non-question:

* yes
* no

If you want the general answer whether your should _learn_ C, which at least is a reasonable question - I'd say yes you _should_ learn C because the system happens(#1) to be written in it. 

The reason this makes sense in general, that is regardless of what language you're currently using at any given time - is that typical C-problems sometimes show up, even while working in other languages, because those languages depend on software written in C. You sometimes also need to communicate with software (parts of your system) written in C to be able to do things not supported in your current language. You need to know C to be able to do this properly.

But that does not make C a _good choice_ whatsoever, for whatever - in general. It totally depends on context.

#1: ..yes, it's totally random; if your system was written in Lisp I'd recommend Lisp based on the same reasons and argumentation..

---

### Post by Grey on 2007-02-12
Huh?  There's something with a C compiler that doesn't have a C++ compiler?  Can someone point me towards that?  =P  I am terribly curious now.

---

### Post by LordHunter317 on 2007-02-12
That's very, very common on embedded platforms.   Especially 4, 8, and 16-bit microcontrollers (though hardly exclusively).  I've also worked on platforms that even where C++ was supported, many applications lacked the RAM/ROM to fit a C++ applications and didn't call for the added expressiveness anyway.

---

### Post by Grey on 2007-02-12
Interesting.  I didn't know that.  I always thought that when you get down to the REALLY low level programming, you had to use some weird proprietary language, or assembly.  But really, I wouldn't think that C++ would add much overhead to C, if the programmer didn't go nuts with C++ specific things.

Btw, I'm sorry to go offtopic here, but you seem to be fairly knowledgeable about this area.  I do programming on the Nintendo DS, which uses an ARM7 and an ARM9, but I was thinking that sometime when I have some time, I would LOVE to deal with lower level stuff.  I was thinking that it might be a nice project at some point to build my own MP3 player, and I looked into it.  It seems that most people who do such projects use a PIC microcontroller, which I know nothing about, but doesn't seem to be a general purpose processor like I am used to.  I would love to know how to learn to program for such things.  Can you give me any advice on a starting point for such a task?

---

### Post by samjh on 2007-02-12
I've used 8-bit PIC micro-controllers (PIC 16 series) for a few projects - chosen because of cost more than any other reason (limited project budgets). :)  But they have grown on me.

They are produced by Microchip Technology Inc, and there is extensive documentation available from their website: [http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=64](http://www.microchip.com/stellent/idcplg?IdcService=SS_GET_PAGE&nodeId=64)

Note that PIC series are usually micro-controllers, which have limited capability compared to microprocessors: less registers, less processing power, etc., but very affordable and easy to understand.

If you want to get into firmware programming, you need to first learn assembly, and then C.  But before that, you will need to learn about computer system theory.  I'll refer you to a course from my alma mater (I took this very course several years ago - some details have changed but fundamentals remain the same), which should give you enough knowledge to learn more later: [http://www.itee.uq.edu.au/~csse1000/notes.html](http://www.itee.uq.edu.au/~csse1000/notes.html)

Building your own MP3 player is a pretty advanced undertaking.  You will need to know how to work with electronic circuits.  This site offers basic MP3 player kits and technical documentation including schematics: [http://www.pjrc.com/mp3/](http://www.pjrc.com/mp3/)

---

### Post by LordHunter317 on 2007-02-12
> **Grey said:**
> Interesting.  I didn't know that.  I always thought that when you get down to the REALLY low level programming, you had to use some weird proprietary language, or assembly.Assembly is the weird properitary language ;)

>   But really, I wouldn't think that C++ would add much overhead to C, if the programmer didn't go nuts with C++ specific things.If you use C++ as C with stronger type checking, it doesn't add much (if any) overhead.  But it doesn't take much overhead to shift you to needing a larger ROM, for example, which may simply not be acceptable.

Most programs on microcontrollers are tiny (not that microcontrollers are all embedded systems, but I'm making a point).  Like, a few hundred **bytes** of asembly.  In such cases, even C may be too much overhead--the controller may have 256 bytes of EPROM on-board and exceeding that is unacceptable.

> It seems that most people who do such projects use a PIC microcontroller, which I know nothing about, but doesn't seem to be a general purpose processor like I am used to.  I would love to know how to learn to program for such things.  Can you give me any advice on a starting point for such a task?MP3 player may be a little complicated for a first task unless you have lots of digital design experience.  Start with some simplier projects first so you can really understand the PIC and its operation, then do the MP3 player.  Practically speaking, you're going to want to have an oscilloscope / logic analyzer.  I really prefer mixed-signal units over seperate hardware.

---

### Post by Grey on 2007-02-14
I kind of figured that would be the response.  ;)  I do know some MIPS assembly.  I'm not good with it by any means, but I'm sure I could fake it enough to hack together UI/input for an MP3 player.  I have a bachelor's degree in Computer Science, and a requirement for my degree was computer architecture.  So in theory, I could design my own microprocessor.  But I was a really bad student in that particular class.  All I really took out of it was assembly, but I am trying to make amends.

Where I really fail is the logic and circuit design.  Coding shouldn't really be an issue for me.  I am accustomed to low spec machines... (although not THAT low spec), and I am sure that I can make it work.  It's the actual design of the circuits that really scares me.

But thank you both for your replies.  I actually feel a whole lot more confident about my idea now.  :)  Knowing that I can program a PIC controller with assembly makes me feel loads better.  (somehow it just never clicked in my head)

But yeah, I was thinking of starting with some smaller, hello world type stuff, and moving up.  I have no doubts that such a project would take me a lot of time.  But it would be fun and educational.  Which is what I'm after.

---

### Post by Klipt on 2007-02-14
Forth is also used for some embedded systems - it requires very little space to implement. But it's a completely different way of thinking from assembly or C.

---

### Post by Devilcut on 2007-02-15
If you already kniw java then just use that instead of learning C

roflbbqpizza

---

### Post by Ben Sprinkle on 2007-02-16
> **Devilcut said:**
> If you already kniw java then just use that instead of learning C

roflbbqpizza

Leel nathan. I probably will use Java instead as C is not as cross platform as I would like it to be.

---

### Post by g3k0 on 2007-02-16
C is good to know because it is very widely used and is very efficient but.....
it is easy to use incorrectly
common things link strcat are very susceptible to buffer overflow.  There are often better things to use such as stlcat but still needs to be used correctly. gets is dangerous too.  Other problems arise if you dont use prototypes for your functions and dont forget to deallocate those mallocs!

C should have been replaced long ago.


Ack! PICs!   Noooooo i want a larger instruction set.. Bad risc bad!

---

### Post by Ben Sprinkle on 2007-02-17
I just can't decide what to use. :S:S:S

---

### Post by lnostdal on 2007-02-17
> **Ben Sprinkle said:**
> I just can't decide what to use. :S:S:S

..you can't decide what to use -- _for what_? what are you developing?

use many languages .. be flexible .. you "picking" C doesn't mean you're picking it as The One Language you're going to use for everything thereafter .. actually doing that would be incredibly stupid

---

### Post by Ben Sprinkle on 2007-02-18
> **lnostdal said:**
> ..you can't decide what to use -- _for what_? what are you developing?

use many languages .. be flexible .. you "picking" C doesn't mean you're picking it as The One Language you're going to use for everything thereafter .. actually doing that would be incredibly stupid
That's basically the idea being hit on the head with a hammer. I am looking for a language to use as 1 and only 1, that way it's much easier to remember.

---

### Post by Mirrorball on 2007-02-18
After you learn your first language well, it's very easy to pick others. It's not hard to remember at all. Don't worry about languages, almost everyone know several and we are not geniuses.

---

### Post by lnostdal on 2007-02-18
> **Ben Sprinkle said:**
> That's basically the idea being hit on the head with a hammer. I am looking for a language to use as 1 and only 1, that way it's much easier to remember.

This is not going to happen anytime soon so get over this ASAP so you're able to move along and not be stuck at this.

If you only do _certain kinds_ of tasks you might find One Language or a limited set of languages that are among the "most suitable" for those kinds of tasks. 

But you will _not_ find One Language or even a limited set of languages that are "most suitable" for _all_ tasks.

Do you have a certain idea what you want to work with? Here is three types of tasks:

* develop a linux device driver (a driver for a new wireless card for instance)
* develop a im-client for the desktop (jabber- or msn-based for instance)
* develop a web-site that manages customer contact information

..each type has a somewhat limited set of languages that are suitable for various reasons. A clear example is that you would never develop a device driver in PHP, but you could develop a web-site in PHP.

I know many languages but try to keep two of them (the ones with the least "overlap"#1) fresh in my mind at all times. 


#1: If they are too similar, or have too much overlap - there is almost no point in learning the second one.

---

### Post by Ben Sprinkle on 2007-02-19
But but but but. =\

---

### Post by Wybiral on 2007-02-19
It's true... At least as far as efficiency goes... Some languages are more efficient for certain tasks than others. Almost every languages has it's strong and weak points.

If you're wanting to develop for mobile devices for instance... This is where one of Java's strong points are.

If you're writing websites and web applications... HTML/PHP/Javascript/Java one of those is usually required.

If you're looking for fast portable development, you might look into python.

If you need speed and more direct communication with the hardware... C/C++ might be best.

But neither of those languages is the most efficient for all of those...

Unless you're developing the same type of program over-and-over... One language will not be enough... Unless you want to write grossly inefficient hacks to make one language do everything you need, but that's not productive or efficient at all.

Learn a few of them, at least.

---

### Post by Ben Sprinkle on 2007-02-20
I don't wanna.
C is cool but is crap because of the wide spread librarys and not directly cross platform. Plus gtk and the whole kde issue. =\

---

### Post by g3k0 on 2007-02-20
C is evil.  How I long for c++.  Or java ....

> That's basically the idea being hit on the head with a hammer. I am looking for a language to use as 1 and only 1, that way it's much easier to remember.

Languages get much easier to pick up once you understand the concepts behind code.  And any way you cut it you will be looking up syntax all the time.

---

### Post by samjh on 2007-02-21
> **Ben Sprinkle said:**
> But but but but. =\

Here is a simple answer for you: **use Java**.

Now, I may get flamed for this, but here are my justifications:

1. Java has a shallower learning curve than C++ (although similar learning curve to C).

2. Java is widely distributed across a massive range of computing platforms, including Windows, Linux, Solaris, and MacOS.

3. Java provides a massive set of standard APIs that make most common programming tasks as simple as looking up an encyclopedia.

4. Java provides a rich GUI library in the form of Swing.  If you use Netbeans IDE, you can use the very easy form designer to visually design GUI interfaces.  (I came from MS Visual Studio background, and you can take my word that GUI design in Netbeans is as easy it gets.)

Ignore the crap about slow performance, etc., as most of those issues have been resolved since Java 1.4 was released.  Now Java is almost as fast as pure C/C++, faster than pure Python, and sits between the two of them for ease-of-learning and coding efficiency.  It is also a good language for building good software engineering discipline: strong typing helps to avoid laziness that might be picked up by using dynamically typed languages like Python, while memory management is mostly automated so the programmer can concentrate on solving the problem at hand, instead of micro-managing memory.

Also worthy of mention is the demand for skilled Java programmers.  If you learn it well enough, you could even get a job as a professional programmer using Java skills.

Anyway that's just my recommendation.

---

### Post by Ben Sprinkle on 2007-02-21
> **samjh said:**
> Here is a simple answer for you: **use Java**.

Now, I may get flamed for this, but here are my justifications:

1. Java has a shallower learning curve than C++ (although similar learning curve to C).

2. Java is widely distributed across a massive range of computing platforms, including Windows, Linux, Solaris, and MacOS.

3. Java provides a massive set of standard APIs that make most common programming tasks as simple as looking up an encyclopedia.

4. Java provides a rich GUI library in the form of Swing.  If you use Netbeans IDE, you can use the very easy form designer to visually design GUI interfaces.  (I came from MS Visual Studio background, and you can take my word that GUI design in Netbeans is as easy it gets.)

Ignore the crap about slow performance, etc., as most of those issues have been resolved since Java 1.4 was released.  Now Java is almost as fast as pure C/C++, faster than pure Python, and sits between the two of them for ease-of-learning and coding efficiency.  It is also a good language for building good software engineering discipline: strong typing helps to avoid laziness that might be picked up by using dynamically typed languages like Python, while memory management is mostly automated so the programmer can concentrate on solving the problem at hand, instead of micro-managing memory.

Also worthy of mention is the demand for skilled Java programmers.  If you learn it well enough, you could even get a job as a professional programmer using Java skills.

Anyway that's just my recommendation.

Now that's what I am talkin abour brother! :D

---

### Post by Wybiral on 2007-02-21
> **Ben Sprinkle said:**
> Now that's what I am talkin abour brother! :D

Well... If you plan to write detailed 3d stuff... You probably aren't going to get very far with Java. I know Java is capable of it (making 3d applications), but it does have some overhead that gets in the way when you get to writing incredibly memory intensive applications (such as more detailed 3d games). I too am not trying to start a flame ware, just making a point...

You can't write device drivers or much hardware communication... 

You are limited to the user base of people who actually care enough to download Java (I actually deleted it because frostwire was the only program I used that required it... And frostwire was so memory intensive I could hardly do anything else with my computer when it was up. I have programmed in it for a while... But it never really appealed to me)

You also can't do things like shellcode insertion or inline assembly (two great speed enhancers, shellcode insertion actually allows you to write simple self modifying code)

NOTE:

I'm not trying to dog Java... I actually am beginning to see that it is not all that bad. That was not the point of this post... The point was that there is NO once-and-for-all language. Just learn one, when you feel confident with it... Learn something else. It's not hard... It will give you a wider range of experience and show you how to solve the same problems in different ways (habits will carry over from one language to another and you will generally become a better programmer as a result)

---

### Post by lnostdal on 2007-02-21
just let him have his simple answers

his lack of ability to provide any context with his questions even when asked is a sure sign it does not matter to him; he seeks to understand programming in general and java is suitable for that

---

### Post by hod139 on 2007-02-21
> **Wybiral said:**
> Well... If you plan to write detailed 3d stuff... You probably aren't going to get very far with Java. I know Java is capable of it (making 3d applications), but it does have some overhead that gets in the way when you get to writing incredibly memory intensive applications (such as more detailed 3d games). I too am not trying to start a flame ware, just making a point...

While I mostly agree with your post, Java is quite capable of doing "detailed 3D stuff".  The [JOGL]("https://jogl.dev.java.net/") project "provides hardware-supported 3D graphics to applications written in Java. JOGL provides full access to the APIs in the OpenGL 2.0 specification as well as nearly all vendor extensions."  What's really amazing are the [demos]("https://jogl-demos.dev.java.net/").  Anything you can do with C++/OpenGL you can do with Java/OpenGL.  Since most of the work is done on the graphics card, the performance issues you mention are not prohibitive.

---

### Post by Lster on 2007-02-21
I think Java is a really cool langauge and brilliant for begginners. However Sun's JVM just eats so much memory I would never reccommend using it for a comercial application. Netbeans (made in Java) runs with >100MB of memory for me!

To compare performance look at [this]("http://shootout.alioth.debian.org/gp4/benchmark.php?test=all&lang=gcc&lang2=java").

Whatever language, it usually isnt very hard to learn another so Java may be ideal.

---

### Post by g3k0 on 2007-02-21
> **samjh said:**
> Here is a simple answer for you: **use Java**.

Now, I may get flamed for this, but here are my justifications:

1. Java has a shallower learning curve than C++ (although similar learning curve to C).

2. Java is widely distributed across a massive range of computing platforms, including Windows, Linux, Solaris, and MacOS.

3. Java provides a massive set of standard APIs that make most common programming tasks as simple as looking up an encyclopedia.

4. Java provides a rich GUI library in the form of Swing.  If you use Netbeans IDE, you can use the very easy form designer to visually design GUI interfaces.  (I came from MS Visual Studio background, and you can take my word that GUI design in Netbeans is as easy it gets.)

Ignore the crap about slow performance, etc., as most of those issues have been resolved since Java 1.4 was released.  Now Java is almost as fast as pure C/C++, faster than pure Python, and sits between the two of them for ease-of-learning and coding efficiency.  It is also a good language for building good software engineering discipline: strong typing helps to avoid laziness that might be picked up by using dynamically typed languages like Python, while memory management is mostly automated so the programmer can concentrate on solving the problem at hand, instead of micro-managing memory.

Also worthy of mention is the demand for skilled Java programmers.  If you learn it well enough, you could even get a job as a professional programmer using Java skills.

Anyway that's just my recommendation.

Don't get this debate going..
1.  Hardly... maybe you can just do more with c++
2.  What major language isn't?
3.  Well lets not exaggerate
4.  Other languages have this too depending on the IDE
5.  Java is slow and efficiency is a good thing.  But He should stay away from pointers for a while so go java...
6.  Actually what you really need is a degree

So learn java... but don't get the Java rules mindset.

---

### Post by Mirrorball on 2007-02-21
Let him learn Java then. Why not? He will soon find out that it's not the answer to all problems but his time learning Java won't be wasted.

---

### Post by Wybiral on 2007-02-21
> **hod139 said:**
> While I mostly agree with your post, Java is quite capable of doing "detailed 3D stuff".  The [JOGL]("https://jogl.dev.java.net/") project "provides hardware-supported 3D graphics to applications written in Java. JOGL provides full access to the APIs in the OpenGL 2.0 specification as well as nearly all vendor extensions."  What's really amazing are the [demos]("https://jogl-demos.dev.java.net/").  Anything you can do with C++/OpenGL you can do with Java/OpenGL.  Since most of the work is done on the graphics card, the performance issues you mention are not prohibitive.

Once again... I am NOT trying to downplay Java, it certainly has it's role in the programming community. And yes... It can handle a relative amount of 3d in terms of speed. 

This is my opinion... Unfortunately I haven't seen Java run large enough 3d app's to prove either way, but those demo's were pretty simple. Once you get into large amounts of dynamic memory (such as loading large levels, models, particle systems, collision data) and then factor in the garbage collection processes that will have to check on all of that (and I mean hundreds of thousands of dynamically allocated floating point values) it just seems to me like that would be too much overhead.

Once again... I have no proof, and I may be totally wrong! Actually, it might sway my opinion some to see someone prove me wrong and present a large 3d simulation that can keep up with the speeds of a good C simulation. But, thats just my opinion based on what I've read about Java's methods of handling dynamic memory.

That's also only one factor... To truly reach maximum speed with most of my 3d programs, I often have to break them into assembly and optimize at a very low level (something I can't do in Java). Most of the really big and fast 3d/game engines use a substantial amount of assembly optimization, and I can't see them going that far if there weren't a reason.

Anyway... Like I said, Java does have it's place in the programming community since it's so portable and so widespread in mobile devices. I was just making a point that it is not the end-all language... Because there is none!

---

### Post by samjh on 2007-02-22
> **lnostdal said:**
> just let him have his simple answers

his lack of ability to provide any context with his questions even when asked is a sure sign it does not matter to him; he seeks to understand programming in general and java is suitable for that

That's why I recommended Java.

It's not the Universal Programming Language for Everything (tm).  But it's a solid starting language for most applications.

---

### Post by Ben Sprinkle on 2007-02-22
Not gonna use 3D, thanks for all the info guys! :)

---

### Post by Devilcut on 2007-02-23
Yer start it like 2d then once your gqme becomes done and you want challaenge thats when you make it 3d

but you probably wont even work on your game when we get internets roflbbq

---

### Post by Ben Sprinkle on 2007-02-23
I might make a 2d final fantasy type game.

---

### Post by Ben Sprinkle on 2007-02-23
Or I will start out with a 2d shooter, I was thinking of making an FPSRPG type. Where you grow levels by blowing the hell out of people. :)

---

