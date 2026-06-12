---
title: "A good C++ compiler"
date: 2009-11-15
forum: Programming Talk
---

### Post by RedSingularity on 2009-11-15
Can i get some recommendations on good C++ compilers?  Thanks.

---

### Post by MadMan2k on 2009-11-15
[http://www.microsoft.com/exPress/](http://www.microsoft.com/exPress/)

[COLOR="White"][SIZE="1"]dumb question - dumb answer[/SIZE][/COLOR]

---

### Post by RedSingularity on 2009-11-15
I agree with you MadMan.  Thats a good compiler but it isn't compatible with linux unfortunately.

---

### Post by phrostbyte on 2009-11-15
[this]("apt:build-essential") package includes GCC, which has a C++ frontend

```

g++ blah.cpp -o blah
./blah

```

Don't forget an [IDE]("apt:geany"). There are many more options, just giving you my preference :)

---

### Post by RedSingularity on 2009-11-15
I have found something called "eclipse".  But i dont know where to begin.  Are there any HOW TO'S out there that can help me out.  I am trying to learn C++.

---

### Post by phrostbyte on 2009-11-15
> **RedSingularity said:**
> I have found something called "eclipse".  But i dont know where to begin.  Are there any HOW TO'S out there that can help me out.  I am trying to learn C++.

Eclipse is an IDE, there is a difference between a compiler and IDE

(1) Compiler only generates object code from source files, it does not help you edit source
(2) And IDE helps you edit source and interface with a compiler / linker

Please download the packages I listed, it will provide you with a proper compiler as well a lightweight IDE less confusing then Eclipse for a beginner.

---

### Post by RedSingularity on 2009-11-15
Ok great.  Thanks.

---

### Post by RedSingularity on 2009-11-15
Got it.  Now lets say i want to start writing a program.  What do i do to start?  I plan on looking at some simple examples later but first i need to know how to start geany properly.

---

### Post by phrostbyte on 2009-11-15
When you get Geany, copy and paste this code in:

```

#include <iostream>
#include <string>

using namespace std;

int main()
{ 
  string foo;

  // this is a comment! whoa!
  cout << "Hello World!" << endl;   
  cout << "Pizza is yummy!" << endl;
  cout << "What is your name? ";
  cin >> foo;
  cout << endl << "Hello " << foo << endl;

  // return without issue
  return 0;
 
}

```

Then save as something ending with .cpp (eg: pizza.cpp) and hit "Run" in Geany. Hopefully it'll work, I didn't test it. :D

---

### Post by lisati on 2009-11-15
> **RedSingularity said:**
> Got it.  Now lets say i want to start writing a program.  What do i do to start?  I plan on looking at some simple examples later but first i need to know how to start geany properly.

The first step is to have clear idea of what you want to achieve.

My next suggestion is to start small but functional, and add the "bells and whistles" later.

---

### Post by phrostbyte on 2009-11-15
Actually hit "Build" and then "Run". It's in the toolbar. I just tested it and it works.

That is real C++ code, you can work from that example if you so desire. Maybe extend it to do something different.

---

### Post by rustik on 2009-11-15
How to get to work emc2 on kubuntu 9.4, 9.10?

---

### Post by RedSingularity on 2009-11-15
Yes it does work.  Thanks a lot for the advice.  :)

---

### Post by BenAshton24 on 2009-11-15
> **MadMan2k said:**
> [http://www.microsoft.com/exPress/](http://www.microsoft.com/exPress/)

[COLOR="White"][SIZE="1"]dumb question - dumb answer[/SIZE][/COLOR]

lol. [COLOR="White"][SIZE="1"]dumb response to dumb answer to dumb question[/SIZE][/COLOR]

A good book you can read is thinking in C++ ([http://www.codeguru.com/cpp/tic/tic_c.shtml](http://www.codeguru.com/cpp/tic/tic_c.shtml)) I haven't read all of it but from what I have read it's really interesting.

Although when I first started learning I never really read any books or anything, I preferred the trial and "while( 1 ){ error++; }" method :P

---

### Post by lisati on 2009-11-15
Anyone else read [Wiley's Teach Yourself C++]("http://books.theregister.co.uk/catalog/browse.asp?id=597960&group=5035&subcat=14&cat=B")? A month or two back I picked up a copy that my local library was disposing of, including CD (Windows based, of course!) but haven't had a chance to get into it yet.

---

### Post by Barriehie on 2009-11-15
I'm endeavoring this language also and found this [link](http://www.planetpdf.com/developer/article.asp?ContentID=6634).  It's referenced in the stickies and google tends to cough it up frequently.

Barrie

---

### Post by CptPicard on 2009-11-16
It should be noted that on Linux, "which C/C++ compiler to use" tends to be a wrong question to ask simply because GCC is de facto "the" compiler for those languages... :)

---

### Post by nvteighen on 2009-11-16
> **CptPicard said:**
> It should be noted that on Linux, "which C/C++ compiler to use" tends to be a wrong question to ask simply because GCC is de facto "the" compiler for those languages... :)
Not to mention that the GNU Compiler Collection is also sometimes preferred in Windows development using the MinGW32 port.

Other quality compilers seem to be the Intel ones, from the comments of some people in these forums.

---

### Post by RandyFulcher on 2009-11-16
Thanks, I had the same questions and Geany seems to do the trick!

---

### Post by grayrainbow on 2009-11-16
> **MadMan2k said:**
> [http://www.microsoft.com/exPress/](http://www.microsoft.com/exPress/)

[COLOR="White"][SIZE="1"]dumb question - dumb answer[/SIZE][/COLOR]
That's the shittiest compiler ever! But it could be probably couse I got every day access to it's bigger brother, which is real compiler(and de facto standard on windows).

For open source gcc family are as was mentioned standard.
And Intel compiler is probably the best in optimization nowadays, also got some free version for Linux as far as I remember.
Some people, for some reasons(which I don't know) like Code Warrior.

---

### Post by something132 on 2009-11-16
Dev C++ is good :)

---

