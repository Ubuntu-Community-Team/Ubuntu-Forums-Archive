---
title: "Error on decimal input C++"
date: 2010-07-20
forum: Programming Talk
---

### Post by patrickaupperle on 2010-07-20
I have created a C++ program to solve combinations and permutations, but I can't seem to make it give a nice error when you enter a decimal number.
Here is my code
[PHP]
#include <iostream>
using namespace std;

int factorial(int x)
{
    int num = 1;
    while (x != 0)
        num = num * x--;
    return num;
}

double permutation(int a, int b)
{
    return (factorial(a)/factorial(a-b));
}

double combination(int a, int b)
{
    return (factorial(a)/(factorial(b)*factorial(a-b)));
}

int main() 
{
    cout << "Enter A: ";
    int a;
    cin >> a;
    while (cin.fail()) {
        cin.clear();
        cin.ignore(256,'\n');
        cerr << "Invalid Input!" << endl;
        cout << "Enter A: ";
        cin >> a;
    }
    cout << "Enter B: ";
    int b;
    cin >> b;
    while (cin.fail()) {
        cin.clear();
        cin.ignore(256,'\n');
        cerr << "Invalid Input!" << endl;
        cout << "Enter B: ";
        cin >> b;
    }  
    if (b > a) {
        cerr << "B is greater than A" <<  endl;
        return 1;
    }
    cout << "Enter 'P' for Permutation or 'C' for Combination: ";
    char c;
    cin >> c;
    if (c == 'p' || c == 'P')
        cout << permutation(a,b) << endl;
    else if (c == 'c' || c == 'C')
        cout << combination(a,b) << endl;
    else 
        cerr << "You entered something other than 'P' or 'C'!" << endl;
}
[/PHP]

Can somebody show me how to print an error when a decimal is entered?
Also, I welcome any other corrections/improvements.

---

### Post by dwhitney67 on 2010-07-20
I'm not sure what you mean by "decimal" input, but you probably mean floating-point input, for example 5.0 vs 5

I use the following to get input:
```

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

```


Usage is something like:
```

int  value = getInput<int>("Enter a number: ");
char ch    = getInput<char>("Enter a single character: ");

... 


```
The getInput() method will check for input errors.

---

### Post by patrickaupperle on 2010-07-20
> **dwhitney67 said:**
> I'm not sure what you mean by "decimal" input, but you probably mean floating-point input, for example 5.0 vs 5

I use the following to get input:
```

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

```


Usage is something like:
```

int  value = getInput<int>("Enter a number: ");
char ch    = getInput<char>("Enter a single character: ");

... 


```
The getInput() method will check for input errors.

Your code works, but I still don't really understand why mine doesn't. Thank you,but I'd really like to learn what I did wrong. Can you, or somebody else, explain why my code doesn't work?

Edit:
It would seem that my program reads input up to the decimal point, and then the second time it reads everything after the decimal. 

Here is my solution (based on your code): 
[php]
 #include <iostream>
using namespace std;

int factorial(int x)
{
    int num = 1;
    while (x != 0)
        num = num * x--;
    return num;
}

double permutation(int a, int b)
{
    return (factorial(a)/factorial(a-b));
}

double combination(int a, int b)
{
    return (factorial(a)/(factorial(b)*factorial(a-b)));
}

int main() 
{
    cout << "Enter A: ";
    int a = 0;
    cin >> a;
    while (cin.fail() || cin.peek() != '\n') {
        cin.clear();
        cin.ignore(256,'\n');
        cerr << "Invalid Input!" << endl;
        cout << "Enter A: ";
        cin >> a;
    }
    cout << "A = " << a << endl;
    cout << "Enter B: ";
    int b = 0;
    cin >> b;
    while (cin.fail() || cin.peek() != '\n') {
        cin.clear();
        cin.ignore(256,'\n');
        cerr << "Invalid Input!" << endl;
        cout << "Enter B: ";
        cin >> b;
    }  
    cout << "B = " << b << endl;
    if (b > a) {
        cerr << "B is greater than A" <<  endl;
        return 1;
    }
    cout << "Enter 'P' for Permutation or 'C' for Combination: ";
    char c;
    cin >> c;
    if (c == 'p' || c == 'P')
        cout << permutation(a,b) << endl;
    else if (c == 'c' || c == 'C')
        cout << combination(a,b) << endl;
    else 
        cerr << "You entered something other than 'P' or 'C'!" << endl;
}
[/php]

Thank you. Your example did give me the answer.

Edit 2: I guess I would have been better off just throwing your function into my program. Oh well, this way, I understand what is going on now.

---

