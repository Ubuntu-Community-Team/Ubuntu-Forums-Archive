---
title: "installing xft"
date: 2020-03-08
forum: New to Ubuntu
---

### Post by stockfish10 on 2020-03-08
I am trying to work with the x11 font library xft. I have already ran
```
sudo apt install libxft-dev
```
Trying to compile a program that has
```

#include <X11/Xft/Xft.h>

```
, however, returns```

/usr/include/X11/Xft/Xft.h:39:10: fatal error: ft2build.h: No such file or directory
 #include <ft2build.h>


```
What other libs do I need to use Xft?

---

### Post by wildmanne39 on 2020-03-08
*Thread moved to **New to Ubuntu a more appropriate sub-forum**.*

---

### Post by norobro on 2020-03-08
Here's what I do when I encounter errors like this:

[LIST]
[*]go to this page: [https://packages.ubuntu.com/](https://packages.ubuntu.com/)
[*]under "search the contents of packages" enter "ft2build.h"
[*]click the radio button for "packages that contain files named like this"
[*]choose your distribution and architecture
[*]click search
[/LIST]
Unless you are running focal, you need to install libfreetype6-dev.

---

### Post by stockfish10 on 2020-03-08
> **norobro said:**
> Here's what I do when I encounter errors like this:

[LIST]
[*]go to this page: [https://packages.ubuntu.com/](https://packages.ubuntu.com/) 
[*]under "search the contents of packages" enter "ft2build.h" 
[*]click the radio button for "packages that contain files named like this" 
[*]choose your distribution and architecture 
[*]click search 
[/LIST]
Unless you are running focal, you need to install libfreetype6-dev.
libfreetype6-dev is alright up to date. The errors still persist though

---

### Post by Impavidus on 2020-03-09
ft2build.h isn't in the location where your compiler expects it. You have to add /usr/include/freetype2 to the directories where the compiler searches for header files. If using gcc, try the -I option```
-I /usr/include/freetype2
```

---

### Post by stockfish10 on 2020-03-11
I added the line. The error is now gone, but the compiler is still complaining about not finding the functions I am using,
```

undefined reference to `XftFontOpenName'
undefined reference to `XftColorAllocName'

```
etc, even though the man page specifically wrote having #include <X11/Xft/Xft.h> is enough

---

### Post by Impavidus on 2020-03-12
That's a linker error. The compiler found the headers, but the linker (the next stage of compilation) doesn't know to which library to link. It's fixed with the compiler option```
-l<somelib>
```I don't know which library you need for this, probably it's called xft, giving **-lxft**.

A trick to get these compiler and linker options is using pkg-config. It's a small tool that looks op information on various libraries and generates the appropriate compiler and linker options. For example:```
$ pkg-config --cflags freetype2
-I/usr/include/freetype2 -I/usr/include/libpng16
$ pkg-config --libs freetype2
-lfreetype
```I've no xft installed, so I can't check for you.

---

### Post by norobro on 2020-03-12
On my box:```
~$ lsb_release -r
Release:    19.04
~$ pkg-config --libs --cflags xft
-I/usr/include/uuid -I/usr/include/freetype2 -I/usr/include/libpng16 -lXft
```

---

### Post by Impavidus on 2020-03-12
So it's a capital X.

norobro, you're not the OP but I'll mention this anyway, you appear to be running 19.04. That reached end of life two months ago. I suggest you get 19.10 in whatever ways seems convenient to you.

---

### Post by norobro on 2020-03-12
[COLOR=#000000]@Impavidus - thanks for the heads up! I multi-boot and sometimes don't stay on top of updating all of the dists on my machine.[/COLOR]

---

