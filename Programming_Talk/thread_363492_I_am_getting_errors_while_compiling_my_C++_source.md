---
title: "I am getting errors while compiling my C++ source"
date: 2007-02-17
forum: Programming Talk
---

### Post by billdotson on 2007-02-17
I downloaded "Think Like a Computer Scientist: C++ Programming" from greenteapress.com and I did their example 

#include <iostream> (it said <iostream.h> but I have heard that is the old way)
// main: generate some simple output
void main()
{
cout << "Hello, world." << 
endl; // output one line
cout << "How are you?"
<< endl; // output another
}

and I got the following error

#include <iostream> (it said <iostream.h> but I have heard that is the old way)
// main: generate some simple output
void main()
{
cout << "Hello, world." << 
endl; // output one line
cout << "How are you?"
<< endl; // output another
}

is this book a bad resource?

---

### Post by Lux Perpetua on 2007-02-17
Looks sketchy. main() should always return **int**, not void. 

Also, you didn't say what the error was.

---

### Post by runningwithscissors on 2007-02-17
If you are indeed typing the program as you've pasted here (without breaking lines properly), it won't work. You need to break lines using the backslash character.

Like so:
```
cout<<"Hello World."\
<<endl;
```

---

### Post by WW on 2007-02-17
runningwithscissors: Actually, that is not necessary.  The linebreak in the strange place doesn't look good, but the code will compile.

billdotson: I think you posted your source code twice, instead of the errors.

Two corrections to your code: As lux pointed out, main must return int.  Also, you will need the line 'using namespace std;' before main if you want to use cout, endl, etc without qualifying them with the namespace prefix std::.  This code will compile with g++:
```

#include <iostream>

using namespace std;

// main: generate some simple output
int main()
{
    cout << "Hello, world." << endl; // output one line
    cout << "How are you?" << endl; // output another
}

```

---

