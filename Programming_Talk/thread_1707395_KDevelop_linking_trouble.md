---
title: "KDevelop linking trouble"
date: 2011-03-15
forum: Programming Talk
---

### Post by barisurum on 2011-03-15
Hi there;

I try to compile a simple app with Kdevelop but it gives these errors:
```

main.cpp:9: undefined reference to `DeckOfCards::DeckOfCards()'
main.cpp:11: undefined reference to `DeckOfCards::shuffle_cards()'
main.cpp:12: undefined reference to `DeckOfCards::deal_cards()'
collect2: ld returned 1 exit status
```

As I understand KDevelop doesn't configure the project by itself. How can I make it understand that I want to link the executable with the library deckofcards.h I created?

---

### Post by Arndt on 2011-03-15
> **barisurum said:**
> Hi there;

I try to compile a simple app with Kdevelop but it gives these errors:
```

main.cpp:9: undefined reference to `DeckOfCards::DeckOfCards()'
main.cpp:11: undefined reference to `DeckOfCards::shuffle_cards()'
main.cpp:12: undefined reference to `DeckOfCards::deal_cards()'
collect2: ld returned 1 exit status
```

As I understand KDevelop doesn't configure the project by itself. How can I make it understand that I want to link the executable with the library deckofcards.h I created?

Does main.cpp do #include on deckofcards.h?

---

### Post by barisurum on 2011-03-15
Yes it does. But the problem is with the linking stage. Some linker options are not set. And i can't find any linker settings in KDevelop. Code::Blocks used to do it for me. But KDevelop lacks this facility. Code::Blocks' code completion is not good enough so I switched to KDevelop.

---

### Post by AbhiJais on 2011-03-19
Seeing your error log, it seems like your application requires linking to libraries(containing the said functions' definition). Since Kdevelop uses the gcc compiler, Can you configure the compilation manually? Try to use '-L' and '-l' options to locate the libraries.

-L: path to the lib dir
-l: lib name. for example -lqtcore.

But you have to know to name of lib, you are about to use.

---

### Post by AbhiJais on 2011-03-19
Else you can try manipulating the Makefile by adding the lib name with absolute path under 'LIB' variable. try to see this link:
[http://www.linuxquestions.org/questions/programming-9/linking-static-and-shared-libraries-in-the-kdevelop-environment-374624/](http://www.linuxquestions.org/questions/programming-9/linking-static-and-shared-libraries-in-the-kdevelop-environment-374624/)

---

### Post by giofol on 2012-09-28
I had the same problem. Until I read the cmake manual. or you can quick read this tutorial 
[http://techbase.kde.org/Development/Tutorials/CMake]("http://techbase.kde.org/Development/Tutorials/CMake")

the solution is to add the source files to your  project in the CMakeLists.txt file.

open the CMakeLists.txt
and there is a line like this 
```

add_executable(example2 main.cpp)
```

instead type this 

```
set(MyProjectSources example01.cpp example01.h main.cpp )

add_executable(example2 ${MyProjectSources})
```

this is a quick solution to your problem.

---

