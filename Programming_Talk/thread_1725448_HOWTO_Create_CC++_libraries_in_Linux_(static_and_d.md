---
title: "HOWTO: Create C/C++ libraries in Linux (static and dynamic linking)"
date: 2011-04-09
forum: Programming Talk
---

### Post by MarkoCro on 2011-04-09
Hi people. I've wrote two howtos on my site about C/C++ library programming on Linux. I think this would be useful to many people because many people ask me about it.

Here are the links, hope you find it useful:

[C/C++ library programming on Linux &#8211; Part one: Static libraries]("http://www.techytalk.info/c-cplusplus-library-programming-on-linux-part-one-static-libraries/")

[C/C++ library programming on Linux &#8211; Part two: Dynamic libraries]("http://www.techytalk.info/c-cplusplus-library-programming-on-linux-part-two-dynamic-libraries/")

[C/C++ library programming on Linux &#8211; Part three: Dynamic libraries using POSIX API]("http://www.techytalk.info/c-cplusplus-library-programming-on-linux-part-three-dynamic-libraries-using-posix-api/")

Long live Ubuntu and Linux!

---

### Post by Jonas thomas on 2011-04-09
Thanks... poke around your side a bit... Clicked on a few links..;)  Nice site..  Need to get my c++ homework done at the moment.. But it's some topic of interest.

---

### Post by MarkoCro on 2011-04-09
> **Jonas thomas said:**
> Thanks... poke around your side a bit... Clicked on a few links..;)  Nice site..  Need to get my c++ homework done at the moment.. But it's some topic of interest.

Thanks Jonas especially for clicking on "the" links, i spend a lot of time writing articles about things other people helped me learn. Then I hope they will do the same for other people and our Linux will go forward. Feel like I need to give something back to the community. If I can help with the homework please let me know :)

---

### Post by jon zendatta on 2011-04-10
:ks

---

### Post by slavik on 2011-04-10
stickied.

Critique:
In the first part, you are defining function prototypes in the "user" code. I would suggest having a library header and loading that instead and having the protection defines in the library header.

---

### Post by MarkoCro on 2011-04-10
> **slavik said:**
> stickied.

Critique:
In the first part, you are defining function prototypes in the "user" code. I would suggest having a library header and loading that instead and having the protection defines in the library header.

Yes that would be better approach but I've tried to keep things simple and all in one place. I will add sentence or two about the right way of putting function prototypes in the header file. Thanks slavik.

---

### Post by jackzayum on 2011-05-06
Hey, thank you for this resources. They're very helpful.

---

### Post by nvteighen on 2011-06-25
I wanted to note that there's an alternative to setting LD_LIBRARY_PATH in order to make the linker aware of a library that's not installed in any of the default paths.

It goes like this, when you're about to link your program to your homebrew library, add the following flags (where DIRECTORY is the path to the library):

```

-Wl,-rpath,DIRECTORY

```

This will record the library's given path in the executable. The only issue with this is that if you relocate the library, the linker won't find it and you'll have to recompile the program. But it may be worth for people that are just learning about library development and don't want to be setting an environment variable everytime neither want to change .bashrc just for this.

Hope this helps.

(Source: [http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html](http://tldp.org/HOWTO/Program-Library-HOWTO/shared-libraries.html) and tested by myself :))

EDIT: Corrected code. $(DIRECTORY) was incorrect for obvious reasons...

---

### Post by JupiterV2 on 2011-06-25
I would also like to point out that libtool ([http://www.gnu.org/software/libtool/manual/libtool.html]("http://www.gnu.org/software/libtool/manual/libtool.html")) makes creating static and dynamic libraries exceedingly easy. Couple with an appropriate autotools project (autoconf, automake, etc.) and you really need do nothing more than write the library itself.

If trying to create portable (Linux <-> Windows) libraries, you'll need to look up a few tricks like the __declspec extension to properly export/import symbols for .dlls. You'll also need to look up dlltool unless using an autotools project w/ msys or cygwin, which will take care of that for you.

---

### Post by Tuvi on 2012-04-26
Thanks for the link...

great help...:p

---

