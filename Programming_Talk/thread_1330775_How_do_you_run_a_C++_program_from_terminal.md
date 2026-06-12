---
title: "How do you run a C++ program from terminal?"
date: 2009-11-18
forum: Programming Talk
---

### Post by D3mon_Spawn on 2009-11-18
I just finished a very basic C++ project which involves simple cout/cin (I am using Netbeans); does anybody how I can run the actual compiled program from the terminal. I know I can just do this through Netbeans but I'm just curious. I think I have to find the .exe file or something bur I'm not sure what terminal cmds to use.

---

### Post by jdunn on 2009-11-18
./<program_name> ?
Executables normally don't have a .exe extension in linux.  However, object files usually have an .obj extension and C++ source normally has the .cpp extension.  I do not use Netbeans so, I'm not sure where your executable is in your project.

---

### Post by akvino on 2009-11-18
> **D3mon_Spawn said:**
> I just finished a very basic C++ project which involves simple cout/cin (I am using Netbeans); does anybody how I can run the actual compiled program from the terminal. I know I can just do this through Netbeans but I'm just curious. I think I have to find the .exe file or something bur I'm not sure what terminal cmds to use.

Compile it with c++ compiler and run .exe file 

./file.exe

---

### Post by D3mon_Spawn on 2009-11-18
> **jdunn said:**
>  Executables normally don't have a .exe extension in linux. 

What extension do they have in Linux?

---

### Post by akvino on 2009-11-18
> **D3mon_Spawn said:**
> What extension do they have in Linux?

Whatever you tell it to be? Pending on how Netbeans saves the file. 
The best way to find it (if you are not sure what extension it is) would be to run 'file' command against it.

#file filename.exe
or whatever extension you might have.

Here is example against hw.exe:

file hw.exe
hw.exe: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.18, not stripped

---

### Post by meson2439 on 2009-11-19
> What extension do they have in Linux?

I'd prefer it without extension. For example, if the c++ code is hello.cpp, then the executables should be just **hello** and you run that on the terminal using **./hello **

To compile a basic c++ codes in the terminal, type 
```
g++ -Wall hello.cpp -o hello
```

That will save you a lot of trouble in identifying which file is an executable. They don't have extensions but they're not folders either, so the color for an executable is different compared with the folders. This also reminds us that folders is also a file in linux, including drivers and everything else.

---

### Post by A_Fiachra on 2009-11-19
> **D3mon_Spawn said:**
> What extension do they have in Linux?

Linux doesn't have extensions ... it's not a brain dead OS like Windoze, at least not when it comes to actually developing anything.

To make life easy, however, there are certain conventions.

If I have a c++ source file called foo.cpp and I run

```

gcc -c -Wall -g foo.cpp

```

The program gcc will understand that foo.cpp is a C++ source file (not a fortran, C or java source file) and generate an object file with the extension .o

If I then do:

```

gcc -g -L/usr/lib -lstdc++ foo.o

```

gcc will understand that i intend to invoke the linker (ld) and use libstdc++.so in the /usr/lib directory, also -- add debugging symbols.

Because I didn't specify a target, gcc will produce a file a.out and set executable permissions on it.

I type:

```

./a.out

```

et voila.


On the other hand I can specify a target with gcc:

```

gcc -g -L/usr/lib -lstdc++ foo.o -o foo.blah.blippity.blah
./foo.blah.blippity.blah

```

It makes no difference what I call the compiled binary executable, linux could care less.

Of course, for a simple program, I would skip the intermediate object:

```

gcc -g -Wall -lstdc++ foo.cpp -o foo

```

and now gcc understands that I want to compile a c++ source file, link it to the system's standard c++ shared object and put the result (with debugging symbols) in a file called foo.

Or I can make my life even easier:

```

g++ -g -Wall foo.cpp -o foo

```

g++ is a program that does everything gcc did in the example above, but it only deals with c++ code and linkage.

This is why I always steer new developers away from IDE's -- they cause brain damage.  In the *nix world, learn vi, emacs and the command line (bash, sh and ksh, not csh!)  Learn how to use the shell!  IMHO, Integrated Development Environments are for pussies.

