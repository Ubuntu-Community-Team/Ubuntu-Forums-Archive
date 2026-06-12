---
title: "I have a C++ book copyrighted in 1999, should I get a newer source to start C++??"
date: 2007-02-13
forum: Programming Talk
---

### Post by billdotson on 2007-02-13
I have Teach Yourself C++ in 21 Days: Third Edition (C) 1999
I have gotten to the first sample program that goes as follows:

#include <iostream.h>

int main()
{
     cout << "Hello World!\n";
     return 0;
}

I created it using gedit and saved it as hello.cpp and then cd'ed into Desktop and did 
gcc <hello.cpp> to compile and I got an error that says: bash: syntax error near unexpected token `newline'

Should I get a newer source to start learning C++ seeing as how this book is (C) 8 years ago?  Or is the language the same?

If I need a new source could someone recommend a free, legal, C++ guide that has walkthroughs and sample programs to write?  Thanks.  

BTW Linux got me interested into programming, web development, operating from the command line, etc.

---

### Post by Wybiral on 2007-02-13
You should use "g++ hello.cpp" to compile and use "#include <iostream>" instead of "<iostream.h>" (thats oldschool)

Other than that it looks OK... Make sure you have your build-essential installed.

---

### Post by billdotson on 2007-02-13
so is C++ pretty much the same as it was then, so that the source I have is sufficient?

---

### Post by maxamillion on 2007-02-13
I think the book will be fine, the worst I think that will happen is that you will pick up some old style programming habits along the way but the language itself hasn't changed much (if at all) since 1999. C++ isn't my main language to code in so I don't stay too current with it, but I would imagine I would read somewhere in my array of tech news sites that I check daily if there was some massive overhaul of the C++ programming language.

---

### Post by Jucato on 2007-02-14
For C++ basics, I think the book would be fine. However, the problem would be if  you want to get started or to be familiar with Standard C++, which wasn't ISO approved until 1998, iirc. Your book, though published in 1999, seems to still be using non-standard things, like <iostream.h> and the absence of namespaces or std. 

You can stick to your book, learn C++, and then learn the Standards. But like what maxamilion said, you might pick up a few bad habits along the way. Or a few non-standard habits. It might be harder to unlearn those than to start clean with Standard C++.

I'm also a C++ newbie. I decided to take the "Standards" path and buy a book that is aware of (ISO) Standard C++, and also teaches STL. It was an added plus that the authors also know about GCC, so it's not a biased book. 

Anyway, gotta get back to reading it. :D

---

### Post by po0f on 2007-02-14
billdotson,

Read [this](http://mindview.net/Books/TICPP/ThinkingInCPP2e.html) book instead.  It's free for download, and is a little more recent than the book you have.  ;)

---

### Post by runningwithscissors on 2007-02-14
I would advise _not_ learning from an old book.

C++ is not the easiest language to learn, and getting off on the wrong foot is not something that should be done when you have more up-to-date resources available.

Standardisation brings a few things to C++ that definitely make it nicer to deal with. Working with the STL being the most prominent.

EDIT: Whoops. I read 1999 as 1989. So, sorry. I think a book published in 1999 would be alright.

---

