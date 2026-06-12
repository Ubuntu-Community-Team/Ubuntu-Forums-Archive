---
title: "unusual compiling problem"
date: 2008-07-17
forum: Programming Talk
---

### Post by iofthemourning on 2008-07-17
I'm running Hardy Heron with gcc and build-essentials installed.

I have a C program that includes math.h at the beginning and uses the pow function. pow **WORKS** in the main function but if it is in any other function (absolutely any other), I get a really odd error message when I try to compile:

```
/tmp/ccxeWacg.o: In function 'det':
wah.c:(.text+0x46b): undefined reference to 'pow'
collect2: ld returned 1 exit status
```

What makes this especially frustrating and perplexing is that this code compiled and ran flawlessly on windows with Cygwin.

Has anybody experienced anything like this or know of a solution?

Thanks

-i

---

### Post by samjh on 2008-07-17
Do you mind posting the source so we can try to compile it ourselves?

It looks like a very strange problem.

---

### Post by iofthemourning on 2008-07-17
sure thing.the error comes up in the det function but if I comment out the line in det with pow, it compiles (note: pow is still in main).

```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>



#define MATRIX_NOT_INITIALIZED "Matrix Not Initialized.\n"

#define DISPLAY_SEPARATOR "--------\n"

struct _matrix{

	int rows;

	int cols;

	double* values;

};

typedef struct _matrix matrix;



typedef matrix *matrix_pointer;



matrix_pointer matrix_new(int rows, int columns, double *numbers) {

	int i, j;

	matrix_pointer new_matrix = (matrix_pointer) (malloc(sizeof(matrix)));

	

		new_matrix->values = (double *)(malloc(rows*columns*(sizeof(double))));

		new_matrix->rows=rows;

		new_matrix->cols=columns;

		for(i=0;i<rows;i++) {

				for(j=0;j<columns;j++) {

						new_matrix->values[(i*columns)+j]= numbers[(i*columns)+j];

				}

		}

		return new_matrix;

}





void matrix_display(matrix_pointer matrix, int precision) {

		int i,j;

	

		printf("%s",  DISPLAY_SEPARATOR);

		for(i=0;i<matrix->rows;i++) {

				for(j=0;j<matrix->cols;j++) 	{

						if(j==matrix->cols-1) {

								printf("%.*f\n", precision,matrix->values[(i*matrix->cols)+j]);

						}

						else {

									printf("%.*f, ",precision, matrix->values[(i*matrix->cols)+j]);

						}



				}

		}



}	





void matrix_free(matrix_pointer matrix)

{

	if (matrix==NULL)

		printf(MATRIX_NOT_INITIALIZED);

	if (matrix->values != NULL)

		free(matrix->values);

	

	free(matrix);

}



matrix_pointer matrix_shrink(matrix_pointer matrix, int row, int col){

	int rows=matrix->rows-1;

	int cols=matrix->cols-1;

	matrix_pointer lawl;

	double *nums=malloc(sizeof(double)*((rows)*(cols)));

	int i, j, k=0;

	for (i=0; i<matrix->rows; i++){

		for (j=0; j<matrix->cols; j++){

			if (i!=row && j!=col){

				nums[k]=matrix->values[i*matrix->cols+j];

				k++;

			}

		}

	}

	lawl=matrix_new(rows, cols, nums);

	return lawl;

}



int det(matrix_pointer matrix){

	int sum=0, i;

	matrix_pointer temp;

	if (matrix->rows==2 && matrix->cols==2){

		return matrix->values[0]*matrix->values[3]-matrix->values[1]*matrix->values[2];

	}

	else{

		for(i=0; i<matrix->rows;i++){

			temp=matrix_shrink(matrix, 0, i);

			sum+=(matrix->values[i])*pow(-1,i)*det(temp);

			matrix_free(temp);

		}

		return sum;

	}

		

}

void numbers_read(double *numbers, int length){

	int x;

	for (x=0; x<length; x++){

		if(scanf("%lf", numbers++)!=1){

			printf("error\n");

		}

	}

}


	
int main(void){
	printf("%lf\n", pow(-4,2));
	int i=3, j=3;

	double *nums=malloc(sizeof(double)*i*j);

	numbers_read(nums, i*j);

	matrix_pointer blah=matrix_new(i, j, nums);

	matrix_display(blah,2);

	matrix_display(matrix_shrink(blah, 1, 1),2);

	printf("det: %d\n", det(blah));
	return 0;
}


```

---

### Post by LaRoza on 2008-07-17
Are you linking the the math library?

---

### Post by iofthemourning on 2008-07-17
Thanks roza. I'm used to Cygwin where that isn't necessary. My bad guys. Thanks so much!

-i

---

### Post by LaRoza on 2008-07-17
> **iofthemourning said:**
> Thanks roza. I'm used to Cygwin where that isn't necessary. My bad guys. Thanks so much!

-i

That is alright. It confuses a lot of people. "-lm" isn't really intuitive, but it is needed.

---

