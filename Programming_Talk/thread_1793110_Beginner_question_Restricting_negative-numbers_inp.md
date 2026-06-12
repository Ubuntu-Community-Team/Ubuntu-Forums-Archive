---
title: "Beginner question: Restricting negative-numbers input into unsigned types?"
date: 2011-06-29
forum: Programming Talk
---

### Post by abraxyz on 2011-06-29
```
#include <iostream>
int main()
{
   unsigned long n;
   cout << "Enter a positive number: ";
   while (!(cin >> n))
   {
      cin.clear();
      while (cin.get() != '\n')
         continue;
      cout << "Try again: ";
   }
   return 0;
}
```So, here I have a defense against bad input, but how do I set the limit on entering negative numbers? As long as the user enters a number below 0, it goes past the reset point for unsigned long type, subtracts that number from 4294967296 (depending on implementation), and assigns it to n.

---

### Post by Petrolea on 2011-06-29
Look for cin.fail(). It checks whether the input from a user fits into that variable.

---

### Post by dwhitney67 on 2011-06-29
You could opt to capture the input as a string.  If this string contains a non-numeric character, then you can assume it is invalid input.  Otherwise, an attempt can be made to convert it to an unsigned int.

Here's a test program that has not been fully tested for all scenarios:
```

#include <iostream>
#include <string>
#include <sstream>

int main()
{
   unsigned long n;

   for (;;)
   {
      std::string input;

      std::cout << "Enter a positive number: ";
      std::getline(std::cin, input);

      if (input.find_first_not_of("0123456789") == std::string::npos)
      {
         std::stringstream iss(input);

         if (iss >> n)
         {
            break;
         }
      }

      std::cerr << "Bad input given!\n" << std::endl;
      std::cin.clear();
   }

   std::cout << "Success; you entered: " << n << std::endl;
}

```

---

### Post by nvteighen on 2011-06-29
As a general rule of thumb, underlying dwhitney67's post and also valid for other languages, consider strings as a "raw" format where you can do all kind of tests before converting its content to any kind of data. This means "test before converting".

---

### Post by cgroza on 2011-06-29
I would check if the first non white space character equals a "-".

---

### Post by dwhitney67 on 2011-06-29
> **cgroza said:**
> I would check if the first non white space character equals a "-".

It's a little more complicated than that.  What if the '-' is in the middle of the input?  For example, "123-456".

---

### Post by Uubnewb on 2011-06-30
Not to hijack the thread, but could someone please explain this:
> 
if (input.find_first_not_of("0123456789") == std::string::npos)
      {
         std::stringstream iss(input);

         if (iss >> n)
         {
            break;
         }
      }


I'm only asking because my personnal solution would be something like this:
```

int main()
{
   unsigned long n;
   long temp; // note not unsigned.

   for (;;)
   {
      std::cout << "Enter a positive number: ";
      std::cin >> temp;

      if (temp < 0)
      {
         std::cout << "A positive number is one without the funny line in front of it.";
         break;
      }
      else
      {
         n = temp;
      }
   }
}

```

---

### Post by dwhitney67 on 2011-06-30
> **Uubnewb said:**
> Not to hijack the thread, but could someone please explain this:


A long type (at least on my 32-bit system), occupies 4 bytes, or 32-bits.  The most significant bit is reserved for the sign bit, thus only leaving 31-bits to hold the value.  With an unsigned long, one is able to use the msb for something other than the sign bit, thus allowing for the storage of a larger number.

Here's a little program for you to play with:
```

#include <iostream>
#include <limits>

int main()
{
   std::cout << "Max long : " << std::numeric_limits<long>::max()          << "\n"
             << "Min long : " << std::numeric_limits<long>::min()          << "\n"
             << "Max ulong: " << std::numeric_limits<unsigned long>::max() << "\n"
             << "Min ulong: " << std::numeric_limits<unsigned long>::min()
             << std::endl;
}

```
The results on a 32-bit system:
```

Max long : 2147483647
Min long : -2147483648
Max ulong: 4294967295
Min ulong: 0

```

P.S.  Your approach to solving the problem would fail if the user enters a "valid" value of 2147483648.

---

