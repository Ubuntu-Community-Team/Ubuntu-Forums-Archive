---
title: "C++ help needed..."
date: 2009-04-22
forum: Programming Talk
---

### Post by Kolmogorov on 2009-04-22
Hi everyone, 

I don't understand why this isn't working!

```
// delete.cpp

#include <iostream>
#include <string>

using std::cout; 
using std::cin;
using std::endl;
using std::string;

string * getname(void);

signed int main(void)
{
       string * name;
       name = getname();
       // name isn't displayed -- it's the address of name
       cout << name << " at " << (int *) name << endl;
       
       name = getname();
       cout << name << " at " << (int *) name << endl;
       
       cin.get();
       
       return 0;
}

string * getname(void)
{
       string temp;
       cout << "\nEnter last name: ";
       getline(cin, temp);
       
       string * pn = new string [temp.size()];
       
       pn = &temp;
       
       return pn;
}

```

Any clue? Normally, when we feed a pointer-to-string to the cout operator, it print onscreen sequentially all the characters in string until the \0 is attained...why this isn't working?

Thanks for the help.

---

### Post by cabalas on 2009-04-22
Your code is working as you coded it to.  I think you are getting a pointer to a char confused with a pointer to a string.  AFAIK cout will only dereference char pointers in all other cases it will print the address that the pointer points to.

---

### Post by mshipman on 2009-04-22
There are two issues with this program...

1. Passing a string pointer to cout displays the value of the pointer (it's address). To display the value that the pointer is pointing to, you must dereference it.

2. In getname(), you were returning a pointer that referenced a local variable... a local variable that gets destroyed at the end of the function call, so it doesn't exist by the time we return to main.

```


// delete.cpp

#include <iostream>
#include <string>

using std::cout; 
using std::cin;
using std::endl;
using std::string;

string * getname(void);

signed int main(void)
{
       string * name;
       name = getname();
       // name isn't displayed -- it's the address of name
       cout << (*name) << " at " << name << endl;
       
       name = getname();
       cout << (*name) << " at " << name << endl;
       
       cin.get();
       
       return 0;
}

string * getname(void)
{
       string *temp = new string("");
       cout << "\nEnter last name: ";
       getline(cin, (*temp)); 
       return temp;
}


```

---

### Post by mdurham on 2009-04-23
After 'name' is finished with each time I think it should be deleted, the method you use is a very messy way of doing things because main() must have knowledge of the internals of another function (getname()).
Anyway, as it stands, you should have two 'delete name' lines in main(), I'll leave it to you to work out where to put them.
Cheers, Mike

---

### Post by eye208 on 2009-04-23
> **Kolmogorov said:**
> I don't understand why this isn't working!
It's because you are screwing with pointers when there's no need to do so. Here's your program translated to C++:
```
// delete.cpp

#include <iostream>
#include <string>

using std::cout;
using std::cin;
using std::endl;
using std::string;

string getname();

int main()
{
       string name;

       name = getname();
       cout << name << " at " << &name << endl;

       name = getname();
       cout << name << " at " << &name << endl;

       cin.get();

       return 0;
}

string getname()
{
       string temp;

       cout << endl << "Enter last name: ";
       cin >> temp;

       return temp;
}
```
Seriously, the whole point of using C++ instead of C is to get rid of pointers and manual resource management.

---

### Post by dwhitney67 on 2009-04-23
> **eye208 said:**
> ...Here's your program translated to C++:
...

Very funny!   :lolflag:

I've got to remember to quote you again should I find the need to help someone with their "C++" application.  It must be that courses and/or tutorials spend too much time discussing the similarities between C++ and C programming, that inevitably C programming techniques creep into the C++ example programs.

One thing I have enjoyed with C++ is the very infrequent need to allocate anything manually.  I leave that to the STL containers.  Similarly, I do not deal with pointers too often; I pass pretty much pass objects by reference when calling a function.

---

