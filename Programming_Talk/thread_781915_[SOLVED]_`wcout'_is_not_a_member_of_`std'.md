---
title: "[SOLVED] `wcout' is not a member of `std'"
date: 2008-05-04
forum: Programming Talk
---

### Post by WitchCraft on 2008-05-04
I have a problem with compiling unicode C++ programs.

I'm developing a very little cross-platform application.

Now I use Unicode in Linux, and it works very well.
Compiling the same with MinGW on Windows outputs:
`std::wios' has not been declared
load.hpp:51: error: `std::wifstream' has not been declared
load.hpp:69: error: `wofstream' is not a member of `std'

Now there is a problem with Unicode, so I wrote a little test program to be sure:

```

#define UNICODE
#define _UNICODE
#define __UNICODE

#include <iostream>
#include <fstream>

int main() {

        std::cout  <<  "Test ASCII\n";
        std::wcout << L"Test UNICODE! \n";

        return 0;
}

```

min@FROOGLEBOT ~/dialog
$ g++ bla.cpp -o bla

This outputs:
bla.cpp:11: error: `wcout' is not a member of `std'

Anybody knows what to do about this?

---

### Post by tseliot on 2008-05-04
Have a look at [this page]("http://www.mingw.org/MinGWiki/index.php/wide%20characters").

---

### Post by WitchCraft on 2008-05-04
> **tseliot said:**
> 
Have a look at [this page]("http://www.mingw.org/MinGWiki/index.php/wide%20characters").


8+ years of Unicode and the C++ STL hasn't yet been ported to MinGW so you need to use 3rd party Software ? Disgusting.

---

### Post by tseliot on 2008-05-04
Why don't you try QT4 (which is cross platform)? QStrings use unicode.

---

### Post by WitchCraft on 2008-05-04
OK, now the install file says.

Supply the "lib" subdirectory to the library search path and add desired library to the list of libraries to link with.

Where do I add "search path" if I'm compiling from the command line with MSYS?

---

### Post by WitchCraft on 2008-05-04
> **tseliot said:**
> Why don't you try QT4 (which is cross platform)? QStrings use unicode.

I use wxWidgets - not Qt, but I said if I can I use the STL, I'll do it, because it surely is ported and works everywhere, unlike wxWidgets and Qt... 

Well, what to say... 1063 lines of code wasted. DAMN! I wanted to be progressive and use Unicode. Now I can rewrite everything, because MinGW does not support it...

Well, today I have learned something about THE standard template library...
In the future I will try to avoid it, whenever I can.

---

### Post by LaRoza on 2008-05-04
> **WitchCraft said:**
> I use wxWidgets - not Qt, but I said if I can I use the STL, I'll do it, because it surely is ported and works everywhere, unlike wxWidgets and Qt... 

Well, what to say... 1063 lines of code wasted. DAMN! I wanted to be progressive and use Unicode. Now I can rewrite everything, because MinGW does not support it...

Well, today I have learned something about THE standard template library...
In the future I will try to avoid it, whenever I can.

QT works in Windows.

---

### Post by WitchCraft on 2008-07-05
> **LaRoza said:**
> QT works in Windows.

If only the end user had the runtime libraries (of the correct = != latest version!...).
But C/C++ win-libc runtime should be installed by default... It's Windows.
Unfortunately this is not true for win-libc-dev...

---

