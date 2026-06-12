---
title: "minesweeper"
date: 2008-04-07
forum: Programming Talk
---

### Post by jus71n742 on 2008-04-07
For my C++ class I am having difficulty coming up with a program that will create the random locations of the mines....not sure where to get started

the link to the assignment is here
[http://www.cs.utk.edu/~cs102/labs/labsholder/lab9.html](http://www.cs.utk.edu/~cs102/labs/labsholder/lab9.html)

---

### Post by nhandler on 2008-04-07
This should probably go in the programming section. You should also read this thread: [http://ubuntuforums.org/showpost.php?p=4465816&postcount=1](http://ubuntuforums.org/showpost.php?p=4465816&postcount=1)

I would start by looking up how to generate a random number within a certain range. Then I would learn how to do 2-dimensional arrays. You will use the array to represent the board. Then you just use some sort of loop to generate a certain number of randomly placed mines.

---

### Post by msgyrd on 2008-04-07
Pretty good random number tutorial:

[http://www.cplusplus.com/reference/clibrary/cstdlib/rand.html](http://www.cplusplus.com/reference/clibrary/cstdlib/rand.html)


Without doing your homework for you, I would just create 2-D array and then pull rand()%whatever a few times to populate the board.

---

### Post by jus71n742 on 2008-04-08
ok I understand that this is not a hw help forum and I really am trying to do this the right way and do not want anyone to do this for me...just help me start thinking the right way..or some ideas.  

I have 
```

void printArray(const int[100][100]);

int main
{
int rows,columns, num_mines;
int array[r][c];
int r,c;
srand((unsigned)seed);
cout << "enter rows, columns, num_mines;
cin >> array[r][c]>>num_mines>> seed;

srand(seed);

int count;
for (int count = seed;count =<100;count++)
{
cout <<count(100)<<(1+count %rows, columns);
}

if (seed > 400)
else if(number_mines>400
else
cout << "enter bad arguments\n";

if (rows <100)
cout << rows;

if (columns < 100)
cout << columns;

int random_integer;
for (seed = random_integer; random_integer<400;random_integer++)
{
cout << "*";
}
int a1[0][0];
for (a1[0][0]; a1<400 ; a1++)
if (a1<400 )
cout << ".";
}
return 0;
}


```

---

### Post by AndrewEsther on 2008-04-08
are you having trouble with the actual coding part or the thinking up the math part?

---

### Post by jus71n742 on 2008-04-08
little bit of both.

---

### Post by Mick8882003 on 2008-04-08
One random for the horizontal and one for the vertical?

---

### Post by Sef on 2008-04-08
> This should probably go in the programming section.

My thoughts exactly, so moved to Programming Talk.

---

### Post by mike_g on 2008-04-08
First, you want to declare main as: int main[COLOR="DarkRed"]()[/COLOR]. Next, you have never declared 'seed'. To get different random numbers each time you will need to have a different seed each time you run the program. On common way to do this would be seeding randomisation on the time:
```
#include <time.h>
....
srand(time(NULL));
```
Also, you should only need to call srand once.

As for filling the grid heres some pseudo code of how you could go about it:
```
for each mine to lay
    do
        x = random 0 to GRID_WIDTH -1
        y = random 0 to GRID_HEIGHT -1
    while grid[x][y] has mine in cell
    grid[x][y] = true
end for loop
```

---

### Post by insineratehymn on 2008-04-08
...then you need a way to keep track of the precise location of all of the mines so each box will know how many are touching it.

Maybe a hash array?

Like: (0,1) = 1 or (4,3) = 3

Or maybe assign each box a UID and just store it like that?

I don't know. I had the same assignment in one of my classes and I had too much fun with it; mine was in Java, though.

---

### Post by pedro_orange on 2008-04-08
You could do this a number of ways:

eg.
 - Write a routine that knows the size of the grid, and searches around a given element to return a value of the number of mines surrounding the element.
 - Create a class for each element that knows who it's surrounding elements are, and has a method for checking those element's values.

Probably would be alot less work to stick with your 2D arrays, and write a function to check the surrounding blocks.

Incidentally this would be a good little programming challenge!

---

### Post by smartbei on 2008-04-08
Easier still is to just add one to all the surrounding tiles that aren't mines every time you place a mine.

---

### Post by insineratehymn on 2008-04-08
I'm sure there is an algorithm to calculate the locations in a 2-d matrix for all surrounding points, but I don't know what it is. :)

---

