---
title: "Noob question about dynamic arrays"
date: 2010-11-05
forum: Programming Talk
---

### Post by VanillaCone on 2010-11-05
I'm doing an assignment for school and I've been brought to a standstill, I'm VERY new to programming, this is my first year so it's pretty difficult for me.

I'm getting a segmentation fault when i try to run this and im not sure why.

> 

[PHP]#include <stdlib.h>
#include <stdio.h>
#include <stdbool.h>
 int **createMatrix (int m, int n)
    {
        int **matrix;
        int i;

        matrix = (int**) malloc(m* sizeof (int*));
            for (i=0; i<m; i++)
                {
                    matrix[i]=(int*) malloc(n * sizeof (int));
                }

        return matrix;

    }

int **readMatrix (int m, int n)
{
    int **matrix = createMatrix(m, n);


    int value;
    int i = 0;

   while (i < m)
        {
            int j = 0;
                while (j < n)
                {
                    scanf("%d", &value);
                    matrix[i][j] = value;
                    j++;
                }
                    char newline;
                    scanf("%c", &newline);
                    i++;

                }

        }

    void printMatrix (int **matrix, int m, int n)
{

        int i;
        int j;

        for (i = 0; i < m; i++)
        {
            for (j = 0; j < n; j++)
            {
                printf("%10d", matrix[i][j]);
            }

            printf("\n");
        }


}



int main (void)
{
    int n = 4;
    int m = 4;
    int **A;


    printf("Enter a 4x4 matrix:\n");

    A = readMatrix(m,   n);
    printMatrix(A, m, n);

    return 0;






}
[/PHP]



edit- also im trying to figure out how to post this code in a more readable fashion, i apologize ><

Kay I found the PHP button sorry about that
So the objective Of this assignment is to dynamically Allocate Memory for a matrix Of unknown Size, then read a user inputted matrix Into each individual Slot of the matrix, then print it out.

Both My Create matrix and read matrix functions work fine, it was after i implemented my printMatrix function That i got a segmentation fault, any advice would be appreciated I dont know how to continue :)

---

### Post by randumnumber on 2010-11-05
for me i am able to read in an array 1 line at a time but after the 16th number it gives seg fault. so your reading in correctly...look through the part where you are printing the array. 

this program should readlike this right?
enter 4x4 array
1
2
3
4
1
2
3
4
1
2
3
4
1
2
3
4

then print the array back right?

---

### Post by VanillaCone on 2010-11-05
Ive been Inputting numbers like this:
1 2 3 4
1 2 3 4
1 2 3 4
1 2 3 4 

but i think itl Work both ways, and yes I know theres a problem with how im printing It im just not sure what it is, or what to change

---

### Post by randumnumber on 2010-11-05
[http://bytes.com/topic/c/answers/537723-print-matrix](http://bytes.com/topic/c/answers/537723-print-matrix)

here are some examples of how to print an array in the fashion you are trying... try testing your method by hard coding an array and printing it. once that works try inputing the array.

---

### Post by VanillaCone on 2010-11-05
Ya i found that site too, i tried their exact example but no luck.

---

### Post by randumnumber on 2010-11-05
googling "print a matrix in c" bring up a ton of sites that could help. i took c and c++ but that was 4 years ago. and i dont remember much now.

---

### Post by randumnumber on 2010-11-05
Does it have to use your subroutine structure?

---

### Post by randumnumber on 2010-11-05
sorry i cant help more.

BUMP.

---

### Post by VanillaCone on 2010-11-05
Its okay thanks for your help :), ill keep trying

---

### Post by worksofcraft on 2010-11-05
well IMO you need to return a value from readMatrix.
Would you like me post a working version or you ok with that?

---

### Post by Some Penguin on 2010-11-05
I would be very surprised if -Wall didn't print warnings for functions that declare a non-void return type but have paths which don't actually have return statements.

---

### Post by VanillaCone on 2010-11-05
What Would i return From read matrix, Not sure what to write

---

### Post by VanillaCone on 2010-11-05
NVM im so silly ^.^, I just put Return matrix, thank you very Much it works now!

---

### Post by GeneralZod on 2010-11-05
Follow Some Penguin's advice and compile with GCC's -Wall and -Wextra options from now on: it will save you plenty of heartache in the future :)

---

### Post by NovaAesa on 2010-11-05
Try the -pedantic option as well, I find it helps make sure code is written in a standard way.

---

