---
title: "Need a Good and Easy C++ IDE for Ubuntu"
date: 2014-12-31
forum: Programming Talk
---

### Post by panjgoori on 2014-12-31
Hello everyone. Im searching for a good and easy to use C++ IDE like Dev C++ for windows. Im considering KDevelop. Is there any other good C++ IDE ? Im currently learning Loop's and Functions. and any good book regarding Programming will be a bonus. thanks.:KS

---

### Post by flaymond on 2014-12-31
Well, I'm just using a text editor(vim or anything else) and the gcc compiler. You should try Geany(lightweight) or Codeblocks(slightly heavy, but better for devs)...if you a learner or beginner..I prefer using text editor instead IDE....but yeah..it's your choice...I will only prefer these IDE to use...

I'm using C++ primer plus and the C++ official book by Bjourne(The creator of C++)

---

### Post by Gustaf_Alhll on 2014-12-31
> **InterProg said:**
> if you a learner or beginner..I prefer using text editor instead IDE....but yeah..it's your choice...

Gotta agree to some extent. Working with a text editor leaves some advantages and disadvantages. For example: IDE's highlights errors to make it easy to spot misspelling, syntax errors, ect. But IDE's can also slow your work down since it has to constantly check the code you write, while text editors doesn't have that limitation. With other words: You can write faster with regular text editors, but you have to pay more attention to avoid errors (Which is in my case good, since paying attention can also avoid errors that isn't highlighted in an IDE and overall solves problems in the future).

---

### Post by slickymaster on 2014-12-31
[Eclipse]("https://eclipse.org/downloads/packages/eclipse-ide-cc-developers/keplerr")

---

### Post by QIII on 2014-12-31
As a professional software developer, let me just say that using an IDE has never slowed me down.  Quite the opposite, in fact.  I could not do what I do nearly as rapidly or efficiently without an IDE.

Schools eschew IDEs for purposes of standardization and enforcing good practices. You are in class to learn a language, not the intricacies of an IDE.  That would burn up precious time. By and large, professionals use IDEs these days.

Eclipse and the hated Netbeans (with the C++ plugins) both work pretty well for me.

But I will agree that if you are just at the beginning of your adventure, you can get wrapped around the axle by the IDE and using a text editor will keep you focused on the language.

That said...  If you are taking a class, do as instructed.  If you are learning on your own with an eye to one day being employed in the industry, learn how to use an IDE since that is generally how it's done in a production environment.

---

### Post by 3246251196 on 2015-01-01
> **QIII said:**
> As a professional software developer, let me just say that using an IDE has never slowed me down.  Quite the opposite, in fact.  I could not do what I do nearly as rapidly or efficiently without an IDE.

Schools eschew IDEs for purposes of standardization and enforcing good practices. You are in class to learn a language, not the intricacies of an IDE.  That would burn up precious time. By and large, professionals use IDEs these days.

Eclipse and the hated Netbeans (with the C++ plugins) both work pretty well for me.

But I will agree that if you are just at the beginning of your adventure, you can get wrapped around the axle by the IDE and using a text editor will keep you focused on the language.

That said...  If you are taking a class, do as instructed.  If you are learning on your own with an eye to one day being employed in the industry, learn how to use an IDE since that is generally how it's done in a production environment.

No doubt you are more experienced that me. But I have the sort of mind that makes me suggest this:

Stick it to the man and use Emacs as your IDE at all costs.

But, this is probably the worst suggestion of all time, so simply disregard it.

---

### Post by Rocket2DMn on 2015-01-01
I recommend using a text editor if you are learning a language.  This forces you to explicitly write everything out and manually write properly formatted code.  Also +1 for using a text editor in an academic environment - it can take too long to learn or fiddle with an IDE, and if you run into trouble, things can get nasty quickly when an assignment deadline is close.

However, IDEs are great for professional developers/engineers.  In my experience, most professionals use them (and other tools) when possible as they allow more automated integration and can reduce coding time and contribute to other development-related activities.  I use Code::Blocks (previously mentioned here) for development.  It's not perfect, but it gets the job done fairly well, even if you need to do your compiling outside the IDE.

---

### Post by JKyleOKC on 2015-01-02
> **QIII said:**
> As a professional software developer, let me just say that using an IDE has never slowed me down.  Quite the opposite, in fact.  I could not do what I do nearly as rapidly or efficiently without an IDE.As another pro, for more than 40 years now (starting on mainframes, then minis, finally micros), I cannot agree more. A good IDE does much of the repetitive work and housekeeping for me, allowing me to concentrate on the essentials of each new program. I've found the Delphi package, originally from Borland, to be essential when developing tools for my Windows-using customers.

I'm now moving into a bit of tool-making for Linux, and adding Python to my list of languages -- which brought me to this thread hoping to find references to general-purpose IDEs similar to that of Delphi. Currently I'm trying to wrap my head around Geany rather than using just a plain text editor, and it seems almost good enough to keep. However during the learning curve for a new language I really need an excellent context-help interface -- and haven't yet found it.

However to stay on topic here, any IDE is better than none, once you've learned the language. While vi or emacs or even dear old ed will work, why walk when you can ride?

---

### Post by Holger_Gehrke on 2015-01-03
> **JKyleOKC said:**
> As another pro, for more than 40 years now (starting on mainframes, then minis, finally micros), I cannot agree more. A good IDE **does much of the repetitive work and housekeeping for me**, allowing me to concentrate on the essentials of each new program. 

