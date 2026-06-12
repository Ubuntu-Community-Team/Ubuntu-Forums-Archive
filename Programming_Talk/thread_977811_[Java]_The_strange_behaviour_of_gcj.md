---
title: "[Java] The strange behaviour of gcj"
date: 2008-11-10
forum: Programming Talk
---

### Post by Bichromat on 2008-11-10
Hi,
I was testing java's speed with the following code (2000x2000 matrix product) which outputs the time taken by the operation:
[PHP]class Hello{
   public static void main(String[] args){
      
      int msize=2000;
      
      double[][] A = new double[msize][msize];
      double[][] B = new double[msize][msize];
      double[][] C = new double[msize][msize];
   
      int i, j;
      long t1, t2;
      
      for(i=0 ; i<msize ; i++){
         for(j=0 ; j<msize ; j++){
            A[i][j] = Math.random();
            B[i][j] = Math.random();
            C[i][j] = 0.;
         }
      }
      
      t1 = System.nanoTime();   
      mult(A,B,C);
      t2 = System.nanoTime();
      
      System.out.println(1.e-9 * (t2 - t1));
   
   }
   
   public static void mult(double[][] A, double[][] B, double[][] C){
      int msize = A.length;
      int i,j,k;
      for(i=0 ; i<msize ; i++){
         for(k=0 ; k<msize ; k++){
            for(j=0 ; j<msize ; j++){
               C[i][j] += A[i][k] * B[k][j];
            }
         }
      }
   }
}[/PHP]

Now, if I compile with Sun's javac:
```
$ javac Hello.java
$ java Hello
68.091926583
```
It takes the same time as an unoptimized C version. The executable I get with gcj is a bit faster:
```
$ gcj --main=Hello -O3 Hello.java
$ ./a.out
51.543304147
```
But, if I use gcj-wrapper with Sun's java:
```
$ gcj-wrapper -O3 Hello.java
$ java Hello
17.095693110000003
```
I get a speed close to an optimized C version (compiled with gcc, it takes around 15 s on my machine). gcj-wrapper with gij took so long I stopped the program before completion.

Is this behaviour normal?

---

### Post by Zugzwang on 2008-11-11
> **Bichromat said:**
> Is this behaviour normal?

Good question. I must admit that I cannot find out (by googling) what gcj-wrapper is actually doing. The man page just states that it's a wrapper. Do you have more information on that? Otherwise, it's not *too* likely that you will get good answers on that question here (since I would assume that the rest of use here won't know either).

---

### Post by Bichromat on 2008-11-11
> **Zugzwang said:**
> Good question. I must admit that I cannot find out (by googling) what gcj-wrapper is actually doing. The man page just states that it's a wrapper. Do you have more information on that? Otherwise, it's not *too* likely that you will get good answers on that question here (since I would assume that the rest of use here won't know either).

The only thing I know about gcj-wrapper is that it creates a .class whereas gcj creates a native executable. gcj-wrapper seems to force 'java' to optimize the code.

---

