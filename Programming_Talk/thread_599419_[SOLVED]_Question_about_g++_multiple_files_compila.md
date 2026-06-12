---
title: "[SOLVED] Question about g++ multiple files compilation"
date: 2007-11-01
forum: Programming Talk
---

### Post by leileicats on 2007-11-01
Just a simple, whilst unexpected compilation error:

I have three simple files:
1, **[COLOR="Red"]main.cpp[/COLOR]**
```
#include <iostream>
using namespace std;
#include "helloworld.h"

int main(){
  hello_world();
  return 0;
}
```
2, [COLOR="Red"]**helloworld.h**[/COLOR]
```
#ifndef _HELLOWORLD_H
#define _HELLOWORLD_H

#include <iostream>
using namespace std;

void hello_world();

#endif
```
3,[COLOR="Red"]**helloworld.cpp**[/COLOR]
```
#include "helloworld.h"

void hello_world(){
     cout << "Hello World!\n";
}
```

When I was trying to compile, I got this error:
```
lei@maverick:~/code/example/HelloWorld$ g++ -o main main.cpp helloworld.h
/tmp/ccixBBMs.o: In function `main':
main.cpp:(.text+0x84): undefined reference to `hello_world()'
collect2: ld returned 1 exit status
```

I guess there is something wrong with the function prototype, but I can't find it.:confused:

---

### Post by slavik on 2007-11-01
1. don't use "using namespace std;" in header files
2. include header files BEFORE "using namespace std;" line in main.cpp
3. your compile line should be "g++ -o hello main.cpp helloworld.cpp"

---

### Post by Kadrus on 2007-11-01
> **slavik said:**
> 1. don't use "using namespace std;" in header files
2. include header files BEFORE "using namespace std;" line in main.cpp
3. your compile line should be "g++ -o hello main.cpp helloworld.cpp"

your compile should be g++ hello main.cpp
without the -o

---

### Post by leileicats on 2007-11-01
> **slavik said:**
> 1. don't use "using namespace std;" in header files
2. include header files BEFORE "using namespace std;" line in main.cpp
3. your compile line should be "g++ -o hello main.cpp helloworld.cpp"

I removed "using namespace std;" from "helloworld.h", and then include "#include "helloworld.h" BEFORE "using namespace std;" line in main.cpp
```
#include "helloworld.h"
#include <iostream>
using namespace std;
```
The result after compiling as shown:
```
lei@maverick:~/code/example/HelloWorld$ g++ -o main main.cpp helloworld.cpp
helloworld.cpp: In function &#8216;void hello_world()&#8217;:
helloworld.cpp:6: error: &#8216;cout&#8217; was not declared in this scope

```

It seems that the code don't know about "iostream" before compiling function "void hello_world()". This is weired. So I have to add:

[B][COLOR="Blue"]#include <iostream>
using namespace std;[/COLOR][/B]


```
#include "helloworld.h"
#include <iostream>
using namespace std;

void hello_world(){
     cout << "Hello World!\n";
}
```
Then it works! But it is tedious if I need add "iostream" library in every source file.

---

### Post by hod139 on 2007-11-01
> **Kadrus said:**
> your compile should be g++ hello main.cpp
without the -o

This is wrong advice, slavik was correct.  The -o flag tells g++ to name the executable hello.

---

