---
title: "C open source"
date: 2010-06-13
forum: Programming Talk
---

### Post by cap10Ibraim on 2010-06-13
Do you know any open source program in C ? 
How to get the source code ?
I just want any C program to study more codes this summer

---

### Post by WitchCraft on 2010-06-13
apt-get source openarena, apt-get build-dep openarena

---

### Post by wmcbrine on 2010-06-13
A very large share of *all* open source software is written in C; in fact, it has the largest share of any language, AFAIK. (One study last year said 40% of open source software was written in C.) You shouldn't have any trouble finding it.

---

### Post by rye_ on 2010-06-13
Have a look at sourceforge.net

---

### Post by Simian Man on 2010-06-13
Reading source code is not a good way to learn a language.  The good majority of code in the wild is poorly written, either out of practical concerns or a lack of time.  More importantly reading code does not give you any indication of why the programmer chose to do things in the way that they did.

I'd really recommend a good book on C if you want to learn it rather than just reading straight code.

---

### Post by cap10Ibraim on 2010-06-13
> **Simian Man said:**
> Reading source code is not a good way to learn a language.  The good majority of code in the wild is poorly written, either out of practical concerns or a lack of time.  More importantly reading code does not give you any indication of why the programmer chose to do things in the way that they did.

I'd really recommend a good book on C if you want to learn it rather than just reading straight code.
I finished  two C courses basic and other one about memory allocations lists structures file operations ......
but I want more , like real applications and implementations

---

### Post by Simian Man on 2010-06-13
> **cap10Ibraim said:**
> I finished  two C courses basic and other one about memory allocations lists structures file operations ......
but I want more , like real applications and implementations

Sorry I assumed you were just beginning.  I see a lot of beginners who download 100K line of code programs and try to make sense of it :).  If you want to read code, it would be best to choose something you're interested in.  What kind of applications do you like?

That said, I do feel writing code will teach you a lot more about real applications and implementations than reading it.

---

### Post by cap10Ibraim on 2010-06-13
> **Simian Man said:**
>   What kind of applications do you like?

That said, I do feel writing code will teach you a lot more about real applications and implementations than reading it.
networking applications depend on the OS right ?

---

### Post by StephenF on 2010-06-13
> **cap10Ibraim said:**
> networking applications depend on the OS right ?
They are generally built on the sockets API which was originally part of an early version of BSD and has since become standard in Linux and Windows XP, so while built into the OS the implementation is pretty standard. Of course there are specialised layers that run on top like D-Bus for example or the network interfaces of databases.

What doesn't depend on the OS in any way shape or form anyway? Memtest86 is a stark example. Perhaps you could clarify that point?

---

### Post by Simian Man on 2010-06-13
> **cap10Ibraim said:**
> networking applications depend on the OS right ?

Pretty much yes.  The standard way to do network programming in C on Unix is to use the Berkley sockets API.  Almost all other low-level networking APIs are based on this, but are not exactly the same.  For example Winsock on Windows or the Java or .NET socket API.  There are also cross-platform socket APIs that wrap up the specific functions in an independent way such as SDL_Net or the socket APIs in QT or wxWidgets.

Learning any one of these ways of doing network programming will enable you to pick up another very easily because they all use the same concepts.  The best resource for learning sockets is definitely [Beej's Guide to Network Programming ]("http://beej.us/guide/bgnet/output/html/multipage/index.html").  An essential read for any C/Unix programmer!

---

### Post by LoloftheRings on 2010-06-13
Try applications you use every day, like pidgin. Pidgin is still a very complex and large program, and not really well commented (I've edited serveral parts of pidgin to meet my own taste), but if you use it every day, it's far more interesting.

Hmm I just checked out the source code of empathy, and that one might be better to learn, well commented, which is really important if you want to understand the code.

A lot of open source software is C, like the linux kernel itself. You shouldn't have much trouble finding a good application.

Downloading source code isn't too hard, you just go to the project's hompage (often sourceforge) and press the download button.

---

