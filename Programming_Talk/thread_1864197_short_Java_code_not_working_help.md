---
title: "short Java code not working help"
date: 2011-10-18
forum: Programming Talk
---

### Post by falcon12 on 2011-10-18
so here is my program it is Stanford Karel program and i cant get anything after the run body to work im trying to learn how to program in java so if anyone could help me i would appreciate it! 
thanks


```
import stanford.karel.*;

public class CollectNewspaperKarel extends Karel {    
    public void run(){
        move();
        moveBack();
        turnLeft();
        turnLeft();
        turnLeft();
        move();
        turnLeft();
        move();
        move();
        move();
    }
    
    public void moveBack() {
        turnLeft();
        turnLeft();
        move();
        turnLeft();
        turnLeft();
    }
    
    public void doublebeepersinpile() {
        while (beepersPresent()) {
            pickBeeper();
            moveBack();
            putTwoBeepersDown();
            pickBeeper();
            move();
            putTwoBeepersDown();
        }
        doublebeepersinpile();
    }
    public void putTwoBeepersDown() {
            putBeeper();
            putBeeper();
        }

    }
```

---

### Post by cgroza on 2011-10-18
Are there any compiler errors?

---

### Post by moldaviax on 2011-10-19
isn't that an infinitely recursive call to doublebeepersinpile() ?

M.

---

### Post by 11jmb on 2011-10-19
> **moldaviax said:**
> isn't that an infinitely recursive call to doublebeepersinpile() ?

M.

Yes, but it doesn't matter because doublebeepersinpile() is also an infinite loop

Falcon,  can you take a step back and tell us (in plain English, not code) what goal this class is supposed to accomplish?

---

### Post by 11jmb on 2011-10-19
Also, can you post whatever main you are running?

I haven't seen Karel in years, but if I remember correctly, there should be something about setting up a World object

---

### Post by falcon12 on 2011-10-20
well basically the purpose of the program is me simply being able to understand the basic syntax on java and how it works its been going all good so far but for some reason i cant get it to execute the doublebeepersinpile() i dont know what i did wrong.
also what do you mean by what main i am running? sorry if thats a noobie question im new to all this.
thanks in advance

and yes there is a world selection thing that allows you to select between different maps Karel can do. 
another problem im having is that when i make a program that applies to a different map that has different obstacles and i try to run the new program i made it switches to a different program i wrote that does not apply to the map i am running

---

