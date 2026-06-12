---
title: "learning more c++"
date: 2007-04-30
forum: Programming Talk
---

### Post by DrPppr242 on 2007-04-30
Hi, I'm pretty new to programming I took a class in school on c++ and learned the basic (OOP, arrays, classes, functions ect.) now I want to keep learning more but I'm not sure where to go from here, can anyone reccomend a good next step?  I kind of want to learn to make a GUI for the simple programs I've written for consoles, but I don't know if that's to difficult, also the class was all C++.NET and everything was for win32 consoles do I need to learn something different to program in linux?

---

### Post by wizardofyendor on 2007-04-30
No .NET works on linux.  There is a project called mono. ([http://www.mono-project.com](http://www.mono-project.com)) that is an open source alternative to the .NET libraries.  For the most part the same code that is compiled on windows will run on linux (no modifications needed) and vice-versa.  There is even a really good C# IDE for linux (gnome) called monodevelop ([http://www.monodevelop.com)](http://www.monodevelop.com)).

Both mono and monodevelop are in the repos, but the monodevelop in the repos is very buggy, and I suggest you install it, and then install the updated deb files from here: ([http://packages.debian.org/unstable/devel/monodevelop](http://packages.debian.org/unstable/devel/monodevelop))

Congrats on wanting to learn more.  The world needs more able programmers.

---

### Post by DrPppr242 on 2007-04-30
thanks for the reply, I'm not familar with C# is that another language different from C/C++?

---

### Post by wizardofyendor on 2007-04-30
slightly but anything programed in .NET can run in linux with the mono package.

---

### Post by finer recliner on 2007-05-01
> **DrPppr242 said:**
> thanks for the reply, I'm not familar with C# is that another language different from C/C++?

C# is a language Microsoft invented to compete with Sun's Java. It's been said that its about 70% the same as java. some of it is taken from C++ ideas as well.

---

### Post by thumper on 2007-05-01
Don't use C++ to program in .NET.  C++/CLI is an abomination (sorry Herb).

To program in C++ on ubuntu you need to install the build-essential package, then use g++ as the compiler.

If you are happy to buy books, then I'd suggest the following:
  Scott Meyer's books "Effective C++" and "More Effective C++"
  Nico Josuttis's book on "The C++ standard library"

I'd avoid Bjarne Stroustrup's "C++ programming language" for a new learner.  I didn't actually find it that helpful.  Nico's book was better as a reference, and what I couldn't find there I found the actuall C++ standard documentation to be better.

Once you are through those, get
   "Exceptional C++" by Herb Sutter

"C++ Coding Standards" by Herb Sutter and Andre Alexandrescu is also a good book as you get more knowledge 

C++ is a great tool, and a really interesting language, but you do need a good understanding of it to be really proficient (which is one of the reasons many students are taught Java).

Join ACCU ([www.accu.org](www.accu.org)) if you are serious about developing as a professional developer.  It really is very good.

---

