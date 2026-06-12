---
title: "g++ is broken"
date: 2009-11-15
forum: Programming Talk
---

### Post by helino on 2009-11-15
[SOLUTION] A shut down and then power on fixed it [/SOLUTION]

hi,

my g++ just broke down :( I don't know how I did it, I was playing around with qt creator installed from the repos, developing a basic video player with phonon, and then suddenly my code didn't compile anymore.

Right now, when I'm trying to compile the following program:
```

#include <iostream>

int main()
{
    std::cout << "hello world" << std::endl;
    return 0;   
}

```

I get the following output from g++:
```

In file included from /usr/include/c++/4.4/ios:40,
                 from /usr/include/c++/4.4/ostream:40,
                 from /usr/include/c++/4.4/iostream:40,
                 from hello.cpp:1:
/usr/include/c++/4.4/exception: In constructor ‘std::exception::exception()’:
/usr/include/c++/4.4/exception:62: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.4/README.Bugs> for instructions.

```

Can anyone help with me this? I've tried to reinstall g++,libc6-dev and removed qtcreator, but nothing helps..

Thanks in advance!

---

