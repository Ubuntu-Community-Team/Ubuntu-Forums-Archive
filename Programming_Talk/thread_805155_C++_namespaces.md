---
title: "C++ namespaces"
date: 2008-05-23
forum: Programming Talk
---

### Post by Sockerdrickan on 2008-05-23
Hello how can I use namespaces across multiple cpp files, I found an example but it sucked and didn't work, please help me!:)

---

### Post by amingv on 2008-05-23
Lookie here:
[http://www.cplusplus.com/doc/tutorial/namespaces.html](http://www.cplusplus.com/doc/tutorial/namespaces.html)

To use a namespace from other file:

[PHP]#include "header_with_namespace.h"

int main(){

int foo = myNamespace::bar;

}[/PHP]

---

### Post by Sockerdrickan on 2008-05-23
I already know how they work, but something went wrong when I was trying to use them across more cpp files. I'll try again now.

---

### Post by Sockerdrickan on 2008-05-23
```
robin@PC:~/a/engine/source$ make
Compiling: console.cpp
Linking...main.o: In function `__static_initialization_and_destruction_0':
/usr/include/c++/4.2/iostream:77: multiple definition of `Engine::system'
console.o:/usr/include/c++/4.2/iostream:77: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/usr/include/c++/4.2/iostream:77: multiple definition of `Engine::arch'
console.o:/usr/include/c++/4.2/iostream:77: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/usr/include/c++/4.2/iostream:77: multiple definition of `Game::name'
console.o:/home/robin/a/engine/source/console.cpp:85: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/home/robin/a/engine/source/defs.h:7: multiple definition of `Game::player'
console.o:/home/robin/a/engine/source/console.cpp:85: first defined here
main.o:(.data+0x28): multiple definition of `Game::version'
console.o:(.data+0xc): first defined here
main.o:(.data+0x1c): multiple definition of `Engine::version'
console.o:(.data+0x0): first defined here
main.o: In function `__static_initialization_and_destruction_0':
/home/robin/a/engine/source/defs.h:7: multiple definition of `Video::fullscreen'
console.o:/home/robin/a/engine/source/console.cpp:91: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/home/robin/a/engine/source/defs.h:7: multiple definition of `Video::width'
console.o:/home/robin/a/engine/source/console.cpp:85: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/home/robin/a/engine/source/console.h:9: multiple definition of `Video::height'
console.o:/home/robin/a/engine/source/console.cpp:85: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/home/robin/a/engine/source/console.h:9: multiple definition of `Video::depth'
console.o:/home/robin/a/engine/source/console.cpp:85: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/home/robin/a/engine/source/console.h:9: multiple definition of `Sound::on'
console.o:/home/robin/a/engine/source/console.cpp:85: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/home/robin/a/engine/source/console.h:9: multiple definition of `Sound::music'
console.o:/home/robin/a/engine/source/console.cpp:89: first defined here
main.o: In function `__static_initialization_and_destruction_0':
/home/robin/a/engine/source/console.h:9: multiple definition of `Sound::volume'
console.o:/home/robin/a/engine/source/console.cpp:89: first defined here

```

that's when I use the namespace from 2 cpp files

---

### Post by wootah on 2008-05-23
Are you using the #ifndef and #define so that you don't include prototypes more than once ?

---

### Post by Sockerdrickan on 2008-05-23
yeah

```
#ifndef _SHARED_
#define _SHARED_

#include <string>

using namespace std;

namespace Engine {
	extern int version[3];
	extern string system;
	extern string arch;
}

namespace Game {
	extern int version[3];
	extern string name;
	extern string player;
}

namespace Video {
	extern bool fullscreen;
	extern unsigned int width;
	extern unsigned int height;
	extern unsigned int depth;
}

namespace Sound {
	extern bool on;
	extern bool music;
	extern float volume;
}

#endif

```

---

### Post by hessiess on 2008-05-23
looks like you may be including files that are including outher files. multiple definition meens that you are defining a vairiable/ class/ function etc multiple times. I cannot say exactily what the problem is without seeing the code.

---

### Post by Sockerdrickan on 2008-05-23
Well I'll make you an example then

shared.h
```
#ifndef _SHARED_
#define _SHARED_

#include <string>
using namespace std;

namespace Game {
	extern int version[3];
	extern string name;
	extern string player;
}

#endif

```

shared.cpp
```
#include "shared.h"
#include <string>

namespace Game {
	int version[3]={1,0,0};
	std::string name="Unknown";
	std::string player;
}

```

main.cpp
```
#include <iostream>
#include "other.h"
#include "shared.h"

using namespace std;

int main() {
	cout<<Game::name<<endl;	
	foo();
	return 0;
}

```

other.cpp
```
#include "shared.h"
#include "other.h"
#include <iostream>

using namespace std;

void foo() {
	cout<<Game::name<<endl;	
}

```

other.h
```
void foo();

```

---

### Post by Sockerdrickan on 2008-05-23
Ok I think I got it now

---

### Post by amingv on 2008-05-23
It works well for me:

```
$ g++ main.cpp shared.cpp other.cpp -o main
$ ./main
Unknown
Unknown
$

```

---

### Post by Fedomer_OSX on 2008-09-02
Be carefull!
Template aren't as normal C++ code!
Your head have to be:

shared.h
```
#ifndef _SHARED_
#define _SHARED_

#include <string>
using namespace std;

namespace Game {
	extern int version[3];
	extern string name;
	extern string player;
};

#include "shared.cpp"
#endif
```

then your cpp code as:

shared.cpp
```

#ifdef _SHARED_
#include <string>

namespace Game {
	int version[3]={1,0,0};
	std::string name="Unknown";
	std::string player;
}
#endif
```

it will work on GCC and intel c++ compiler

---

