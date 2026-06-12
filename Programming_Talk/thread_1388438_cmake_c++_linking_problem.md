---
title: "cmake c++ linking problem"
date: 2010-01-23
forum: Programming Talk
---

### Post by daasdingo on 2010-01-23
hi,

Me and some guys  have this little SDL game hosted on launchpad.net/mage-wars
We are trying to use cmake, but the project just won't link.
Maybe it's our template class that is wrong, but maybe we just have a wrong cmake configuration. We can't figure it out since 2 days, so I would appreciate your help!

that is the linking output:
```
make
[ 10%] Building CXX object CMakeFiles/mage-wars.dir/src/ui/graphics.cpp.o
[ 20%] Building CXX object CMakeFiles/mage-wars.dir/src/player/Player.cpp.o
[ 30%] Building CXX object CMakeFiles/mage-wars.dir/src/utils/ivector.cpp.o
[ 40%] Building CXX object CMakeFiles/mage-wars.dir/src/utils/vector3D.cpp.o
[ 50%] Building CXX object CMakeFiles/mage-wars.dir/src/utils/timer.cpp.o
[ 60%] Building CXX object CMakeFiles/mage-wars.dir/src/core/BL.cpp.o
[ 70%] Building CXX object CMakeFiles/mage-wars.dir/src/spell/TargetedSpell.cpp.o
[ 80%] Building CXX object CMakeFiles/mage-wars.dir/src/spell/State.cpp.o
[ 90%] Building CXX object CMakeFiles/mage-wars.dir/src/spell/Spell.cpp.o
[100%] Building CXX object CMakeFiles/mage-wars.dir/src/main.cpp.o
Linking CXX executable mage-wars
CMakeFiles/mage-wars.dir/src/ui/graphics.cpp.o: In function `Graphics::renderPlayers(IVector<Player*>&) const':
graphics.cpp:(.text+0x63): undefined reference to `IVector<Player*>::at(int)'
graphics.cpp:(.text+0x77): undefined reference to `IVector<Player*>::size()'
CMakeFiles/mage-wars.dir/src/ui/graphics.cpp.o: In function `Graphics::renderSpells(IVector<Spell*>&) const':
graphics.cpp:(.text+0xfc): undefined reference to `IVector<Spell*>::at(int)'
graphics.cpp:(.text+0x110): undefined reference to `IVector<Spell*>::size()'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::Player()':
Player.cpp:(.text+0x36): undefined reference to `IVector<Spell>::IVector()'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::Player()':
Player.cpp:(.text+0xa8): undefined reference to `IVector<Spell>::IVector()'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::Player(Player const&)':
Player.cpp:(.text+0x11e): undefined reference to `IVector<Spell>::IVector()'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::Player(Player const&)':
Player.cpp:(.text+0x18a): undefined reference to `IVector<Spell>::IVector()'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::~Player()':
Player.cpp:(.text+0x1e2): undefined reference to `IVector<Spell>::~IVector()'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::~Player()':
Player.cpp:(.text+0x260): undefined reference to `IVector<Spell>::~IVector()'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::~Player()':
Player.cpp:(.text+0x2de): undefined reference to `IVector<Spell>::~IVector()'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::addSpell(Spell)':
Player.cpp:(.text+0x3ca): undefined reference to `IVector<Spell>::addEntry(Spell)'
CMakeFiles/mage-wars.dir/src/player/Player.cpp.o: In function `Player::removeSpell(Spell)':
Player.cpp:(.text+0x45e): undefined reference to `IVector<Spell>::removeEntry(Spell)'
CMakeFiles/mage-wars.dir/src/core/BL.cpp.o: In function `BL::BL()':
BL.cpp:(.text+0x26): undefined reference to `IVector<Player>::IVector()'
BL.cpp:(.text+0x36): undefined reference to `IVector<Spell>::IVector()'
BL.cpp:(.text+0x4d): undefined reference to `IVector<Player>::~IVector()'
CMakeFiles/mage-wars.dir/src/core/BL.cpp.o: In function `BL::BL()':
BL.cpp:(.text+0x8e): undefined reference to `IVector<Player>::IVector()'
BL.cpp:(.text+0x9e): undefined reference to `IVector<Spell>::IVector()'
BL.cpp:(.text+0xb5): undefined reference to `IVector<Player>::~IVector()'
CMakeFiles/mage-wars.dir/src/core/BL.cpp.o: In function `BL::BL(BL const&)':
BL.cpp:(.text+0xfa): undefined reference to `IVector<Player>::IVector()'
BL.cpp:(.text+0x10a): undefined reference to `IVector<Spell>::IVector()'
BL.cpp:(.text+0x121): undefined reference to `IVector<Player>::~IVector()'
CMakeFiles/mage-wars.dir/src/core/BL.cpp.o: In function `BL::BL(BL const&)':
BL.cpp:(.text+0x166): undefined reference to `IVector<Player>::IVector()'
BL.cpp:(.text+0x176): undefined reference to `IVector<Spell>::IVector()'
BL.cpp:(.text+0x18d): undefined reference to `IVector<Player>::~IVector()'
CMakeFiles/mage-wars.dir/src/core/BL.cpp.o: In function `BL::~BL()':
BL.cpp:(.text+0x1ce): undefined reference to `IVector<Spell>::~IVector()'
BL.cpp:(.text+0x1de): undefined reference to `IVector<Player>::~IVector()'
BL.cpp:(.text+0x1fe): undefined reference to `IVector<Player>::~IVector()'
CMakeFiles/mage-wars.dir/src/core/BL.cpp.o: In function `BL::~BL()':
BL.cpp:(.text+0x24c): undefined reference to `IVector<Spell>::~IVector()'
BL.cpp:(.text+0x25c): undefined reference to `IVector<Player>::~IVector()'
BL.cpp:(.text+0x27c): undefined reference to `IVector<Player>::~IVector()'
CMakeFiles/mage-wars.dir/src/core/BL.cpp.o: In function `BL::~BL()':
BL.cpp:(.text+0x2ca): undefined reference to `IVector<Spell>::~IVector()'
BL.cpp:(.text+0x2da): undefined reference to `IVector<Player>::~IVector()'
BL.cpp:(.text+0x2fa): undefined reference to `IVector<Player>::~IVector()'
collect2: ld returned 1 exit status
make[2]: *** [mage-wars] Error 1
make[1]: *** [CMakeFiles/mage-wars.dir/all] Error 2
make: *** [all] Error 2
```

