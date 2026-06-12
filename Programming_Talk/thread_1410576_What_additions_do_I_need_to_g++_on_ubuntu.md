---
title: "What additions do I need to g++ on ubuntu"
date: 2010-02-18
forum: Programming Talk
---

### Post by akvino on 2010-02-18
I just loaded latest Ubuntu and installed g++ (don't ask me how, did some apt-get install g++ or something to that extent).

I am coming from Fedora world in which I live daily, where C++ standard library recognises #include <string> statement.


I have #include <string> statement and when I compile this happens:

```

arrays.cpp: In function ‘int main()’:
arrays.cpp:11: warning: deprecated conversion from string constant to ‘char*’
arrays.cpp:13: error: ‘strlen’ was not declared in this scope

```

Then I went in and changed #include <string> to #include <string.h> and it compiles with a warning:

```

g++ arrays.cpp -o arrays
arrays.cpp: In function ‘int main()’:
arrays.cpp:11: warning: deprecated conversion from string constant to ‘char*’

```


Dear Ubuntu C++ gurus, dear visitors of this forum, respected programmers (since I hate word developers), what do I need to install, what library package, what update, in order to get latest - greates g++. 
So when I put in #include <string> it screams 'Yes Sir' instead of 'I dunno what you're trying to compile, me don't understand'.....


Thanks :-({|=

---

### Post by Simon17 on 2010-02-18
If you're compiling as c++, then the proper header is <cstring>, not <string.h>
<string> contains the class std::string.
The conversion error you are getting is because string literals, "like this", are to be declared const char*

---

### Post by sgosnell on 2010-02-19
Install build-essential.  That will install everything you need to preprocess, compile and make.

---

### Post by Simon17 on 2010-02-19
apt-get g++ will do it. Everything else you need is installed by default.

---

### Post by MadCow108 on 2010-02-19
that conversion was deprecated ages ago. It is not a problem of your version, but a (minor) coding mistake

use const char *as a type for string **const**ants or compile with -Wno-write-strings

and the right c string include is
#include <cstring>

---

