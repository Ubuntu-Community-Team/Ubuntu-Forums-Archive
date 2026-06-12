---
title: "C++ Crossplatform?"
date: 2006-12-12
forum: Programming Talk
---

### Post by Lycaon on 2006-12-12
Here's another question, how about c++ and crossplatform compilation?
I talked with LiraNuna on irc, and he showed me that he was able to  program cross platform. But he uses c++ and asm, and mostly codes low level applications.
I on the other hand look at c++ in the higher level part. 

Can i program in linux so i can compile it for windows too, and don't have to worry that it doesn't work there?

As an example he showed me that he uses: 
mingw32 - win32 libraries
wxWidgets - cross platform

does anyone have experience with this? For example socket's aren't the same in linux and windows. How could a accomplish that? And no I am not planing on using phyton nor JAVA.

Thanks in advance:)

---

### Post by maxamillion on 2006-12-12
C++ can be cross platform, but it will depend on what you want to do with it. I wrote an application for a course at my university in C++ that used a cross platform gui library and I was able to compile on linux, windows, and mac os x successfully. But just because of my success in a certain implementation can not guarantee your success for another.

This may or may not have been helpful. Sorry if it wasn't.

/me

---

### Post by winch on 2006-12-12
> **Lycaon said:**
> For example socket's aren't the same in linux and windows. How could a accomplish that?

The easy way would be to find a cross platform network library that provided all the features you needed.

If one doesn't exist you would have to deal with the differences yourself.

You could for instance abstract out the differences using a class with methods such as open_socket send_data recive_data close_socket.
Your application would then use the methods implemented in the class without needing to care what platform it was running on.
Each platform would need an implementation of the class that used its native socket api.
Of course you could well spend more time messing around with this than actually writing your application. Part of the reason people like languages with large and varied standard libraries.

---

### Post by Wybiral on 2006-12-12
Well, you would need a cross compiler, something that will compile to window's "exe" instead of linux's "elf". Or you can always compile the source you wrote in linux on windows (or have a friend with windows do it). But, yeah... if you can do one of those two methods it is 100% possible. Next you have to worry about the headers and libraries you use. There are plenty of good crossplatform ones, I do a lot of graphical stuff so I use SDL and GLUT and never include specific headers for either OS. Following these rules it isn't too hard to develop your software for each system.

---

