---
title: "Undefined Refrence when function is defined?"
date: 2008-05-07
forum: Packaging and Compiling Programs
---

### Post by MrPickle on 2008-05-07
I am trying to run my program but when I do so it's saying that I haven't defined some functions that are defined. They are defined in a header file in a class. It is picking up the header because if I comment it out it says that the functions are undeclared.

It works fine if I put all the code into one file.

Here's the code:

Main.cpp
```
//Basic Headers
#include <iostream>
#include <string>

//SDL Headers
#include <SDL/SDL.h>
#include <SDL/SDL_image.h>

//Custom Headers
#include "Core.h"

using namespace std;

int main(int argc, char* argv[]){
	Core aCore;
	return aCore.onExecute();
}
```


Core.h
```
#ifndef CORE_H
#define CORE_H

#include <SDL/SDL.h>
#include <SDL/SDL_image.h>

class Core {
	public:
		Core();
		int onExecute();
};

#endif
```

Core.cpp
```
#include "Core.h"

Core::Core(){}

int Core::onExecute(){
		return 0;
}

```

Here is the exact output from compiler:
```
/tmp/ccS5J7Bg.o: In function `main':
Main.cpp:(.text+0x6f): undefined reference to `Core::Core()'
Main.cpp:(.text+0x77): undefined reference to `Core::onExecute()'
collect2: ld returned 1 exit status
```

Am I missing something with this jazzy compiler thing? It's alot different to windows which I have been coding in previously (Moved from Vista about a week ago)

---

### Post by jaddle on 2008-05-07
That's a linker error actually, not a compiler error. It's saying "I know there's a Core::Core() function somewhere, I've seen the header, but I can't find the actual code!"

You probably tried to compile with something like this:

g++ Main.cpp -o executable

You need to compile the Core.cpp file as well though:

g++ Main.cpp Core.cpp -o executable

You might also need to link in the SDL libraries, since it looks like you'll be using those too.

---

### Post by MrPickle on 2008-05-08
Yey, Thank you very much :)

I need help with linking the SDL libraries, do I just add SDL.h SDL_Image.h to the command or the .cpp files or whatnot?

---

### Post by jaddle on 2008-05-08
No, you probably want to just add -lSDL, plus any other sdl modules you are using (e.g. -lSDL_mixer). See [http://gpwiki.org/index.php/C:How_to_set_up_your_SDL_Build_Environment#All_Platforms:_GCC_and_G.2B.2B](http://gpwiki.org/index.php/C:How_to_set_up_your_SDL_Build_Environment#All_Platforms:_GCC_and_G.2B.2B) for some more info.

---

### Post by MrPickle on 2008-05-09
Ahh, I see, thank you :)

---

