---
title: "C error passing structs to functions with header files"
date: 2010-10-01
forum: Packaging and Compiling Programs
---

### Post by J3TTBlack88 on 2010-10-01
My friend and I have been working solidly for 4 hours trying to fix an error when compiling a project. 

Our main function code is:

#include <stdio.h>
#include <stdlib.h>
#include "gridFunctions.h"

struct entry
{
	int options[9];
	int done;
};

int main()
{
	element arr[9][9];
	element* ptr;
	ptr = &arr[9][9];
	
	arr[0][0].done = 0;
	arr[0][1].done = 0;
	arr[0][2].done = 4;
	arr[0][3].done = 0;	
	arr[0][4].done = 8;	
	arr[0][5].done = 0;	
	arr[0][6].done = 6;	
	arr[0][7].done = 0;	
	arr[0][8].done = 0;
	
	arr[1][0].done = 9;	
	arr[1][1].done = 1;	
	arr[1][2].done = 8;	
	arr[1][3].done = 5;	
	arr[1][4].done = 0;	
	arr[1][5].done = 0;	
	arr[1][6].done = 4;	
	arr[1][7].done = 0;	
	arr[1][8].done = 2;
	
	arr[2][0].done = 2;	
	arr[2][1].done = 0;	
	arr[2][2].done = 0;	
	arr[2][3].done = 0;	
	arr[2][4].done = 0;	
	arr[2][5].done = 4;	
	arr[2][6].done = 0;	
	arr[2][7].done = 0;	
	arr[2][8].done = 0;
	
	arr[3][0].done = 0;	
	arr[3][1].done = 0;	
	arr[3][2].done = 0;	
	arr[3][3].done = 9;	
	arr[3][4].done = 0;	
	arr[3][5].done = 0;	
	arr[3][6].done = 0;	
	arr[3][7].done = 0;	
	arr[3][8].done = 0;
	
	arr[4][0].done = 7;	
	arr[4][1].done = 0;	
	arr[4][2].done = 6;	
	arr[4][3].done = 0;	
	arr[4][4].done = 2;	
	arr[4][5].done = 0;	
	arr[4][6].done = 1;	
	arr[4][7].done = 0;	
	arr[4][8].done = 8;
	
	arr[5][0].done = 0;	
	arr[5][1].done = 0;	
	arr[5][2].done = 0;	
	arr[5][3].done = 0;	
	arr[5][4].done = 0;	
	arr[5][5].done = 7;	
	arr[5][6].done = 0;	
	arr[5][7].done = 0;	
	arr[5][8].done = 0;
	
	arr[6][0].done = 0;	
	arr[6][1].done = 0;	
	arr[6][2].done = 0;	
	arr[6][3].done = 8;	
	arr[6][4].done = 0;	
	arr[6][5].done = 0;	
	arr[6][6].done = 0;	
	arr[6][7].done = 0;	
	arr[6][8].done = 1;
	
	arr[7][0].done = 5;	
	arr[7][1].done = 0;	
	arr[7][2].done = 2;	
	arr[7][3].done = 0;	
	arr[7][4].done = 0;	
	arr[7][5].done = 1;	
	arr[7][6].done = 3;	
	arr[7][7].done = 4;	
	arr[7][8].done = 7;
	
	arr[8][0].done = 0;	
	arr[8][1].done = 0;	
	arr[8][2].done = 1;	
	arr[8][3].done = 0;	
	arr[8][4].done = 3;	
	arr[8][5].done = 0;	
	arr[8][6].done = 2;	
	arr[8][7].done = 0;	
	arr[8][8].done = 0;

	fillGrid(ptr);

	return 0;
}

Where gridFunctions.h is:

struct entry
{
	int options[9];
	int done;
};

void fillGrid(element* grid[9][9]);

and gridFunctions.c is:

void fillGrid(struct entry grid[9][9])

	int i, j, k;

	for(i = 0; i < 9; i++)
	{
		for(j = 0; j < 9; j++)
		{
			for(k = 0; k < 9; k++)
			{
				grid[i][j].options[k] = (k + 1);
			}
		}
	}
}

When compiling we recieve a number of very strange errors, including:

1>------ Build started: Project: Project_part01, Configuration: Debug Win32 ------
1>Compiling...
1>part01.c
1>c:\users\j3ttblack88\documents\programming\project_part01\project_part01\gridFunctions.h(7) : error C2143: syntax error : missing ')' before '*'
1>c:\users\j3ttblack88\documents\programming\project_part01\project_part01\gridFunctions.h(7) : error C2143: syntax error : missing '{' before '*'
1>c:\users\j3ttblack88\documents\programming\project_part01\project_part01\gridFunctions.h(7) : error C2059: syntax error : ')'
1>.\part01.c(6) : error C2011: 'entry' : 'struct' type redefinition
1>        c:\users\j3ttblack88\documents\programming\project_part01\project_part01\gridFunctions.h(2) : see declaration of 'entry'
1>.\part01.c(107) : warning C4013: 'fillGrid' undefined; assuming extern returning int
1>gridFunctions.c
1>.\gridFunctions.c(1) : error C2146: syntax error : missing ')' before identifier 'grid'
1>.\gridFunctions.c(1) : error C2061: syntax error : identifier 'grid'
1>.\gridFunctions.c(1) : error C2059: syntax error : ';'
1>.\gridFunctions.c(1) : error C3409: empty attribute block is not allowed
1>.\gridFunctions.c(1) : error C2143: syntax error : missing ']' before 'constant'
1>.\gridFunctions.c(1) : error C2059: syntax error : ')'
1>.\gridFunctions.c(5) : error C2059: syntax error : 'for'
1>.\gridFunctions.c(5) : error C2143: syntax error : missing '{' before '<'
1>.\gridFunctions.c(5) : error C2059: syntax error : '<'
1>.\gridFunctions.c(5) : error C2143: syntax error : missing '{' before '++'
1>.\gridFunctions.c(5) : error C2059: syntax error : '++'
1>.\gridFunctions.c(5) : error C2059: syntax error : ')'
1>.\gridFunctions.c(15) : error C2059: syntax error : '}'

If anyone can help, we would greatly appreciate it.

---

