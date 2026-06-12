---
title: "weird compiler error; doesn't make sense"
date: 2008-05-28
forum: Programming Talk
---

### Post by JohnnyBoy022 on 2008-05-28
I'm trying to program a tetris game, and I'm just getting the classes down right now. I'm getting a really strange compiler error and I can't seem to figure out what is going wrong here.

[php]
#include <iostream>
using namespace std;

// Represents a single tetris block
class Block
{
public:
    Block(int x, int y);
    int m_x, m_y;   // X and y positions on the tetris grid
};

// Holds a single tetromino (tetris shape) with an array of blocks
class Tetroid
{
public:
    Tetroid(int tetroidType, int x, int y);

    int m_x, m_y;
    Block m_blocks[4];    // 4 tetroid block positions
};

// Constructor
Block::Block(int x, int y)
{
    m_x = x;
    m_y = y;
}

Tetroid::Tetroid(int tetroidType=-1, int x=5, int y=5)
{

}

int main()
{
    return 0;
}
[/php]

This is the error:
```

C:\Users\hotojohn\Documents\Projects\Tetris\main.cpp||In constructor `Tetroid::Tetroid(int, int, int)':|
C:\Users\hotojohn\Documents\Projects\Tetris\main.cpp|42|error: no matching function for call to `Block::Block()'|
C:\Users\hotojohn\Documents\Projects\Tetris\main.cpp|8|note: candidates are: Block::Block(const Block&)|
C:\Users\hotojohn\Documents\Projects\Tetris\main.cpp|26|note:                 Block::Block(int, int)|
||=== Build finished: 1 errors, 0 warnings ===|

```

Why am I getting an error in the Tetroid constructor for creating  a block when I'm not doing anything in the Tetroid constructor?? Any help is greatly appreciated.

---

### Post by kknd on 2008-05-28
In Block m_blocks[4] you are implicit creating 4 object with the default constructor. But you don't have a default coinstructor =).

You can fix this by creating a Block() {}; constructor or by using pointers and creating the objects latter (Block* m_blocks[4], m_blocks[0] = new Block(1,2).

---

### Post by JohnnyBoy022 on 2008-05-28
Thanks, I think I will go with the pointer route. This was a really confusing one, the error message didn't help me out at all.

---

### Post by kknd on 2008-05-28
I don't like gcc error reporting with C++ too. Its very hard to find errors, specially when using templates.

---

