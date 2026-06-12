---
title: "Undefined reference, not sure what to do"
date: 2013-05-21
forum: Programming Talk
---

### Post by agjoshi on 2013-05-21
I am trying to use gcc and graphics. I am getting an error 

undefined reference to `graphresult'

Do not know where to ask for help

---

### Post by lisati on 2013-05-21
*Thread moved to **Programming Talk**.*

---

### Post by mörgæs on 2013-05-21
Welcome to the fora.

Feel free to post here. Worst case scenario is that we'll simply move it.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by lisati on 2013-05-21
Hi, and welcome to the forum.

I've renamed your thread and moved it to a section of the forum that deals with programming questions.

---

### Post by spjackson on 2013-05-21
What is it that you are trying to compile? Is it something you have written yourself or that you have copied from somewhere?


What is graphresult? It isn't a standard C function, so you need to link to either the source for that function, or to a library containing the object code for it. e.g.
```

gcc -o myprogram myprogram.c -lNameOfLibraryContainingGraphresult

```


Google tells me that graphresult is in a Turbo-C library (for Windows), but this might not be what you mean.

---

### Post by agjoshi on 2013-05-22
Let me narrate what was I exactly compiling.

I want to write a C program for interraction with the user. Normal scanf and printf use a standard font for the input and out put. I want to be able to control the font and the font size while interracting with the user.
I located a program that demonstrates this aspect of programming. I found this program on the following link

[http://www.syvum.com/cgi/online/serve.cgi/squizzes/cpp/cpp_p18a.html](http://www.syvum.com/cgi/online/serve.cgi/squizzes/cpp/cpp_p18a.html)

the program is titled  [COLOR=navy]C++ Programming : Program 18-A[/COLOR] on the forum  Syvum.

I noticed that I need to have the graphics.h and found detailed instructions for getting it at the link

[http://vksalian-techblog.blogspot.in/2010/10/how-to-install-graphics-libraries-and.html](http://vksalian-techblog.blogspot.in/2010/10/how-to-install-graphics-libraries-and.html)

The post says that I should install the package [[SIZE=1][COLOR=#cc3300]libgraph-1.0.1[/COLOR][/SIZE]]("http://download.savannah.nongnu.org/releases/libgraph/libgraph-1.0.1.tar.gz") I installed libgraph-1.0.2 thinking that latter version is better.

I followed the instructions on the blog to compile the program that was to show me how to manipulate the fonts while interracting with the user.
I got the above error - undefined reference to `graphresult'
This was one of the errors. There were other functions also like settextstyle etc.

What must have been my error?

---

