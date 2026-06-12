---
title: "Codeblocks,C++, rand() was not declared."
date: 2009-10-06
forum: Programming Talk
---

### Post by myromance123 on 2009-10-06
Hopefully i posted this in the right area (sorry if i didnt).
 Hey there. Learning C++ from C++ For Dummies All-In-One Second edition where they teach it with Codeblocks (the reason why i bought it).

 Ok, my problem is basically I get an error as such when building:
```
error; 'rand' was not declared in this scope
```

Here's my sourcode (slightly modified from the books version. Just added a prototype for the function).
 rand() is located in the GetSecretCode() function :)
```
#include <iostream>
#include <sstream>

using namespace std;

string *GetSecretCode();

int main()
{
    string *newcode;
    int index;

    for ( index = 0; index < 10; index++ )
    {
        newcode = GetSecretCode();
        cout << newcode << endl;
    }

    cout << "All done here" << endl;

    return 0;
}

string *GetSecretCode()
{
    string *code = new string;
    code->append("CR");

    int randomnumber = rand();
    ostringstream converter;
    converter << randomnumber;

    code->append(converter.str());
    code->append("NQ");

    return code;
}

```

 What am I missing code wise?
something I didn't "#include" ?

---

### Post by MadCow108 on 2009-10-06
rand is defined in cstdlib (there is no standard c++ random function yet). so include:
#include <cstdlib>

also you have memory leaks in your code as you don't delete the created string
generally you should avoid dynamically allocating stuff where it is not needed.
you can rewrite it to something like this:
```

// very long string which might be expensive to copy, so use a reference
void createCopyExpensiveString(string & str) {
// dostuff
}

// short string, cheap to copy
string createShortString()
{
   return "shortstring";
}

void main()
{
  string str;
  createCopyExpensiveString(str);
  cout << str << endl;
  string str2 = createShortString();
  cout << str2 << endl;
} // str and str2 go out of scope here and get deleted automatically

```

---

### Post by myromance123 on 2009-10-06
Hey thanks, it worked off the bat.
 
 Just out of curiosity I tried it on Vista as well but without cstdlib
and it works.....whats with that?

 It's obvious now that although they promote crossplatform code in this For Dummies book, they only tested the code on Winduhs...
  
 For shame..
Any idea why it works differently?

---

### Post by peetbull on 2009-10-06
It is a usual phenomenon...

Many compilers include some "hidden" libraries that support the underlying operating system. For example, in Vista, your compiler may add <cstdlib> subtlely.

Another example is GCC's linker in Linux that automatically adds "stdlib.h" by default, without prior declaration by the programmer.

I hope I made it clear for you.

Happy coding!

---

### Post by myromance123 on 2009-10-06
Thanks guys.
 that was the case with C when I learned it earlier this year.. 
  MadCow, I shall ponder upon your unique(odd?) code and when I have better grasped C++ then maybe I shall better understand it.
 Toodles~


:guitar:

---

### Post by forrestcupp on 2009-10-06
> **myromance123 said:**
> Thanks guys.
 that was the case with C when I learned it earlier this year.. 
  MadCow, I shall ponder upon your unique(odd?) code and when I have better grasped C++ then maybe I shall better understand it.
 Toodles~


:guitar:

MadCow's code isn't really odd.  He makes a great point.  A lot of people use a lot of pointers when they're not really needed.  It is important to really understand what pointers are for, and only use them when necessary because pointers can be the main source for memory leaks.  If you don't really need them, don't use them.

---

### Post by foxgoooo on 2011-04-18
ok i new to programming and went i try to use the ‘rand’ i get this was not declared in this scope|


#include <iostream>
#include <cmath>

int main()
{
    using namespace std;

    double num1;
    num1 = rand ();
    cout << num1 <<endl;



    return 0;
}

---

### Post by Linteg on 2011-04-18
> **foxgoooo said:**
> ok i new to programming and went i try to use the &#8216;rand&#8217; i get this was not declared in this scope
...
Probably because rand belongs to cstdlib, not cmath. Also, avoid resurrecting long forgotten threads.

---

