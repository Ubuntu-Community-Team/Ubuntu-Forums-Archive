---
title: "Fake windows.h in Linux for compiling windows applications to work on Linux?"
date: 2008-12-25
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-25
Maybe there could be a "fake" windows.h, which would have functions with exactly same names than original windows.h 
but the functions' content would be different, like instead of windows' window manager the functions would call X11/Gnome/KDE?

And a fake directX library, which could contain all DX functions but the functions would actually call openGL functions?

Maybe we could compile windows games to work under linux that way?

---

### Post by Tony Flury on 2008-12-25
There would be so much that one would need to replicate so as to make it so entirely impractical : for instance : 
Windows management
Memory
Registry
Networking
File and resource management
Graphics handling

they are they things i have used in windows - there will be plenty of others I am sure.

It is almost certainly easier to replicate/emulate in code/framework (for instance in WINE or use Virtual box), rather than try to build a fully functioning cross compiler linker.

The other way to do things is for all developers to use cross-platform frameworks in the first place - such as posix libraries, gtk or qt for windows management, Open GL for graphics etc.

---

### Post by WitchCraft on 2008-12-25
> **Tony Flury said:**
> 
The other way to do things is for all developers to use cross-platform frameworks in the first place - such as posix libraries, gtk or qt for windows management, Open GL for graphics etc.

Exactly, needn't to reinvent the wheel.

SDL for 3d
OpenAL for audio
Curl for networking
wxWidgets for GUI Interfaces
Boost for just about everything else.

If you use CodeBlocks, you don't even have to create a Makefile/SConscript for all platforms...

Wine / Crossover Office/Games for running windows applications on Linux without having to recompile them...

What more do you want ?
You just have to use these libraries in the first place, then you won't have many problems porting your application.

---

### Post by nvteighen on 2008-12-25
> **crazyfuturamanoob said:**
> Maybe there could be a "fake" windows.h, which would have functions with exactly same names than original windows.h 
but the functions' content would be different, like instead of windows' window manager the functions would call X11/Gnome/KDE?

And a fake directX library, which could contain all DX functions but the functions would actually call openGL functions?

Maybe we could compile windows games to work under linux that way?
Problem: In a header file there's no information on how a function is implemented... so, you can write your windows.h, but it will serve nothing if you don't have the libraries. And if you try to link the symbols declared at your windows.h against GNU/Linux libraries, you'll get lots of "unresolved symbol" errors. (Which will only be solved by using the libraries' symbols and therefore, by not complying to the Win32 API!).

---

### Post by crazyfuturamanoob on 2008-12-25
I'm not sure if you get what I mean with that fake windows.h.

It would look like this:
```

// windows library

#include <blahblahblah>
#include <...>

int create_window_for_windows( ... )
{
    create_x11_window_for_linux();
    ...
}

int directx_draw_stuff( abc123 )
{
   opengl_draw_stuff( :P );
   return something;
}

void mess_with_windows_registry()
{
    mess_with_linux_registry();
}

```
And so on. Like replacing function contents with Linux equivalents.

This how we could compile a windows application under Linux for better performance & functioning.

No need to rewrite everything. Of course, same thing for every windows library.

---

### Post by albinootje on 2008-12-25
> **crazyfuturamanoob said:**
> 
This how we could compile a windows application under Linux for better performance & functioning.

No need to rewrite everything. Of course, same thing for every windows library.

Your posting reminds me a little bit of this rather new project :
[http://freshmeat.net/projects/ring3k/](http://freshmeat.net/projects/ring3k/)

---

### Post by Npl on 2008-12-25
[Winelib]("http://www.winehq.org/winelib") is what you are seeking. Im not sure if you can port Apps with just using header, might need to install a few runtime-libraries as well, but its a good start.

---

### Post by ankursethi on 2008-12-25
What the OP is asking is exactly what the WINE project is trying to do. When you run a Windows executable in WINE, it translates Windows API calls to their equivalent calls under UNIX. If you have Windows specific source code, then you use winelib to compile it, as Npl said.

The WINE guys have been at it for over 10 years now, and we *still* don't have Windows compatibility. IMHO, it'll be better if teach people how to write code for UNIX systems rather than pushing for compatibility layers that barely work.

---

### Post by Npl on 2008-12-25
> **ankursethi said:**
> The WINE guys have been at it for over 10 years now, and we *still* don't have Windows compatibility. IMHO, it'll be better if teach people how to write code for UNIX systems rather than pushing for compatibility layers that barely work.I dont see why Unix would be an improvement, or the POSIX-"Standard" which is basically Unix APIs. I`d rather teach people to use crossplattform libraries like GTK+, Qt and SDL and keep everything thats using native calls behind such libraries or abstractions.

---