---

### Post by meson2439 on 2009-11-21
IDE is good because it handles indentations naturally and we need all the help we can writing the codes. Nevertheless, I'd prefer IDE with built-in terminal to compile my codes though. In another words, I treat my IDE as an extension of the text editor. Geany and emacs are good IDE on these terms. Never tried vim, but it might be just as good. Visual MS are the pinnacle of bad IDE's because it removes too many important stuff from your consciousness.

---

### Post by John Bean on 2009-11-21
> **A_Fiachra said:**
> In the *nix world, learn vi, emacs and the command line (bash, sh and ksh, not csh!)  Learn how to use the shell!  IMHO, Integrated Development Environments are for pussies.
Am I in a time warp? That sounded like my backward-looking section manager way back when crude IDEs were starting to pop up. It's sad to still hear the attitude persists today.

PS: using an IDE for code development has nothing whatsoever to do with whether or not you know how to use the shell. It's also a bit ironic that vi and emacs were equally scorned by the elite of an earlier era who shunned any kind of visual display in favour of a teletype - "real programmers use ed" ;-)

---

### Post by Tony Flury on 2009-11-21
Personally I find vi and emacs incredibly difficult to use effectively - due to the need to remember all of those keystrokes and modes etc.

For people with learning difficulties like me (and many millions of others who just want to get on with life and not remember 100s of keystrokes) modern editors with menus which use the mouse and window managers etc are simply far more effective.

---

### Post by dwhitney67 on 2009-11-21
> **Tony Flury said:**
> Personally I find vi and emacs incredibly difficult to use effectively - due to the need to remember all of those keystrokes and modes etc.

For people with learning difficulties like me (and many millions of others who just want to get on with life and not remember 100s of keystrokes) modern editors with menus which use the mouse and window managers etc are simply far more effective.

I agree... up until the point where "you find yourself up the creek and without a paddle".

An IDE, as great as they are conceived to be, are NOT available on every development system!  And don't expect them to be.  Of course, if you are just developing on your home system as a recreational programmer, then my argument does not weigh in too much.

I've had experiences in the past where Linux (that includes Ubuntu!), where the X11 has died, and all I have before me is the wonderful console.  How the #$%^* am I to edit a file with Eclipse... or CodeBlocks... or whatever?

Learn to use vi; this editor is available on every *nix system, from here to Timbuktu.

At work, I have at my fingertips a Mac, from which I use to connect to Redhat 5.4.  On occasion, I need to run over to the lab, which has legacy systems supporting Solaris 2.6 (yes... version 2.6!)

Does anyone think that an all-encompassing IDE will be available?  Nope... I have got to use vi. 

So, for recreational s/w developers... use what tickles your fancy; if you are serious about being adaptable to any *nix environment, and no matter how 'cruel' this may seem, learn vi or (sigh!) emacs.

Now it's time to go "fishing".
\rant

---

### Post by A_Fiachra on 2009-11-22
> **John Bean said:**
> Am I in a time warp? That sounded like my backward-looking section manager way back when crude IDEs were starting to pop up. It's sad to still hear the attitude persists today.

PS: using an IDE for code development has nothing whatsoever to do with whether or not you know how to use the shell. It's also a bit ironic that vi and emacs were equally scorned by the elite of an earlier era who shunned any kind of visual display in favour of a teletype - "real programmers use ed" ;-)

I don't let myself get too attached to any IDE because I am working in the real world.

Consider this scenario -- your boss tells you you can fire up several instances of some Linux variant on Amazon's EC2.

You get your ssh keys all lined up, you are on virgin virtual box with nothing installed, you have hitherto only used Eclipse. That's proper screwed.

Once, ed was the minimal standard.  Now, at least, vi comes with every *nix variant, sometimes emacs.  They have become the minimal standard.  That's the only thing I can trust.

With *nix, you are not in a time warp -- you have to be on the command line as you jump from box to box in most production environments, it's the de facto interface.  

Real programmers use the tool that will get the job done.  Everything else is for pussies and dilettantes.

---

