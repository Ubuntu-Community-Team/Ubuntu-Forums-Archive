---
title: "[SOLVED] C++ Is Wierd"
date: 2008-08-12
forum: Programming Talk
---

### Post by Mr.Macdonald on 2008-08-12
test.cc
[PHP]#include <iostream>

int main(int argc, char * argv[]) {
	std::cout << "argc = " << argc << std::endl;
	std::cout << "argv[1] = " << argv[1] << std::endl;
	std::cout << "argv[1] length = " << sizeof(argv[1])/sizeof(char)+1 << std::endl;
	
	return 0;
}[/PHP]
```
$ g++ test.cc -o test
$ ./test hello
argc = 2
argv[1] = hello
argv[1] length = 5
$ ./test hello.txt
argc = 2
argv[1] = hello.txt
argv[1] length = 5

```

Um What??

---

### Post by Lster on 2008-08-12
sizeof gives the size of that data type, which in your case is a char pointer. For a 32bit machine this is 4bytes... So sizeof returns 4, which you divide by sizeof(char) which is usually 1 and add 1. Answer = 5! :KS

I think what you want to do is import cstring and use strlen to find the length.

---

### Post by dwhitney67 on 2008-08-12
> **Lster said:**
> sizeof gives the size of that data type, which in your case is a char pointer. For a 32bit machine this is 4bytes... So sizeof returns 4, which you divide by sizeof(char) which is usually 1 and add 1. Answer = 5! :KS

I think what you want to do is import cstring and use strlen to find the length.
Bingo!  Good answer!

---

### Post by SledgeHammer_999 on 2008-08-12
> **Lster said:**
> sizeof gives the size of that data type, which in your case is a char pointer. For a 32bit machine this is 4bytes... So sizeof returns 4, which you divide by sizeof(char) which is usually 1 and add 1. Answer = 5! :KS

I think what you want to do is import cstring and use strlen to find the length.

I think he means **include** instead of **import** (#include)

EDIT:And since it is C++ you better include "string" and not "cstring"

EDIT2: String reference-->[http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/) use the "length" method

---

### Post by happysmileman on 2008-08-12
> **SledgeHammer_999 said:**
> I think he means **include** instead of **import** (#include)

EDIT:And since it is C++ you better include "string" and not "cstring"

EDIT2: String reference-->[http://www.cplusplus.com/reference/string/string/](http://www.cplusplus.com/reference/string/string/) use the "length" method

No he needs cstring to do thing because argv[1] is a char array, not a C++ string

---

### Post by dwhitney67 on 2008-08-12
The OP can use whichever is more convenient, <cstring> or <string>.

For the first case:
[PHP]#include <cstring>

...

size_t strLen = strlen( argv[1] );[/PHP]

For the second case:
[PHP]#include <string>

...

size_t strLen = std::string( argv[1] ).length();   // or use size()
[/PHP]

---

