---
title: "Return an array, c++"
date: 2007-11-30
forum: Programming Talk
---

### Post by rzrgenesys187 on 2007-11-30
We have to do a program for my engineering class where they want us to return an array from a function to the main function.  I have no idea how to do this without pointers (which is what they want).  Any help would be appreciated.

```

#include <stdio.h>

double read_datafile();

int main()
{
	double temp_var[30][30], size1[2], size2[2];
	int i, j;
	
	temp_var = read_datafile(); // Calls the read_datafile function
	size1[0] = temp_var[0][0];
	size1[1] = temp_var[0][1];
	double matrix1[(int)size1[0]][(int)size1[1]];
	for (i = 0; i <= size1[0] - 1; i++)
	{
		for (j = 0; j <= size1[1] - 1; j++)
		{
			matrix1[i][j] = temp_var[i + 1][j];
		}
	}
	
	temp_var = read_datafile();
	size2[0] = temp_var[0][0];
	size2[1] = temp_var[0][1];
	double matrix2[(int)size2[0]][(int)size2[1]];
	for (i = 0; i <= size2[0] - 1; i++)
	{
		for (j = 0; j <= size2[1] - 1; j++)
		{
			matrix2[i][j] = temp_var[i + 1][j];
		}
	}
}

double read_datafile()  //Reads in the size of the matrix and the matrix itself.  Returns this to the main function
{
	char filename[30];
	FILE *input;
	double rows, columns;
	double matrix[30][30];  // Declares the matrix variable
	double return_var[30][30];  // Declares the variable to be returned
	
	printf("What is the name of the file the matrix is in? ");
	scanf("%s", filename);
	
	input = fopen(filename, "r");
	
	fscanf(input, "%lf %lf", &rows, &columns);
	
	return_var[0][0] = rows;
	return_var[0][1] = columns;
	
	for (int i = 0; i <= rows -1; i++)
	{
		for (int j = 0; j <= columns - 1; j++)
		{
			fscanf(input, "%lf", &matrix[i][j]);
			return_var[i + 1][j] = matrix[i][j];
		}
	}
	
	return(return_var);
}

```

the errors i get are
Assignment12.cpp: In function &#8216;int main()&#8217;:
Assignment12.cpp:10: error: incompatible types in assignment of &#8216;double&#8217; to &#8216;double [30][30]&#8217;
Assignment12.cpp:22: error: incompatible types in assignment of &#8216;double&#8217; to &#8216;double [30][30]&#8217;
Assignment12.cpp: In function &#8216;double read_datafile()&#8217;:
Assignment12.cpp: error: cannot convert &#8216;double (*)[30]&#8217; to &#8216;double&#8217; in retur

---

### Post by rzrgenesys187 on 2007-11-30
Sorry to waste anyone's time and a thread i solved the problem.

Apologies again.

---

### Post by evarlast on 2007-11-30
Could you post the solution so that others can learn from what you did?

---

### Post by rzrgenesys187 on 2007-11-30
No problem
```

#include <stdio.h>
#include <ctype.h>

double read_datafile();
char menu();

int main()
{
	double temp_var[30][30], size1[2], size2[2];
	int i, j;
	char choice();
	
	temp_var[30][30] = read_datafile(); // Calls the read_datafile function
	size1[0] = temp_var[0][0];
	size1[1] = temp_var[0][1];
	double matrix1[(int)size1[0]][(int)size1[1]];
	for (i = 0; i <= size1[0] - 1; i++)
	{
		for (j = 0; j <= size1[1] - 1; j++)
		{
			matrix1[i][j] = temp_var[i + 1][j];
		}
	}
	
	temp_var[30][30] = read_datafile();
	size2[0] = temp_var[0][0];
	size2[1] = temp_var[0][1];
	double matrix2[(int)size2[0]][(int)size2[1]];
	for (i = 0; i <= size2[0] - 1; i++)
	{
		for (j = 0; j <= size2[1] - 1; j++)
		{
			matrix2[i][j] = temp_var[i + 1][j];
		}
	}
	
	choice = menu(); // Calls the menu function
}

double read_datafile() //Reads in the size of the matrix and the matrix itself.  Returns this to the main function
{
	char filename[30];
	FILE *input;
	double rows, columns;
	double matrix[30][30];  // Declares the matrix variable
	double return_var[30][30];  // Declares the variable to be returned
	
	printf("What is the name of the file the matrix is in? ");
	scanf("%s", filename);
	
	input = fopen(filename, "r");
	
	fscanf(input, "%lf %lf", &rows, &columns);
	
	return_var[0][0] = rows;
	return_var[0][1] = columns;
	
	for (int i = 0; i <= rows -1; i++)
	{
		for (int j = 0; j <= columns - 1; j++)
		{
			fscanf(input, "%lf", &matrix[i][j]);
			return_var[i + 1][j] = matrix[i][j];
		}
	}
	
	return(return_var[30][30]);
}

char menu() // Calls a function to display a menu and return the user's choice
{
	char choice;
	int i = 1;
	
	printf("\nEnter A to add two matrices\nEnter S to subtract two matrices\nEnter M to multiply two matrices\nEnter E to multiply the element by elements of two matrices\nEnter N to move to next case\nEnter X to exit\nPlease enter your choice\n");
	
	do
	{
		printf("choice: ");
		fflush(stdin);
		scanf(" %c", &choice);
		
		switch (tolower(choice))
		{
			case 'a': case 's': case 'm': case 'e': case 'n': case 'x':
				i = 0;
				break;
			default:
				printf("Invalid Entry!\n");
		}
	} while (i);
	
	return(choice);
}

```

i just added [30][30] into the return statement.  I've also added another function.

---

### Post by Majorix on 2007-11-30
That's a pointer, myArray[x][y] that is. It points to the x,y'th element in the array. So is myArray alone, which points to the first element of the array.

---

