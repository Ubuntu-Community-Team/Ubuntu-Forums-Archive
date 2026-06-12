---
title: "C++ on Ubuntu?"
date: 2007-10-17
forum: Programming Talk
---

### Post by marenkar on 2007-10-17
I got it already, but it wont install, guess it wont work here. I heard there was a program that works on Ubuntu and runs C++, Codeblocks IDE I think, where will I be able to get this program. No, i'm not looking for something like WINE.

---

### Post by Druke on 2007-10-17
> **marenkar said:**
> I got it already, but it wont install, guess it wont work here. I heard there was a program that works on Ubuntu and runs C++, Codeblocks IDE I think, where will I be able to get this program. No, i'm not looking for something like WINE.

Your wanting an IDE? In the package manager Anjuta works very well (though I prefer getting the latest version from them. The generic C++ compiler in ubuntu is gcc

---

### Post by ankursethi on 2007-10-17
I think I know where you're coming from. Is it Turbo C++/Microsoft Visual C++/Borland C++ that you want to install? Or is it the Code::Blocks IDE?

Code::Blocks is available from Codeblocks.org. Just click the download button and choose to download the unstable build instead of the latest stable version. You will find Ubuntu packages in the forums.

You will also need to do :
```
sudo aptitude install build-essential
```
in the terminal to get the compiler.

You should also take a look at Anjuta. To install Anjuta, go to Applications->Add/Remove and look for it there.

---

