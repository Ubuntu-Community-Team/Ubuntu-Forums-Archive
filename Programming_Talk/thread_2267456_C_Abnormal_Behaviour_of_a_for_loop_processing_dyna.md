---
title: "C: Abnormal Behaviour of a for loop processing dynamically created 2d arrays"
date: 2015-03-01
forum: Programming Talk
---

### Post by Ayush_Agrawal on 2015-03-01
**Scenario: **I was working on this simple problem of creating(dynamically) a 2d array: taking input from the user and printing out the elements in matrix fashion.

**Problem: **There was _no compilation error_ but during runtime something strange happened. For eg. a 2X2 matrix should take 4 inputs but it took two only. The other two values were provided garbage value or zero.

[B]Code:

[/B]#include <stdio.h>
#include <stdlib.h>

int main(int argc, char const *argv[])
{
    int **twoD;
    printf("Enter the number of rows: ");
    int r;
    scanf("%d",&r);

    twoD=(int**)malloc(r*sizeof(int*));
  
    printf("Enter the number of columns: ");
    int c;
    scanf("%d",&c);

    int i=0,j=0;
    for(;i<r;i++)
    {
        twoD[i]=(int*)malloc(c*sizeof(int));
        for(;j<c;j++)
            scanf("%d",&twoD[i][j]);
    }

    printf("The entered matrix is: \n");
    
        int x=0,y=0;
    for(x=0;x<r;x++)
    {
        for(y=0;y<c;y++)
            printf("%d\t",twoD[x][y]);
    puts("");
    }
    return 0;
}

[B]
My attempt:  [/B]I did try to change things in order to fix it and I came across a solution. The problem can be solved by completing the blank field in the nested for loops which are used for storing the inputs. If i use "i=0" (and "j=0" in the inner loop) the problem would cease.

I could not really understand the reason behind it. I did initialise 'i' and 'j' with zero.


!!!!!!!!!!!!!!!!!! HELP !!!!!!!!!!!!!!!!!!!!

---

### Post by spjackson on 2015-03-01
You need to reset j to 0 for each iteration of the outer loop. Otherwise, the second (and any subsequent) time through the outer loop j is already equal to c and therefore the inner loop won't execute at all.

---

### Post by Ayush_Agrawal on 2015-03-03
That was simple.. :) 

Thanks for your help . ;)

---

