---
title: "whats wrong with my code"
date: 2012-04-29
forum: Programming Talk
---

### Post by qwertyuu on 2012-04-29
Define 5x5 matrix randomly and pass the matrix to the function then the user defined functin must calculate sum of every column then print smallest sum of column and the result whats wrong with my code


#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <conio.h>
int i1,i2;
int array[5][5];
int *b;
void calsum (int *a);
int main ()
{
    
    srand (time(NULL));
    for (i1=0;i1<5;i1++)
    {
        for(i2=0;i2<5;i2++)
        {
          array[i1][i2]=1+rand()%7;
          printf (" %d ",array[i1][i2]);
        }
        printf ("\n");
    }
    b=&array[0][0];
    calsum (b);
    getch();
}
void calsum (int *a)
{
     int *b,minsum=9999,minsumc,checksum=0;
     for (i1=0;i1<5;i1++)
     {
         b=a+sizeof(int)*i1;
         checksum=0;
        
        for (i2=0;i2<5;i2++)
        { 
          
          checksum+= *(b+sizeof(int)*5*i2);
     
        }
             if (checksum<minsum)
              {
                minsum=checksum;
                minsumc=i1+1;
              }  
         
     }   
     printf("smallest sum is %d in %d'th column",minsum,minsumc);
}

---

### Post by alegomaster on 2012-04-29
Welcome to Ubuntu Forums!

Can you put your code in code tags so it is easier to read.

Just advance edit your post and press the # button and copy and paste your code between the two code words, and it will be in code tags.

I am looking at your code right now

What error did you get?

EDIT: Can you elaborate on your task

---

### Post by r-senior on 2012-04-29
> **qwertyuu said:**
> Define 5x5 matrix randomly and pass the matrix to the function then the user defined functin must calculate sum of every column then print smallest sum of column and the result whats wrong with my code
Welcome to the forum :)

In addition to elaborating on your task, could you also confirm whether you are writing/compiling this on Ubuntu/Linux, or some other platform?

---

### Post by DaviesX on 2012-04-29
> **qwertyuu said:**
> Define 5x5 matrix randomly and pass the matrix to the function then the user defined functin must calculate sum of every column then print smallest sum of column and the result whats wrong with my code

```

#include <stdio.h>
#include <stdlib.h>
#include <time.h>
#include <conio.h>
int i1,i2;
int array[5][5];
int *b;
void calsum (int *a);
int main ()
{
    
    srand (time(NULL));
    for (i1=0;i1<5;i1++)
    {
        for(i2=0;i2<5;i2++)
        {
          array[i1][i2]=1+rand()%7;
          printf (" %d ",array[i1][i2]);
        }
        printf ("\n");
    }
    b=&array[0][0];
    calsum (b);
    getch();
}
void calsum (int *a)
{
     int *b,minsum=9999,minsumc,checksum=0;
     for (i1=0;i1<5;i1++)
     {
         b=a+sizeof(int)*i1;
         checksum=0;
        
        for (i2=0;i2<5;i2++)
        { 
          
          checksum+= *(b+sizeof(int)*5*i2);
     
        }
             if (checksum<minsum)
              {
                minsum=checksum;
                minsumc=i1+1;
              }  
         
     }   
     printf("smallest sum is %d in %d'th column",minsum,minsumc);
}

```


You must be sure it is not your homework, because it is forbidden in this forum. (Just learn that few days ago :( )

---

### Post by DaviesX on 2012-04-29
*(b+sizeof(int)*5*i2) 
Here sizeof ( int ) is unnecessary(just make the code wrong) because compiler knows how many address it should jump over, and here b is the base address, 5*i2 doesn't make any sense
this line has the same problem 
b = a + sizeof(int)*i1;

Last thing is, you shouldn't pass &array[0][0], instead, it ought to be the base address of the first dimension
b = &array[0][0];
calsum (b);

So, it might be
calsum ( array[0] );

---

