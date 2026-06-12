---
title: "Beginner Error C++"
date: 2010-07-25
forum: Programming Talk
---

### Post by Blumoon94 on 2010-07-25
Hey, I am a beginner trying to learn C++ in Dev C++ using this tutorial [http://newdata.box.sk/bx/c/htm/ch02.htm#Heading1](http://newdata.box.sk/bx/c/htm/ch02.htm#Heading1)
and I get these errors with the code written here
```
#include <cstdlib>
#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{
 cout << "Hello there.\n";
7:        cout << "Here is 5: " << 5 << "\n";
8:        cout << "The manipulator endl writes a new line to the screen." <<  
                      endl;
9:        cout << "Here is a very big number:\t" << 70000 << endl;
10:       cout << "Here is the sum of 8 and 5:\t" << 8+5 << endl;
11:       cout << "Here's a fraction:\t\t" << (float) 5/8 << endl;
12:       cout << "And a very very big number:\t" << (double) 7000 * 7000 << 
                      endl;
13:       cout << "Don't forget to replace Jesse Liberty with your name...\n";
14:       cout << "Jesse Liberty is a C++ programmer!\n";
    system("PAUSE");
    return EXIT_SUCCESS;
}
```

I get the error "expected `;' before ':' token"

---

### Post by user_none on 2010-07-25
When you copied the code you didn't remove the line numbers. The 7: 8: 9: and so forth are not part of the code.

---

### Post by thetaz_x on 2010-07-25
```

#include <cstdlib>
#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{
 cout << "Hello there.\n";
 cout << "Here is 5: " << 5 << "\n";
 cout << "The manipulator endl writes a new line to the screen." <<  endl;
 cout << "Here is a very big number:\t" << 70000 << endl;
 cout << "Here is the sum of 8 and 5:\t" << 8+5 << endl;
 cout << "Here's a fraction:\t\t" << (float) 5/8 << endl;
 cout << "And a very very big number:\t" << (double) 7000 * 7000 << endl;
 cout << "Don't forget to replace Jesse Liberty with your name...\n";
 cout << "Jesse Liberty is a C++ programmer!\n";
 system("PAUSE");
 return EXIT_SUCCESS;
}

```

the guy above be is right your code should look like this

---

