---
title: "Quick question about Arrays in Java"
date: 2010-12-11
forum: Programming Talk
---

### Post by alexmoca on 2010-12-11
I have never been so confused about programming in my life.

I always knew and always programmed with arrays [C++] this way:
```
int array = new int[ROWS][COLUMNS]
```

Basically the first index represents the number of rows, while the second index represents the number of columns. So far, so good.

However now at uni we have been told several times that in Java you declare it exactly the opposite way:

```
int array = new int[COLUMNS][ROWS]
```

I am pretty sure that this is not correct, though I remember websites that also supported the idea. Anyway, at my last homework I used this new approach and never had any problems running my program. However, I always get an ArrayIndexOutOfBoundsException at my new homework and everything's fine when I use the "C++ approach".

This is the code that was causing problems:

```

    public int getSquare(int column, int row) throws NoSuchElementException {
        if(column < 0 || column >= COLUMN || row < 0 || row >= ROW) {
            throw new NoSuchElementException("No such element");
        } else {
            return grid[column][row];
        }
        
    }

```

This is how grid, column and row had been initialized:

```
        grid = new int[][]{
             {0,0,0,0,1,1,1,1,1,0,0,0,0,0,0,0,0,0,0},
             {0,0,0,0,1,0,0,0,1,0,0,0,0,0,0,0,0,0,0},
             {0,0,0,0,1,3,0,0,1,0,0,0,0,0,0,0,0,0,0},
             {0,0,1,1,1,0,0,3,1,1,0,0,0,0,0,0,0,0,0},
             {0,0,1,0,0,3,0,3,0,1,0,0,0,0,0,0,0,0,0},
             {1,1,1,0,1,0,1,1,0,1,0,0,0,1,1,1,1,1,1},
             {1,0,0,0,1,0,1,1,0,1,1,1,1,1,0,0,2,2,1},
             {1,0,3,0,0,3,0,0,0,0,0,0,0,0,0,0,2,2,1},
             {1,1,1,1,1,0,1,1,1,0,1,5,1,1,0,0,2,2,1},
             {0,0,0,0,1,0,0,0,0,0,1,1,1,1,1,1,1,1,1},
             {0,0,0,0,1,1,1,1,1,1,1,0,0,0,0,0,0,0,0}
        };

    final int COLUMN = 19;
    final int ROW = 11;
```

Help!;)

---

### Post by Reiger on 2010-12-11
You declare an array of arrays of ints. So the first index retrieves the array, and the second index retrieves the particular int. Columns and rows don't come into it, the language (be it C++ or Java) has no concept of them when it comes to arrays.

So in short it depends on how you initialise your array which translation from a given column & row indices pair to array access is correct. I.e. if you initialised grid as an array of “columns” you must first select the column, then the row to get the desired “cell”; if you initialised grid as an array of “rows” you must select the column from the row which is the opposite order in array syntax.

---

### Post by alexmoca on 2010-12-11
Cheers, Reiger. ;)

---

### Post by GregBrannon on 2010-12-12
With respect to Reiger, even in Java, the human visualization of a 2-dimensional array is typically in a ROW x COLUMN arrangement.  I don't know where you're hearing that 2-dimensional arrays in Java are COLUMN x ROW, but that's nonsense.

I think Reiger's point is that the computer doesn't care whether we call the first index ROWs or COLUMNs, but it sure helps us mere mortals to use a visualization that we can describe in consistent terms to achieve a common understanding.

BTW - Your examples of Java array declarations are incorrect.  A correct 2-dimensional array declaration in Java would be:

```

int[][] intArray = new int[ROW][COLUMN];

```

where ROW and COLUMN are defined int values.

When I get confused about topics like this due to misinformation or differences in other languages, I refer to a copy of Fred Swartz' Java Notes that I carry with me always, electronically of course.  I started a similar set of notes myself, but it would take me years to match what Mr. Swartz has done:

[Fred Swartz' Java Notes]("http://leepoint.net/notes-java/index.html")

---

