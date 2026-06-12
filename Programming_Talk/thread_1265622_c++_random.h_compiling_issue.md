---
title: "c++ random.h compiling issue"
date: 2009-09-13
forum: Programming Talk
---

### Post by EternallyNoob on 2009-09-13
Hello, all. I've joined a programming class in my high school, and the book they give us is 1. Old and 2. Is written for some common Windows compiler. So, obviously, I'm having some issues =/ The most recent one I can find NO fixes for is an issue with trying to use random.h. So originally my code went:
#include <iostream>
#include <random>
[PHP]
#include <iostream>
#include <random>
using namespace std;

int main() {
  for (int i=1; i<=10; i++)
    cout << random(100) << endl;
}
[/PHP]
I just compiled with "g++ random.cpp", and I got a TON of errors, almost all of which came from /usr/include/c++/4.3/tr1_impl/random.tcc. After a little bit of searching and some trial and error, I tried the following:
[PHP]
#include <iostream>
#include <cstdlib>

int main() {
  for (int i=1; i<=10; i++)
    std::cout << random(100) << std::endl;
}
[/PHP]
This only generated a few errors, so I figured it was closer to the "right" code.
```

/usr/include/stdlib.h: In function ‘int main()’:
/usr/include/stdlib.h:327: error: too many arguments to function ‘long int ran
dom()’                                                                       
randoms.cpp:6: error: at this point in file

```

Can anyone shed some light on this issue for me? Thanks in advance!

---

### Post by dribeas on 2009-09-13
Random (AFAIK) is not a standard header in either C or C++. In the stdlib.h (or cstdlib) headers, there is a random function that takes no arguments and returns a long int. My guess is that you have some header in your program that defines a random function taking an integer argument (maybe random.h) and that you are not including it. Else, the code is dependant on an specific compiler. If that is the case, ask what the semantics of the random function are and check how you can adapt. Knowing what the windows compiler is can help finding docs on that matter.

At any rate, the compiler is only seeing the 'long random()' function definition in stdlib.h and it is complaining about you passing an argument the function does not have.

---

### Post by Habbit on 2009-09-13
Random will be a standard header in the next version of C++, C++0x, and it is already available as a part of the Technical Report 1 (TR1). However, the procedure for including TR1 files differs between compilers. In g++, if you want the random file from tr1, you have to include tr1/random instead of just random. If you don't, libstdc++ interprets that you want C++0x support, which has to be explicitly enabled with -std=c++0x.

---

### Post by dribeas on 2009-09-14
I am assuming the OP is not dealing with the C++0x random header for two main reasons: it is stated in the question that the book is old and there is no random(int) function in the C++0x random header. That header provides many random number generators written as templated classes, and the OP code would not compile against those headers either. It looks more like either user code or a vendor extension.

---

### Post by Wistful on 2009-09-14
[PHP]
#include <iostream>
#include <cstdlib>
using namespace std;

int main()
{       int i, a[100], n;

        cout << "n="; cin >> n;
        srand(time(0)); // randomize
        for(i = 0; i<n; ++i)
                a[i] = rand()%100; //random from 0 to 99
        for(i = 0; i<n; ++i) 
                cout << a[i] << ' ';

        return 0;
}
[/PHP]

Take a look at **rand** and **srand** @ [http://www.cplusplus.com/reference/clibrary/cstdlib/](http://www.cplusplus.com/reference/clibrary/cstdlib/) && [http://members.cox.net/srice1/random/crandom.html](http://members.cox.net/srice1/random/crandom.html)

---

