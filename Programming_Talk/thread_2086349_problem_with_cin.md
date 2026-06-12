---
title: "problem with cin"
date: 2012-11-20
forum: Programming Talk
---

### Post by hatsoff on 2012-11-20
hi,
in my code there are 2 prompt statements in do- while loop,one prompt works fine to get string of characters but when it comes to take integer input by 2nd prompt it does not work ,just display statement and when i type i does not appear and program crashes
,[HTML]
do
            {
                
                cout << "Enter the book name  " << endl;
                getline(cin, book);
                cin.ignore() ;
                cout << "Enter the page number " << endl;//it prints and program crashes
                cin >> page;
                xxxx.xxxxx(book, page);//function
                cout << "do you want to add more : (y/n)";
                cin >> input;
            } while (input == 'y' || 'Y');
[/HTML]

---

### Post by dwhitney67 on 2012-11-20
See!  Your questions are getting better and better.

As for cin, it reads one object at a time.  If all you ask it to do is read a single inputted character, then you also have to instruct it to read the newline character that is also inputted.

For example:
```

char letter;
char number;

std::cout << "Enter any lowercase letter: ";
std::cin  >> letter;

std::cout << "Enter any number between 0-9: ";
std::cin  >> number;   <----- THIS WILL FAIL... because it will read the newline from the previous prompt.

```
Use std::getline() to ensure that you read the entire line; then convert the input to the desired format if necessary.  For example:
```

std::string input;
char letter;
char number;

while (true)
{
    std::cout << "Enter any lowercase letter: ";
    std::getline(std::cin, input);

    if ((input[0] >= 'a' && input[0] <= 'z') && std::cin.good())
    {
        letter = input[0];
        break;
    }
    else
    {
        std::cerr << "Bad input; try again...\n" << std::endl;
    }
}

while (true)
{
    std::cout << "Enter any number between 0-9: ";
    std::getline(std::cin, input);

    if ((input[0] >= '0' && input[0] <= '9') && std::cin.good())
    {
        number = input[0];
        break;
    }
    else
    {
        std::cerr << "Bad input; try again...\n" << std::endl;
    }
}

```
Of course, if you really required a number, and not a character representation of a number, then you would use istringstream to assist in parsing the number.  I'll save discussing this topic for another day.

P.S.  Here's a somewhat "advanced" program that shows, IMHO, a comprehensive, but not necessarily better way, to capture raw input from a user:
```

#include <string>
#include <iostream>
#include <limits>

template <typename T>
T getInput(const char* prompt)
{
   using namespace std;

   T    input;
   bool done = false;

   while (!done) {
      // prompt user and attempt to read input
      cout << prompt;
      cin  >> input;

      // check if valid input given; break from loop if so.
      if (cin.peek() == '\n' && cin.good())
      {
         done = true;
      }
      else
      {
         // user gave bad input; let them know about it.
         cout << "Invalid input!  Try again...\n" << endl;
         cin.clear();
      }

      do { cin.ignore(numeric_limits<streamsize>::max(), '\n'); } while (!cin);
   }

   return input;
}

int main(void)
{
   char        ch   = getInput<char>("Enter a char: ");
   std::string str1 = getInput<std::string>("Enter a string: ");
   int         num  = getInput<int>("Enter a number: ");
   std::string str2 = getInput<std::string>("Enter another string: ");

   std::cout << "Your char is        : " << ch   << std::endl;
   std::cout << "Your string is      : " << str1 << std::endl;
   std::cout << "Your number is      : " << num  << std::endl;
   std::cout << "Your other string is: " << str2 << std::endl;
}

```

---

### Post by hatsoff on 2012-11-22
i'll do practice and will try to understand it..thank u very much

---

