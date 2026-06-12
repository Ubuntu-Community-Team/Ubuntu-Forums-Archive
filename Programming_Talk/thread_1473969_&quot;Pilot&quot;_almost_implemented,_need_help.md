---
title: "&quot;Pilot&quot; almost implemented, need help"
date: 2010-05-05
forum: Programming Talk
---

### Post by jukzh on 2010-05-05
Hi! Pilot drops stones into given areas, to find how many of them are delivered into the area. First is (3) number (in INPUT.TXT)of lines, next two first nums on each row is x,y position of stone, and others are x,y are corners of the given area, how to check for stone which fell into 4,8 for instance or 7,5 marked # in the graph. So I've done part which I know, now I'm stuck and asking for direction, not just asking to do for me homework.
[PHP]/*INPUT.TXT	
  3
  6 6 3 6 6 9 8 7 5 4
  13 5 9 2 9 8 12 8 12 2
  3 2 2 1 2 3 6 3 6 1	
  OUTPUT.TXT
  2 
 +-------------------------+
 |10   |     |   |         |
 |9----|----.o.--|---      |
 |8    | #.`   `.|         |
 |7-----.`       o---      |
 |6----o     x .`|         |
 |5    |`.   .`# |         |
 |4----|--`o`|---|---      |
 |3    |   | |   |         |
 |2    |   | |   |         |
 |1    |   | |   |         |
 |+1-2-3-4-5-6-7-8-9-10-11-|
 +-------------------------+
  6 6 3 6 6 9 8 7 5 4

 +-------------------------------+
 |13                             |
 |12                             |
 |11                             |
 |10                             |
 |9                              |
 |8----------------o--------o    |
 |7                |        |    |
 |6                |        |    |
 |5----------------|--------|--x |
 |4                |        |  | |
 |3                |        |  | |
 |2----------------o--------o  | |
 |1                |        |  | |
 |+1-2-3-4-5-6-7-8-9-10-11-12-13-|
 +-------------------------------+
  13 5 9 2 9 8 12 8 12 2

 +-------------------------+
 |10                       |
 |9                        |
 |8                        |
 |7                        |
 |6                        |
 |5                        |
 |4  |       |             |
 |3--o-------o---          |
 |2  | x     |             |
 |1--o-------o---          |
 |+1-2-3-4-5-6-7-8-9-10-11-|
 +-------------------------+
  3 2 2 1 2 3 6 3 6 1*/
#include <stdio.h>
#define S 1000
#define MAX(a,b) a >= b ? a : b
#define MIN(a,b) a <= b ? a : b
int Yes=0;
int main() {
 int line[S][11],n,i,j,x[S],y[S],k[S][5],l=0,m[S][5];
 int minK[S],minM[S],maxK[S],maxM[S];
 freopen("INPUT.TXT","r",stdin);
 freopen("OUTPUT.TXT","w",stdout);
 scanf("%d",&n);
 for(i=0;i<n;i++) {
  for(j=0;j<10;j++) {
   scanf("%d ",&line[i][j]);
  } 
 }

 for (i=0;i<n;i++) {
       x[i]=line[i][0];
       y[i]=line[i][1];
       //printf("%d %d\n",x[i],y[i]);
 }

 for (i=0;i<n;i++) {
      l=0;
      for (j=2;j<10;j+=2,l++) {
           k[i][l]=line[i][j];
           //printf("%d ",k[i][l]);
      } 
      //puts("");
 }
 for (i=0;i<n;i++) {
      l=0;
      for (j=3;j<10;j+=2,l++) {
           m[i][l]=line[i][j];
           //printf("%d ",m[i][l]);
      }
      //puts("");
 }

 for (i=0;i<n;i++) {
      minK[i]=k[i][0];
      maxK[i]=k[i][0];
      minM[i]=m[i][0];
      maxM[i]=m[i][0];
  }
 
 for (i=0;i<n;i++) {
  for (j=0;j<l;j++) {
   if (minK[i] >= k[i][j]) 
       minK[i]=k[i][j];
   if (maxK[i] <= k[i][j])
       maxK[i]=k[i][j];
   if (minM[i] >= m[i][j])
       minM[i]=m[i][j];
   if (maxM[i] <= m[i][j])
       maxM[i]=m[i][j];
  } 
 }
 
 for (i=0;i<n;i++) {
  printf("%d %d\t(%d,%d)\t%d %d\n",minK[i],minM[i],x[i],y[i],maxK[i],maxM[i]);
  if (x[i] > minK[i] && y[i] > minM[i] && x[i] < maxK[i] && y[i] < maxM[i]) 
      Yes++;
 }

 printf("%d\n",Yes);

return 0;
}
[/PHP]

