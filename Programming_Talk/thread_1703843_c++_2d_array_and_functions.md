---
title: "c++ 2d array and functions"
date: 2011-03-09
forum: Programming Talk
---

### Post by nbo10 on 2011-03-09
Hi All,
I have been using python and love it, but the size of the arrays I have to analyse are increasing and python isn't fast enough. I've wrote test program in c++ and it is significantly faster. The problem I'm having is passing and returning 2d arrays from a function.

Goggling hasn't helped and has given me a headache.. 

Here is the base code I have. The data for a is read in from a file. How do I define the function func and its prototype so that I can access the 2d array a? pointers and references are really confusing me. 

```

int H = arvg[1];
int W = arvg[2];
double a[H][W]= {...}
double ans[H][W]

ans[][] = func(a[][])


```

---

### Post by cgroza on 2011-03-10
Create a pointer to a function and insert it into the array.

```
void (*func) (int arg1,int arg2)
```This is just an example.
In the prototype, you might want to initialize it to 0;
```
And then just assign a function reference to the pointer.
void (*func) (int arg1,int arg2) = &MyFunction;
```EDIT: Sorry, misunderstood the question.
Take a look here. [http://www.java2s.com/Tutorial/Cpp/0140__Function/Passingatwodimensionalarraytoafunction.htm](http://www.java2s.com/Tutorial/Cpp/0140__Function/Passingatwodimensionalarraytoafunction.htm)

---

### Post by PaulM1985 on 2011-03-10
Here is some test code.  Instead of using a 2d array, I am using a 1d array which is large enough to hold all of the values.  Values are input and retreived from the array using rowNum * number of columns + colNum.

I hope this helps:

```

#include "iostream" 

const int MAX_ROWS = 10;
const int MAX_COLS = 5;

void fillMyMatrix(int myMatrix[])
{
  for (int i = 0; i < MAX_ROWS; i++)
  {
    for (int j = 0; j < MAX_COLS; j++)
    {
       myMatrix[i * MAX_COLS + j] = i * MAX_COLS + j;
    }
  }
}

void printMyMatrix(const int myMatrix[])
{
  for (int i = 0; i < MAX_ROWS; i++)
  {
    for (int j = 0; j < MAX_COLS; j++)
    {
       std::cout << myMatrix[i * MAX_COLS + j] << std::endl;
    }
  }
}

int main()
{
  int matrix[MAX_ROWS * MAX_COLS];
  fillMyMatrix(matrix);
  printMyMatrix(matrix);

  return 0;
}

```

So instead of returning a matrix, you pass it in as an argument and it can be filled.

Paul

---

