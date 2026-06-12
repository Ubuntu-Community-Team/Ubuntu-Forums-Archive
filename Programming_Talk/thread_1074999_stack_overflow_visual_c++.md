---
title: "stack overflow visual c++"
date: 2009-02-19
forum: Programming Talk
---

### Post by 65daysofstatic on 2009-02-19
hi, 
I have a problem in a program in c++, in the recursive call it shows the error of stack overflow.I also tried in java and gave me the same error but i could handle it a bit with the try-catch.


i dont know if you need more info...hehe

When i call for a matrix of 2*2 there is no problem because its the base of the solution, the problem starts when the function has to make its recursive calls and give me the message of Stack overflow

heres the code:
[PHP]#include <iostream>
#include <Math.h>
#include <cstdlib>
#include <ctime>
#define randomize() (srand((unsigned)time(NULL)))
#define random(x) (rand() % x) 

using namespace std;

void triomino(int firstRow, int lastRow, int firstColumn, int lastColumn, int keyRow, int keyCol);

static int cont;
static int mat[32][32];

/*
this function uses the Divide and Conquer approach
You have a matrix of 2^i * 2^i and divide it in four equal sections
when the size is 2*2 you fill it with a number and one spot is like a key
1  1  2  2
1  3  3  2
4 -1  3  5
4  4  5  5
thats the example of what should be the result, the -1 indicates the cell that is the main key and when it 
divides in subproblems you assign like a temporary key like the 3 in the position (1,2)
*/
void triomino(int firstRow, int lastRow, int firstColumn, int lastColumn, int keyRow, int keyCol)
{
	if((lastRow - firstRow) == 2) //this is the base when the matrix is 2*2 you fill the cells 
	{
		for(int i = firstRow; i <lastRow;i++)
		{
			for(int j = firstColumn ; j < lastColumn; j++)
			{
				if(i != keyRow || j != keyCol)//to avoid filling the cell that is the key.
				{
					mat[i][j] = cont;
				}
			}
		}
		cont++;//this counter is for asigning the numbers that are in the cells and each time it fill 3 cells it changes
	}else
	{
		int rm = (lastRow + firstRow) /2;  // half of the rows
		int cm = (firstColumn + lastColumn) / 2; // half of the columns
		//the next ifs are to locate the key and call the function in the appropiate way
		if(keyRow <= rm && keyCol <= cm) //asks if the key is in that section
		{
			mat[rm][cm+1] = cont;
			mat[rm + 1][cm] = cont;
			mat[rm + 1][cm+1] = cont;
			cont++;
			triomino(firstRow,rm,firstColumn,cm,keyRow,keyCol);
			triomino(firstRow, rm, cm + 1, lastColumn, rm, cm + 1);
			triomino(rm + 1, lastRow, firstColumn, cm, rm + 1,cm);
			triomino(rm + 1, lastRow, cm + 1, lastColumn, rm + 1, cm+1);
		}else if (keyRow <= rm && keyCol > cm)
		{
			mat[rm][cm] = cont;
			mat[rm + 1][cm] = cont;
			mat[rm + 1][cm+1] = cont;
			cont++;
			triomino(firstRow,rm,firstColumn,cm,rm,cm);
			triomino(firstRow, rm, cm + 1, lastColumn, keyRow, keyCol);
			triomino(rm + 1, lastRow, firstColumn, cm, rm + 1,cm);
			triomino(rm + 1, lastRow, cm + 1, lastColumn, rm + 1, cm+1);
		}else if(keyRow > rm && keyCol <= cm)
		{
			mat[rm][cm] = cont;
			mat[rm][cm + 1] = cont;
			mat[rm + 1][cm+1] = cont;
			cont++;
			triomino(firstRow,rm,firstColumn,cm,rm,cm);
			triomino(firstRow, rm, cm + 1, lastColumn, rm, cm + 1);
			triomino(rm + 1, lastRow, firstColumn, cm, keyRow,keyCol);
			triomino(rm + 1, lastRow, cm + 1, lastColumn, rm + 1, cm+1);
		}else if(keyRow > rm && keyCol > cm)
		{
			mat[rm][cm] = cont;
			mat[rm][cm + 1] = cont;
			mat[rm + 1][cm] = cont;
			cont++;
			triomino(firstRow,rm,firstColumn,cm,rm,cm);
			triomino(firstRow, rm, cm + 1, lastColumn, rm, cm + 1);
			triomino(rm + 1, lastRow, firstColumn, cm, rm + 1,cm);
			triomino(rm + 1, lastRow, cm + 1, lastColumn, keyRow, keyCol);
		}
	}

}


void main()
{
	randomize();
	int row, col, keyRow, keyCol;
	cout<< "de que tamano va a ser la matriz (2^i)?:"; //ask for matrix's size 2^i * 2^i you give the i
	cin>> row;
	row = pow(2.0, row);
	col = row ;
	cont = 0;
	keyRow = random(row); //assign the key in a random position
	keyCol = random(col);
	mat[keyRow][keyCol] = -1;
	triomino(0,row,0,col,keyRow,keyCol);
	for (int i = 0; i < row; i++)//displays the matrix
	{
		for (int j = 0; j < col ; j++)
		{
			cout << mat[i][j] << "  ";
		}
		cout << endl;
	}
	cin.get();
	cin.get();

}
[/PHP]

