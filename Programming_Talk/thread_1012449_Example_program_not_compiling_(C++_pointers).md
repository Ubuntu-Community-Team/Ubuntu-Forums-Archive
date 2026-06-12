---
title: "Example program not compiling (C++ pointers)"
date: 2008-12-15
forum: Programming Talk
---

### Post by Miles_Prower on 2008-12-15
As the title suggests, I've got a sample program from a book that will not compile. 

So, here's the code:
```

// VariableSize - output the size of each type of
//                variable
#include <cstdio>
#include <cstdlib>
#include <iostream>
using namespace std;
int main(int nNumberofArgs, char* pszArgs[])
{
  bool   b;
  char   c;
  int    n;
  long   l;
  float  f;
  double d;
  cout << “sizeof a bool =  “  << sizeof b << endl;
  cout << “sizeof a char =  “ << sizeof c << endl;
  cout << “sizeof an int =  “ << sizeof n << endl;
  cout << “sizeof a long =  “ << sizeof l << endl;
  cout << “sizeof a float = “ << sizeof f << endl;
  cout << “sizeof a double= “ << sizeof d << endl;
  // wait until user is ready before terminating program
  // to allow the user to see the program results
  system(“PAUSE”);
  return 0;
}
```

, And here's the output I get when I try to compile it:

```

taels@tornado:~/code$ g++ main.cpp
main.cpp:15: error: stray ‘\342’ in program
main.cpp:15: error: stray ‘\200’ in program
main.cpp:15: error: stray ‘\234’ in program
main.cpp:15: error: stray ‘\342’ in program
main.cpp:15: error: stray ‘\200’ in program
main.cpp:15: error: stray ‘\234’ in program
main.cpp:16: error: stray ‘\342’ in program
main.cpp:16: error: stray ‘\200’ in program
main.cpp:16: error: stray ‘\234’ in program
main.cpp:16: error: stray ‘\342’ in program
main.cpp:16: error: stray ‘\200’ in program
main.cpp:16: error: stray ‘\234’ in program
main.cpp:17: error: stray ‘\342’ in program
main.cpp:17: error: stray ‘\200’ in program
main.cpp:17: error: stray ‘\234’ in program
main.cpp:17: error: stray ‘\342’ in program
main.cpp:17: error: stray ‘\200’ in program
main.cpp:17: error: stray ‘\234’ in program
main.cpp:18: error: stray ‘\342’ in program
main.cpp:18: error: stray ‘\200’ in program
main.cpp:18: error: stray ‘\234’ in program
main.cpp:18: error: stray ‘\342’ in program
main.cpp:18: error: stray ‘\200’ in program
main.cpp:18: error: stray ‘\234’ in program
main.cpp:19: error: stray ‘\342’ in program
main.cpp:19: error: stray ‘\200’ in program
main.cpp:19: error: stray ‘\234’ in program
main.cpp:19: error: stray ‘\342’ in program
main.cpp:19: error: stray ‘\200’ in program
main.cpp:19: error: stray ‘\234’ in program
main.cpp:20: error: stray ‘\342’ in program
main.cpp:20: error: stray ‘\200’ in program
main.cpp:20: error: stray ‘\234’ in program
main.cpp:20: error: stray ‘\342’ in program
main.cpp:20: error: stray ‘\200’ in program
main.cpp:20: error: stray ‘\234’ in program
main.cpp:23: error: stray ‘\342’ in program
main.cpp:23: error: stray ‘\200’ in program
main.cpp:23: error: stray ‘\234’ in program
main.cpp:23: error: stray ‘\342’ in program
main.cpp:23: error: stray ‘\200’ in program
main.cpp:23: error: stray ‘\235’ in program
main.cpp: In function ‘int main(int, char**)’:
main.cpp:15: error: ‘a’ was not declared in this scope
main.cpp:15: error: expected `;' before ‘bool’
main.cpp:16: error: expected `;' before ‘char’
main.cpp:17: error: ‘an’ was not declared in this scope
main.cpp:17: error: expected `;' before ‘int’
main.cpp:18: error: expected `;' before ‘long’
main.cpp:19: error: expected `;' before ‘float’
main.cpp:20: error: expected `;' before ‘double’
main.cpp:23: error: ‘PAUSE’ was not declared in this scope
taels@tornado:~/code$ 
```

I'm not familiar with the (stray ‘\235’) variety of error, and this is supposed to be an example of FUNCTIONAL code, but I can't help but think this kind of thing would have been caught before it was published...


Could someone who has experience with pointers tell me who's at fault, me or the book?

---

### Post by jimi_hendrix on 2008-12-15
isnt it sizeof(foo)?

---

### Post by Miles_Prower on 2008-12-15
changing it all to sizeof(variable) still returns the same errors.

---

### Post by jimi_hendrix on 2008-12-15
i realize this wont solve the problem with the book program but try

sizeof(bool)

and stuff like that instead of the variables

---

### Post by Miles_Prower on 2008-12-15
ok, i got it compiling. For some reason those quotation mark looking things aren't quotation marks, they're... well, whatever they are, I replaced them with quotation marks and removed system("PAUSE") (which i'm pretty sure is a windows command). and the program compiled and ran.

Thanks for the help.

---

### Post by jimi_hendrix on 2008-12-15
they are `ticks i think` and yes PAUSE is windows (just tried it)

---

### Post by jimi_hendrix on 2008-12-15
btw im guessing your a sonic fan?

---

### Post by Miles_Prower on 2008-12-15
Good catch. The dlna/fileserver's named 'icecap' to boot.

---

### Post by jimi_hendrix on 2008-12-15
heh i loved sonic when i was 6...and the early SEGA games were great...but now...ya...

i only recently figured out that miles prower = miles per hour

---