### Post by John Bean on 2009-11-23
> With *nix, you are not in a time warp -- you have to be on the command line as you jump from box to box in most production environments, it's the de facto interface.Your argument doesn't withstand close scrutiny, especially since IDEs are by definition intended for development environments. I repeat: using an IDE from choice (or even any modern editor for that matter) has absosultely nothing to do with knowledge (or lack of) command line tools. I can use vi (or ed for that matter) *if I really must*, but it certainly wouldn't be my first choice of editor in a development environment. 

> Real programmers use the tool that will get the job done. Everything else is for pussies and dilettantes.No disagreement there, unless you are implying that "the tool" must be the one that you have defined rather than one that someone else prefers. The elitist jibe in the last sentence seems to be a recurring theme.

Real programmers do use the tool that will get the job done, but they also don't wear hair shirts and beat themselves up just to maintain their elitist reputation; instead they use the right tool to make the routine development tasks simpler and easier. And that may well be an IDE of some sort.

---

### Post by Arndt on 2009-11-23
> **John Bean said:**
> Your argument doesn't withstand close scrutiny, especially since IDEs are by definition intended for development environments. I repeat: using an IDE from choice (or even any modern editor for that matter) has absosultely nothing to do with knowledge (or lack of) command line tools. I can use vi (or ed for that matter) *if I really must*, but it certainly wouldn't be my first choice of editor in a development environment. 

No disagreement there, unless you are implying that "the tool" must be the one that you have defined rather than one that someone else prefers. The elitist jibe in the last sentence seems to be a recurring theme.

Real programmers do use the tool that will get the job done, but they also don't wear hair shirts and beat themselves up just to maintain their elitist reputation; instead they use the right tool to make the routine development tasks simpler and easier. And that may well be an IDE of some sort.

When an IDE user has a problem with building an executable and asks the forum, the solution usually comes from studying what the IDE really does, expressed in individual gcc commands (or g++ or whatever) or by doing similar commands and comparing the result with what the IDE does, in a shell. Thus someone who is (for the time being, by inexperience, or by circumstances) locked into an IDE needs to seek help from the elite who knows what the computer really does. Nothing strange with that - those who know help those who do no. What some people among the elite (not a word I usually use, actually) do is suggest that the IDE user doesn't really need to be locked in, but can learn the real stuff himself and so become a more versatile programmer. That in itself is not an elitist view.

Being independent of an IDE of course means having to know one independent editor well. The most used ones have been along a really long time, probably because they do their job well, and certainly not because they have a lot of financial backing. So, no time-warp.

If you start with one of those editors, you come to know it so well that all the modes and key combinations are never felt as a problem. If you feel forced to switch to it from something perceived to be simple, it's a different story - I didn't go the latter route.

---

### Post by A_Fiachra on 2009-11-23
> **John Bean said:**
> ..
No disagreement there, unless you are implying that "the tool" must be the one that you have defined rather than one that someone else prefers. The elitist jibe in the last sentence seems to be a recurring theme.

Real programmers do use the tool that will get the job done, but they also don't wear hair shirts and beat themselves up just to maintain their elitist reputation; instead they use the right tool to make the routine development tasks simpler and easier. And that may well be an IDE of some sort.

The tool is one that will work across machines, across *nix variants and is reliable and predictable.

As of yet, no IDE fits the bill.

The IDE is a "wish list" item from windoze, let's face it.  If you want to work in the widows world, work in the windows world.  This is Unix/Linux.  There are no such luxuries that one can depend on in any real world development environment.

---

### Post by John Bean on 2009-11-23
> **Arndt said:**
> What some people among the elite (not a word I usually use, actually) do is suggest that the IDE user doesn't really need to be locked in, but can learn the real stuff himself and so become a more versatile programmer. That in itself is not an elitist view.

I entirely agree to both points, that of course it makes sense to know the basics and that this advice is in no way elitist. But if that same advice is postfixed with adolescent jibes about those who choose to use other tools - for whatever reason - then it becomes elitist.

> If you feel forced to switch to it from something perceived to be simple, it's a different story - I didn't go the latter route.

There's no "force" involved, simply the ability to make a choice. Choice is good.

---

