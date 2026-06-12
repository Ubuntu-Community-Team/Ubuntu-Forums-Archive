---
title: "Error when trying to include most qt header files in c++ program"
date: 2007-05-18
forum: Programming Talk
---

### Post by reldruH on 2007-05-18
hello. I'm just starting out with developing using qt and kde and I'm running into an odd problem. Whenever I try to include qapplication.h or most qt header files (but not all, qstring.h seems to work fine) I get a bunch of error messages about undefined references to things I'm not using in my program. The header file itself is being found and I have every qt and kde -dev package I could find installed but I can't seem to get rid of these error messages. Google has been particularly unhelpful in this case. Can anybody point me in the right direction?

Here's the program that I'm trying to compile:
#include <qapplication.h>
#include <iostream>
using namepsace std;

int main()
{
cout << "Test test test" << endl;
}

Yes, that's actually the whole thing and I still get a bunch of error messages like this one:
/tmp/cceHCj6O.o:(.rodata._ZTV6QGList[vtable for QGList]+0xc): undefined reference to `QGList::clear()'

To compile it I'm running g++ test.cpp -o test -I/usr/include/qt3

Help?

---

### Post by WW on 2007-05-18
You need to tell the linker that you are using a qt library.  I just tried your example, and I had to add the option **-lqtmcop** to the g++ command.

By the way, an alternative to **#include <qapplication.h>** is **#include <qt3/qapplication.h>**.  With this change to the C++ file, you can drop the **-I/usr/include/qt3** option.  After I made that change (and after I fixed the "namespace" typo :), I could compile the example with the command
```

g++ qtest.cpp -o qtest -lqtmcop

```
(I called it qtest.cpp instead of test.cpp; a "test" command already exists.)

---

### Post by WW on 2007-05-18
I just want to add a reminder to consider using the **pkg-config** command to figure out the approprate options for compiling and linking.  In dapper, I have the multi-threaded version of Qt3 installed (package libqt3-mt-dev).  To get the compiler options, use:
```

pkg-config --cflags qt-mt

```
To get the linker options,
```

pkg-config --libs qt-mt

```
To use these in the g++ command, you can do this:
```

g++ qtest.cpp -o qtest `pkg-config --cflags qt-mt` `pkg-config --libs qt-mt`

```
By the way, I didn't see **-lqtmcop** in the output of  **pkg-config --libs qt-mt**, but the above g++ command also works for me.  I don't know enough about qt to know why.

I also noticed that the output of **pkg-config --cflags qt-mt** includes **-I/usr/include/qt3**, so perhaps in the qt world, **#include <qapplication.h>** is preferable to **#include <qt3/qapplication.h>**.

---

### Post by reldruH on 2007-05-18
*Thank you.* Everything you said worked perfectly. I don't understand why that extra compiler option is needed but it's completely solved my problem (everything except the typo :)) i wonder why none of the tutorials I was reading mentioned that. You'd think it would be pretty important to let people know that nothing will compile without this extra option. Thank you again, I'm going to go have some fun with qt (and read the man page for pkg-config :)).

---

