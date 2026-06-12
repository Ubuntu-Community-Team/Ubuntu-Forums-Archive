---
title: "should we make our own libraries????"
date: 2008-12-09
forum: Programming Talk
---

### Post by abhilashm86 on 2008-12-09
when i do c++ object programming programs,i am not able to go as smooth as i did in windows,there are no much library functions,how to go about it?
in linux i am not able to use getch(),initgrapgh() and other functions in my programs,cannot do backtrack tracing,so should we build our own library for these functions????
are there any other options,please help..........
:p

---

### Post by lert on 2008-12-09
So you need to install libs which provide the functions you want. For example, if you want to use zlib, then install zliblg-dev. Include <zlib.h> in your c++ files, and compile and link it against libz.a with a flag -lz....

---

### Post by Zugzwang on 2008-12-09
@OP: The functions you are referring to are actually plain old *DOS* functions, there are no replacements since there's no need to have them in a modern operating system (the initgrapgh function even refers to specific drivers for DOS). Writing a replacement library is almost futile as almost nobody will actually use it. If you want to stick with those functions, then simply use the compiler, linker & programs in dosbox. This is often done for legacy programs.

However, there are projects to re-implement some of the old DOS functions, like the libconio project. But at least "libconio" is far away from being mature.

---

### Post by abhilashm86 on 2008-12-09
> **Zugzwang said:**
> @OP: The functions you are referring to are actually plain old *DOS* functions, there are no replacements since there's no need to have them in a modern operating system (the initgrapgh function even refers to specific drivers for DOS). Writing a replacement library is almost futile as almost nobody will actually use it. If you want to stick with those functions, then simply use the compiler, linker & programs in dosbox. This is often done for legacy programs.

However, there are projects to re-implement some of the old DOS functions, like the libconio project. But at least "libconio" is far away from being mature.

yes i did downloaded dosbox 3 days back,but it din't mount c drive properly,maybe it was a windows dosbox supported,can u give me a link to download proper linux dosbox and maybe mounting and other stuff should work right?

---

### Post by meson2439 on 2008-12-09
> **abhilashm86 said:**
> yes i did downloaded dosbox 3 days back,but it din't mount c drive properly,maybe it was a windows dosbox supported,can u give me a link to download proper linux dosbox and maybe mounting and other stuff should work right?
To mount C: in DosBox type (in DOsBox console)
```
mount C: /FolderWithDosApps
```

You can replace the folder name with /home if lazy and navigate from there. FYI your c++ files can still function even without those function and their libraries. So remove it. getch() and conio is dispensible.

---

### Post by ankursethi on 2008-12-09
I know where the OP is coming from. In India, most schools and colleges (including mine) are *still* using Turbo C++ v3.0 from 1992 to teach C and C++. It's a shame, really.

@OP
If you want to create commandline interfaces with buttons, windows, sliders etc. then ncurses is what you're looking for. Just Google it. If you're trying to build games, then I'm afraid you'll have to learn something more advanced like SDL or Allegro (again, Google).

Also, I hope you used apt or Synaptic to install DOSBox, did you not? If yes, then look up the documentation using the 'man dosbox' command.

---

### Post by abhilashm86 on 2008-12-09
> **ankursethi said:**
> I know where the OP is coming from. In India, most schools and colleges (including mine) are *still* using Turbo C++ v3.0 from 1992 to teach C and C++. It's a shame, really.

@OP
If you want to create commandline interfaces with buttons, windows, sliders etc. then ncurses is what you're looking for. Just Google it. If you're trying to build games, then I'm afraid you'll have to learn something more advanced like SDL or Allegro (again, Google).

Also, I hope you used apt or Synaptic to install DOSBox, did you not? If yes, then look up the documentation using the 'man dosbox' command.

ya ankur u r right,we are not at all forward in technical aspects in colleges,i am doing computers in engineering,but no linux stuff,no modern programing,i adjusted c programing in linux quiet a bit,but when it comes to other c++ and functions,a lot of linking and functions not available freind,so what r u doing ankur?

---

### Post by nvteighen on 2008-12-09
Just a note: you can a getch() function from ncurses... install libncurses5-dev and look at the documentation (FYI, ncurses is written in C and it's a terminal-manipulation library).

---

### Post by ankursethi on 2008-12-13
> **abhilashm86 said:**
> ya ankur u r right,we are not at all forward in technical aspects in colleges,i am doing computers in engineering,but no linux stuff,no modern programing,i adjusted c programing in linux quiet a bit,but when it comes to other c++ and functions,a lot of linking and functions not available freind,so what r u doing ankur?

B.Tech in Information Technology from Indraprastha University, New Delhi. I'm only doing it for the degree, though.

PM me if you want to talk. Chatting about stuff on a public forum == bad.

---