and this is our CMakeLists.txt:

```
cmake_minimum_required(VERSION 2.6)
project(magewars)
find_package(SDL REQUIRED)
find_package(SDL_image REQUIRED)
find_package(SDL_mixer REQUIRED)
find_package(SDL_net REQUIRED)
find_package(SDL_sound REQUIRED)
find_package(SDL_ttf REQUIRED)
include_directories(${SDL_INCLUDE_DIR}
                              ${SDLIMAGE_INCLUDE_DIR}
                              ${SDLSOUND_INCLUDE_DIR}
                              ${SDLTTF_INCLUDE_DIR}
                              ${SDLMIXER_INCLUDE_DIR})
                              
include_directories(src)
link_libraries(${SDL_LIBRARY} ${SDLIMAGE_LIBRARY} SDLmain)
add_executable(mage-wars
src/ui/graphics.cpp
src/player/Player.cpp
src/utils/ivector.cpp
src/utils/vector3D.cpp
src/utils/timer.cpp
src/core/BL.cpp
src/spell/TargetedSpell.cpp
src/spell/State.cpp
src/spell/Spell.cpp
src/main.cpp
)

```

if you see any errors, please tell! Thanks

---

### Post by Zugzwang on 2010-01-23
You normally write the definitions of the methods of template classes in header files as otherwise you will end up with a lot of .o files of which none of them contains the actual functions for certain template instantiations. So try moving the template class definitions to the header files.

I think that there are some compilers for which this isn't necessary, but the way stated above is at least safe (and is likely to fix your problem).

---

### Post by daasdingo on 2010-01-23
thanks a lot, I'll try that

EDIT: Thanks, that solved the linker problem! Weird that GCC isn't smart enough for this..

---

