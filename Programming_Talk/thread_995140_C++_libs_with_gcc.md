---
title: "C++ libs with gcc"
date: 2008-11-27
forum: Programming Talk
---

### Post by _self on 2008-11-27
Hi all.
Really don't know which category is the most suitable for this thread, so just post here.
I have some complications with C++ in Ubuntu. Got some books to learn this language and installed almost everything related to gcc and C++ via aptitude.
So then, got the simple exercise, wrote the .cpp file and tried to compile it. g++ couldn't even find the simplest i/o commands as "cin" and "cout", even I included "iostream" lib in the file being compiled. Firstly, gcc couldn't find that file. So I've copied it from /usr/include/c++/4.3 to /usr/lib/gcc/i486-linux-gnu/4.3/include. When compiling, g++ successfully found the lib, but... no necessary functions could be read from it! g++ recognized "cin" and "cout" as undeclared variables... So I'm stalled, could anyone give me an advice how to make it work? Thanks in advance!

---

### Post by geirha on 2008-11-27
[Programming talk](http://ubuntuforums.org/forumdisplay.php?f=39) would be the best place to post this question. But anyway, could you post the .cpp-file you are trying to compile? I'm guessing you either have to add a 
```
using namespace std;
```
or prepend std:: to cin and cout and the likes.
```
std::cout << "Hello, World!" << std::endl;
```

---

### Post by cmay on 2008-11-27
i have asked for your tread to moved to the programming talk section. and maybe it would be a good idea to post the compiler log and code in question.

---

### Post by bapoumba on 2008-11-27
Moved to Programming Talk.

---

### Post by snova on 2008-11-27
Post the exact code you have, and the compiler command you use. It's probably pretty simple, but just in case.

Since you have the STL headers available, I'm going to assume you already have build-essential installed, or enough of it anyway.

And delete the file you copied. That's not going to do you any good, and will probably mess things up eventually.

---

### Post by CptPicard on 2008-11-27
I'm quite sure it's just that build-essential is not installed.. :)

And yeah, don't go manually copying stuff around, you'll hose your system beyond help.

---

### Post by _self on 2008-11-28
geirha, thank you, it works =) can you give me some links what to read to find out where the mistake was?
2CptPicard: build-essential was installed for that moment, however. I've read some mans and tried to search the solution by Google before posting here, but could find nothing helpful (of course, I can suppose I've spent too little time to do it) ;)

---

