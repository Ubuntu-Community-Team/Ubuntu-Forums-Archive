---
title: "c++ program problem"
date: 2010-08-28
forum: Programming Talk
---

### Post by shadowstep0705 on 2010-08-28
Hey everyone, I'm creating a fighting game with anjuta in c++, but when I run it and enter option 4 (which isn't supported), my game runs in a loop, here is the code that I have already
```
#include <iostream>
#include <fstream>
#include <stdlib.h>
bool Checksafefile();
using namespace std;



int main()
{
    bool savefileexists = Checksafefile();
    do {
        int clear = system("clear");
        int option;
        cout << "\033[0mWelcome To freefighter 0.1 by shadowstep0705" << endl;
         cout << "MAIN MENU:" << endl;
        cout << "1 - New game" << endl;
        if (savefileexists)
            cout << "2 - Load game" << endl;
        else
            cout << "\033[22;31m2 - Load game\033[0m" << endl;
        cout << "3 - Leave game" << endl;
        cin >> option;
        }
        while(option != 1||option != 2||option !=3);
        return 0;
}

bool Checksafefile()
{
    ifstream myfile("save.dat");
    return myfile;
}
```So what im trying to do is that when the user enters an option which isn't equal to 1,2 or 3, he will be returned to the main menu, what am I doing wrong?

EDIT: I got it, syntax error

---

### Post by GregBrannon on 2010-08-28
Mark it solved.

---

### Post by trent.josephsen on 2010-08-28
Don't #include <stdlib.h> in C++, and please indent your code properly.

---

### Post by dwhitney67 on 2010-08-28
> **trent.josephsen said:**
> Don't #include <stdlib.h> in C++, and please indent your code properly.

Yes, the OP needs to include <cstdlib> (for the use of the system() call).

---

### Post by trent.josephsen on 2010-08-28
Thanks for making that clarification.

---

