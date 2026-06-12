---
title: "[SOLVED] C++ header files what am I doing wrong"
date: 2008-12-15
forum: Programming Talk
---

### Post by Tpolich on 2008-12-15
I am going to post files if you guys could point out what I am doing wrong it would be great.

file "main.cpp"
```

#include <iostream>
#include "stuff.h"



int main(){

	Cube gg;
	gg.show();

}

```

file "stuff.h"
```

#ifndef stuff_h
#define stuff_h


class Cube{

public:
	void show();


};

#endif

```

file "stuff.cpp"
```

#include <iostream>
#include "stuff.h"

void Cube::show(){

std::cout<< "come on work";
};

```

When I do 
```
g++ main.cpp -o test
```

yields 
```

/tmp/ccPAbXk8.o: In function `main':
main.cpp:(.text+0x194): undefined reference to `Cube::show()'
collect2: ld returned 1 exit status

```


What am I doing wrong. Thanks for the help in advance.

---

### Post by Max Carey on 2008-12-15
You have an extraneous semicolon in stuff.cpp at the end of the Cube::show definition. It should look like

```
#include <iostream>
#include "stuff.h"

void Cube::show(){

std::cout<< "come on work";
}
```

---

### Post by Sinkingships7 on 2008-12-15
Move the Cube::show() function from stuff.cpp into stuff.h and get rid of the semicolon at the end of it.

Is there any particular reason that you want to have a seperate stuff.cpp and stuff.h?

---

### Post by Tpolich on 2008-12-15
> **Max Carey said:**
> You have an extraneous semicolon in stuff.cpp at the end of the Cube::show definition. It should look like

```
#include <iostream>
#include "stuff.h"

void Cube::show(){

std::cout<< "come on work";
}
```

I always thought extra semicolons didn't mean anything in c++. I tried it without the semicolon, same error.

---

### Post by Tpolich on 2008-12-15
> **Sinkingships7 said:**
> Move the Cube::show() function from stuff.cpp into stuff.h and get rid of the semicolon at the end of it.

Is there any particular reason that you want to have a seperate stuff.cpp and stuff.h?

I am trying to figure out how to properly use header files in c++. If you have any idea where I could find a guide or if you could explain it I would appreciate it a lot.

---

### Post by mali2297 on 2008-12-15
Try compiling with
```

g++ main.cpp stuff.cpp -o test

```

---

### Post by ubuser_7 on 2008-12-15
You have to compile the class source file too, so it would be something like:

```

g++ stuff.cpp main.cpp -o test

```

---

### Post by Tpolich on 2008-12-15
> **mali2297 said:**
> Try compiling with
```

g++ main.cpp stuff.cpp -o test

```

It worked!!! thank you, now I have one more favor to ask "why did that work".

---

### Post by Sinkingships7 on 2008-12-15
> **Tpolich said:**
> It worked!!! thank you, now I have one more favor to ask "why did that work".

stuff.cpp is another source file, just like main.cpp. They way you were compiling it was only saying to compile main.cpp.

However, there's no reason to have a separate file called stuff.cpp with the code to the class coded in stuff.h.

stuff.h should have everything pertaining to the class Cube, and would also be better named "Cube.h".

---

### Post by Max Carey on 2008-12-15
You were never compiling stuff.cpp so your main method could not resolve Cube::show().

---

### Post by mdurham on 2008-12-15
> Move the Cube::show() function from stuff.cpp into stuff.h 
This is not good advice, it's better to keep code and definitions separate. It would work for this small example but would cause problems with a larger program.
Cheers, Mike

---

### Post by mkrahmeh on 2008-12-15
separating interface from implementation is a good practice..
furthermore, IMHO proxy classes are adorable, though many fella's think they're obsolete

---

### Post by monkeyking on 2008-12-15
> **mkrahmeh said:**
> separating interface from implementation is a good practice..
furthermore, IMHO proxy classes are adorable, though many fella's think they're obsolete

What excatly is a proxy class?

---

