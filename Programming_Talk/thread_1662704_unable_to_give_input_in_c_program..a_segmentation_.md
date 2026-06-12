---
title: "unable to give input in c program..a segmentation fault occurs"
date: 2011-01-08
forum: Programming Talk
---

### Post by Gopal Mondal on 2011-01-08
[SIZE=2][COLOR=Red]hello,
I am learning C.
I have a problem..
I have written a program,but input.it gives segmentaion fault after giving some input..
I have checked it many times.but did not find any problem.
I am using cc compiler[/COLOR][/SIZE][SIZE=2].[/SIZE]

[SIZE=4][COLOR=Blue]#include<stdio.h>
#include<stdlib.h>
main()
{
  int **a,**b;
  int i,j,m,n,k,l;
  printf("**************creating matrix****************\n");
  printf("please enter the row number\n");
  scanf("%d",&m);
  printf("please enter the column number\n");
  scanf("%d",&n);
  if(!(a=(int**)malloc(sizeof(int)*m)))
    {
      printf("memory unavailable for row\n");
      exit(0);
    }
  if(!(*a=(int*)malloc(sizeof(int)*n)))
    {
      printf("memory unavailable for column\n");
      exit(0);
    }
  printf("please enter the value in matrix\n");
  for(i=0;i<m;i++)
    for(j=0;j<n;j++)
      scanf("%d",&a[i][j]);
  printf("your entered matrix is\n");
  for(i=0;i<m;i++)
    {
      for(j=0;j<n;j++)
    printf("%d",a[i][j]);
      printf("\n");
    }
  l=count(a,m,n);
  if(l>((m*n)/2))    //condition for deciding a sparse matrix
    {
      printf("this is not a sparse matrix\n");
      exit(0);
     }
[/COLOR][/SIZE][SIZE=4][COLOR=Blue]     printf("this is a sparse matrix\n");
      k=0;[/COLOR][/SIZE]
[SIZE=4][COLOR=Blue]  b=(int**)malloc(sizeof(int)*l);
  *b=(int*)malloc(sizeof(int)*3);
  for(i=0;i<m;i++)
    {
      for(j=0;j<n;j++)
    {
      if(a[i][j]!=0)
        {
          b[k][0]=i;
          b[k][1]=j;
          b[k][2]=a[i][j];
          k++;
        }
    }
    }
  printf("now its converted in sparse matrix\n");
  for(i=0;i<l;i++)
    {
      for(j=0;j<3;j++)
    printf("%d",b[i][j]);
      printf("\n");
    }
}
int count (float **b,int m,int n)
{
  int q=0,i,j;
  for(i=0;i<m;i++)
    for(j=0;j<n;j++)
      if(b[i][j]!=0)
    q++;
  return q;
}[/COLOR][/SIZE]

---

### Post by MadCow108 on 2011-01-08
you only allocate memory for one row
do something like this (pseudocode):
```

// get n and m
mat = malloc(sizeof(int*) * n);
for (i in 1..m)
  mat[i] = malloc(sizeof(int) * m
...

```

or linearize it:
```

mat = malloc(sizeof(int) * m * n)
val = mat[i % m +j];

```

---

### Post by worksofcraft on 2011-01-08
hint:

You need to allocate memory for all the rows... (not just one) and you need to save the pointer to each row in the array of columns, which has elements the size of pointers and not of ints.

---

### Post by Gopal Mondal on 2011-01-09
thank you..it works....

---

