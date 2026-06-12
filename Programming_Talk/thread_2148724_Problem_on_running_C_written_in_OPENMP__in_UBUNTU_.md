---
title: "Problem on running C written in OPENMP  in UBUNTU 12.04"
date: 2013-05-26
forum: Programming Talk
---

### Post by tollyfather on 2013-05-26
MY CODE IS BELOW
# include <stdlib.h> 
# include <stdio.h> 
# include <omp.h> 
main(){ 
int i,k,j,a[100][100],b[100][100],c[100][100]; 
int nthreads,maxt,procs,tid,inpar,n; 
       for(i=0;i<100;i++){ 
        for(j=0;j<100;j++){ 
            a[i][j]=rand()%10; 
            b[i][j]=rand()%10; 
        } 
    } 
printf("\n MATRIX A\n\n"); 
    for(i=0;i<100;i++){ 
        for(j=0;j<100;j++){ 
            printf("%d \t",a[i][j]); 
             
        } 
        printf("\n"); 
    } 
    printf("\n MATRIX B\n\n"); 
 
    for(i=0;i<100;i++){ 
        for(j=0;j<100;j++){ 
            printf("%d \t",b[i][j]); 
             
        } 
        printf("\n"); 
    } 
printf("\nENTER THE NUMBER OF THREAD U WANT TO USE:"); 
scanf("%d",&n); 
    printf("\nMULTIPLICATION OF MATRIX A & MATRIX B\n\n"); 
#pragma omp parallel private(nthread,tid,i,j,k){ 
omp_set_num_threads(n) ; 
/* Obtain thread number */ 
tid= omp_get_thread_num(); 
/* Only master thread does this */ 
 
printf("Thread %d getting environment info...\n", tid); 
/* Get environment information */ 
procs = omp_get_num_procs(); 
nthreads = omp_get_num_threads(); 
maxt = omp_get_max_threads(); 
inpar = omp_in_parallel(); 
/* Print environment information */ 
printf("Number of processors = %d\n", procs); 
printf("Number of threads = %d\n", nthreads); 
printf("Max threads = %d\n", maxt); 
printf("In parallel? = %d\n", inpar); 
 
 
     
for(i=0;i<100;i++){ 
        for(j=0;j<100;j++){ 
            for (k=0;k<100;k++){ 
                c[i][j]=a[i][k]*b[k][j]; 
            } 
                } 
            } 
printf("\n"); 
 
 
for( i=0;i<100;i++){ 
for(j=0;j<100;j++){ 
printf("%d\t",c[i][j]); 
} 
printf("\n"); 
} 
        } 
 
     



after trying to run it below is the error that keep pumping up>>>
 
/tmp/ccKib029.o: In function `main':
phundred.c:(.text+0x20a): undefined reference to `omp_set_num_threads'
phundred.c:(.text+0x20f): undefined reference to `omp_get_thread_num'
phundred.c:(.text+0x233): undefined reference to `omp_get_num_procs'
phundred.c:(.text+0x23f): undefined reference to `omp_get_num_threads'
phundred.c:(.text+0x24b): undefined reference to `omp_get_max_threads'
phundred.c:(.text+0x257): undefined reference to `omp_in_parallel'
collect2: ld returned 1 exit status

---

### Post by Mark Phelps on 2013-05-26
You'd get better response in the future if you posted coding problems to the Development and Programming section.

---

### Post by oldos2er on 2013-05-26
Moved to Programming Talk.

---

### Post by r-senior on 2013-05-26
You need to link against the correct libraries by passing the correct options.

See the section here on "Command Line Examples, Linux and Mac OS":

[http://software.intel.com/sites/products/documentation/studio/composer/en-us/2011Update/compiler_c/optaps/common/optaps_par_compat_libs_using.htm](http://software.intel.com/sites/products/documentation/studio/composer/en-us/2011Update/compiler_c/optaps/common/optaps_par_compat_libs_using.htm)

---

### Post by MadCow108 on 2013-05-26
add -fopenmp to your gcc call

---

