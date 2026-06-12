---
title: "error: expected ‘]’ before ‘:’ token error"
date: 2009-03-11
forum: Programming Talk
---

### Post by lolthisiscool on 2009-03-11
Hi, I am new here as well as towards the C programming language.

I have been getting an error as per the thread's title.

LUdecomposition.c: In function &#8216;main&#8217;:
LUdecomposition.c:56: error: expected &#8216;]&#8217; before &#8216;:&#8217; token
LUdecomposition.c:56: error: expected &#8216;]&#8217; before &#8216;:&#8217; token


The code was copied from another website which makes me rather confused as it should work for most. Anyhow, here's the code. 





// Gaussian Elemination
// 
// Copyright by mpC team, 1999
//
//    [http://www.ispras.ru/~cbr](http://www.ispras.ru/~cbr)
//    [email]mpc@ispras.ru[/email]
//
// Version with variable  matrix size



#include<stdio.h>


void init_matrix(int dim, double (*a) [dim][dim]) {
  int i,j;
  
  for(i=0;i<dim;i++)
    for(j=0;j<dim;j++)
      (*a)[i][j]=10.;

  for(i=0;i<dim;i++) 
     (*a)[i][i]=10. * dim;
}


void print_matrix(int dim,double (*a) [dim][dim]){
  int i,j;
  for(i=0;i<dim;i++) {
    for(j=0;j<dim;j++) 
      printf("%lf\t",(*a)[i][j]);
    printf("\n");
  }
  
}

main()
{
  int N;
  int i,j;

  printf("\nEnter N (matrix dimension): ");
  scanf("%d",&N);

  {
    double A[N][N];

    init_matrix(N,&A);
    printf("\n Source Matrix :\n");
    print_matrix(N,&A);
    
    for(i=0;i<N-1;i++) {
      for(j=i+1;j<N;j++) {
        double t;
	t=A[j][i]/A[i][i];
        if(A[j][i]!=0) A[j][i:N-1]-=t*A[i][i:N-1];
      }
    }
    

    printf("\n Matrix after LU transformation: \n");
    print_matrix(N,&A);
  }
    
}
  
  


Thank you!

---

### Post by sujoy on 2009-03-11
```
if(A[j][i]!=0) A[j][i:N-1]-=t*A[i][i:N-1];
```

array indexes can be integers only or variables that evaluates to integers. 
[i:N-1] is not allowed, ':' is used to slicing in some languages but not in C

---

### Post by lolthisiscool on 2009-03-11
Oh, thank you, but do you have any suggestions on how I can actually amend the code in order to suit that line? 

Once again, thanks.

---

### Post by wmcbrine on 2009-03-11
This isn't C code, despite a superficial resemblance. As it says at the URL in the comments in your example, it's meant to illustrate a feature of a C-derived language called "C[]" (which I'd never heard of before). As such, there is no straightforward translation to C, since the whole point of the example is to show you something you can't do in C.

---

### Post by sujoy on 2009-03-11
> **wmcbrine said:**
> This isn't C code, despite a superficial resemblance. As it says at the URL in the comments in your example, it's meant to illustrate a feature of a C-derived language called "C[]" (which I'd never heard of before). As such, there is no straightforward translation to C, since the whole point of the example is to show you something you can't do in C.

whoa i didnt hope to be surprised in this way :o
eyes can be so misleading !!

---

