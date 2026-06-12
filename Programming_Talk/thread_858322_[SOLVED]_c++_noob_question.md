---
title: "[SOLVED] c++ noob question"
date: 2008-07-13
forum: Programming Talk
---

### Post by YellowSnot on 2008-07-13
I'm trying to learn the basics of c++. I'm trying to seperate my class code from my main code. Unfortunately the author of the book I'm reading apparently didn't feel this was necessary, and didn't give any examples of it. I've read a couple of tutorials, and still can't get it to work right. Here are my 3 source files:

Main.cpp :
```
#include <iostream>
#include "Website.h"

int main () {
  Website test(10);
  std::cout << test.getId();
  return 0;
}
```

Website.cpp :
```
class Website {
  int id;

public:
  Website ();
  Website (int);
  int getId();
};

Website::Website () {}

Website::Website (int i) {
  id = i;
}

int Website::getId() {
  return id;
}
```

and Website.h :
```
#ifndef WEBSITE_H
#define WEBSITE_H

int getId();

#endif
```

When I try to compile I get these errors:
```
theo@falcon:~/programs/Test$ g++ Main.cpp Website.cpp
Main.cpp: In function ‘int main()’:
Main.cpp:8: error: ‘Website’ was not declared in this scope
Main.cpp:8: error: expected `;' before ‘test’
Main.cpp:10: error: ‘test’ was not declared in this scope
```

What am I doing wrong here?

---

### Post by Mordred on 2008-07-13
Within the file Main.cpp the compiler has no notion of what a 'Website' is.
You should put your class declaration in the header file (Website.h).

Also, don't forget to include Website.h from Website.cpp

Good luck

---

### Post by Npl on 2008-07-13
try it that way:

Website.cpp :
```

#include "Website.h"

Website::Website () {}

Website::Website (int i) {
  id = i;
}

int Website::getId() {
  return id;
}
```

put the whole class declaration in the header.
Website.h :
```
#ifndef WEBSITE_H
#define WEBSITE_H

class Website {
  int id;

public:
  Website ();
  Website (int);
  int getId();
};

#endif
```

---

### Post by Mordred on 2008-07-13
And you might want to construct your Website test in Main.cpp in this way:

```
Website test = new Website(10);

```

---

### Post by Npl on 2008-07-13
> **Mordred said:**
> And you might want to construct your Website test in Main.cpp in this way:

```
Website test = new Website(10);

```err, unless you need dynamic allocation thats a bad idea.
Its better (and faster) to just use the stack instead of heap-allocations.

---

### Post by YellowSnot on 2008-07-13
Thanks, I had the class declaration in the header file earlier, but hadn't included Website.h in Website.cpp. I was under the assumption the compiler automatically included it for some reason. Its working now!

---

### Post by nvteighen on 2008-07-13
In summary:

Header files define an interface, just ways to access things from a source code: you should just write declarations in them (It's the way the compiler knows about the API...).

Source files define the implementation, the way things work.

Try always to keep interface & implentation separate. It easies things up when problems arrive, at least in my humble experience (with C, not C++; but in this case, it's the same).

---

