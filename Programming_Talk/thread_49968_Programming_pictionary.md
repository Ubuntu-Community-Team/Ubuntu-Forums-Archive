---
title: "Programming pictionary"
date: 2005-07-18
forum: Programming Talk
---

### Post by NoTiG on 2005-07-18
Im in the "planning" stage right now... and I want some advice.....

What im looking to do is a pictionary type game with multiple users, and while one person draws in real time while the others guess. A similar game is Isketch, but it is made with shockwave (proprietary). I wanted to make a free/open version..

I was thinking about using C++/anjuta/glade/ gtk+ .... but was wondering if this is the best idea? i have a little experience coding in c++ and i like the object oriented ness of it... ALso... when xgl and cairo come along with hardware accelerated desktop rendering , i wanted my program to be able to use it. so my questions are basically:

I will need a database... for storing user names, and their passwords. Also to store their profiles... and also to store their statistics (rankings, usage etc....) . I will also need a database for the worldlists... and to randomly generate them. What i dont understand is... isn't an array a database? why are database programs necessary if you can simply use arrays? Would it be the best thing to integrate a database? Is [Sqllite](http://www.sqlite.org/)  my best choice? 

Now the drawing window... If i make it a fixed amount of pixels then it will look different on diff peoples screens. Do you think it will be possible to scale it so that people using different resolutions can see it the same size? Will the different aspect ratios (widescreen vs full screen) make it distorted? Do i need to use cairo somehow to make this possible? (vector based graphics) 

THe drawing tools I need would be pretty simple... although i wanted to introduce a couple of complex things... like layers . Should i use code from an open source program like gimp? 

The book that i do have on c++ is pretty basic... it does not delve into the realm of networking. Obviously i was thinking of making this program as a server , and clients ... so i would need some kind of networking code. What book/online tutorial should i read? what functions will i need?

there are also some other cool "dream" features i would like. But are probably way over my head (at the moment) . FOr instance take this idea: 

> I plan to update and extend a plugin called Crazy Chat that I made for Gaim for my senior software project at Stanford University. During a Crazy Chat session, the program uses the input from the local user’s webcam, and does image processing to detect key facial features such as the eyes and the corners of the mouth. It uses these features to determine parameters that describe the user’s expression, such as head tilt, head distance, mouth shape, and blinking. These parameters are then sent across the network, and are used to render a 3D “cartoony” version of the person’s face on the remote user’s computer (in the current version of Crazy Chat, there is a dog and a shark face).

Crazy Chat has several appealing benefits beyond the inherent fun of being turned into a three dimensional Labrador. The first is that it is extremely low bandwidth. For each frame, we only need to send about one hundred bytes, rather than many kilobytes for streaming video. This could potentially allow for large multi-conference Crazy Chats, in which each user represents a different creature in an online RPG troop. Another advantage of Crazy Chat over ordinary video conferencing is that it allows the user a higher degree of privacy. Rolled eyes, bed hair and messy rooms are all suppressed behind the exaggerated smiles of an urban hyena or razor sharp winks of a lady killer whale. And of course the inherent fun alluded to earlier should not be casually dismissed. Gaim is first and foremost and entertainment application. 

I even thought of a name for my program already. ANd i would like to include it with the ubuntu distro (and make it small) . And maybe even Edubuntu because i think it has some good eduational purposes.

[Here](http://ubuntuforums.org/gallery/showimage.php?i=543&original=1&c=4) is a mockup.

---

### Post by LordHunter317 on 2005-07-18
> **NoTiG]ALso... when xgl and cairo come along with hardware accelerated desktop rendering ,[/quote]By and large, choice of language will have little effect on whether you support these technologies or not.  The GUI toolkit does it for you.  It's only when you don't use it/go around it that language would start to matter.

> I will need a database...No, you likely won't.

