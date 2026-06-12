---
title: "C++: referring to an object via one of its variables?"
date: 2009-11-04
forum: Programming Talk
---

### Post by daweefolk on 2009-11-04
I'm trying to make a minesweeper type game and I'm stuck at getting the squares to communicate with each other (so they know how many mines are nearby). Each square is in a class i made, and they have the variables sq_X (its x location on the "map"), sq_Y (its y location), sq_HasMine (does this square have a mine on it?), sq_Id (number, 1-100, of the square. 1 is at 1,1 and 100 is at 10,10), an array sq_AdjacentSquares (stores the sq_Ids of the adjacent squares), and sq_MinesNearby (how many mines are adjacent to this square?).
I think I need to get the squares to "contact" the ones that are one x and or y away. However, I don't know how to refer to them. I'm kinda a newbie at c++, and especially to oop. 
when I create the squares in my program, I call them "square1" to "square100", and assign their sq_Id to their name's number.
How can I retrieve the sq_Id from one of the objects without referring to them by name?


Short version:How can I access an object's variable without calling the object by name? is this even possible?

---

### Post by terry_a_g on 2009-11-04
If I'm understanding you, I don't think what you want is possible.

It sounds like you did something like this

```
Square *square1 = new Square();
Square *square2 = new Square();
Square *square3 = new Square();
// Tons more omitted
Square *square100 = new Square();
```If so you need to look into arrays and loops, or linked lists.

---

### Post by IllegalCharacter on 2009-11-04
> **daweefolk said:**
> Short version:How can I access an object's variable without calling the object by name? is this even possible?

You can if you have a pointer (which I'm assuming you don't have). But even then you'd still need the name of the pointer.
If the square object does not have a reference/pointer to the parent, then there isn't really a way to access the parent.

I'd recommend instead of storing all your squares in a variable for each cell, you should have a single array of cells:
```
Square squares[10][10];
```
Then your game object or whatever is holding the squares should have a method called GetSquare(int x, int y) which will return the square at squares[x][y].

---

### Post by terry_a_g on 2009-11-04
IllegalCharacters solution is the way to go, but it's going to require rethinking your problem and redesigning your classes.  Perhaps instead of a Square class, you should think more along the lines of a Board class, and shove that two dimensional array inside of it to store your game state.

---

