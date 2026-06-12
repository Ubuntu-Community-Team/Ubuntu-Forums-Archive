---
title: "matrix multiplication using threads"
date: 2006-10-26
forum: Programming Talk
---

### Post by lazyme on 2006-10-26
This is a simple program of matrix multiplication using threads.It works on my friends machine using RED HAT 9 but is not executing in Ubuntu.
The result matrix only contains zeroes](*,) 



```
#include<stdio.h>
#include<pthread.h>
#include<unistd.h>
#include<stdlib.h>
#define max 10

int r1,r2,c1,c2,res_mat[max][max],mat1[max][max],mat2[max][max];

void *mult_thread(void *t)
	{
		int i,r,c,tot=0,*rc;
		
		rc=(int *) t;
		r=rc[0];
		c=rc[1];
		
		for(i=0;i<c1;i++)
			{
				tot += mat1[r][i]*mat2[i][c];
			}
		
		res_mat[r][c]=tot;
		return(NULL);
	}

void accept(int mat[max][max], int r,int c)
	{
		int i,j;
				
		for(i=0;i<r;i++)
			for(j=0;j<c;j++)
				{
					printf("\nEnter the value at [%d:%d] : \n",i,j);
					scanf("%d",&mat[i][j]);
				}
		printf("\n");
	}

void display()
	{
		int i,j;
		
		printf("\n");
		for(i=0;i<r1||i<r2;i++)
			{
				for(j=0;j<c1;j++)
					{
						if(i<r1)
						printf(" %d ",mat1[i][j]);
					}
				
				
				if(i==r1/2)
					printf("\t*\t");
				else
					printf("\t\t");
				for(j=0;j<c2;j++)
					{
						if(i<r2)
						printf(" %d ",mat2[i][j]);
					}
				
				if(i==r1/2)
					printf("\t=\t");
				else
					printf("\t\t");
					
				for(j=0;j<c2;j++)
					{
						if(i<r1)
						printf(" %d ",res_mat[i][j]);
					}
					
				printf("\n");
			}
		printf("\n");
	}
	

int main(void)
	{
		int i,j,rc[2];
		pthread_t p[max][max];
				
		printf("\nEnter the number of rows for first matrix : \n");
		scanf("%d",&r1);
		printf("\n");
		
		printf("\nEnter the number of rows for first matrix : \n");
		scanf("%d",&c1);
		printf("\n");
		
		accept(mat1,r1,c1);
		
		printf("\nEnter the number of rows for second matrix : \n");
		scanf("%d",&r2);
		printf("\n");
		
		printf("\nEnter the number of rows for second matrix : \n");
		scanf("%d",&c2);
		printf("\n");
		
		accept(mat2,r2,c2);

		
		if(c1==r2)
			{
				for(i=0;i<r1;i++)
					for(j=0;j<c2;j++)
						{
							rc[0]= i;
							rc[1]= j;
							pthread_create(&p[i][j],NULL,mult_thread,rc);
						}
			}

		display();
		
		return 1;
	}
```

Execution
> 
gcc thread.c -l pthread


Is there anything i'm doing wrong?

---

### Post by shining on 2006-10-26
IIRC, linuxthreads were removed recently in ubuntu. NPTL seems to be the way to go.
I don't have any experience with linuxthreads or NPTL though, so I can't help you there, but I doubt it'll be hard to port your code.

---

### Post by lazyme on 2006-10-26
Well any way to override this?

---

### Post by amo-ej1 on 2006-10-27
NPTL and linuxthreads have nothing to do with this since they operate on way lower levels. It is glibc that performs the abstraction.

---

### Post by amo-ej1 on 2006-10-27
The issue you are experiencing is nothing more than synchronisation. What you do is like

```

READ THEM
PTHREAD_CREATE
PTHREAD_CREATE
PTHREAD_CREATE
PTHREAD_CREATE
PTHREAD_CREATE
PTHREAD_CREATE
PTHREAD_CREATE
PTHREAD_CREATE
PTHREAD_CREATE
PTHREAD_CREATE
DISPLAY
                    SWITCH_TO_THREAD_1

```

Display should wait until all other threads have finished. Because it is possible that your results get printed even before one of the worker threads is started.  The reason why it works on some of your friends red hat boxes is just luck ;)

---

### Post by lazyme on 2006-10-27
Just added sleep(1)
```
pthread_create(&thr[i][j],NULL,mult_thread,rc); 
sleep(1);
```
and the code is working now:o. Thanks for the help guys.;)

---

### Post by shining on 2006-10-27
> **amo-ej1 said:**
> NPTL and linuxthreads have nothing to do with this since they operate on way lower levels. It is glibc that performs the abstraction.

Oops, sorry for the totally wrong information, I may as well shut up next time :)
Though, I'm sure I heared about troubles with linuxthreads vs nptl, but don't remember what were the problems exactly.

