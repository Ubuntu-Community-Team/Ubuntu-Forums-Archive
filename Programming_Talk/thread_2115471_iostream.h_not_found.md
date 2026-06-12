---
title: "iostream.h not found"
date: 2013-02-13
forum: Programming Talk
---

### Post by bitsaman on 2013-02-13
Please help!
Whenever  i try to run a c++ program my g++ compiler gives an error iostream.h not found! How do i rectify that ?(Because of that i'm unable to execute my c++ programs in ubuntu 12.04....Is there some packages need to be installed  )
Also tell me how to work with graphic.h ?

---

### Post by QIII on 2013-02-13
Moved to Programming Talk

---

### Post by lisati on 2013-02-13
*Thread moved to **Programming Talk**.*

I've edited the title of your thread to something more likely to get a response.

---

### Post by lisati on 2013-02-13
> **QIII said:**
> Moved to Programming Talk

Noticed! :D

---

### Post by QIII on 2013-02-13
You are quicker, master!

---

### Post by lisati on 2013-02-13
Back on topic: If memory serves correctly, it's more usual to include <iostream> rather than <iostream.h>

Are you converting MS-DOS or Windows software to work with Ubuntu by any chance?

---

### Post by fdrake on 2013-02-13
I would still be kinda of worried if <iostream.h> did not work. try this:
```

sudo apt-get install build-essential && sudo apt-get upgrade && sudo apt-get update

```

---

### Post by Warren Hill on 2013-02-13
try replacing <iostream.h> with <iostream> and compile again.  If this still does not work and the code is small enough post the source so we can see whats wrong

---

### Post by iMac71 on 2013-02-13
if you have installed a recent release of c++, for instance with```
sudo apt-get install g++
```you should use iostream instead of iostream.h.
iostream.h is the old name of iostream.

---

### Post by Malsasa on 2013-02-13
Yes, but install first your **build-essential**.

---

### Post by malakar.subhendu on 2013-02-13
try replacing <iostream.h> with <iostream> and after declaring all the necessary preprocessor directives write:

using namespace std;

If g++ is not installed (which is by default), then type this in terminal:

sudo apt-get install g++

For the second part: graphics.h is not supported in gcc. If you need to work on graphics.h, you can install dosbox from the sofware center and work with it.

---

### Post by bitsaman on 2013-02-17
I have installed g++ ! and now it shows error : cout   not defined in this scope! What needs to be done ?

---

### Post by r-senior on 2013-02-17
See if you can compile this program:

*hello.cpp*
```
#include <iostream>

using namespace std;

int main()
{
    cout << "Hello World" << endl;
}

```

Create it in a file called hello.cpp and compile as follows:

```
$ g++ -o hello hello.cpp
$ ./hello
Hello World

```

Post any error messages from the compilation process.

---

### Post by Virtuality314 on 2013-02-17
You need to put 

```
using namespace std;
```

after including iostream.

---

