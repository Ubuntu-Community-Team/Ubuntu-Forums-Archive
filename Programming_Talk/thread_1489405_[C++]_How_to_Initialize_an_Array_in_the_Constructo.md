---
title: "[C++] How to Initialize an Array in the Constructor"
date: 2010-05-21
forum: Programming Talk
---

### Post by dodle on 2010-05-21
I want to have an array as a class member, but the only way I know how to initialize the array in the constructor is by adding each element individually (array[x] = char).

[php]#include <iostream>
using namespace std;

class MyClass
{
  public:
    MyClass();
    ~MyClass();
    void PrintLetters(); // Prints each character in the array
  private:
    char alpha[3]; // Allocate memory for array
};

MyClass::MyClass()
{
    // Initialize the array
    alpha[0] = 'A';
    alpha[1] = 'B';
    alpha[2] = 'C';

    PrintLetters();
}

MyClass::~MyClass()
{
}

void MyClass::PrintLetters()
{
    for (int x = 0; x < 3; x += 1)
    {
        cout << alpha[x] << endl;
    }
}

int main()
{
    MyClass abc;
    abc;

    return 0;
}
[/php]

Is there another way to do it?  If I try to do it like this:
[php]MyClass::MyClass()
{
    // Initialize the array
    alpha[3] = {'A', 'B', 'C'};

    PrintLetters();
}[/php]

I get the following error:
```
$ g++ test.cpp -o test
test.cpp: In constructor &#8216;MyClass::MyClass()&#8217;:
test.cpp:17: error: expected primary-expression before &#8216;{&#8217; token
test.cpp:17: error: expected `;' before &#8216;{&#8217; token
```

The reason I ask is because I want an array with many more elements than three.

---

### Post by dodle on 2010-05-21
I figured out what I wanted to do using a [color=red]for[/color] loop:
[php]
string letters = "ABC";
for (int x = 0; x < sizeof(alpha); x +=1)
{
    alpha[x] = letters[x];
}[/php]

---

### Post by dwhitney67 on 2010-05-21
Why didn't you use an STL string???

```

#include <string>
#include <iostream>

class Foo
{
public:
   Foo() : str("ABC") {}

   friend std::ostream& operator<<(std::ostream& os, const Foo& f)
   {
      os << f.str;
      return os;
   }
private:
   std::string str;
};


int main()
{
   Foo f;

   std::cout << f << std::endl;
}

```
You can access each character of an STL string using the [] operator.  For example, to access the second element of the string shown above:
```

char ch = str[1];

```

---

### Post by nvteighen on 2010-05-21
> **dwhitney67 said:**
> Why didn't you use an STL string???


Because some people write C++ tutorials thinking C++ is C... and then people just use char * instead of std::string... *sigh*

---

### Post by dwhitney67 on 2010-05-21
> **dodle said:**
> I figured out what I wanted to do using a [color=red]for[/color] loop:
[php]
string letters = "ABC";
for (int x = 0; x < sizeof(alpha); x +=1)
{
    alpha[x] = letters[x];
}[/php]

Or this way:
```

#include <string>
#include <algorithm>
#include <iostream>

int main()
{
   std::string letters("ABC");
   char*       array = new char[letters.size() + 1];

   std::copy(letters.begin(), letters.end(), array);

   std::cout << array << std::endl;
}

```

---

