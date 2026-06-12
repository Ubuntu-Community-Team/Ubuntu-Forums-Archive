---
title: "What does this mean? &quot;Command terminated by signal (11: SIGSEGV)&quot;"
date: 2007-12-21
forum: Programming Talk
---

### Post by dolgion1 on 2007-12-21
hello 
can anybody tell me what this error message means?
what are possible reasons for this to appear?

if its necessary here is the code:

#include <stdio.h>
#include <stdlib.h>

int checkSame (int *array1, int *array2)
{
	int i;
	for (i = 0; i < 8; i++)
	{
		if (array1[i] != array2[i])
			return -1;
	}
	return 1;
}

int* A (int *array)
{
	int *new_array = malloc (8*sizeof(int));
	new_array[0] = array[1];
	new_array[1] = array[2];
	new_array[2] = array[3];
	new_array[3] = array[4];
	new_array[4] = array[5];
	new_array[5] = array[6];
	new_array[6] = array[7];
	new_array[7] = array[0];
	return new_array;
}

int* B (int *array)
{
	int *new_array = malloc (8*sizeof(int));
	new_array[0] = array[0];
	new_array[1] = array[4];
	new_array[2] = array[1];
	new_array[3] = array[5];
	new_array[4] = array[2];
	new_array[5] = array[6];
	new_array[6] = array[3];
	new_array[7] = array[7];
	return new_array;
}

int* C (int *array)
{
	int *new_array = malloc (8*sizeof(int));
	new_array[0] = array[4];
	new_array[1] = array[0];
	new_array[2] = array[5];
	new_array[3] = array[1];
	new_array[4] = array[6];
	new_array[5] = array[2];
	new_array[6] = array[7];
	new_array[7] = array[3];
	return new_array;
}

int* (*funcTable[3])(int*) = {A, B, C};

int main()
{
	int positions[8], blank[8], idx = 0, i, j, k = 3, found = 0,
		*arrays[500][500], f = 0, a = 0;
	float currentk, currenti;
	char way[100000];

	for (i = 0; i < 8; i++)
	{
		scanf("%d",&positions[i]);	
		blank[i] = i+1;
	}

	for (i = 0; i < k; i++)
	{
		arrays[idx][i] = malloc(8*sizeof(int));
		for (j = 0; j < 8; j++)
		{		
			arrays[idx][i][j] = blank[j];
		}	
	}
	idx++;
	while (found != 1)
	{	
		for (i = 0; i < k; i++)
		{	
			arrays[idx][i] = funcTable[f](arrays[idx-1][a]);			
			if ((i+1) == (k/3)*(f+1)) {f++; a=0;}	
			else a++;	
		}
		for (i = 0; i < k; i++)
		{
			if (checkSame(arrays[idx][i],positions) == 1)
			{
				currentk = (float)k/3;
				currenti = (float)i;
				int lowend = 0;
				int highend = k;
				for (j = idx; j > 0; j--)
				{
					if (currenti < lowend + currentk) {way[j-1] = 'A'; highend = lowend + currentk;}
					else if (currenti < lowend + currentk*2) {way[j-1] = 'B'; highend = lowend + currentk*2; lowend = lowend + currentk;}
					else if (currenti < highend) {way[j-1] = 'C'; lowend = highend - currentk;}
					currentk /= 3;						
				} 
				printf("%s",way);
				found = 1;
			}				
		}
		k *= 3;
		idx++;
		f = 0;
		a = 0;
		for (i = 0; i < k; i++)
		{
			arrays[idx][i] = malloc(8*sizeof(int));
		}
	}
	printf("\n");	
	return 0;
}

thank for help

---

### Post by Tuna-Fish on 2007-12-21
SIGSEGV Means that you just got a segmentation fault, which in turn means that you tried to access memory that you shouldn't have.

