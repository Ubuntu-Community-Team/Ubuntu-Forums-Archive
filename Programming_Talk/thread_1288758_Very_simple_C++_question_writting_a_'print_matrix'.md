---
title: "Very simple C++ question: writting a 'print matrix' function.."
date: 2009-10-11
forum: Programming Talk
---

### Post by geo909 on 2009-10-11
Hi all,

I am having a hard time writing a function that prints out a matrix (2-dimensional integer array) in c++. Any help would be appreciated.

I wrote the function below:

```

void print_matrix(int* matrix, int rows, int cols){
	for(int i=0; i < rows; ++i){
		for (int j=0; j < cols; ++j){
			cout << matrix[i][j] << " ";
		}
		cout << endl;
	}
}

``` 

I wrote this before the main function. Then I got this when I compiled:
```

assign1.cpp: In function &#8216;void print_matrix(int*, int, int)&#8217;:
assign1.cpp:12: error: invalid types &#8216;int[int]&#8217; for array subscript

```

Ok, so Instead of "int *" I tried "int **" and got no errors.
But then, if I write this:
```

int B[2][3]={{1,2,3},{4,5,6}};
print_matrix(B, 2, 3);

```
inside main, I get the error
```

assign1.cpp: In function &#8216;int main()&#8217;:
assign1.cpp:89: error: cannot convert &#8216;int (*)[3]&#8217; to &#8216;int**&#8217; for argument &#8216;1&#8217; to &#8216;void print_matrix(int**, int, int)&#8217;

```

Could you please light my darkness here? What is the mistake I am doing?
(In fact I think I am right and the compiler is mistaken :) )
How should I pass the 2-dimensional array inside a function?

 
Thanks a lot in advance..

---

### Post by dwhitney67 on 2009-10-11
I think below is the solution you require.  Note the "arithmetic" used to access the array members in the print() function.  Essentially I have linearized the array when I passed it to the function.

```

#include <iostream>

void print(int* array, int rows, int cols)
{
   for (int r = 0; r < rows; ++r)
   {
      for (int c = 0; c < cols; ++c)
      {
         std::cout << array[ (r*rows) + c ] << " ";
      }
      std::cout << std::endl;
   }
}

int main()
{
   int array[2][3] = {{1,2,3}, {4,5,6}};

   print(reinterpret_cast<int*>(array), 2, 3);
}

```

---

### Post by fct on 2009-10-11
Same solution:

```
#include <iostream>
using namespace std;
void print_matrix(int *matrix, int rows, int cols){
        for(int i=0; i < rows; ++i){
                for (int j=0; j < cols; ++j){
                        cout << matrix[i*cols + j] << " ";
                }
                cout << endl;
        }
}
int main(int argc, char **argv)
{
        int B[2][3]={{1,2,3},{4,5,6}};
        print_matrix((int *)&B, 2, 3);
        return 0;
}

```
Normally you would declare your function like this:

void print_matrix(int matrix[][COLS],etc...

But since you're making a function with no known boundaries in either dimension that's a problem.

I have a feeling that the solution that both dwhitney67 and I have for this particular problem might not fly when what you're working with is an int** where you dinamically alloc and free the rows inside, since the memory assigner might make those rows not contiguous in memory and you'd hit wrong memory addresses using the (i*cols + j) conversion.

So be wary if the requirement for the function is handling int ** instead of arrays declared statically.

---

### Post by MadCow108 on 2009-10-11
to answer the original question:
your function head must look like this:
void print_matrix(int matrix[][3], int rows, int cols){

the reason is that a pointer is not the same as an array, although one dimensional arrays implicitly convert to a pointer, this is not the case for two (or higher) dimensional arrays

for that reason you should either use dwhitneys solution or use pointers to simulate arrays (or hardcode the size)

---

### Post by geo909 on 2009-10-12
Hi,

thanks a lot for your replies, that makes sense now.
This:
```
print_matrix(&B[0][0], 2, 3);

```

also worked, I guess it's the same.

Many thanks again

---

