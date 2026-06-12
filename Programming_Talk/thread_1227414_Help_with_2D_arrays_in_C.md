---
title: "Help with 2D arrays in C"
date: 2009-07-30
forum: Programming Talk
---

### Post by tom66 on 2009-07-30
I'm not sure how to make a 2D array in C.

```

#include <stdlib.h>

void init_matrix(float*** matrix, int w, int h)
{
	int x, y;
	float** tmpmatrix = (float**)malloc(sizeof(float*) * h);
	
	if( tmpmatrix == NULL ) {
		printf("Couldn't allocate memory for grid, got NULL pointer.\n");
		exit(0);
	}
	
	for( y = 0; y < h; y++ ) {
		/* Allocate row. */
		float* row = (float*)malloc(sizeof(float) * w);
		
		if( row == NULL ) {
			printf("Couldn't allocate memory for row (%d), got NULL pointer.\n", y);
			exit(0);
		}
		
		for( x = 0; x < w; x++ ) {
			row[x] = (y * w) + x;
		}
		
		/* Store row. */
		printf("y = %d\n", y);
		tmpmatrix[y] = &row;
	}
	
	matrix = &tmpmatrix;
}

int main(int argc, char *argv[])
{
	/* Initialize matrix. */
	float** matrix;
	int w = 512, h = 512, x = 0, y = 0;
	init_matrix(&matrix, w, h);
	
	/* Test matrix. */
	for( y = 0; y < h; y++ ) {
		for( x = 0; x < w; x++ ) {
			printf("trying to access %d,%d (y,x)\n", y, x);
			printf("answer=%d\n", matrix[y][x]);
		}
	}
}

```

The code segfaults... I'm not very good with pointers could someone 'point' (no pun intended) me in the right direction?

---

### Post by cb951303 on 2009-07-30
[php]
#include <stdio.h>
#include <stdlib.h>

float **create_matrix(int w, int h)
{
	int i;
	float **matrix;
	
	matrix = (float **)calloc(h, sizeof(float *));
	if(matrix == NULL)
	{
		fprintf(stderr, "Not enough memory!\n");
		exit(1);
	}
	
	for(i = 0; i < h; i++)
	{
		matrix[i] = calloc(w, sizeof(float));
		if(matrix[i] == NULL)
		{
			fprintf(stderr, "Not enough memory!\n");
			exit(1);
		}
	}
	
	return matrix;
}

int main(int argc, char *argv[])
{
	int i, j, h = 9, w = 7;
	float **test = create_matrix(w, h);

	for(i = 0; i < h; i++)
		for(j = 0; j < w; j++)
			fprintf(stdout, "matrix[%d][%d] = %f\n", i, j, test[i][j]);

	return 0;
}
[/php]

here is a simpler and easier to understand method. note that calloc fills the newly created memory with 0 so there is no need to _init_ the array.

---

### Post by tom66 on 2009-07-30
Thanks much-ly, I'll give that code a go.

---

