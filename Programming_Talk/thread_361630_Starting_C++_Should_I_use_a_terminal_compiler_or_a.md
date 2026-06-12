---
title: "Starting C++ Should I use a terminal compiler or an IDE?"
date: 2007-02-14
forum: Programming Talk
---

### Post by billdotson on 2007-02-14
I am starting to learn C++ (I have no prior knowledge to programming other than just knowing what it is and while shell isn't programming I heard it helps a bit so in saying that I have simple proficiency with BASH and DOS shells where I can create directories, move around, copy files , etc.)

I have Anjuta installed but it is the most annoying program I have ever used.  I created a simple source code so that Hello World! would show up in the terminal and when I open it with Anjuta there is no build menu where I can compile, link, etc. 

Yesterday for some reason the build menu was there and I compiled it but then the only output from Anjuta was a .o file on the Desktop.  There was no other output and Anjuta wouldn't open the .o file.

I went into the terminal and cd'ed into Desktop and and then did g++ Hello.cpp
The output of that command was a.out and if I do ./a.out in the terminal it works.  So it seems that g++ compiles and links it.

I don't know anything about programming but as I understand it all I need to program is a text-editor like gedit, a program to compile the source code, an interpreter, a linker, and the development libraries (I think)

I hear that C++ is mostly cross-platform and I want to be able to make any type of program with it (desktop app/applet, GUI programs, terminal programs) so I won't end up trying to compile source code later and get an error.  Is all I need to ensure that I can do whatever I need to is to have all the C++ libraries installed?

Should I just use the g++ or should I get a IDE (will an IDE have more options and help?)?   Please help, I don't know anything about what I need in terms on libraries and other programming stuff.

---

### Post by Wybiral on 2007-02-14
Well, you'll get different responses here... It just depends on what it more comfortable.

For me Gedit+command line works great... That's all I need for about 99.9% of my projects. Gedit offers syntax highlighting, tabs, and bracket highlighting. Plus you can get plugins for it to make it better (like the embedded terminal, the auto-comment/uncomment and auto-tab/untab).

But, some people will call it downright blasphemy to not use an IDE... It's just a preference issue.

As far as the libraries go... It doesn't matter if you use an IDE or the command line to compile, you're still using GCC. Libraries will be libraries either way... You can link exactly the same with both.

---

### Post by lnostdal on 2007-02-14
i do not understand how one can exclude the other .. you need to know both how to use the compiler/linker "directly" (from the terminal) .. _and_ find an environment (ide/editor - or whatever really) that let's you work efficiently 

i prefer splitting things up so i have the compiler/linker at the "bottom" .. build-tool in the "middle" .. and ide/editor at "the top" .. here's a link with writings that will get you started with an environment that doesn't "hide" anything from you like many other ides might seem or try to do: [http://nostdal.org/~lars/writings/](http://nostdal.org/~lars/writings/)

edit:
just to be safe you're not misunderstanding something here .. every editor/ide calls or uses gcc/g++ in the "background" .. anjuta also

---

### Post by maxamillion on 2007-02-14
Terminal .... clicking buttons in an IDE won't teach you much.

---

### Post by Engnome on 2007-02-14
gEdit + terminal is what I used, good to get a feeling of the basic tools.

But I switched to geany, it somewhere between a text editor and an IDE. It's like an IDE without all the "project files and stuff management" or a text editor with many IDE features. It's really great. You can either use the built in compile/run buttons (which are very easy to configure) or the built in terminal. 
(which didn't work properly for me at first, but there's an easy fix for that, can't remembar what though...)

Good luck!

---

### Post by Wybiral on 2007-02-14
> **maxamillion said:**
> Terminal .... clicking buttons in an IDE won't teach you much.

That's my feelings exactly.

Plus... It might take an extra couple of seconds, but you can write a makefile or even a compile script (since you've done some bash scripting) for your large projects (so you don't have to type out all of the object file compiles).

I really don't see why anyone needs much more than that. Also, using a makefile/compile script ensures that others will be able to effortlessly compile it without having to have the correct IDE to go with your project file.

As an added note... This is strictly opinion, but I think it's easier to learn a language by having to actually memorize things... Relying on an IDE for autocomplete will make it much less comfortable if you're ever in a situation where you can't use autocomplete and it will make you have to actually remember and understand the language.

---

### Post by theDentist on 2007-02-14
The first thing to learn is the C++ language. forget about complicated IDEs that are geared for GUI apps.  In Linux, gedit with the g++ command line compiling is the simplest way to learn the language, I've never found anjuta works very well for C++, it is best used with C only, (well for me anyway others probably have managed it ). Stay in the terminal (Or console in Windows) until you have a reasonable grasp of the language.  Then move on to GUI programming where IDEs really help.  If you do use Windows as well, I found the best way is using the console option in a good IDE program like Bloodshed's Dev-C++ open source IDE.
By the way, nothing like a few good books, and forums when your stuck, to learn the language.    :)   Enjoy!

---

### Post by Mirrorball on 2007-02-14
Maybe you should forget about IDEs for a while, because Anjuta is great, you just have to learn how to use it.

---

### Post by billdotson on 2007-02-14
the thing with Anjuta is that there isn't even a drop-down menu for build.  Sometimes there is sometimes there isn't.  Now there is not.  

So I should use the command line and g++ to compile and link and do all of that.  

How do the libraries work and how do I know which ones I need?  

Is there a DOS compiler for Windows?

So I guess I am going to learn basic C++ to learn how to program applications that run in the terminal and then when I feel comfortable enough with that I will start trying to do GUI apps like desktop apps (like gdesklets or widgets) or other GUI programs.

When I do start GUI what free (legal), mostly simple (as in easy enough to use so that I don't spend half my time trying to learn it instead of programming), very capable (as capable as I am gonig to get for free) IDE would you recommend for Windows XP Pro and Ubuntu 6.10?

If anyone has any good web links to free (legal) starting C++ guides or books (not walls of text, interactive like they give you sample programs to do and such) that I can use to start off?  I don't have a bunch of money to go spending on manuals and such.

Thanks alot, I am really excited about learning more technical things about computers.

---

### Post by Wybiral on 2007-02-14
> **billdotson said:**
> ... How do the libraries work and how do I know which ones I need? ...

That depends which libraries you use... Libraries are just external chunks of code that you can link into your program to use it's functionality. For instance, if you want to write a multithreaded app, you'll probably need to link to the pthread library.

For a 3d app, you will probably want to use opengl... And you may need to use GLUT or SDL as well.

Linking to a library during command line compiling is easy...

First, check out the libraries that you have... Go to the folder "/usr/lib"... Every file that starts with "lib" and ends with ".a" is a library. To link to one of them, you will use the compile flag "-l"

For instance, if I want to link to "pthread" for my multithreaded app... I notice that the file "libpthread.a"

So, when I compile, I use... "g++ myProgram.cpp -lpthread"

Say I want to use pthread, SDL, and OpenGL (which is comprised of GL and GLU) I would compile with... "g++ -lpthread -lSDL -lGL -lGLU"

It's pretty simple.

Also, when you use a library, you often have to use the appropriate header file in your source code. So, browse on over to the "/usr/include" folder... There are your headers!

Do you see that "pthread.h"? You have to include that into your source code to use the "pthread" library... The just remember to link it in when you compile. It's very simple.

---

### Post by rekahsoft on 2007-02-14
IDE's are meant to make an experianced developer more productive. When you are just learning it is best to use a terminal and editor :D <--my two cents

---

### Post by theDentist on 2007-02-15
I'm not sure why you have a problem in Anjuta regarding compiling.  Select the' Build' menu in the toolbar and the dropdown menu is full of options, it is not necessary to go near a command line.  If you select 'Gnome 2' project in the new project wizard then both C++ and C for the language, you will be presented with a template of a teminal (or console) 'Hello World' program, you can use this project type for all your learning.  Have you got Anjuta installed correctly? As regards books, I learn't using several, one by O'Reilly, and another by Horton, if you look up amazon there are loads!  Get one that gives you exercises to do, and do them, there is nothing like programming to learn programming, just reading is not enough.  As for free IDE's I agree with former posts of this thread, Anjuta is GREAT! and FREE.For windows, Get the Free (yes you can download it free from MS website) MS Visual C++ Express 2005 if you want .NET but I wouldn't touch it yet, learn the language first as the .NET Framework is yet another load of Classes to learn. Start simple first and never give!       :)

---

### Post by theDentist on 2007-02-15
I mean't never give up! (typo error)    :(

---

### Post by theDentist on 2007-02-15
By the way another free IDE for Both Linux and Windows is Code::Blocks

---

### Post by Lux Perpetua on 2007-02-15
My two cents: start out on the command line. Start from the bottom. You can always pick up an IDE later.

---

### Post by big_gie on 2007-02-17
As many have stated, you are best with command line + good editor. Some have suggested gedit. I don't like it, I prefer Kate (KDE), but this is a personnal choice.

Good simple editors :
Kate
Gedit
Advanced good editors :
Emacs
vim/gvim/cream
Scite

IDE are to much complicated. You get really lost when all you want to do is a simple "hello world". All you need is a  editor with syntax highlighting.

Thats it :)

---

### Post by Vorian on 2007-02-17
Everyone needs to cool it.  This thread will be closed for 24 hours to allow everyone to cool off a bit.

---

### Post by Vorian on 2007-02-18
Time up - Play nice

---

