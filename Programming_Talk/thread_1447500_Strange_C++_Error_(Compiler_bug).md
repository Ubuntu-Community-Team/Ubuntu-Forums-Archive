---
title: "Strange C++ Error (Compiler bug?)"
date: 2010-04-05
forum: Programming Talk
---

### Post by weezerBo on 2010-04-05
Header
```
#ifndef ENGINE_H_
#define ENGINE_H_

class Engine
{
public:
  Engine();
  ~Engine();

  void run();
  virtual void onKeyPress(SDL_Event *event) = 0;
  virtual void onMousePress(SDL_Event *event) = 0;

  virtual void render() = 0;
};

#endif

```Source
```

#include "engine.h"

Engine::Engine()
{
}

Engine::~Engine()
{
}

void Engine::run()
{
}

```Error
```
engine.cpp:11: error: no &#8216;void Engine::run()&#8217; member function declared in class &#8216;Engine&#8217;
```Yes, yes. I know the it shouldn't compile, so that's not what I'm complaining about. The problem is the error message. The error has nothing to do with void Engine::run. It's because I didn't forward declare SDL_Event or include "SDL.h". So why is it complaining about Engine::run when it should be complaining about that?

I've never had a compiler point me in the wrong direction.

---

### Post by sharpdust on 2010-04-05
What compiler are you using?

I get the following when I try to compile your code

```
gcc engine.C
engine.h:11: error: 'SDL_Event' has not been declared
engine.h:12: error: 'SDL_Event' has not been declared
distcc[21685] ERROR: compile engine.C on localhost failed
```

---

### Post by weezerBo on 2010-04-05
> **sharpdust said:**
> What compiler are you using?

I get the following when I try to compile your code

```
gcc engine.C
engine.h:11: error: 'SDL_Event' has not been declared
engine.h:12: error: 'SDL_Event' has not been declared
distcc[21685] ERROR: compile engine.C on localhost failed
```
gcc version 4.4.3 20100316 (prerelease) (GCC)
okay, now I'm _****REALLY****_ confused

```
[weezer@dev]~/projects/playtheorycpp: g++ main.cpp engine.cpp window.cpp extractor.cpp point.cpp surface.cpp -o bgame `sdl-config --cflags --libs` -lGL -Wall -ansi -pedantic -g3 -ggdb
main.cpp: In function &#8216;int main(int, char**)&#8217;:
main.cpp:201: warning: comparison between signed and unsigned integer expressions
main.cpp:207: warning: comparison between signed and unsigned integer expressions
main.cpp:212: warning: comparison between signed and unsigned integer expressions
In file included from engine.cpp:1:
engine.h:12: error: &#8216;SDL_Event&#8217; has not been declared
engine.h:13: error: &#8216;SDL_Event&#8217; has not been declared
[weezer@dev]~/projects/playtheorycpp: make
g++ -ggdb -g3 `sdl-config --cflags` -c main.cpp
g++ -ggdb -g3 `sdl-config --cflags` -c surface.cpp
g++ -ggdb -g3 `sdl-config --cflags` -c window.cpp
g++ -ggdb -g3 `sdl-config --cflags` -c blob.cpp
g++ -ggdb -g3 `sdl-config --cflags` -c point.cpp
g++ -ggdb -g3 `sdl-config --cflags` -c extractor.cpp
g++ -ggdb -g3 `sdl-config --cflags` -c engine.cpp
engine.cpp:11: error: no &#8216;void Engine::run()&#8217; member function declared in class &#8216;Engine&#8217;
make: *** [engine.o] Error 1
```
It gives the correct error when I build by hand, but not make. 

fwiw

```

CC = g++ -ggdb -g3
CFLAGS = `sdl-config --cflags`
LIBS = `sdl-config --libs` -lGL

bgame : main.o surface.o window.o blob.o point.o extractor.o engine.o
        $(CC) main.o surface.o window.o blob.o point.o extractor.o engine.o $(LIBS) -o bgame

main.o : main.cpp surface.h window.h point.h extractor.h engine.h 
        $(CC) $(CFLAGS) -c main.cpp

surface.o : surface.cpp surface.h
        $(CC) $(CFLAGS) -c surface.cpp

window.o : window.cpp window.h
        $(CC) $(CFLAGS) -c window.cpp

blob.o : blob.cpp blob.h surface.h
        $(CC) $(CFLAGS) -c blob.cpp

point.o : point.cpp point.h
        $(CC) $(CFLAGS) -c point.cpp

extractor.o : extractor.cpp extractor.h
        $(CC) $(CFLAGS) -c extractor.cpp

engine.o : engine.cpp engine.h
        $(CC) $(CFLAGS) -c engine.cpp

clean:
        rm -rfv *~ *.o 

```

---

### Post by MattThLinuxNewb on 2010-04-05
I think it is because you have pure virtual methods meaning Engine is an abstract class, and yet you have declared run() as non-virtual. Your definition for run() could never be called because Engine can't be instantiated! The compiler is trying to tell you, in it's unhelpful way, that your code doesn't make sense :)
The answer is to make run() virtual.
Also make your Engine's destructor virtual so your inherited objects are destroyed in the right order.

---

### Post by dribeas on 2010-04-05
> **MattThLinuxNewb said:**
> I think it is because you have pure virtual methods meaning Engine is an abstract class, and yet you have declared run() as non-virtual. Your definition for run() could never be called because Engine can't be instantiated! The compiler is trying to tell you, in it's unhelpful way, that your code doesn't make sense :)
The answer is to make run() virtual.
Also make your Engine's destructor virtual so your inherited objects are destroyed in the right order.

This answer actually makes no sense. The following code is valid and does what you would expect:

```

struct base {
   void foo() { std::cout << "base::foo" << std::endl; }
   virtual bar() = 0;
};
struct derived : base {
   virtual bar() { std::cout << "derived::bar" << std::endl; }
};
int main() {
   derived d;
   d.foo();    // base::foo
   d.bar();    // derived::bar
}

```

The fact that you cannot instantiate an object that is only 'base', but you can define methods (or any other thing) to be used once the class is derived and the pure virtual methods implemented.

---

### Post by weezerBo on 2010-04-05
> **MattThLinuxNewb said:**
> I think it is because you have pure virtual methods meaning Engine is an abstract class, and yet you have declared run() as non-virtual. Your definition for run() could never be called because Engine can't be instantiated! The compiler is trying to tell you, in it's unhelpful way, that your code doesn't make sense :)
The answer is to make run() virtual.
Also make your Engine's destructor virtual so your inherited objects are destroyed in the right order.
Post above + It builds and runs fine when "SDL.h" is included -- it not being included is the reason why it fails to build. 

The failure to build isn't my issue, I know why it doesn't build. I'm wondering why GCC is giving different (wrong?) errors when I use make but not when I invoke it by hand.

---

### Post by weezerBo on 2010-04-06
I guess I was correct when I said it was strange? :P

---

### Post by MattThLinuxNewb on 2010-04-07
Apparently it is perfectly legal to define non-virtual methods in an abstract class, my mistake.

Compiling your code with without including the SDL header gave me the correct error message (‘SDL_Event’ has not been declared). That's with gcc 4.2.4. Strange indeed, perhaps that prerelease version does have problems. Are you using an alpha/unstable distro version by any chance

---