> **amo-ej1 said:**
> 
Display should wait until all other threads have finished. Because it is possible that your results get printed even before one of the worker threads is started.  The reason why it works on some of your friends red hat boxes is just luck ;)

Oh indeed, there was an obvious race there, I suck :)

> **lazyme said:**
> Just added sleep(1)
```
pthread_create(&thr[i][j],NULL,mult_thread,rc); 
sleep(1);
```
and the code is working now:o. Thanks for the help guys.;)

Well, indeed that works, but I think it's really ugly.
I hope there are better way to synchronize threads than that. Or am I wrong again?

---

### Post by Eric_T on 2006-10-29
I've never used threads, but I do program for parallel machines, and there
you have a barrier function that basically makes every process wait until
all the other processes have called the barrier function.
A google search on pthread barrier turned up a function called "pthread_barrier_wait". I guess that's what you're looking for...
[http://sourceware.org/pthreads-win32/manual/pthread_barrier_wait.html](http://sourceware.org/pthreads-win32/manual/pthread_barrier_wait.html)

---

### Post by amo-ej1 on 2006-10-29
noooooooooooooooooooooooooooooo 

running sleep(1) here won't solve your problem, if any of the other threads will take more processing time than one second you program will fail again.

The quickest way to solve this is by allocating a shared 'count' variable and have each worker drone increment this 'count' while you have you main thread in a tight

```

while(counter != NUM_THREADS){}

```

loop (called busy waiting). The more decent way to do so would be by using counting semaphores or perhaps pthread signals to notify the printer each time a thread has ended, or you could use pthread_join to wait for all other threads to have finished. Hmmz ain't concurrency great ? ;)

---

### Post by EVIL_GEEK on 2006-11-07
here is a version that generates two pseudo random square  matrices and multiplies them.  I borrowed some you guys' code.  I hope you can use this too.  The program has decent example of common pthread routines.   

#include<stdio.h>
#include<pthread.h>
#include<unistd.h>
#include<stdlib.h>
#define max 10

#define MX_SZ 10           	    /* maxium size */
#define MX_THREADS MX_SZ*MX_SZ  /* maximum number of threads */
#define SEED 2397           	/* random number seed */

pthread_mutex_t mutex1;

int size,A_matrix[max][max],B_matrix[max][max],C_matrix[max][max];
int global_row,global_column;


void *mult_thread(void *t) {
   int i,row,col,tot=0,*rc;
   pthread_mutex_lock(&mutex1);
      row=global_row;
      col=global_column;
      global_column++;
      if(global_column==size) {
      	 global_column=0;
         global_row++;
         if(global_row==size) {
            global_row=0;
         }
      }
   pthread_mutex_unlock(&mutex1);

   for(i=0;i<size;i++)  tot += A_matrix[row][i]*B_matrix[i][col];
   C_matrix[row][col]=tot;	
   return(NULL);
}

void fill_matrix(int matrix[max][max], int size, int seed) {
   int i,j;				
   for(i=0;i<size;i++)
      for(j=0;j<size;j++)  {
         matrix[i][j]=rand()/10000000;
      }
}

void display() {
   printf("\n");
   int i,j; 
   for(i=0;i<size;i++) {
	  /* print A_matrix */
      for(j=0;j<size;j++)  if(i<size) printf(" %d ",A_matrix[i][j]);
      if(i==size/2) printf("\t*\t");
      else printf("\t\t");

	  /* print B_matrix */
      for(j=0;j<size;j++) if(i<size) printf(" %d ",B_matrix[i][j]);
      if(i==size/2) printf("\t=\t");
      else printf("\t\t");

      /* print C_matrix */
      for(j=0;j<size;j++)  if(i<size) printf(" %d ",C_matrix[i][j]);
      printf("\n");
    }
    printf("\n");
}
	

int main(void)  {
   int i,j,rc[2];
   global_row=0;
   global_column=0;

   pthread_t p[max][max];
   pthread_mutex_init(&mutex1,NULL);
				
   printf("\nEnter the dimension of the matricies : ");
   scanf("%d",&size);
   int seed1 = SEED;
   int seed2 = seed1*exp(1);
   fill_matrix(A_matrix,size, seed1);
   fill_matrix(B_matrix,size, seed2);
		

   for(i=0;i<size;i++)
      for(j=0;j<size;j++)  {
	 if( pthread_create(&p[i][j],NULL,mult_thread,NULL) != 0)
	     perror("Pthread_create failed");
      }

   for(i=0;i<size;i++)
      for(j=0;j<size;j++)  {
	 if( pthread_join(p[i][j],NULL) != 0)
	     perror("Pthread_join failed");
      }

   display();
   return 1;
}

---

### Post by Ahmadasd on 2011-11-12
Hi all,
all of previous work are so helpful so thanks a lot 
but I have a question: how to print out the thread id for each thread created in the previous program
any helpful notes will be appreciated

---