And that's the reason to avoid an IDE like the plague when you're just beginning or learning a new language: it does things for you and assumes you know about these thing and would do them this way yourself.

---

### Post by JKyleOKC on 2015-01-03
I agree completely!!! Once you've gathered enough experience to know what's going on, and thus enough to tweak the preferences of an IDE to suit your own needs, such a tool can be an essential item. Until then, you should steer clear.

My own search for an IDE suited for use with Python, which I'm just beginning to learn, seems to have succeeded at Geany. Its context-sensitive help leaves quite a bit to be desired, but I think that's because Python's documentation is more scattered than that of many older languages. I did find, in less than a dozen hours of learning curve, that Geany's ability to execute the script and display error conditions in a separate terminal window, provided me a very workable substitute. 

Using print statements to display output from expressions using features of which I wasn't sure, and viewing their result instantly, enabled me to get up to (acceptable if not ideal) speed in just a few days. I'm by no means as fluent in Python yet as I am in several other languages that I've used for years, but at least I can already get useful results -- and that's what counts. I'll learn lots more as I refine my initial program from "useful" to "ready for prime time" condition, thanks to a friendly but not overbearing IDE.

---

### Post by TheFu on 2015-01-08
IDEs have a place, but shouldn't always be used, because you become an expert at the IDE, not at the language.  That's happened to many Windows programmers.  They can't easily migrate to Linux programming because they've become 100% dependent on 1 specific IDE.  Plus some IDEs will use non-standard suggestions for help which breaks code on other compilers.

When just starting out a properly configured IDE can make you feel more productive, but if there is any error in the configuration, you will be completely screwed.

At some point, perhaps a few months into learning the language, you need to do it the hard way - editor, makefile, CLI debugger for at least a month. This will solidify and fill-in parts of your training that you've missed.  It will be hard and you'll get frustrated especially for compiled languages.

Eclipse? Seriously?  Is there any program that takes more RAM and runs slower than that?  I only have a Core i5 and 8G, so it isn't worth the slowdown to me.

For quick scripts, I use vim. For longer programming sessions I use geany (regardless of platform).  I'm a reformed emacs, Borland-IDE, VisualStudio user. For me geany is just enough IDE, but doesn't remove my thoughts too far from the code.  It is also trivial to migrate geany between different systems and in a team environment, that is highly critical.  
Ever tried to clone an eclipse environment between different systems, programmers and OSes?  I have.  I've also tried to create identical VC++ configs for teams of 20 developers getting new computers with a number of 3rd party libraries and tools.  Painful doesn't describe it. The loss of developer productivity was a big hit for about a week. Unacceptable.

If you are the only programmer - do whatever. But if you are in a team, getting a solution that easily can be mirrored matters more, IMHO.

---

### Post by panjgoori on 2015-02-25
thanks all for such informative replies and also sorry for late replying to this thread. I have installed both Geany and Codeblocks both gives error when i execute a compiled program like simple cout program. it says permission denied. seems like these two doesn't have required permission to compile and run a program. any help ? and which text editor you people are referring to ? Leafpad ?

to further ease things im a student of Computer Science. In university we mostly work on Dev C++. but are free to try anything.

---

### Post by JKyleOKC on 2015-02-25
> **panjgoori said:**
> thanks all for such informative replies and also sorry for late replying to this thread. I have installed both Geany and Codeblocks both gives error when i execute a compiled program like simple cout program. it says permission denied. seems like these two doesn't have required permission to compile and run a program. any help ? and which text editor you people are referring to ? Leafpad ?

to further ease things im a student of Computer Science. In university we mostly work on Dev C++. but are free to try anything.If you are compiling the program and then trying to execute it immediately, which is a quite normal approach in Windows, you're probably running into the lack of the "execute" permission in the program. In Linux, this permission is never set automatically when a file is created; it must be set manually after creating the file but before attempting to execute it. This makes the "compile and immediately run" technique impossible under Linux, no matter which distribution or IDE you use.

If you can find a C++ interpreter that's fully compatible with your compiler, you might use it to emulate the desired technique; other languages do something of this sort. When I'm developing Python apps under Geany, for instance, I can use the "compile and run" approach with no problem. The IDE launches a child terminal window and runs the code in it, giving me the ability to use "print" statements as debugging aids.

It's also possible that the "permission denied" error could come from attempting to work in a directory outside of your $HOME tree, in which you don't have write permission so the compile step fails to finish, but lack of the execute bit seems much more likely.

---

### Post by TheFu on 2015-02-25
> **panjgoori said:**
> thanks all for such informative replies and also sorry for late replying to this thread. I have installed both Geany and Codeblocks both gives error when i execute a compiled program like simple cout program. it says permission denied. seems like these two doesn't have required permission to compile and run a program. any help ? and which text editor you people are referring to ? Leafpad ?

to further ease things im a student of Computer Science. In university we mostly work on Dev C++. but are free to try anything.

This is exactly why you need to use a simple editor and run compile from a shell.  Even with these simple IDEs, this minor issue is throwing you off.  By using a Makefile, you can have the link command output to the filename you want AND change the file permissions, if needed, to whatever you need. This is very common.  

> When just starting out a properly configured IDE can make you feel more productive, but if there is any error in the configuration, you will be completely screwed. - TheFu ... er ... Jan 8, in this thread.

Please build it from the command line and post both the command used AND the output.  If you are trying to build on NTFS, don't. It doesn't support nominal POSIX file permissions and you will just have issues.

---

