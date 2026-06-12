---
title: "[SOLVED] JAVA nullPointer"
date: 2007-12-02
forum: Programming Talk
---

### Post by mevets on 2007-12-02
I am developing an incredibly simple Jail cell program as homework. Each Jail has an array of 200 cells. Each cell has a field telling whether it is locked or not. For some reason, when I try to check each of the cells in the Jail's array of cells to see if they are locked, it get a nullPointer.

Class Jail:
```

public class Jail
{
    private static int NUM_CELLS = 200;
    Cell[] cells = new Cell[200];
    
    public Jail() {
        
    }
    
    public String toString() {
        String soFar = "";
        for(int i = 0; i < NUM_CELLS; ++i) {
            if(this.cells[i].getLocked()) {
                soFar = "Cell " + i+1 + " Locked\n";
            }
            else {
                soFar = "Cell " + i+1 + " Open\n";
            }
            i++;
        }
        return soFar;
    }
}


```

Class Cell:
```

public class Cell
{
    public boolean locked = true;
    
    public Cell() {

    }
    
    public boolean getLocked() {
        return this.locked;
    }
}


```
Line 20 inside of the Jail class seems to always be wrong. I am dumb founded as to why this could be. I tried converting this to a for each loop and it has the same problem. Can anyone tell me what I am doing wrong?

---

### Post by CptPicard on 2007-12-02
You never initialize your array of Cells... it is full of nulls before you stick a "new Cell()" into each location :)

---

### Post by mevets on 2007-12-02
I thought line 4 correctly initilized the array
```

Cell[] cells = new Cell[200];

```
I guess not though. How am I correctly supposed to initilize the array?

---

### Post by CptPicard on 2007-12-02
It just reserves the array for the references, which are initially null.

In your Jail constructor:

```

for (int i = 0; i < cells.length; i++)
  cells[i] = new Cell();

```

---

### Post by mevets on 2007-12-02
Great! I understand now.
My fixes are as such...

Class Jail:
```

public class Jail
{
    private static int NUM_CELLS = 200;
    Cell[] cells = new Cell[200];
    
    public Jail() {
        for (int i = 0; i < cells.length; i++)
            cells[i] = new Cell();
    }
    
    public String toString() {
        String soFar = "";
        for(int i = 0; i < NUM_CELLS; ++i) {
            int num = i + 1;
            if(this.cells[i].getLocked()) {
                soFar = soFar + "Cell " + num + " Locked\n";
            }
            else {
                soFar = soFar + "Cell " + num + " Open\n";
            }
        }
        return soFar;
    }
}

```

I did not have to make any changes to the Cell class.

---

