---
title: "char type variable in switch in C++"
date: 2008-08-30
forum: Programming Talk
---

### Post by Nergar on 2008-08-30
Why if I use "char menuNum;" instead of "int menuNum" (in menu ()) the function never gets called?

Code:
```
#include <stdlib.h>
#include <iostream>
#include <string>  
using namespace std;

void message1 () {
    cout << "Hello World!" << endl;
}

void message2 () {
    cout << "I'm a C++ program :)" << endl;
}

void quit () {
    exit(0);
}

void menu () {
    int menuNum=0;

    cout << "Menu:" << endl;
    cout << "1. Message 1" << endl;
    cout << "2. Message 2" << endl;
    cout << "3. Exit" << endl;
    cin >> menuNum;

    switch (menuNum) {
    case 1:
        message1 ();
        break;
    case 2:
        message2 ();
        break;
    case 3:
        quit ();
	}
}

int main(int argc, char** argv) {
	do {
        menu ();
	}
	while (true);
}

```

Another thing, is this the right way to keep a program running? Am I doing the right thing or there is a better way to achieve the same?

---

### Post by samjh on 2008-08-30
When you used char, did you enclose the characters in single-quotes in the case labels?

Example: **case 'a': // CODE**

For your second question, no it is not a particularly good way.  Some will actually consider it bad style to use exit() unnecessarily, as you're falling back on a C library function when alternative methods exist.

You could try something like this:
```
int menu() {
    
    // Code to get menuNum from user.

    return menuNum;
}

...

int main(int argc, char** argv) {
    ...
    while (menu() != 3) {
        if (menu() == 1) {
            // Call function.
        }
        // etc.
    }
    ...
}
```

OR

If you don't want to change your code so much, you can change your **void menu()** to **bool menu()** and when menuNum is 3, use **return true** and test for the menu() function's return value in your main do-while loop.
```
bool menu() {
    switch (menuNum) {
        ...
        case 3:
            return true;
    }
}

int main(int argc, char** argv) {
    bool quitprog;
    quitprog = false;

    do {
        quitprog = menu();
    } while (quitprog == false);

    ...
}
```

There are other ways too.  These two just come to my head automatically.

---

### Post by Nergar on 2008-08-30
Thanks for you help

---

