---
title: "Compiling a C++ Program"
date: 2013-10-03
forum: Programming Talk
---

### Post by fernando6 on 2013-10-03
Hi, everyone! Sorry if this post is in the wrong subforum. I'm trying to compile the following C++ program, called hello.cc, from the command-line:

```
#include <iostream>

int main()
{
    using namespace std;
    
    cout << "Hello world!";
    
    return 0;
}
```

I'm using the command **CC hello.cc**, but the computer tells me the command was not found. I'm trying to use this program because I want to use the Solaris C++ compiler, and, from what I've researched, this is the one, and the cc program is the C compiler, am I correct? If I am, how do I properly install CC? I don't want to use GCC. Thanks in advance!

---

### Post by whitesmith on 2013-10-03
> **fernando6 said:**
> I'm trying to use this program because I want to use the Solaris C++ compiler, and, from what I've researched, this is the one, and the cc program is the C compiler, am I correct?The one for what? Most of us use GCC. Can't help you with others, especially commercial stuff. Also, this thread belongs elsewhere. Good luck to you!

---

### Post by Iowan on 2013-10-03
Moved to Programming Talk.

---

### Post by r-senior on 2013-10-03
Don't worry about the compiler, worry about the language. If you are using Ubuntu, or any other Linux distribution, just use the default GNU compiler:

```
g++ hello.cc -o hello
```

---

### Post by 3v3rgr33n on 2013-10-04
I agree with r-senior, stick with g++ Here's a simple tutorial to get started [http://www.vietspring.org/cpp_linux/gpp.html](http://www.vietspring.org/cpp_linux/gpp.html) . I'm sure you can find other tutorials through Google.

---

