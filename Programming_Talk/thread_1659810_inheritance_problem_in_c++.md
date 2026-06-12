---
title: "inheritance problem in c++"
date: 2011-01-04
forum: Programming Talk
---

### Post by gufide on 2011-01-04
I got this error: expected class name before '{' token

this is my problematic file:
```
#ifndef DEF_LEVEL
#define DEF_LEVEL

#include <SDL.h>
#include <SDL_image.h>
#include "GameWindow.h"
#include "const.h"

using namespace std;

class Level : public GameWin
{      //error here
    public:
    Level();
    Level(int lvl);
    ~Level();
    void openLvl(int lvl);
    Tile getLvlMap(int x, int y);
    Object getLvlObj(int x, int y);
    int getChipNumber();
    void setChip(int num);
    void removeChip();

    private:
    Tile test[9][9];
    int chip;
    int time;
    Tile lvlmap[9][9];
    Object lvlobj[9][9];

};



#endif

```this is GameWindow.h
```
#ifndef DEF_WINDOW
#define DEF_WINDOW

#include <SDL.h>
#include <SDL_image.h>
#include "character.h"
#include "const.h"

class GameWin
{
    public:
        GameWin();
        ~GameWin();
        void display();
        void makeLvlFrame();
        void redrawlvl(Character &pers);

    private:
        SDL_Surface *m_screen, *m_tiles;
};


#endif

```what should I do? I never see this error



this is character.h

```
#ifndef DEF_CHAR
#define DEF_CHAR

#include "level.h"
#include "const.h"

class Character : public Level
{
    public:
        Character();
        ~Character();
        int getPositionX();
        int getPositionY();
        Direction getDirection();
        void setPosition(int x, int y);
        void setDirection(Direction dir);

    private:
        int posX;
        int posY;
};


#endif

```

---

### Post by worksofcraft on 2011-01-04
It looks to me like you have circular depencies:

Your character.h includes level.h and level.h includes GameWin.h and GameWIndow uses Character...

You have to break this loop. Reorganize your includes and if necessary try placing a forward declaration of a class like perhaps:

```

class Character;

```

before GameWin ?!

---

### Post by gufide on 2011-01-04
okay, so I does this:

GameWindow.h
```
#ifndef DEF_WINDOW
#define DEF_WINDOW

#include <SDL.h>
#include <SDL_image.h>
#include "const.h"

class Character;

class GameWin
{
    public:
        GameWin();
        ~GameWin();
        void display();
        void makeLvlFrame();
        void redrawlvl(Character &pers);

    private:
        SDL_Surface *m_screen, *m_tiles;
};


#endif

```level.h
```
#ifndef DEF_LEVEL
#define DEF_LEVEL

#include <SDL.h>
#include <SDL_image.h>
#include "const.h"

using namespace std;

class Level : public GameWin
{
    public:
    Level();
    Level(int lvl);
    ~Level();
    void openLvl(int lvl);
    Tile getLvlMap(int x, int y);
    Object getLvlObj(int x, int y);
    int getChipNumber();
    void setChip(int num);
    void removeChip();

    private:
    Tile test[9][9];
    int chip;
    int time;
    Tile lvlmap[9][9];
    Object lvlobj[9][9];

};

#endif

```character.h
```
#ifndef DEF_CHAR
#define DEF_CHAR

#include "const.h"

class Level;

class Character : public Level
{      //got error here
    public:
        Character();
        ~Character();
        int getPositionX();
        int getPositionY();
        Direction getDirection();
        void setPosition(int x, int y);
        void setDirection(Direction dir);

    private:
        int posX;
        int posY;
};


#endif


```gamewindow.cpp
```
#include "GameWindow.h"
#include "character.h" //errors if removed

using namespace std;

//some fonctions
```I get the same error but now in chracter.h

---

### Post by PaulM1985 on 2011-01-04
Your character.h uses the class Level, so character.h needs to include the file where Level is defined (Level.h).  Similarly, your Level.h uses the GameWin class, so the GameWindow.h needs to be included.

Hopefully, this should solve your problem.

Paul

---

### Post by Lootbox on 2011-01-04
Does it really make sense to have Level extend GameWin and Character extend Level? That violates the "is-a" relationship model for public inheritance, which adhering to will usually keep your program structure more organized and intuitive.

In other words, a character is **not** a level and a level is **not** a game window. The current hierarchy allows you to do things like:
```
Character my_character;

/* initialize my_character... */

my_character.getLvlObj(100, 100); // does this make sense?
```
Anyways, if you want this inheritance hierarchy to work, you can keep GameWindow.h the way it is, add #include "GameWindow.h" in "level.h", and add #include "level.h" in "character.h." Hope that helps.

---

### Post by gufide on 2011-01-04
> **Lootbox said:**
> Does it really make sense to have Level extend GameWin and Character extend Level? That violates the "is-a" relationship model for public inheritance, which adhering to will usually keep your program structure more organized and intuitive.

In other words, a character is **not** a level and a level is **not** a game window. The current hierarchy allows you to do things like:
```
Character my_character;

/* initialize my_character... */

my_character.getLvlObj(100, 100); // does this make sense?
```Anyways, if you want this inheritance hierarchy to work, you can keep GameWindow.h the way it is, add #include "GameWindow.h" in "level.h", and add #include "level.h" in "character.h." Hope that helps.

I see... but it's my first cpp projet ever (exculding tutorial) Thank you for this hint

---

