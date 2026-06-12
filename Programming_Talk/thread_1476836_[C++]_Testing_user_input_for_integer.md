---
title: "[C++] Testing user input for integer"
date: 2010-05-08
forum: Programming Talk
---

### Post by dodle on 2010-05-08
I'm coming from Python, so C++ is pretty confusing for me (although I finally figured out how to use "for" loops).  I'm trying to get a user to input a number, place that number into a string, then test the string to make sure that it is an integer.  

In Python it was as simple as:
[php]user_in = raw_input("Input a number: ")
try:
  num = int(user_in)
except:
  print "That is not a number"[/php]

But I don't know how to get C++ to throw an exception :icon_frown:.  Most of the tutorials that I have found show how to convert a string or char array to int using [color=red]stringstream[/color] and the [color=red]atoi[/color] function.  But neither of these throw an exception if the user inputs "f".

example using stringstream:
[php]string user_in;
int num;
cout << "Input a number: ";
cin >> user_in;
cout << endl;
stringstream ss[user_in]; //I guess here is where I am looking to throw an exception
ss >> num;[/php]That's just to demonstrate what I am trying to do.  I'm sure this has been asked before, but I am unable to find an answer.

So to sum up, basically I want to change a user's input from [color=green]"23"[/color] to [color=red]23[/color] and if the user inputs [color=green]"twenty-three"[/color] print out [color=green]"I'm sorry, that is not a number"[/color].

**Edit:** Oh, and I also found some info on using [color=red]typeinfo[/color], but that is not working for me either.

---

### Post by MadCow108 on 2010-05-08
streams by default set the fail,bad or eof bit on failure and do not throw exceptions
they can be checked with the good, bad, fail, eof functions:
[http://www.cplusplus.com/reference/iostream/ios/ios/](http://www.cplusplus.com/reference/iostream/ios/ios/)

alternatively you can also let them throw exceptions by opening the stream with an appropriate exception mask:
[http://www.cplusplus.com/reference/iostream/ios/exceptions/](http://www.cplusplus.com/reference/iostream/ios/exceptions/)

note you have to clear and flush the stream after a failure with clear() and ignore()

there is also boosts lexical_cast which does all for you:
[http://www.boost.org/doc/libs/1_43_0/libs/conversion/lexical_cast.htm](http://www.boost.org/doc/libs/1_43_0/libs/conversion/lexical_cast.htm)

---

### Post by dodle on 2010-05-08
I figured out what I wanted to do without throwing an exception.  Thank you.

[php]bool sisint(string a)
{
  bool cont = true;
  char store[a.length()]; //Store the characters from string
  for (int x = 0; x < a.length(); x += 1)
  {
    store[x] = a[x];
    if (isdigit(store[x]) == false)
      cont = false;
  }
  return cont;
}
[/php]
[http://www.cplusplus.com/forum/beginner/23504/](http://www.cplusplus.com/forum/beginner/23504/)

---

### Post by dwhitney67 on 2010-05-08
```

#include <string>
#include <iostream>
#include <limits>

template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T input;

   while (true) {
      // prompt user and attempt to read input
      cout << prompt;
      cin  >> input;

      // check if valid input given; break from loop if so.
      if (cin.peek() == '\n' && cin.good()) break;

      // user gave bad input; let them know about it.
      cout << "Invalid input!  Try again...\n" << endl;
      cin.clear();
      do { cin.ignore(numeric_limits<streamsize>::max(), '\n'); } while (!cin);
   }

   return input;
}

int main(void)
{
   int num  = getInput<int>("Enter a number: ");

   std::cout << "Your number is: " << num  << std::endl;
}

```

---

