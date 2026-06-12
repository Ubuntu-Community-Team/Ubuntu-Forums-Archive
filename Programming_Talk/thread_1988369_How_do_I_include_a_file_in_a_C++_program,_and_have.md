---
title: "How do I include a file in a C++ program, and have that program write it?"
date: 2012-05-27
forum: Programming Talk
---

### Post by compiz addict on 2012-05-27
I want to create a program that will compile in both g++ on Ubuntu, and Dev C++ on Win7. What I want to have is a single executable file that will write all the files it needs to run in the directory it's running in.

How would I do this?

---

### Post by trent.josephsen on 2012-05-27
If you just want to write a program that creates and populates files, stick to standard C++ and it will compile on literally any C++ compiler; writing to files is part of the C++ standard.

I suspect there's more to your question than that, but I can't guess what it might be. Can you explain in more detail or give an example of what the program should do?

---

### Post by roelforg on 2012-05-27
dev-c++ uses mingw32 which is basically gcc/g++ for windows.
Stick with cross-platform gui-toolkits like gtk (if you want gui, that is).
And just use normal c++ (e.g ofstream) for the file i/o

---

### Post by ofnuts on 2012-05-28
> **compiz addict said:**
> I want to create a program that will compile in both g++ on Ubuntu, and Dev C++ on Win7. What I want to have is a single executable file that will write all the files it needs to run in the directory it's running in.

How would I do this?Are you talking about self-unpacking executables, by any chance? ie, when you run the executable it unpacks itself as a set of files, that contains at least one other executable, to which execution is transferred. This is fairly common for software installers on Windows.

---

