---
title: "C Segmentation fault in simple (?) program"
date: 2009-05-18
forum: Programming Talk
---

### Post by matmatmat on 2009-05-18
I have a simple c program to play rock paper scissors:
```

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main (int argc, char *argv[])
{
  /* Simple "srand()" seed: just use "time()" */
  unsigned int iseed = (unsigned int)time(NULL);
  srand (iseed);
  int ai;
  int p = 1000;
  while (p != 0){
	printf("0) Quit\n1) Rock\n2) Paper\n3)Scissors\n");
	scanf("%d", p);
	ai = rand() % 3;
	if (ai == 1){
		if (p == 1){
			printf("AI: Rock\n");
			printf("Draw!\n");
		}
		else if (p == 2){
			printf("AI: Rock\n");
			printf("You win!\n");
		}
		else if (p == 3){
			printf("AI Rock\n");
			printf("You lose!\n");
		}
	}
	else if (ai == 2){
		if (p == 1){
			printf("AI: Paper\n");
			printf("You lose!\n");
		}
		else if (p == 2){
			printf("AI: Paper\n");
			printf("Draw!\n");
		}
		else if (p == 3){
			printf("AI: Paper\n");
			printf("You win\n");
		}
	}
	else{
		if (p == 1){
			printf("AI: Scissors\n");
			printf("You win\n");
		}
		else if (p == 2){
			printf("AI: Scissors\n");
			printf("You lose\n");
		}
		else if (p == 3){
			printf("AI: Scissors\n");
			printf("Draw!\n");
		}
	}
  }
  return 0;
}

```
it gives a Segmentation fault, I think it's the loop or the random number?

---

### Post by PmDematagoda on 2009-05-18
Compiling the application using the -Wall argument of GCC gives the problem:-
```
rocks.c: In function ‘main’:
rocks.c:14: warning: format ‘%d’ expects type ‘int *’, but argument 2 has type ‘int’
```

scanf() requires a pointer to variable p, what you are doing is giving it the value 1000, which is invalid and is the reason for the segmentation fault.

---

### Post by matmatmat on 2009-05-18
Do i make a pointer to p?
```

int * pointp = p;

```

---

### Post by PmDematagoda on 2009-05-18
> **matmatmat said:**
> Do i make a pointer to p?
```

int * pointp = p;

```

That is still wrong, you are assigning the pointer the memory address of 1000(which is just the value of p), which would still cause a segfault, haven't you used the & operator which gives the memory address of a particular variable/pointer?

What the scanf statement should be is this:-
```
	scanf("%d", &p);
```

---

### Post by matmatmat on 2009-05-18
Thanks

---

### Post by bostonaholic on 2009-05-18
use
```
scanf("%d", &p);
```

This way scanf will pass the memory address of p.  Before, you were telling scanf to use the memory address of the value of p--which is incorrect.

---