[quote[ for storing user names, and their passwords.[/quote]Why usernames and passwords?  If you provide a matchmaking service, I can understand that needing them.

But I'd provide that seperate from the game proper.  Just let people connect to each other via IP.  

>  Also to store their profiles... and also to store their statistics (rankings, usage etc....) .This also sounds like a matchmaking service, which you should consider a seperate application.

>  I will also need a database for the worldlists... and to randomly generate them.Probably not.  Most wordlists are textfiles, and it's probably eaisest and most efficent to store your data as plain text.

> What i dont understand is... isn't an array a database?In a very general sense, yes. 

But RDBMSes, like PostgreSQL and Oracle, provide hundreds of features a mere array cannot.  You also don't need most of these features.

>  why are database programs necessary if you can simply use arrays?Data integrity, for one thing.  

>  Would it be the best thing to integrate a database?No.

As for storing your wordlist, a tree of some sort may be better as it'll allow for faster  searching.  If the only concern is fast access to random elements, then a std::vector is your best bet.  Randomize the indexes and select words based on the random index.

[quiote]Now the drawing window... If i make it a fixed amount of pixels then it will look different on diff peoples screens. Do you think it will be possible to scale it so that people using different resolutions can see it the same size?[/quote]They are seeing it the same size, as far as your application is concerned.

But the canvas that's drawn on and that the guessers see shouldn't be a fixed size.  It should be allowed to grow as large as someone wants, with perhaps a minimum size set.  People with larger windows just end up with wasted space.

> although i wanted to introduce a couple of complex things... like layers . Seems unecessary to me.

> Should i use code from an open source program like gimp? Possibly, but not likely to be helpful.

> The book that i do have on c++ is pretty basic... it does not delve into the realm of networking.That's because networking isn't part of the C++ standard said:**
>  Obviously i was thinking of making this program as a server , and clients ... so i would need some kind of networking code. What book/online tutorial should i read? what functions will i need?Google for Beej's Sockets Guide for a decent guide on UNIX socket programming.  Look at ACE.

---

### Post by NoTiG on 2005-07-18
[QUOTE=LordHunter317]

> Now the drawing window... If i make it a fixed amount of pixels then it will look different on diff peoples screens. Do you think it will be possible to scale it so that people using different resolutions can see it the same size?They are seeing it the same size, as far as your application is concerned.
[/QUOTE]


Oops mental error there. WHat i meant was it would look like the same size... but with people using larger resolutions there would be wasted space. So it has to be scaled....

Im not sure if you mean likening my program to a matchmaking service as a derogatory term.... but lots of games have ranking systems and user names passwords. I have played this game for over three years and i know what ppl want... more imporantly its what I want ... so yes im going to have passwords and rankings. And with the days where you can get a free account with google for 2 Gigabytes... space isnt that much of an issue for storing information. I see what you mean that i dont have to worry about whats underneath GTK+ (cairo) for it to work properly . But if im going to have profiles for people.. and include a place for them to upload their own avatars... i think i will need a database. A single array wouldn't suffice. 

Thankyou for telling me about the networking....... :P

---

### Post by Hanj on 2005-07-18
For networking in C/C++, have a look at [libnet](http://libnet.sourceforge.net/) or [HawkNL](http://www.hawksoft.com/hawknl/). 

Or, you could use Java instead; it has built-in, very easy-to-use networking.

---

### Post by LordHunter317 on 2005-07-18
[QUOTE=NoTiG]Oops mental error there. WHat i meant was it would look like the same size... but with people using larger resolutions there would be wasted space. So it has to be scaled....[/quote]I think spending a lot of time on this would be a fruitless endevor, as you can't even reliably get things like DPI under X.

> Im not sure if you mean likening my program to a matchmaking service as a derogatory term....Nothing of the sort.

What I'm saying is this: the game part (pictionary) and the matchmaking part are basically **two seperate applications**. 

I would work it out like so:[list=1][*]Work on the part that lets you play pictionary first.  Let a person connect to another over the network, draw pictures, guess, and chat.  Don't worry about username, passwords, ranking for now.[*]Then, worry about the matchmaking service.  This will require a central server to hold all the data.  You'll probably want a web-based interface to it, too. Don't worry about how it interfaces with the game terribly much, just get somethign to show rankings, profiles, etc.[*]Finally, intergrate the two.  Make the matchmaking service show all games in play and who's playing on them.  Have the game allow you to login to the matchmaking service when you start up, and such.[/list]

>  But if im going to have profiles for people.. and include a place for them to upload their own avatars... i think i will need a database. A single array wouldn't suffice.You will.  But only in the server application that stores this stuff.  The game client that people run won't need one.

---

### Post by NoTiG on 2005-07-18
[QUOTE=LordHunter317]I think spending a lot of time on this would be a fruitless endevor, as you can't even reliably get things like DPI under X.[/quote]
How would i do it then? is it not possible using a plain desktop application? I know games can do it... since they support multiple resolutions. Would i have to use opengl libraries? Do i have to wait for xgl or any new technology before this is "reliable" and possible? 

> 

Nothing of the sort.

What I'm saying is this: the game part (pictionary) and the matchmaking part are basically **two seperate applications**. 

I would work it out like so:[list=1][*]Work on the part that lets you play pictionary first.  Let a person connect to another over the network, draw pictures, guess, and chat.  Don't worry about username, passwords, ranking for now.[*]Then, worry about the matchmaking service.  This will require a central server to hold all the data.  You'll probably want a web-based interface to it, too. Don't worry about how it interfaces with the game terribly much, just get somethign to show rankings, profiles, etc.[*]Finally, intergrate the two.  Make the matchmaking service show all games in play and who's playing on them.  Have the game allow you to login to the matchmaking service when you start up, and such.[/list]

You will.  But only in the server application that stores this stuff.  The game client that people run won't need one.

Im sure i couldnt do all of the features at once... so yes a step by step plan would be the best . thankyou :P

btw i dont plan on being "finished" for years... so if some of this isnt possible now i want to be able to incorporate it later.

---

### Post by LordHunter317 on 2005-07-18
[QUOTE=NoTiG]? I know games can do it... since they support multiple resolutions. [/quote]I can't think of any games where the sizing changes the same as I increas resolutions.

> Do i have to wait for xgl or any new technology before this is "reliable" and possible?I'm not sure you'll ever be able to reliably do it, period.  Moreover, I'm not sure you really want to.  I think the headache probably isn't worth the gain.

---

### Post by NoTiG on 2005-07-18
[QUOTE=LordHunter317]I can't think of any games where the sizing changes the same as I increas resolutions.

I'm not sure you'll ever be able to reliably do it, period.  Moreover, I'm not sure you really want to.  I think the headache probably isn't worth the gain.[/QUOTE]

OF course games can do it. That is why if you enter into different resolutions there aren't huge 3 inch borders taking up each side of the screen. If i *dont* do this then any pictionary games are going to be forever hindered by the lowest common denominator of resolution users. The people still using low resolutions would have to be the default (safe) setting , or else the space would be drawn off the screen.

---

### Post by LordHunter317 on 2005-07-18
[QUOTE=NoTiG]OF course games can do it.[/quote]yes, but not for fixed images, in the way you're suggesting.  If they have a picture, they don't rescale to make sure it always is an inch tall on every screen.

I understand what you're getting at now, though.

> If i *dont* do this then any pictionary games are going to be forever hindered by the lowest common denominator of resolution users.I'm not sure that's a terrible flaw.  How much drawing space is really needed, anyway?

---

### Post by NoTiG on 2005-07-18
[QUOTE=LordHunter317]

I'm not sure that's a terrible flaw.  How much drawing space is really needed, anyway?[/QUOTE]

As you can see more than this [here](http://ubuntuforums.org/gallery/showimage.php?i=547&c=4) 

The idea is simple... whatever resolution someone uses the size of the draw screen takes up a proportion, rather than a fixed amount. Now if someone else is using this same resolution, then they should see the same exact picture. If someone has a smaller resolution, they have less pixels to work with therefor the picture would be the same size, but scaled with a slight degredation in quality (the quality is low anyway with low resolutions) . if someone is using a larger resolution, the picture will remain the exact same size (proportion) but just changed to the higher resolution with no change in quality (sinze a higher resolution has more pixels to work with. I think the scaling should be done on the client side of the program to offload the server, and should be scaled in real time on the fly. we are talking about small amounts of information here... the draw starts out blank and as the round progresses... only a very small amount of information is actually drawn at a time.

The benefits are two-fold: it fits your screen, putting less strain on the eyes i... and the quality of the picture is only limited by the clients monitor, not the lowest common denominator. in isketch... its very "pixelated" because the resolution is so small. Less wasted space.

---

### Post by NoTiG on 2005-07-20
Im currently considering c++, python, and mono.... which one ?!?  ](*,)

---

### Post by kamstrup on 2005-07-21
[QUOTE=NoTiG]Im currently considering c++, python, and mono.... which one ?!?  ](*,)[/QUOTE]
 NOT C++, if you're not a seassoned programmer. C++ is perhaps the most complicated and difficult programming language on this planet![1]

Mono on Python are both good. Python is perhaps a tad easier to learn, but Mono has - a bit - better documentation.

[1]: I stress this to all people about to choose programming language: The specification for C++ is > 900 pages! While C is little over 100 pages... If you really want to learn C++ start by learning C# (read: mono) or Java - they resemble it a lot, but are far easier, then you can always move on to C++...

---

### Post by NoTiG on 2005-07-21
I know some basic c++... i think i got up to chapter 15 which introduced classes... but anyways..

What about [ironpython](http://www.ironpython.com)  . Im currently considering plain Gtk+  with anjuta/glade, or C#/mono or Ironpython. Is there any actual advantage to using c# or ironpython which works with .net? I mean.... isnt c++ a cross platform language? why is C# or ironpython any "more" cross platform? Are there any other advantages? Here is what it says for ironpython:

    *  Fast - IronPython-0.6 is up to 1.7x faster than Python-2.3 on the standard pystone benchmark.  An early performance report is are contained in this paper for PyCon 2004.
    * Integrated with the Common Language Runtime - IronPython code can easily use CLR libraries and Python classes can extend CLR classes.
    * Fully dynamic - IronPython supports an interactive interpreter and transparent on-the-fly compilation of source files just like standard Python.
    * Optionally static - IronPython also supports static compilation of Python code to produce static executables (.exe's) that can be run directly or static libraries (.dll's) that can be called from other CLR languages including C#, VB, managed C++ and many more.  Note: static compilation is only partially implemented in the 0.6 public release.  This will need further development before being useful.
    * Managed and verifiable - IronPython generates verifiable assemblies with no dependencies on native libraries that can run in environments which require verifiable managed code.
    * Not finished - IronPython is currently at a pre-alpha stage suitable for experimentation but not for serious development work.  The latest public release can be downloaded below.

---

### Post by LordHunter317 on 2005-07-21
[QUOTE=kamstrup][1]: I stress this to all people about to choose programming language: The specification for C++ is > 900 pages! While C is little over 100 pages...[/quote]And the full standards for  J2SE and C#/.NET are much, much larger, because they provide much more standard API.

Your point?  Size of specification has no bearing on how difficult it is to program in a language.

> If you really want to learn C++ start by learning C# (read: mono) or Java - they resemble it a lot, but are far easier, then you can always move on to C++...No, terrible idea.  As a general rule, learning one language to learn another is always a bad idea.  There are a few exceptions in the functional and esoteric realms, but for C-derived languages, it's silly.

---

### Post by NoTiG on 2005-07-21
it will probably take me a while to decide which... since its probably the most important decision of a program... which program to code in lol. I want the .net framework so im going to either:

C#,
Ironpython,
Boo,
maybe C++ with the CLI? 

The pros ive read about python are that it has elegant syntac, but no compile time error checking. Does boo take the best from C# and python? 

[http://boo.codehaus.org/BooManifesto.pdf](http://boo.codehaus.org/BooManifesto.pdf)

One other minor thing im worried about is documentation, and available classes that i wil be able to use. Boo might be the best , but i might end up using something like C# because it is more popular......... any ideas ?

edit: available classes might not be an issue then: You have access to the standard class library that is included with .NET and Mono.

And the issue of having a compiler time error checking that I understand is more important for large software projects.... Is there any speed diference between Ironpython vs c# ?

---

### Post by LordHunter317 on 2005-07-21
[QUOTE=NoTiG]it will probably take me a while to decide which... since its probably the most important decision of a program...[/quote]Langauge is generally the least important decision.  Design is far more important, and way too under-emphaiszed.

Your language decision should boil down to two factors:[list][*]Do I know the language or can I learn it in sufficent time[*]And is the language going to help me realize my design the eaisest?[/list]

>  maybe C++ with the CLI? Managed C++ isn't available for Mono, so that's right out.

---

### Post by kamstrup on 2005-07-22
Let's not take down a sparrow with a gattling gun LordHunter... Although you are correct in your above points, I don't think they apply to a novice programmer with a hobby project...

> No, terrible idea. As a general rule, learning one language to learn another is always a bad idea. Actually I was hoping that NoTiG would start using another language and forget about C++ in the meantime. My point was merely: "Don't choose C++ as you first programming language".

Maybe I can't use spec page numbers to justify my claims, but the point stands - C++ is really hard to master, and is far from being newbie friendly.


Nothing teaches you more about coding than coding. It is more than possible to drown a hobby project in  the design phase. So I say; just get down and dirty! When you feel confident with a language and some relevant APIs, then proper design is invaluable.

NoTiG: C++ is all about classes! There's not much point in using C++ if you don't use classes. C++ is an object oriented programming language (some would merely say it has *support* for objects) - as is mono and python. 

Mono and Python both has excelent documentation, so that shouldn't be a concern.

---

### Post by LordHunter317 on 2005-07-22
> **kamstrup] I don't think they apply to a novice programmer with a hobby project...[/quote]But they do.  The most important time to learn how to do things the right way is when you're a novice.

> My point was merely: "Don't choose C++ as you first programming language".Then why didn't you just say that?  Instead you said, "Learn C# to learn C++", which is a completely different thing.

> Nothing teaches you more about coding than coding.So why do some schools start their CS curriculum without teaching a language at all?  While I won't argue the value of hands-on experience, there are plently of things that can be learned about writing code probably even if one doesn't know a language.  Algorithms, for the most part.  Data structures, for another.  

>  It is more than possible to drown a hobby project in  the design phase.It's also possible to drown it in the coding phase because someone has no design to code against.  And I'd say for novice programmers working on a design of any complexity, the latter happens more than the former.

I'm not advocating a full design to DOT-STD-2167A or something said:**
> NoTiG: C++ is all about classes! There's not much point in using C++ if you don't use classes.Simply not true.  If it were just about classes, it wouldn't support having functions ouside of classes.  C++ is a multi-paradigm programming language.  You can do procedural, OOP, generic, and even some functional programming in it, which is what makes it so indispensible for many things, once mastered.

---

### Post by kamstrup on 2005-07-22
DISCLAIMER: NoTiG, you have no interest in the following...

> Then why didn't you just say that?Because I'm like an oracle; - I speak in tongues :)

I've followed beginners CS courses myself a few years ago, with a heavy weight on design patterns and data structures at the beginning. End result: Everybody knew the differences between objects and classes, could sketch the basics of a linked list, but could not implement a "for loop". Seriously!

> It's also possible to drown it in the coding phase because someone has no design to code against.  And I'd say for novice programmers working on a design of any complexity, the latter happens more than the former.
Well, both things happen and that's 100% sure, whether one thing or the other is dominant is probably impossible to tell.

> And you can't write good code until you have a good idea of what you want. Yes. There seems to be very little code that is written entirely without purpose :)

> C++ is a multi-paradigm programming language.  You can do procedural, OOP, generic, and even some functional programming in it That's exactly what makes it so difficult to understand. If you're not a skilled programmer you'll quickly mix up the paradigms and make a mess. I'd still argue that C++ is *primarily* an object oriented language. At least that's how you commonly use it.

---

### Post by LordHunter317 on 2005-07-22
[QUOTE=kamstrup] End result: Everybody knew the differences between objects and classes, could sketch the basics of a linked list, but could not implement a "for loop". Seriously![/quote]Yes, but here comes the important question(s): Was that because languages were simply not taught at all?  Or was it because they weren't tought well?

Just like algorithms and data structures have to be taught well, syntax and semantics of a language must be as well.   To be a good progammer, you have to have a good grasp of both.

Unfortunately, most programs seem teach only one well, if at all.

---

### Post by NoTiG on 2005-07-28
I'm leaning towards Just python right now... I don't see much advantage in using Ironpython, except that maybe I won't have to compile it for each architecture i want? But i will have to rely on them having a .Net framework.... what if they don't ? In the future, say 3-4 years from now... will the majority of people even have the .Net framework? 

Another thing.. I realized what i want is scalable vector Graphics A la Inkscape. If i used python would i be able to use code from inkscape which is in C++ ???

---

### Post by charlieg on 2005-07-28
[QUOTE=NoTiG]IAnother thing.. I realized what i want is scalable vector Graphics A la Inkscape. If i used python would i be able to use code from inkscape which is in C++ ???[/QUOTE]
Half of the attraction of .NET / Mono is that, using the CLI, you get access to application libraries written in other programming languages.  If the Inkscape team release a canvas lib then you'll be able to use it in a Mono app, no doubt, especially with Gtk#.

---

### Post by Soulfly on 2005-07-28
[QUOTE=NoTiG]I'm leaning towards Just python right now... I don't see much advantage in using Ironpython, except that maybe I won't have to compile it for each architecture i want? But i will have to rely on them having a .Net framework.... what if they don't ? In the future, say 3-4 years from now... will the majority of people even have the .Net framework? 

Another thing.. I realized what i want is scalable vector Graphics A la Inkscape. If i used python would i be able to use code from inkscape which is in C++ ???[/QUOTE]
Python [c-types ](http://starship.python.net/crew/theller/ctypes/) (aptitude install python-ctypes) lets you use c datatypes in a nice fashon (call dlls etc). To wrap classes I should look at [SIP](http://directory.fsf.org/devel/prog/cpp/Python-SIP.html). It's a very good chance however that someone allready done this for you so try google or the incscape web site.

If you want to distribute python code I would stay out of the .NET world. Use ironpython if you must integrate with legacy .NET code, but this is a rather rare scenario.

---

