---
title: "Make .exe file in ubuntu"
date: 2007-01-31
forum: Programming Talk
---

### Post by yolloms on 2007-01-31
iv just written a simple snake game in c for my final year project.
is there a way i can make it an executable file so i can upload it and give it to friends to have a look and play with

---

### Post by mcglnx on 2007-01-31
It's better to provide him with the source code an a Makefile.
Or even better using automake + autoconf (See [http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aofficial&hs=e0f&q=autoconf+automake++&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aofficial&hs=e0f&q=autoconf+automake++&btnG=Search))

Now if he cannot compile on his machine, you'll have to provide him with an binary compatible with his OS.

An other way (may be involving too much work) is to use a Virtual Machine based language (Java, Python,...)

HTH,
M

---

### Post by Wybiral on 2007-01-31
It's called cross compiling... Yes, there are free cross compilers for linux that compile to windows exe's. I believe you can find one in synaptic.

---

### Post by ansi on 2007-01-31
> **Wybiral said:**
> It's called cross compiling...
True :). The package is named *mingw32*.

---

### Post by lnostdal on 2007-01-31
well, just note that it already is an executable file - but in a format that isn't executable on Windows, which i assume is what you're after here

one option is to install vmware-player (it's in the ubuntu repos), then installing winxp inside that, then installing mingw and compiling your game using that setup

another option might be to cross-compile:
```

sudo aptitude install mingw32
lars@ibmr52:~/programming/c$ cat hello.c 
#include <stdio.h>

int main()
{
  printf("Hello Windows World!\n");
  return 0;
}
lars@ibmr52:~/programming/c$ i586-mingw32msvc-gcc -g -Wall hello.c -o hello.exe
lars@ibmr52:~/programming/c$ wine hello
Hello Windows World!

```

..magic? :)  ..now this might not be as easy at it seems; you might need some libraries etc.

---

### Post by mcglnx on 2007-01-31
I did not know this one. Does it also provide GUI support (GTK, KDE)?

---

### Post by Wybiral on 2007-01-31
> **mcglnx said:**
> I did not know this one. Does it also provide GUI support (GTK, KDE)?

If you have the windows libraries for it.

---

### Post by lnostdal on 2007-01-31
> **mcglnx said:**
> I did not know this one. Does it also provide GUI support (GTK, KDE)?

i have never tried .. but i suppose it does (edit: work) if you supply it with mingw-compiled gtk+-libraries ..

this might mean that you'll have to download and compile the source for things like glib, pango and finally gtk+ yourself as i doubt you'll find mingw-compiled binaries for these libraries in the ubuntu-repos :)   edit: but you'll find developer-libraries elsewhere: [http://gladewin32.sourceforge.net/modules/news/](http://gladewin32.sourceforge.net/modules/news/)

edit:
just give the poor Windows-sobs an account on your ubuntu server and setup freenx and they'll be having your "Web3.0 Real GUI(tm)" application up in no time :}

---

### Post by sailingboarder on 2007-01-31
yolloms,
every one assumes that by executable you mean on windows
.exe files that run on windows will not run on a linux system
if you want a windows executable, follow what has been said already
if you are looking for a linux file, look into make files, or even packaging, if your adventurous

---

### Post by yolloms on 2007-02-01
Thanks guys.

i'll give it a go.
none of my mates have linux, i have it on my laptop
thanks again

---

