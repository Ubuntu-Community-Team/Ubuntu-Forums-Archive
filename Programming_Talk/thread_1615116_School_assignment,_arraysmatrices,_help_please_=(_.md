---
title: "School assignment, arrays/matrices, help please =( (again)"
date: 2010-11-06
forum: Programming Talk
---

### Post by VanillaCone on 2010-11-06
i need to transpose a matrix, my function returns my matrix as 

0 0 0 0 
0 0 0 0 
0 0 0 0 

when the inputted matrix is 
1 2 3 4
1 2 3 4
1 2 3 4

[PHP] void transpose (int ***A, int m, int n)

{
   int i;
   int j;
   int **matrix = createMatrix(m, n);

   while (j<n)
    {
        for (i = 0; i < m; i++)
        {
        matrix[j][i]= *A[i][j];
        }
            j++;
        }

    freeMatrix(*A, m, n);


    *A=matrix;



    return;
}
[/PHP]

also it wont ALWAYS be a square matrix.

---

### Post by worksofcraft on 2010-11-06
> **VanillaCone said:**
> i need to transpose a matrix, my function returns my matrix as 

0 0 0 0 
0 0 0 0 
0 0 0 0 

when the inputted matrix is 
1 2 3 4
1 2 3 4
1 2 3 4

[PHP] void transpose (int ***A, int m, int n)

{
   int i;
   int j;
   int **matrix = createMatrix(m, n);

   while (j<n)
    {
        for (i = 0; i < m; i++)
        {
        matrix[j][i]= *A[i][j];
        }
            j++;
        }

    freeMatrix(*A, m, n);


    *A=matrix;



    return;
}
[/PHP]

also it wont ALWAYS be a square matrix.

Well we were told on your last thread not to actually do your assignment for you. So I just a give you a hint...

where you say
```

while (j<n) 

```

What value do you think j has when your program arrives at that while statement ?

---

### Post by holiday on 2010-11-06
> **worksofcraft said:**
> Well we were told on your last thread not to actually do your assignment for you. So I just a give you a hint...

where you say
```

while (j<n) 

```

What value do you think j has when your program arrives at that while statement ?

Dayum! I'm glad you spoke up. I was going to tell him.

You're busted, Vanilla Cone.

---

### Post by VanillaCone on 2010-11-06
SOLVED

[PHP]void transpose (int ***A, int m, int n)

{
   int i;
   int j;
   int **matrix = createMatrix(m, n);

   for(j = 0; j<n; j++)
    {
        for (i = 0; i < m; i++)
        {
        matrix[j][i]= (*A)[i][j];
        }

        }

    freeMatrix(*A, m, n);


    *A=matrix;

}[/PHP]

yes j should = 0, but that wasnt why it wasnt working, *A apparantly needs to be (*A). And Im not asking you to solve my assignments, this wasnt a problem Where i needed to logically work through a problem and find a result, this was just a syntax error That i was not aware Of because ive been doing C for 2 Months... So sue me if i ask for help

---

### Post by holiday on 2010-11-06
My bad.

---

### Post by worksofcraft on 2010-11-06
> **VanillaCone said:**
> SOLVED
...
yes j should = 0, but that wasnt why it wasnt working, *A apparantly needs to be (*A).




Kewl :) I must admit I also get a bit confused when I see things like int ***A

let's hope they don't get you to do 3 (or more) dimensional arrays next ;)

What I tend to do is make them into one dimensional arrays and then index with a calculation:

[php]
int * A = malloc(sizeof(int)*m*n);

for (i = 0; i < m; ++i) {
    for (j = 0; j < n; ++j) {
        A[n*i + j] = ...
    }
}
[/php]
but that's probably just because I think of the whole of memory as a single big long one dimensional array anyway :shock:

---

### Post by VanillaCone on 2010-11-06
that whole ***A business was just confusing :(, a pointer to a pointer that Points to a block Which points to Specific columns ><

---

