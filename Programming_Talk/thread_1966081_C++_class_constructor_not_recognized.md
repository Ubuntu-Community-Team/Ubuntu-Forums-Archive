---
title: "C++ class constructor not recognized"
date: 2012-04-26
forum: Programming Talk
---

### Post by chellrose on 2012-04-26
I'm trying to write a simple test program for the Verse class (a class which I defined).  Here is the relevant code:

Header file, Verse.h
```

#ifndef VERSE_H
#define VERSE_H

#include<iostream>
#include<string>
#include<cctype>

namespace BibleVerses
{
  class Verse
  {
  private:
    // Constant default values are initialized in the implementation file
    static const std::string DEFAULT_BOOK;
    static const std::string DEFAULT_TEXT;
    // Relevant member variables
    std::string book;
    int chapter;
    int verse;
    std::string verseText;

  public:

    // Constructor

    Verse(const std::string& b = DEFAULT_BOOK, int ch = 1, int v = 1, const std::string& txt = DEFAULT_TEXT);
  
    //Operators
    friend std::istream& operator >>(std::istream& ins, Verse& bv);

   // and some other member functions/operators are declared here
  };
}
#endif

```Implementation file, Verse.cpp
```

#include <iostream>
#include "Verse.h"

using namespace std;

namespace BibleVerses
{
  // Initialize constant member strings
  const std::string Verse::DEFAULT_BOOK = "";
  const std::string Verse::DEFAULT_TEXT = "";

  // Constructor
  Verse::Verse(const string& b, int ch, int v, const string& txt)
  {
    book = b;
    chapter = ch;
    verse = v;
    verseText = txt;
  }

  //Operator

    std::istream& operator >>(std::istream& ins, Verse& bv)
  {
    cout << "Enter the book: ";
    getline(ins, bv.book);

   cout << "Enter the chapter: ";
    ins >> bv.chapter;

    cout << "Enter the verse: ";
    ins >> bv.verse;
   }

  // and other member functions/operators defined here
}

```Test file, VerseTest.cpp
```

#include "Verse.h"

using namespace BibleVerses;
using namespace std;

int main()
{
  Verse myVerse("Exodus", 2, 3, "testing.");

  cin >> myVerse;
  
  return 0;
}

```Makefile, make_test
```

CXX = g++
CXXFLAGS = -g -c

LD = g++
LDFLAGS = -g

verseTest: VerseTest.cpp Verse.h Verse.cpp
    ${LD} ${LDFLAGS} VerseTest.cpp -o verseTest

clean:
    rm -rf *.o verseTest core

```When I compile the program with
```

make -f make_test

```I get the error
```

/tmp/ccu9LryD.o: In function `main':
VerseTest.cpp:12: undefined reference to `BibleVerses::Verse::Verse(std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&, int, int, std::basic_string<char, std::char_traits<char>, std::allocator<char> > const&)'
VerseTest.cpp:14: undefined reference to `BibleVerses::operator>>(std::basic_istream<char, std::char_traits<char> >&, BibleVerses::Verse&)'
collect2: ld returned 1 exit status
make: *** [verseTest] Error 1

```Why isn't it recognizing my class functions?


Notes:
-I also tried not initializing myVerse in the test program, i.e. ```
Verse myVerse;
```; this led to the same errors plus -- it didn't recognize the constant DEFAULT_BOOK and DEFAULT_TEXT member variables.
-I wrote this class using exactly the same format (down to the last semicolon!) as a program from my C++ class, 6 years ago (!).  *That* program compiles and runs just fine...

Thanks :D!

---

### Post by 11jmb on 2012-04-26
You need to compile Verse.cpp

you can make an object file with a command like:
```
g++ -c Verse.cpp -o Verse.o
```

Then you can compile & link with:
```
g++ -o VerseTest.cpp Verse.o -o verseTest
```

---

### Post by dwhitney67 on 2012-04-26
> **11jmb said:**
> You need to compile Verse.cpp


+1.

My suggestion however is to revamp the Makefile; something like this will do:
```

APP       = verseTest

SRCS      = VerseTest.cpp Verse.cpp
OBJS      = $(SRCS:.cpp=.o)
DEPS      = $(SRCS:.cpp=.d)

DEPENDS   = -MT $@ -MD -MP -MF $(subst .o,.d,$@)
CXXFLAGS += $(DEPENDS) -g

.PHONY: clean


$(APP): $(OBJS)
        $(CXX) $^ -o $@

clean:
        $(RM) $(APP) $(OBJS) $(DEPS)

-include $(DEPS)

```

---

### Post by chellrose on 2012-04-27
It's been WAY too long since I've done this.  Thank you both for the additional info.  It works now! :KS

---