---

### Post by MindSz on 2010-05-05
Well, from the example, it seems the points are always given in the same order, so you know where the "outside" is. Go from there :)

---

### Post by jukzh on 2010-05-05
> **MindSz said:**
> Well, from the example, it seems the points are always given in the same order, so you know where the "outside" is. Go from there :)
```
1 &#8804; n &#8804; 1000
```
And abs values of x,y positions are less than 50000
that is just 3 examples of 10 random tests.

---

### Post by MindSz on 2010-05-06
Then I'd start by having a small function that tells me the "order" of the points that you're given. Once you know which point correspond to each corner, it'll be a lot easier to determine what's inside the area.

---

### Post by PaulM1985 on 2010-05-06
It looks from the inputs that the points are ordered in a clockwise direction.

Given you know the points in an order, you should be able to define edges of the area.  Then compare if things are inside or outside that area.

Have you heard of "cross products"? If not, have a look, this might help you in solving your problem.

Paul

---

### Post by jukzh on 2010-05-07
> **PaulM1985 said:**
> It looks from the inputs that the points are ordered in a clockwise direction.

Given you know the points in an order, you should be able to define edges of the area.  Then compare if things are inside or outside that area.

Have you heard of "cross products"? If not, have a look, this might help you in solving your problem.

Paul
Yeah, I'm able to find edges now, but that is still not good enough. If for instance we increase all numbers by 1000 it goes wrong, I don't know.
[PHP]/*INPUT.TXT	
  3
  6 6 3 6 6 9 8 7 5 4
  13 5 9 2 9 8 12 8 12 2
  3 2 2 1 2 3 6 3 6 1	
  OUTPUT.TXT
  2
 *******************************************    
 |                              
 |10                         
 |9----+-----.---+          
 |8    | # .` `. |
 |7    | .`     `.          
 |6----.`    @ .`|          
 |5    |`.   .`# |          
 |4----+--`.`+---+          
 |3    |   | |   |           
 |2    |   | |   |               
 |1    |   | |   |           
 |+1-2-3-4-5-6-7-8-9-10-11- 
 +--------------------------------------
  <6 6> 3 6, 6 9, 8 7, 5 4
 *******************************************   
 |                                 
 |13                              
 |12                              
 |11                              
 |10                              
 |09                               
 |08-------------------------+========+
 |07                         |        |
 |06                         |        |
 |05-------------------------+--------+--@
 |04                         |        |  |
 |03                         |        |  |
 |02-------------------------+========+  |
 |01                         |        |  |
 |  01-02-03-04-05-06-07-08-09-10-11-12-13- 
 +--------------------------------------
  <13 5> 9 2, 9 8, 12 8, 12 2
 ******************************************* 
 |11----------------+--------.-----+------
 |10----------------+  X  X.` `.X  +------
 |9-----------------+  X .`     `. +------
 |8-----------------+  .`        .`+------
 |7-----------------+.`        .`  +------
 |6-----------------+ `.     .` X  +------
 |5-----------------+  X`. .`X  X  +------
 |4-----------------+--+--`--+--+--+------
 |3-----+===========+--+--+--+--+--+------
 |2-----+--@--------+--+--+--+--+--+------
 |1-----+===========+--+--+--+--+--+------
 |0 01-02-03-04-05-06-07-08-09-10-11-12-13-14-15-16
 +--------------------------------------
  <3 2> 2 1, 2 3, 6 3, 6 1
 *******************************************/
  
