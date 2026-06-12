---
title: "&quot;this&quot; C++"
date: 2010-10-07
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-10-07
Well it seems that I have no idea how "this" is supposed to work. 

My compiler gives me: 

```
/home/fr0gg3r/workspace/Falling Block Game/Blocks.h||In constructor ‘block::block(int)’:|
/home/fr0gg3r/workspace/Falling Block Game/Blocks.h|28|error: request for member ‘spawnBlock’ in ‘this’, which is of non-class type ‘block* const’|

```

So, I have a
```
class block
```, and within the class is a method called 
```
spawnBlock(int spwn)
``` The job of the **spawnBlock** method is to initialize the main variable of the block class.
```
 std::vector<coord> blockVert
``` with a random block. (tetris block)

The error is occuring when I try to use the constructor 
```
block::block(int spwn){
    this.spawnBlock(spwn);
}
```


To give context here is the code that goes with it Note::It has a lot of errors apparently, but until I can figure out how to use "this" i cant fix any of them.

[PHP]
#ifndef BLOCK_H
#define BLOCK_H

#include <vector>
#include "co-ords.h"
#include "gameMap.h"

class block {
    private:
        std::vector<coord> blockVert;

    public:
        block(); //Constructor
        block(int spwn);

        void spawnBlock(int spwn);
        void move(char dir);
        void rotate();
        bool collision(char dir, gameMap map);
        void printBlock();
};

/*Constructor*/
block::block() {
    //does nothing ( blockVert stays as null until a block is spawned)
}
block::block(int spwn){
    this.spawnBlock(spwn);
}
/*End of Constructors*/

void block::spawnBlock(int spwn) {

    blockVert.erase(blockVert.begin(), blockVert.size()); // removes blocks in the vector.

    int block(0);

    if (spwn != 0) {
        block = spwn;
    } else {
        block = ((rand() % 8) + 1);
    }

    switch (block) {

        case 1:
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(0,0));
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(0,2));
            this.blockVert.push_back(coord(0,3));
            break;
        case 2:
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(0,0));
            this.blockVert.push_back(coord(1,0));
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(0,2));
            break;
        case 3:
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(0,0));
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(0,2));
            this.blockVert.push_back(coord(1,2));
            break;
        case 4:
            this.blockVert.push_back(coord(0,0));
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(1,0));
            this.blockVert.push_back(coord(1,1));
            break;
        case 5:
            this.blockVert.push_back(coord(1,1));
            this.blockVert.push_back(coord(1,1));
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(1,0));
            this.blockVert.push_back(coord(2,0));
            break;
        case 6:
            this.blockVert.push_back(coord(1,1));
            this.blockVert.push_back(coord(1,1));
            this.blockVert.push_back(coord(1,0));
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(2,1));
            break;
        case 7:
               this.blockVert.push_back(coord(1,1));
            this.blockVert.push_back(coord(1,1));
            this.blockVert.push_back(coord(0,0));
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(2,1));
            break;
        default:
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(0,1));
            this.blockVert.push_back(coord(0,2));
            this.blockVert.push_back(coord(0,0));
            this.blockVert.push_back(coord(0,3));
            break;
    }

}

void block::move(char dir) {

    if (dir == 'D'){
        for (int i = blockVert.size()-1 ; i >= 0; i--) {
                blockVert[i] - coord(0,1);
            }

    }

    if (dir == 'L'){
        for (int i = blockVert.size()-1 ; i >= 0; i--) {
                blockVert[i] - coord(1,0);
            }

    }

    if (dir == 'R'){
        for (int i = blockVert.size()-1 ; i >= 0; i--) {
                blockVert[i] + coord(1,0);
            }

    }

}
void block::rotate() {
    coord tmpVert;
    std::vector<coord> square;

        square.push_back(coord(0,0));
        square.push_back(coord(0,1));
        square.push_back(coord(1,0));
        square.push_back(coord(1,1));



    if (square != blockVert) { // dont try to rotate a square. //

                     //For -90 degree turn (90 degrees to the right) we subtract rotating point by the pivot point. then multiply by rotation hen { 0 , -1 }
        //which gives us that P after rotation is [ P(x0,y0) - Piv(x,y) ] = Q(a,b) then new point is (-b,a) + Piv(x,y)                            { 1 ,  0 }
        for (int i = blockVert.size() - 1 ; i > 0 ; i--) {
            tmpVert = blockVert[i] - blockVert[0];
            tmpVert = tmpVert.rotate();
            blockVert[i] = tmpVert + blockVert[0];
        }
    }

}
bool block::collision(char dir, gameMap map) {
    int xInvert(0);

    if (dir == 'L')
        xInvert = -1;
    if (dir == 'R')
        xInvert = 1;

    for (int i = blockVert.size() ; i > 0 ; i--) {
        if (map.blockExists(blockVert[i].getX() + xInvert, blockVert[i].getY() + 1)) { //xinvert tells it to check one block left (-1), or one block right.(+1)
            return true;
        } else
            return false;


    }

}

void printBlock() {
    for (int i = blockVert.size() ; i > 0 ; i-- ) {
        std::cout << blockVert[i].getX() <<"," << blockVert[i].getY() <<"\n";
    }

}

#endif
[/PHP]

---

### Post by dwhitney67 on 2010-10-07
I feel like it's Groundhog Day.

"this" is a pointer; you are not using it as such.  Try
```

block::block(int spwn){
    this**->**spawnBlock(spwn);

    // or if you want to type even more...

    (*this).spawnBlock(spwn);

    // or just keep things simple...

    spawnBlock(spwn);
}

```
Why are you using "this" anyhow?  Are you trying to impress someone with your ability to type extra characters?

---

### Post by YourMomsASmurph on 2010-10-07
Using "this" because the code was downright failing before, and at the time i thought it might help. Apparently it didn't; especially considering that I don't know how to use it. Then I remove it again, and the code works all of a sudden, with the exception of a couple errors, its kind of weird.

---

