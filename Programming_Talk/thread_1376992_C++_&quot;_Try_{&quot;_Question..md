---
title: "C++ &quot; Try {&quot; Question."
date: 2010-01-09
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-01-09
Hokay so this is a seemingly basic question. Im attempting to limit a persons input so that if they put in a string instead of number, and error occurs, the program won't end. 

Was using python before and was wondering how to convert it into a C++ code. 

This is what i have so far.

[php]
    while (x==0) {
          try {
              //Enter some cin code here
              x++ //Assuming that this code wouldnt work UNLESS the cin didn't result in error.
              }
          except ValueError // The python code that would go here. (From my limited experience.)
          
[/php]
Also have 2 more questions, 1 of which deals with user input again.

1:What do i do if I want to limit user input to a specific # of characters? (Could google this one BUT I'm already making a thread so yea)

2:How would I be able to extract 2 numbers from one input.

cin >>xy // entered in the form x,y

and i want to extract the x and the y seperately.

---

### Post by kwyto on 2010-01-10
try {...} catch(...) {...}  
check this : [http://www.java2s.com/Tutorial/Cpp/0120__Exceptions/0020__try-catch.htm](http://www.java2s.com/Tutorial/Cpp/0120__Exceptions/0020__try-catch.htm)
 
cin >> x >> y; // to read x and y

---

### Post by dwhitney67 on 2010-01-10
I don't think you need the try-catch(es).

Something like this would suffice:
```

#include <iostream>

int main()
{
  using namespace std;

  int  x, y;
  bool inputGood = false;

  do
  {
     cout << "Enter two numbers, separated by a white-space: ";
     cin >> x >> y;

     inputGood = cin.good();

     if (!inputGood)
     {
       cerr << "Damn it... I said to enter two numbers!\n" << endl;
       cin.clear();
       cin.ignore(1024, '\n');
     }
  } while (!inputGood);

  // do something with the two numbers
  ...
}

```

---

### Post by MadCow108 on 2010-01-10
but you can use exceptions by setting the exception flag for the stream:
[http://www.cplusplus.com/reference/iostream/ios/exceptions/](http://www.cplusplus.com/reference/iostream/ios/exceptions/)

---