Could you repost the code, but put it between  {PHP} {/PHP} tags (replace { with [), it would preserve indentation and color your code, that would make it a lot more readable, so I can locate the actual error. Thanks.

---

### Post by Wybiral on 2007-12-21
It's probably a buffer overflow or it could be a memory leak from all of those mallocs. I can't tell though because I can't read your code (please use the [ code ] tags to post code that we can read).

EDIT:

Tuna-Fish beat me to it!

---

### Post by Tuna-Fish on 2007-12-21
Actually, I was bored, so I just ran it trough "indent -kr".
Analysis will follow.

[PHP]#include <stdio.h>
#include <stdlib.h>

int checkSame(int *array1, int *array2)
{
    int i;
    for (i = 0; i < 8; i++) {
	if (array1[i] != array2[i])
	    return -1;
    }
    return 1;
}

int *A(int *array)
{
    int *new_array = malloc(8 * sizeof(int));
    new_array[0] = array[1];
    new_array[1] = array[2];
    new_array[2] = array[3];
    new_array[3] = array[4];
    new_array[4] = array[5];
    new_array[5] = array[6];
    new_array[6] = array[7];
    new_array[7] = array[0];
    return new_array;
}

int *B(int *array)
{
    int *new_array = malloc(8 * sizeof(int));
    new_array[0] = array[0];
    new_array[1] = array[4];
    new_array[2] = array[1];
    new_array[3] = array[5];
    new_array[4] = array[2];
    new_array[5] = array[6];
    new_array[6] = array[3];
    new_array[7] = array[7];
    return new_array;
}

int *C(int *array)
{
    int *new_array = malloc(8 * sizeof(int));
    new_array[0] = array[4];
    new_array[1] = array[0];
    new_array[2] = array[5];
    new_array[3] = array[1];
    new_array[4] = array[6];
    new_array[5] = array[2];
    new_array[6] = array[7];
    new_array[7] = array[3];
    return new_array;
}

int *(*funcTable[3]) (int *) = {
A, B, C};

int main()
{
    int positions[8], blank[8], idx = 0, i, j, k = 3, found = 0,
	*arrays[500][500], f = 0, a = 0;
    float currentk, currenti;
    char way[100000];

    for (i = 0; i < 8; i++) {
	scanf("%d", &positions[i]);
	blank[i] = i + 1;
    }

    for (i = 0; i < k; i++) {
	arrays[idx][i] = malloc(8 * sizeof(int));
	for (j = 0; j < 8; j++) {
	    arrays[idx][i][j] = blank[j];
	}
    }
    idx++;
    while (found != 1) {
	for (i = 0; i < k; i++) {
	    arrays[idx][i] = funcTable[f] (arrays[idx - 1][a]);
	    if ((i + 1) == (k / 3) * (f + 1)) {
		f++;
		a = 0;
	    } else
		a++;
	}
	for (i = 0; i < k; i++) {
	    if (checkSame(arrays[idx][i], positions) == 1) {
		currentk = (float) k / 3;
		currenti = (float) i;
		int lowend = 0;
		int highend = k;
		for (j = idx; j > 0; j--) {
		    if (currenti < lowend + currentk) {
			way[j - 1] = 'A';
			highend = lowend + currentk;
		    } else if (currenti < lowend + currentk * 2) {
			way[j - 1] = 'B';
			highend = lowend + currentk * 2;
			lowend = lowend + currentk;
		    } else if (currenti < highend) {
			way[j - 1] = 'C';
			lowend = highend - currentk;
		    }
		    currentk /= 3;
		}
		printf("%s", way);
		found = 1;
	    }
	}
	k *= 3;
	idx++;
	f = 0;
	a = 0;
	for (i = 0; i < k; i++) {
	    arrays[idx][i] = malloc(8 * sizeof(int));
	}
    }
    printf("\n");
    return 0;
}
[/PHP]

---

### Post by wolfbone on 2007-12-21
> **Tuna-Fish said:**
> SIGSEGV Means that you just got a segmentation fault, which in turn means that you tried to access memory that you shouldn't have..

Sure looks that way.

[[IMG]http://img207.imageshack.us/img207/8519/screenshotul5.th.png[/IMG]](http://img207.imageshack.us/my.php?image=screenshotul5.png)

---

### Post by Tuna-Fish on 2007-12-21
Well, I can give you the immediate cause.
One one iteration, idx,i f and a are zero. On the line:
arrays[idx][i] = funcTable[f] (arrays[idx - 1][a]);

arrays[idx-1][a] refers to outside the array if idx is 0. (it's arrays[-1][a] then...)

I still have no idea whatsoever what the code does.

---

### Post by Tuna-Fish on 2007-12-21
On a second look, I think how the code terminates depends on the input.

Mine was with =
9
8
7
6
5
6
5
4

---

### Post by monkeyking on 2007-12-22
As told it is a problem with the memory,
youre trying to access parts of the memory your're not allowed to.

For small programs it's often quite clear, where the problem is.
array index out of bounds or similar.

But for bigger programs, it can be close to hell finding these sigsegv.

I'm using a combination of 2 tools for tracking down these errors.
gdb and valgrind.
First af all compile with -g.
and then
```

gdb ./myprog
valgrind ./myprog

```
gdb will tell you on which line the error occured,
and valgrind can be using to check for errors even though the program doesn't crash.

Actually valgrind should be used to check all programs

---

