---
title: "problem with C++ and strings.."
date: 2007-11-07
forum: Programming Talk
---

### Post by Khao on 2007-11-07
I can't figure out what's the problem with this : (don't mind all the server-related things, the only thing I have problem with is getting strings to work)
```
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
//#include "include/Server.hpp"

#define PORT 1990   // port we're listening on

int main()
{
        string MyString("hello");
        //MyString= Encrypt(MyString);
        printf("here's a string : %s\r", MyString);
        return 0;
[... lots of code that works and is not using strings ... ]
}

```
the error I get when I try to compile is this :
```
Server.cpp: In function âint main()â:
Server.cpp:15: error: 'string' was not declared in this scope
Server.cpp:15: error: expected `;' before 'MyString'
Server.cpp:16: error: 'MyString' was not declared in this scope

```
I'm a noob so please help me :(
Thank you!

---

### Post by aks44 on 2007-11-07
0. <string.h> is a non standard header. Use <string>

1. do you know what are namespaces? **string** belongs to the std namespace, ie. it must be written **std::string**

2. **printf** is not C++, it's C. Use **std::cout** :
```
#include <iostream> // also includes <string>
int main()
{
  std::string str = "Hello world!";
  std::cout << "I'm saying: " << str << std::endl;
  return 0;
}
```

If you really MUST use printf (why would you?) you gotta remember that %s requires a (const?) char*, so you have to use str.c_str()

And BTW, line-feed is \n, carriage-return is \r, on *nix only \n is needed to get a new line. Unless you wanted to go back to first column without actually having a new line.

---

### Post by Khao on 2007-11-07
Thank you very much :) As I said, I'm a noob, this messy thing came from trying to make it work using a lot of different source codes and things and it got all messy :P

---

### Post by aks44 on 2007-11-07
Maybe you may want to read this [very short introduction into namespaces]("http://www.winterdom.com/dev/cpp/nspaces.html")?

---

### Post by Khao on 2007-11-07
that's pretty useful, but I'm having another little problem here : how do I use methods and functions with a string object? I tried MyString.lenght() as it showed in a tutorial and it returned this error : 
 error: 'truct std::string' has no member named 'lenght'

---

### Post by aks44 on 2007-11-07
> **Khao said:**
> I tried MyString.lenght() as it showed in a tutorial and it returned this error : 
 error: 'truct std::string' has no member named 'lenght'

Because it is named leng**th**() not leng**ht**() ;)

---

### Post by Khao on 2007-11-07
haha that's silly of me :P thank you very much!

---