p.s. I am new in C++.

---

### Post by Can+~ on 2009-02-19
-No comments in code.
-2-letter variable names.
-No explanation on what the code does.

A menos de que corrijas lo que mencioné, no te puedo ayudar.

---

### Post by 65daysofstatic on 2009-02-19
srry I was making it fast that I didn't do the documentation of the code.
code with comments:
[PHP]#include <iostream>
#include <Math.h>
#include <cstdlib>
#include <ctime>
#define randomize() (srand((unsigned)time(NULL)))
#define random(x) (rand() % x) 

using namespace std;

void triomino(int firstRow, int lastRow, int firstColumn, int lastColumn, int keyRow, int keyCol);

static int cont;
static int mat[32][32];

/*
this function uses the Divide and Conquer approach
You have a matrix of 2^i * 2^i and divide it in four equal sections
when the size is 2*2 you fill it with a number and one spot is like a key
1  1  2  2
1  3  3  2
4 -1  3  5
4  4  5  5
thats the example of what should be the result, the -1 indicates the cell that is the main key and when it 
divides in subproblems you assign like a temporary key like the 3 in the position (1,2)
*/
void triomino(int firstRow, int lastRow, int firstColumn, int lastColumn, int keyRow, int keyCol)
{
	if((lastRow - firstRow) == 2) //this is the base when the matrix is 2*2 you fill the cells 
	{
		for(int i = firstRow; i <lastRow;i++)
		{
			for(int j = firstColumn ; j < lastColumn; j++)
			{
				if(i != keyRow || j != keyCol)//to avoid filling the cell that is the key.
				{
					mat[i][j] = cont;
				}
			}
		}
		cont++;//this counter is for asigning the numbers that are in the cells and each time it fill 3 cells it changes
	}else
	{
		int rm = (lastRow + firstRow) /2;  // half of the rows
		int cm = (firstColumn + lastColumn) / 2; // half of the columns
		//the next ifs are to locate the key and call the function in the appropiate way
		if(keyRow <= rm && keyCol <= cm) //asks if the key is in that section
		{
			mat[rm][cm+1] = cont;
			mat[rm + 1][cm] = cont;
			mat[rm + 1][cm+1] = cont;
			cont++;
			triomino(firstRow,rm,firstColumn,cm,keyRow,keyCol);
			triomino(firstRow, rm, cm + 1, lastColumn, rm, cm + 1);
			triomino(rm + 1, lastRow, firstColumn, cm, rm + 1,cm);
			triomino(rm + 1, lastRow, cm + 1, lastColumn, rm + 1, cm+1);
		}else if (keyRow <= rm && keyCol > cm)
		{
			mat[rm][cm] = cont;
			mat[rm + 1][cm] = cont;
			mat[rm + 1][cm+1] = cont;
			cont++;
			triomino(firstRow,rm,firstColumn,cm,rm,cm);
			triomino(firstRow, rm, cm + 1, lastColumn, keyRow, keyCol);
			triomino(rm + 1, lastRow, firstColumn, cm, rm + 1,cm);
			triomino(rm + 1, lastRow, cm + 1, lastColumn, rm + 1, cm+1);
		}else if(keyRow > rm && keyCol <= cm)
		{
			mat[rm][cm] = cont;
			mat[rm][cm + 1] = cont;
			mat[rm + 1][cm+1] = cont;
			cont++;
			triomino(firstRow,rm,firstColumn,cm,rm,cm);
			triomino(firstRow, rm, cm + 1, lastColumn, rm, cm + 1);
			triomino(rm + 1, lastRow, firstColumn, cm, keyRow,keyCol);
			triomino(rm + 1, lastRow, cm + 1, lastColumn, rm + 1, cm+1);
		}else if(keyRow > rm && keyCol > cm)
		{
			mat[rm][cm] = cont;
			mat[rm][cm + 1] = cont;
			mat[rm + 1][cm] = cont;
			cont++;
			triomino(firstRow,rm,firstColumn,cm,rm,cm);
			triomino(firstRow, rm, cm + 1, lastColumn, rm, cm + 1);
			triomino(rm + 1, lastRow, firstColumn, cm, rm + 1,cm);
			triomino(rm + 1, lastRow, cm + 1, lastColumn, keyRow, keyCol);
		}
	}

}


void main()
{
	randomize();
	int row, col, keyRow, keyCol;
	cout<< "de que tamano va a ser la matriz (2^i)?:"; //ask for matrix's size 2^i * 2^i you give the i
	cin>> row;
	row = pow(2.0, row);
	col = row ;
	cont = 0;
	keyRow = random(row); //assign the key in a random position
	keyCol = random(col);
	mat[keyRow][keyCol] = -1;
	triomino(0,row,0,col,keyRow,keyCol);
	for (int i = 0; i < row; i++)//displays the matrix
	{
		for (int j = 0; j < col ; j++)
		{
			cout << mat[i][j] << "  ";
		}
		cout << endl;
	}
	cin.get();
	cin.get();

}

[/PHP]

---

### Post by CptPicard on 2009-02-20
Well, simply put, your recursion just simply never terminates because you never reach the terminating base case. Or alternatively you have such a long recursive chain that you run out of stack space first.

Simply a bug in your program, and you'll be best equipped to debug your own code, by the looks of it. :)

---

