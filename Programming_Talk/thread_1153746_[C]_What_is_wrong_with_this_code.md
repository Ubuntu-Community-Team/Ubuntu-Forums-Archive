---
title: "[C] What is wrong with this code??"
date: 2009-05-09
forum: Programming Talk
---

### Post by Znupi on 2009-05-09
Really basic code. It allocates memory for a nxn two-dimensional array and *tries* to fill it out with zeros:
```
#include <stdio.h>
#include <stdlib.h>

int main() {
	short unsigned int n, **a, i, j;
	printf("n: "); scanf("%hu", &n);
	a = malloc(sizeof(short unsigned int) * n);
	for (i=0; i < n; i++) {
		a[i] = malloc(sizeof(short unsigned int) * n);
		for (j=0; j < n; j++) a[i][j] = 0;
	}
	for (i=0; i < n; i++) {
		for (j=0; j < n; j++) {
			printf("%hu ", a[i][j]);
		}
		puts("");
	}
	return 0;
}
```
But it doesn't make it, output:
```
n: 5
41136 466 0 0 0 
0 0 0 0 0 
0 0 0 0 0 
0 0 0 0 0 
0 0 0 0 0
```
What is wrong? I can't figure it out for the life of me.

---

### Post by jespdj on 2009-05-09
a is a pointer to pointers. This line is wrong:
```
a = malloc(sizeof(short unsigned int) * n);
```
It should have been:
```
a = malloc(sizeof(short unsigned int *) * n);
```

---

### Post by Znupi on 2009-05-09
Oh wow, you are right, never thought of that. Thanks a bunch :)

---

### Post by ad_267 on 2009-05-09
Usually if you want a 2D array you simply use a 1D array that is n*n long.

So to access A(i,j) you use A(i*n + j).

Don't know if that's actually helpful or not but thought I'd point it out.

---

