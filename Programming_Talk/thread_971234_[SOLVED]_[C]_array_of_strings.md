---
title: "[SOLVED] [C] array of strings"
date: 2008-11-04
forum: Programming Talk
---

### Post by swappo1 on 2008-11-04
Hello,
I have the following program and I am getting a segmentation fault after I enter the first string.  I am not sure what the problem is.  This is an excercise using pointers to make an array of strings.  The user inputs 10 oceans/seas and the data is printed to the screen. Any help would be greatly appreciated.
[PHP]#include <stdio.h>
#include <stdlib.h>

void input_array(char *seas[10][12], int rows, int cols);
void output_array(char *seas[10][12], int rows, int cols);

int main(void)
{
	int count, rows=10, cols=12;
	char *seas[10][12];
	for(count=0; count<rows; count++)
		*seas[count] = (char *) malloc(cols * sizeof(char));
	
	input_array(seas, rows, cols);
	output_array(seas, rows, cols);
	return(EXIT_SUCCESS);
}
void input_array(char *seas[10][12], int rows, int cols)
{
	int count, count2;

	for(count=0; count<rows; count++)
		{
		
		printf("Enter a string: ");
		for(count2=0; (*seas[count][count2] = getchar()) != '\n'; count2++);
		}
	printf("\n");
	return;
}
void output_array(char *seas[10][12], int rows, int cols)
{
	int count, count2;
	
	for(count=0; count<rows; count++)
		for(count2=0; count<cols; count2++)
			printf("%s\n", *(*(seas + count) + count2));
	printf("\n");
	return;
}
[/PHP]

---

### Post by British0zzy on 2008-11-04
I modified your original code and it seems like your were trying to allocate a matrix of strings.

```
#include <stdio.h>
#include <stdlib.h>

void input_array(char seas[10][12], int rows, int cols);
void output_array(char seas[10][12], int rows, int cols);

int main(void)
{
    int rows=10, cols=12;
    char seas[10][12]; /* this does not need to be a pointer to char because seas[10] is a pointer to char already */

// no mallocing needed as the array was declared
    
    input_array(seas, rows, cols);
    output_array(seas, rows, cols);
    return(EXIT_SUCCESS);
}

void input_array(char seas[10][12], int rows, int cols)
{
    int count, count2;
    
    for(count=0; count<rows; count++)
    {    
        printf("Enter a string: ");
        for(count2=0; (seas[count][count2] = getchar()) != '\n'; count2++);
        seas[count][count2] = '\0';
    }
    printf("\n");
    return;
}

void output_array(char seas[10][12], int rows, int cols)
{
    int count;
    
    for(count=0; count<rows; count++)
        printf("%s\n", seas[rows]); // fancy array math won't get you anywhere (referring to *(*(seas + count) + count2))
    printf("\n");
    return;
}
```

---

### Post by swappo1 on 2008-11-04
Thanks for your reply BrittishOzzy.  I understand and appreciate your changes.  I am trying to do an exercise using pointers(i'm still learning to use them).  That's why I put them in.  Also, using pointers and allocating the memory as it is needed is part of the exercise, and an important part.  There are several other, simpler, ways I have done this exercise, but this is the way that will help me to apply pointers to solve my problem.

Thanks

---

### Post by British0zzy on 2008-11-04
well, then to my previous code, there is just a quick change to the main function:

```
int main(void)
{
    int count, rows=10, cols=12;
    char *seas[10]; //remove the [12] as these 12 chars will be malloc'd later.
    for(count=0; count<rows; count++)
        seas[count] = (char *) malloc(cols * sizeof(char)); // no need for *seas[count] as seas[count] is a char*
    
    input_array(seas, rows, cols);
    output_array(seas, rows, cols);
    return(EXIT_SUCCESS);
}
```

btw, never forget to null terminate a variable length string (or include a way to track length)

---

### Post by swappo1 on 2008-11-05
Ok BritishOzzy that helped.  I got it to work now.  Thanks.

---

