---
title: "C++ Header help"
date: 2006-12-12
forum: Programming Talk
---

### Post by rekahsoft on 2006-12-12
Hi all, i am new to C++ but have been loving it. I have question about headers in C++. Say i define a class (or struct) like the following:```
#ifndef _the_example_H
#define _the_example_H
#include <string>
#include <iostream>

using std::cout;
using std::endl;
using std::string;

class the_example {
     the_example() : output("") {}
     the_example(string str) : output(str) {}
     void show_output() {
          cout << output << endl;
     }
     private:
          string output;
};
#endif
```As you see the class is defined within the header. Is this proper? Also if it is not proper what is the right way to do it? How do you define a the class outside the header then make a header for the class? Thanks you for your help :)

---

### Post by thumper on 2006-12-13
* Don't put using declarations in header files.
* Also the default access specifier for classes is private, so your class above isn't creatable.  My guess is that it was a struct before you pasted the example.

Here is how I'd do it.

Header file example.hpp:
```
#ifndef example_class_hpp
#define example_class_hpp

#include <string>
#include <iosfwd>

class the_example
{
  public:
    the_example(std::string const& output);
    // copy constructor not needed as default is fine
    void show_output(std::ostream& out) const;
  private:
    std::string output_;    
};
#endif
```

Source file example.cpp:
```
#include "example.hpp"
#include <ostream>

the_example::the_example(std::string const& output)
  : output_(output)
{}

void the_example::show_output(std::ostream& out) const
{
  out << output_ << '\n';
}

```

main.cpp
```
#include "example.hpp"
#include <iostream>

int main()
{
   my_example foo("Hello World");
   std::cout << foo;
}
```

Compile with 
```
g++ -o example example.cpp main.cpp
```

---

### Post by rekahsoft on 2006-12-13
I wrote that example. I just made a little mistake. Why should there be no uses of using declarations in a header? Is it just proper or is there a reason? So the declaration of the class or struct goes in the header and then i define what i have declared in a source file; right? Thanks for the help

---

