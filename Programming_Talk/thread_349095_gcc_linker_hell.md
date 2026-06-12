---
title: "gcc linker hell"
date: 2007-01-29
forum: Programming Talk
---

### Post by amiga_os on 2007-01-29
Am I the only person to find gcc really irritatingly pedantic about linker flags?  When I include standard libraries such as <fstream> I seem to get a string of indecipherable errors during linking (indecipherable because they all string from bizarrely named .o files).

I'm having an issue with a current project, because I don't know what -l flag to use for any given header file... is there a list of linker flags somewhere that anybody can point me to?  Is there some kind of environment variable I can enable to make gcc a little more forgiving?

---

### Post by Wybiral on 2007-01-29
I don't generally get weird errors like that unless something is wrong (usually during compiling)

Could you post some of the errors and maybe a snippet of code?

Also, if you are using "<fstream>" then I assume you're using C++, while "gcc" should detect that it's a C++ program by the ".cpp" file extensions, have you tried "g++" instead?

---

### Post by amiga_os on 2007-01-29
Oh... I feel like an idiot, that's a mistake I've made before!  Using g++ solves all my errors.  Thanks for that!

However, if someone did happen to know of a list of useful linker flags somewhere that would be very helpful.

---

### Post by Wybiral on 2007-01-29
You mean for libraries?
Check this out, go to "/usr/lib"
See all of those files that say "lib*.a"
Where "*" is the library name...
That's it. Those are your libraries.
However, instead of using "-llib*.a" you just use "-l*"
So if you have the library "libSDL.a" then you would use the command "-lSDL"
Instead of "libglut.a" you use "-lglut"
So, when I compile a program that uses SDL, GLU, and GL, I use the command...
"g++ myProgram.cpp -lSDL -lGLU -lGL"

You do mean libraries, right?

---

### Post by phossal on 2007-01-29
Wyb,

Do you remember when I had a similar question regarding gcc? I wanted to see what gcc was linking to, because it *does* link in libraries even when you haven't listed any include statements in your program. I think I used the -v argument to gcc to run it "verbose". That way I could see what it was doing. I can't remember who showed me that, now.

[Ed.] To be more specific, I was curious to know what was going on with the assembler.

---

### Post by po0f on 2007-01-29
phossal,

If you want to find out what libraries are linked in to your binary, you could use `ldd`.  It will only tell you after the fact though, not while it's linking.

---

### Post by phossal on 2007-01-29
> **po0f said:**
> phossal,

If you want to find out what libraries are linked in to your binary, you could use `ldd`.  It will only tell you after the fact though, not while it's linking.

lol. Thanks, poOf. Here is the thread where I asked the question. In fact, my problem wasn't quite like the OP's. [GAS - Running the Assembler]("http://ubuntuforums.org/showthread.php?t=330563")

---

