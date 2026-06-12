---
title: "Gtkmm and compiling problems"
date: 2006-11-12
forum: Programming Talk
---

### Post by Sonobana on 2006-11-12
Hello!

I have been learning writing c++, and now i want to learn make GUIs with gtkmm. First thing i realized was that compiling these programs is not so easy as i thinked. I also want learn make things 'right' so i think its better to ask.

so i use scons to compile my program.
heres simple example file that i found from gtkmm's tutorial:
```

#include <gtkmm.h>

int main(int argc, char *argv[])
{
    Gtk::Main kit(argc, argv);

    Gtk::Window window;

    Gtk::Main::run(window);
    
    return 0;
}

```
and my Sconstruct -file:
```

Program('main.cc')

```
and when i try to run scons this is the error:
```

~/Projects/scons-koe
23:11:50 <samuli@samuli-desktop> scons
scons: Reading SConscript files ...
scons: done reading SConscript files.
scons: Building targets ...
g++ -o main.o -c main.cc
main.cc:1:19: error: gtkmm.h: No such file or directory
main.cc: In function 'int main(int, char**)':
main.cc:5: error: 'Gtk' has not been declared
main.cc:5: error: expected `;' before 'kit'
main.cc:7: error: 'Gtk' has not been declared
main.cc:7: error: expected `;' before 'window'
main.cc:9: error: 'Gtk' has not been declared
main.cc:9: error: 'window' was not declared in this scope
scons: *** [main.o] Error 1
scons: building terminated because of errors.

```

How i get my programs done?

---

### Post by ansi on 2006-11-12
Install "libgtkmm-dev" package.

---

### Post by Sonobana on 2006-11-12
> **ansi said:**
> Install "libgtkmm-dev" package.
I have installed it already.

---

### Post by llonesmiz on 2006-11-12
To compile that program you could just use:

g++ -o test main.cc `pkg-config --cflags --libs gtkmm-2.4`

I don't know anything about scons but in their FAQ they mention:

> **4.4. I'm alreadying using ldconfig, pkg-config, gtk-config, etc.  Do I have to rewrite their logic to use SCons?**

  A:        SCons provides explicit support for getting information from programs like ldconfig and pkg-config. The relevant method is ParseConfig(), which executes a *-config command, parses the returned flags, and puts them in the environment through which the ParseConfig() method is called: 
         env.ParseConfig('pkg-config --cflags --libs libxml')
        If you need to provide some special-purpose processing, you can supply a function to process the flags and apply them to the environment in any way you want. 
so you'll probably will have to add that to your file.

PS: after reading a little more I found that putting this in a file named SConstruct works fine:

```

env=Environment()
env.ParseConfig('pkg-config --cflags --libs gtkmm-2.4')
env.Program('main.cc')

```

---

### Post by Sonobana on 2006-11-13
> **llonesmiz said:**
> To compile that program you could just use:

g++ -o test main.cc `pkg-config --cflags --libs gtkmm-2.4`

I don't know anything about scons but in their FAQ they mention:

so you'll probably will have to add that to your file.

PS: after reading a little more I found that putting this in a file named SConstruct works fine:

```

env=Environment()
env.ParseConfig('pkg-config --cflags --libs gtkmm-2.4')
env.Program('main.cc')

```
Thank you about help. That did the trick, but I still can't understand what i did :confused:

---

### Post by llonesmiz on 2006-11-13
In order to compile a program you usually just need to do:

g++ -o program_name source_name.cc

That works because any include file you need (and every library) is in the same directory as your source code. If you needed to use an include file in another directory, let's say in "include/myincludes/" you would need to use the -I (capital i) option in g++ that allows you to specify what directory your files are in. So in the above example you would do:

g++ -Iinclude/myincludes/ -o program_name source_name.cc

You need to do something similar with the libraries (just see man g++ or g++ -help).

Any program that uses gtkmm needs to add a lot of include directories and a lot of libraries, so using -I isn't very practical. This is the reason why pkg-config exists. It returns the options needed for g++(or gcc) for includes (using --cflags) and libraries (using --libs) for gtkmm amongst other frameworks. If you write in the terminal:

pkg-config --cflags --libs gtkmm-2.4

you will see everything that is necessary (and that is a lot).

In:
g++ -o test main.cc `pkg-config --cflags --libs gtkmm-2.4`

the backticks (`) mean "evaluate what is inside", so it puts what you saw previously  after "main.cc".

To let scons know what includes and libraries the program needs you need to create an environment and use the ParseConfig (amongst other methods, this just seems the most convenient in this situation). Then you say that your program is inside that environment, meaning, it needs those options to compile.

Good luck.

---

### Post by Sonobana on 2006-11-13
Ok now i undestrand. Thanks a lot! I really love ubuntu community. You guys are always helping find the road.

---

