---
title: "Heading for a simple matrix addition"
date: 2010-07-16
forum: Programming Talk
---

### Post by navaneethan on 2010-07-16
> void main()
{
	int MAX,matrix[10][10],matrix1[10][10],sum[10][10],rows=2,cols=2,i,j,input;
	clrscr();
	printf("Enter elementd for 2X2 mat:");

	for(i=0;i<rows;i++)
	{
		for(j=0;j<cols;j++)
		{

		  scanf("%d",&matrix[i][j]);
		}
	}
	printf("\nEnter for the Matrix2:");
	for(i=0;i<rows;i++)
	{
		for(j=0;j<cols;j++)
		{

		  scanf("%d",matrix1[i][j]);
		}
	}
	for(i=0;i<rows;i++)
	{
		for(j=0;j<cols;j++)
		{
			sum[i][j]=matrix[i][j]+matrix1[i][j];
			printf("\nSUM is \t%d\t",sum[i][j]);
		}
		
	}

getch();
}

Here is nothing,
just get two input matrices 2X2 and adding finally displaying but getting some garbage values ...friend here i couldn't able think this problem ...plz let me know

---

### Post by dwhitney67 on 2010-07-16
You have an issue when storing the input values for your second matrix.  Here's what it should be:
```

scanf("%d",**&**matrix1[i][j]);

```
Note that an & has been added.


P.S.  Here's another way to write your code:
```

#include <stdio.h>


static const int ROWS = 2, COLS = 2;

void getMatrixValues(int** matrix)
{
   for(int r = 0; r < ROWS; ++r)
   {
      for(int c = 0; c < COLS; ++c)
      {
         printf("matrix[%d][%d] = ", r, c);
         scanf("%d", (int*)((matrix + (r * COLS) + c)));
      }
   }
}


int main(void)
{
   int matrix1[ROWS][COLS];
   int matrix2[ROWS][COLS];
   int sum[ROWS][COLS];

   printf("Enter elements for first %dX%d matrix:\n", ROWS, COLS);
   getMatrixValues((int**)matrix1);

   printf("\nEnter elements for second %dX%d matrix:\n", ROWS, COLS);
   getMatrixValues((int**)matrix2);

   printf("\n\n");
   for(int r = 0; r < ROWS; ++r)
   {
      for(int c = 0; c < COLS; ++c)
      {
         sum[r][c] = matrix1[r][c] + matrix2[r][c];

         printf("sum[%d][%d] = %d\n", r, c, sum[r][c]);
      }
   }
   printf("\n\n");

   getchar();
}

```

---

### Post by navaneethan on 2010-07-16
thanks sorry

---

### Post by trent.josephsen on 2010-07-16
Please, *please* put code in [code] tags.

Also, **main** is of type **int**, and clrscr() and getch() are non-standard; getch() is a standard part of conio.h, which you have already been advised not to use, but clrscr() is a compiler extension, I think.  What tutorial or book are you following?

---