#include <stdio.h>
#define S 1000 
#define MAX(a,b) a >= b ? a : b
#define MIN(a,b) a <= b ? a : b
int Yes=0;
int paral[S];
int Inx[S];
int Iny[S];
int main() {
 int line[S][11],n,i,j,x[S],y[S],k[S][5],l=0,m[S][5],minK[S],minM[S];
 int maxK[S],maxM[S],adx[S][sizeof(int)],ady[S][sizeof(int)], lenx[S],leny[S];
 freopen("INPUT.TXT","r",stdin);
 freopen("OUTPUT.TXT","w",stdout);
 scanf("%d",&n);
 for(i=0;i<n;i++) {
  Inx[i]=0;
  Iny[i]=0;
  for(j=0;j<10;j++) {
   scanf("%d ",&line[i][j]);
  } 
 }

 for (i=0;i<n;i++) {
       x[i]=line[i][0];
       y[i]=line[i][1];
       //printf("%d %d\n",x[i],y[i]);
 }

 for (i=0;i<n;i++) {
      l=0;
      for (j=2;j<10;j+=2,l++) {
           k[i][l]=line[i][j];
           //printf("%d ",k[i][l]);
      } 
      //puts("");
 }
 for (i=0;i<n;i++) {
      l=0;
      for (j=3;j<10;j+=2,l++) {
           m[i][l]=line[i][j];
           //printf("%d ",m[i][l]);
      }
      //puts("");
 }

 for (i=0;i<n;i++) {
      minK[i]=k[i][0];
      maxK[i]=k[i][0];
      minM[i]=m[i][0];
      maxM[i]=m[i][0];
  }

 for (i=0;i<n;i++) {
     paral[i]=0;
     lenx[i]=0;
     leny[i]=0;
     if (k[i][0] == k[i][1] || k[i][1] == k[i][2] || k[i][2] == k[i][3])
         paral[i]=1;
     if (!paral[i]) {/* printf("%d not paral\n",i); */
      for (j=0;j<l;j++) {
       int e;
       if (k[i][j] < k[i][j+1]) {
        for (e=k[i][j]+1;e<k[i][j+1];e++)
             adx[i][lenx[i]++] = e;
       } else {
        for (e=k[i][j]-1;e>k[i][j+1];e--)
             adx[i][lenx[i]++] = e;
       }
       int f;
       if (m[i][j] < m[i][j+1]) {
       for (f=m[i][j]+1;f<m[i][j+1];f++)
            ady[i][leny[i]++] = f;
       } else {
        for (f=m[i][j]-1;f>m[i][j+1];f--)
             ady[i][leny[i]++] = f;
       }
      }
     }
 }
 
 for (i=0;i<n;i++) {
  for (j=0;j<l;j++) {
   if (minK[i] >= k[i][j]) 
       minK[i]=k[i][j];
   if (maxK[i] <= k[i][j])
       maxK[i]=k[i][j];
   if (minM[i] >= m[i][j])
       minM[i]=m[i][j];
   if (maxM[i] <= m[i][j])
       maxM[i]=m[i][j];
  } 
 }
 
 for (i=0;i<n;i++) {
     if (paral[i]) {
      if (x[i] > minK[i] && y[i] > minM[i] && x[i] < maxK[i] && y[i] < maxM[i])
          Yes++;
     } else {
       for (j=0;j<lenx[i];j++) {
            if (x[i] < adx[i][j]) Inx[i]=1;
            /*printf("%d ",adx[i][j]);
       puts("");*/
       }
       for (j=0;j<leny[i];j++) {
            if (y[i] < ady[i][j]) Iny[i]=1;
            /*printf("%d ",ady[i][j]);
       puts("");*/
       }
      if (x[i] > minK[i] && y[i] > minM[i] && x[i] < maxK[i] && y[i] < maxM[i]
          && Inx[i] && Iny[i]) Yes++;
     }
 }
 printf("%d\n",Yes);

return 0;
}

[/PHP]

---

### Post by jukzh on 2010-05-07
Ok, I gave up and here friend of mine gives me implementation:
[http://paste.ubuntu.com/429580/]("http://paste.ubuntu.com/429580/")

---

