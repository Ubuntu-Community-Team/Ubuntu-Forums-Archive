---
title: "C++ - How to use std::string to get length of the string?"
date: 2015-04-21
forum: Programming Talk
---

### Post by flaymond on 2015-04-21
Hello, I still can't figure this out of how to get the value string length and save in a variable, in C++ like in Python.

C++ code:
```
#include <iostream>
#include <cstdlib>
#include <cstring>
#include <string>
using namespace std;

// Program that print strings backward


void revencrypt() {

    string translate;
    string message;
    int i;

    cout << "Please enter message to encrypt: ";
    cin >> message;

        output = "";
        i = std::string str(message) -1;            // This not working :(
                                                   // I want to save string length value in i, but not working. It produce error 'expected ";" in std::string<here> str(message)'
            while ( i >= 0)
                output = output + message[i];
            i = i - 1;
     cout << output << endl;
}

int main() {
 revencrypt();
return 0;
}


```

In Python, this code working:

```

def encrypt():
    message = raw_input ("Please enter your message to encrypt: ")
    if message != 0:
        output = ''
        i = len(message) -1            # This code not working in C++ program above
        while i >= 0:
            output = output + message[i]
            i = i - 1
    print (output)
    
 
def main()
encrypt()

main()             # code starts here
    

```

I expected the both program produce same output, Unfortunately, the data type and STL functions is confusing me in C++. I don't know which function or method will fix this out. Anyone can help? Thanks.

---

### Post by matt_symes on 2015-04-21
Hi

There are a number of things wrong with the program but to get it to compile and run for you i have highlighted the changes required.

Two of the problems are syntactic and one is semantic.

Work through my changes to understand what i have done. After that try to write it more succinctly and remove any cruft on the code.

```

#include <iostream>
#include <cstdlib>
#include <cstring>
#include <string>
using namespace std;

// Program that print strings backward
void revencrypt() {

    string translate;
    string message;
    int i;

    cout << "Please enter message to encrypt: ";
    cin >> message;

        **std:string output("");**
        **i = message.length() -1; **
            **while ( i >= 0) {**
                output = output + message[i];
                i = i - 1;
            **}**

     cout << output << endl;
}

int main() {
 revencrypt();
return 0;
}
```

And it running.

```

matthew-laptop:/home/matthew:1 % g++ t.cpp     
matthew-laptop:/home/matthew:1 % ./a.out 
Please enter message to encrypt: test
tset
matthew-laptop:/home/matthew:1 %
```

Kind regards

---

### Post by flaymond on 2015-04-21
Thanks! It's worked. I think I should explore the C/C++ libraries more often!

---

### Post by spjackson on 2015-04-21
> **InterProg said:**
> Thanks! It's worked. I think I should explore the C/C++ libraries more often!
Perhaps so. A more idiomatic C++ way of reversing a string might be:
```

#include <string>
#include <algorithm>
#include <iostream>

int main(int argc, char * argv[])
{
    if (argc > 1) {
        std::string output(argv[1]);
        std::reverse(output.begin(), output.end());
        std::cout << output << std::endl;
    }
}

```

---

### Post by matt_symes on 2015-04-21
Hi

> **spjackson said:**
> Perhaps so. A more idiomatic C++ way of reversing a string might be:
```

#include <string>
#include <algorithm>
#include <iostream>

int main(int argc, char * argv[])
{
    if (argc > 1) {
        std::string output(argv[1]);
        std::reverse(output.begin(), output.end());
        std::cout << output << std::endl;
    }
}

```

Yep :)

Kind regards

---

### Post by dwhitney67 on 2015-04-25
Another alternative is to use the std::string range constructor:
```

#include <string>
#include <iostream>

int main(int argc, char** argv)
{
    if (argc > 1)
    {
        std::string original(argv[1]);
        std::string reverse(original.rbegin(), original.rbegin() + original.length());

        std::cout << "original: " << original << "\n"
                  << "reverse : " << reverse  << std::endl;
    }
}

```

---

