---
title: "mingw, wine and freeglut"
date: 2006-06-17
forum: Programming Talk
---

### Post by Scratty on 2006-06-17
Hi!
I updated my system to dapper the other day. Anywayz, In breezy, I had succeded to setup mingw so that I could cross-compile using glut, and that worked like a charm... until I upgraded to Dapper.

The first problem that showed up in Dapper was that I couldn't even compile glut programs for linux with the ordinary gcc/g++. Which eventually appeared to be solved pretty easily by just reinstalling freeglut (weird huh?).

Then I tried to compile using i586-mingw32msvc-g++ (and gcc respectively) and  it appeared that the glut in mingw had been broken somehow. I dug into the lib and include dirs to find out what was wrong, and I found that the **glut.h** didn't match the new freeglut version of **libglut32.a** and **libglut.a**. So I removed[ the **glut.h** from Nate Robbins and downloaded the source from freeglut.sourceforge.net and copied the **glu.h** into **/usr/i586-mingw32msvc/include/**.

Now my C/C++ (glut) programs would compile without getting linking errors. (However, my C++ based space game still got warnings regarding the hashmap STL extension, which I never got before Dapper).

So now my programs would work fine in wine, or so I thought.
However, wine reported that the glut fonts were missing:
```

...
freeglut (texttest): font 0x00000004 not found

```
etc.

It seems that only the fonts are missing and everything else in glut works between mingw and wine. Could it be that wine still uses glut and not freeglut (which dapper now seems to prefer) and that there is some inconsistency between **/usr/lib/wine/glut32.dll.so** and [B]/usr/i586-mingw32msvc/lib/libglut32.a
[/B] ??

Oh, and one more thing... since Windows doesn't have glut installed by default, I need to include Nate Robbins' **glut32.dll** in the program distribution. I haven't tested my game on a windows machine yet, but I suspect I need another glut32.dll that is compiled for freeglut. How do I manage that?

I'm very confused.

Thanks in advance.

---

### Post by Scratty on 2006-06-18
...or should I move towards some other windowing toolkit, like GTK or SDL? Something that at least have proper support (is glut too old fashioned?). Suggestions?...

---

### Post by toojays on 2006-06-19
If you move to another toolkit, you will likely run into these kinds of cross-compiling issues again down the track. Since cross-compiling is kind of core to what you are doing, you're better off spending more time figuring out a way you can make that work for you.

Now I've never dealt with freeglut, so you may have to adapt my suggestion somewhat, but: I suggest you download freeglut and "./configure; make; make install" it, but when you configure it, make sure you 1) set it up to build for Windows, and 2) make sure you install it nowhere near your Ubuntu system files (e.g. --prefix=/home/scratty/windows-stuff/install-tree). [Hint: if you have to use "sudo", you're probably doing something dubious.]

Then, when you build your app, point -L and -I flags of gcc to /home/scratty/windows-stuff/install-tree/{lib,include} as appropriate. When you want to run your app under Wine, make sure the directory with the .exe file in it also has the appropriate DLLs (and also maybe those missing fonts, but you'll need to consult the freeglut docs for that). If you have glut.dll in the same directory as the your program, you shouldn't need to worry about what glut library Wine itself uses.

Hope this helps.

---

### Post by Scratty on 2006-06-21
Aha, I C. Hmm.. I just recently got my hands over a PC with windows in it and tried my game (and font testing program) there and with positive results. I suspect the problem lies with Wine rather than MinGW (even though the STL-warnings are rather suspicous). Perhaps I should just assume that the windows-exe is fine when its linux executable is working fine.

Funny that you mentioned the dll. I do have glut32.dll in the same directory as the exe, and that's what's making it work under Windows, but why Wine decides to overlook this library-file is a mystery for me. Perhaps it is possible to give Wine a flag to override Wine's own glut-library file and use the one in the development directory (which contains the glut32.dll) instead?

Thanks for the input toojays! I guess I have to wait for the wine developers to fix this inconsistency in a later version.

---

### Post by toojays on 2006-06-22
Yes, you can tell Wine to override DLLs. You can do it globally in the winecfg program, or per-instance by setting the WINEDEBUG variable (or maybe it's called WINEDLLOVERRIDES?). See the Wine man page or google "wine dll overrides" for more info.

Another option you may have is to statically link your application.

---

### Post by Scratty on 2006-06-22
Whoa!! It was as simple as that!
From **winecfg** I selected the **Libraries** tab, selected **glut32** from the "New override for library", then "Add"-button, then "Edit" and select "Native then builtin".
(writing this algorithm in case other people encounter this problem).

Thank you toojays!

P.S. If I now use my Text-class to render both prerasterized fonts and textured fonts with the same text simultaneously the two texts appear slightly offseted from each other, which wasn't the case prior to my Dapper upgrade. After a closer look, it appears that it in fact is the textured version that is rendered differently, which is quite weird, since that would mean that glTexCoord2f has been altered (the textured counterparts of glut's fonts have been manually generated and tweaked) which is a preposterous claim. Very odd indeed! D.S.

---

